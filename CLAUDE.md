# Fork MickaelFioretti/spotifast

Ce dépôt est un fork personnel de `crmne/spotifast`. `AGENTS.md`, que
Claude Code charge déjà, reste la référence pour le code, l'architecture et les tests. Les règles
ci-dessous le complètent et **remplacent** ses sections *Branches*,
*Releases* et *Issue communication*, qui décrivent le dépôt officiel.

## Langue

- Réponses en français.
- Code, commentaires, messages de commit et notes de release en anglais,
  dans le style du dépôt officiel.

## Branches

- `upstream` = `https://github.com/crmne/spotifast.git`, `origin` = le fork.
- `main` est une copie exacte de `upstream/main`. Uniquement des
  fast-forwards (`git merge --ff-only upstream/main`), jamais de commit
  du fork dessus.
- `fork` = `main` + l'outillage du fork + les fonctionnalités terminées.
  Les tags de release partent de `fork`.
- Une fonctionnalité = une branche `feat/<nom>` partie de `fork`. Pour
  l'intégrer : rebase sur `fork`, CI vert, puis fast-forward de `fork`.
  Jamais de commit de merge, nulle part.
- Un sujet par commit. L'outillage du fork (updater, signature, workflow
  de release, ce fichier) reste dans des commits séparés des
  fonctionnalités, pour que les conflits de rebase soient lisibles.

## Mise à jour depuis l'officiel

1. `git fetch upstream --no-tags`, puis fast-forward de `main` sur
   `upstream/main`. Les tags de l'officiel portent les mêmes noms que ceux
   du fork (`v0.13.0`) : n'en importer aucun, et ne jamais pousser avec
   `--tags`.
2. Branche de sauvegarde avant de réécrire :
   `git branch backup/fork-<version> fork`.
3. `git rebase main` sur `fork`, puis sur chaque `feat/*` en cours.
4. Si l'officiel a intégré une fonctionnalité du fork, retirer la copie du
   fork plutôt que de garder les deux.
5. Lancer le CI du fork sur la branche (voir *Vérification*) et attendre
   qu'il soit vert.
6. Push avec `git push --force-with-lease=<branche>:<sha attendu> origin <branche>`,
   jamais `--force` seul. Vérifier avant qu'aucun commit de merge n'est ajouté.

## Vérification

- Ce PC n'a pas de toolchain Rust : la compilation et les tests passent par
  le CI du fork, `fork-ci.yml` (Windows x64 et Linux x64 seulement). Il se
  lance seul à chaque push sur `fork`, `feat/**` et `update/**`.
- Le `ci.yml` de l'officiel reste tel quel dans le dépôt, pour ne pas créer
  de conflits au rebase, mais il est désactivé sur GitHub. macOS et
  Windows ARM ne sont donc plus compilés du tout.
- `fork` est la branche par défaut du dépôt GitHub : seuls ses pushs
  enregistrent le cache, que les autres branches réutilisent.
- Vérifier que le run teste bien le dernier commit poussé.
- Ne jamais dire qu'une plateforme est testée si elle a seulement été
  compilée par le CI ou raisonnée.

## Releases du fork

Elles remplacent la section *Releases* d'`AGENTS.md` : pas de site web,
Homebrew, AUR, Flatpak ni macOS pour ce fork.

1. Le tag doit être **supérieur** à la version installée, sinon l'updater
   ne propose rien. Il suit la version de l'officiel sur laquelle `fork`
   est basée (`v0.13.0`, etc.). Une release du fork entre deux versions
   officielles prend le patch suivant (`v0.13.1`). Si l'officiel sort
   ensuite ce même numéro, la release du fork basée dessus prend le numéro
   libre suivant (`v0.13.2`), toujours au-dessus de la dernière release du
   fork. La version de `Cargo.toml` doit correspondre au tag.
2. Notes dans `packaging/release-notes/fork-vVERSION.md` (le préfixe
   `fork-` évite d'écraser les notes de l'officiel) : résumé court, `New`,
   limites connues, `Thanks`, lien de changelog. Créditer les auteurs des
   fonctionnalités reprises et renvoyer aux notes officielles plutôt que de
   les recopier.
3. Le workflow ne construit que Windows x64 et Linux x64. Push du tag
   `v*` → release GitHub. Vérifier ensuite que `checksums.txt` et
   `checksums.txt.sig` sont publiés.

## Mises à jour signées

- L'updater (`src/updates.rs`) vérifie les releases de
  `MickaelFioretti/spotifast` avec la clé publique du fork dans
  `assets/update-public-key.hex`. Si l'officiel modifie ce fichier, garder
  la clé du fork.
- La clé privée est dans le secret GitHub `SPOTIFAST_UPDATE_SIGNING_KEY`
  et dans `~/.config/spotifast-fork/`. Ne jamais la lire, l'afficher, la
  copier dans le dépôt ni la passer en argument d'une commande.

## Quota du Web API Spotify

Un incident a déjà consommé environ 10 000 appels en une journée (interrogation
toutes les 4 s au lieu de 15).

- Ne jamais descendre l'interrogation régulière de l'état de lecture sous
  `REMOTE_POLL_MIN` (15 s), ni ajouter d'appel en boucle ou de retry sans
  plafond.
- Signaler explicitement tout nouvel appel au Web API dans une
  fonctionnalité et préférer la session librespot quand elle sert la même
  donnée.
- Les tests ne doivent jamais appeler le vrai Web API ni utiliser de vrais
  identifiants.

## Façon de travailler

- Avancer étape par étape et faire le point à chaque étape.
- Demander avant tout push, tag ou release.

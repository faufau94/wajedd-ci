# wajedd-ci

Verification de compilation iOS pour l'application Wajedd.

Ce depot ne contient pas de code applicatif : il porte uniquement un
workflow GitHub Actions et une reference (submodule `app/`) vers le depot
prive ou vit le code.

## Pourquoi un depot public

Les runners macOS standards sont gratuits et sans limite de minutes dans
un depot public. Dans un depot prive ils consomment le quota a 10x le taux
Linux, soit environ 200 minutes macOS par mois sur le palier gratuit.

Ce depot ne fait donc que ce qui peut l'etre sans risque :

| | ou | quoi |
|---|---|---|
| Verification | ici, depot public | `flutter analyze`, `flutter test`, compilation **sans signature** |
| Livraison | Codemagic, depot prive | compilation **signee** + envoi TestFlight |

## Ce qui n'est volontairement pas ici

Aucun certificat de signature, aucun profil de provisioning, aucune cle
API App Store Connect, aucun IPA signe en artefact. Les artefacts d'un
depot public sont telechargeables par n'importe qui.

Le seul secret utilise est `APP_REPO_TOKEN`, en lecture seule sur le depot
prive, necessaire pour cloner le submodule. GitHub garantit qu'une pull
request ouverte depuis un fork n'a jamais acces aux secrets.

## Limite assumee

Les logs d'execution sont publics. Une erreur de compilation peut afficher
des extraits du code source. C'est le prix des minutes gratuites, et la
raison pour laquelle la signature n'est pas faite ici.

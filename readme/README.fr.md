# SoftwareLogBook

## Langues
- Anglais (par defaut)
- [Deutsch](README.de.md)
- [Español](README.es.md)
- [Français](README.fr.md)
- [日本語](README.ja.md)

SoftwareLogBook est un journal pour les systemes logiciels utilisant des fichiers Markdown avec frontmatter YAML.

## Motivation et perimetre
SoftwareLogBook documente les outils logiciels, leurs deploiements et les evenements du cycle de vie dans un format lisible et verifiable sans outils speciaux.

Pourquoi fichiers + Markdown + Git :
- Le texte brut est facile a lire, a comparer et a relire.
- Git apporte l'historique, la tracabilite et la discipline append-only.
- La structure reste utilisable dans des environnements peu outilles.

Scenarios vises :
- Inventaires petits a moyens d'outils internes ou de fournisseurs.
- Equipes qui veulent un lieu unique et auditable pour les releases, incidents et notes de maintenance.
- Environnements ou un journal leger base sur un depot suffit.

Ce que ce n'est pas :
- Pas une CMDB.
- Pas un systeme de tickets.
- Pas un systeme de monitoring.

## Concepts centraux (haut niveau)
- Software : un enregistrement qui decrit un outil et son contexte de responsabilite.
- Deployment : une instance installee d'un outil logiciel dans un environnement.
- Entry : un enregistrement d'evenement en append-only (par ex., release, incident, maintenance).
- Global entry : un evenement ou une politique qui s'applique a tous les outils.
- Corrections : un enregistrement dedie qui reference l'enregistrement corrige.

## Structure du depot
- `software/<softwareKey>/` : dossier par outil.
- `software/<softwareKey>/software.md` : enregistrement logiciel.
- `software/<softwareKey>/deployments/` : enregistrements de deploiement.
- `software/<softwareKey>/entries/<YYYY>/` : enregistrements du journal par outil et par annee.
- `_global/entries/<YYYY>/` : enregistrements globaux du journal par annee.
- `taxonomy/` : enumerations partagees et types de reference.
- `templates/` : modeles de depart pour de nouveaux enregistrements.

## Flux de travail minimal
1. Creez un nouvel enregistrement logiciel avec `../templates/software.template.md`.
2. Ajoutez des enregistrements de deploiement avec `../templates/deployment.template.md`.
3. Ajoutez des entries avec `../templates/entry.template.md` (release, incident, maintenance).
4. Si une correction est necessaire, ajoutez une nouvelle entry avec `type: correction` qui reference l'entry d'origine.

## Pour aller plus loin
- `../SPEC.md` : source de verite pour la structure et les regles.
- `../CONTRIBUTING.md` : guide sur les noms, l'unicite et l'append-only.
- `../GUARDRAILS.md` : controles recommandes et conseils d'hygiene.

## Viewer et tooling (optionnel)
Le depot est pleinement utilisable sans outils. Des viewers ou des CLI peuvent etre construits par-dessus, mais ils ne font pas partie du standard.

## Licence
MIT (voir `../LICENSE`)

## Translation note
This text was translated by ChatGPT.

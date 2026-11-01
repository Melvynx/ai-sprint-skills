# AI Sprint Skills

Les 3 skills gratuits du **Sprint IA** : donne un cerveau à ton agent. Tu les installes une fois, et Claude connaît qui tu es, range tout ton travail par projet, se branche à tes outils et apprend tes méthodes.

## En 4 étapes

Tout se passe dans l'app [Claude](https://claude.ai/download), onglet **Code**. Chaque étape dans une nouvelle session.

### 1. Installe le kit

Envoie juste cette phrase à Claude, il installe les skills tout seul :

```text
Installe ces skills : https://github.com/Melvynx/ai-sprint-skills
```

Tu as déjà Node.js ? Une seule commande dans ton terminal fait pareil :

```bash
npx skills add Melvynx/ai-sprint-skills -g -a claude-code -s '*' -y
```

### 2. Crée ton brain

Crée un dossier (par exemple `BrainIA`), ouvre-le dans Claude et envoie cette phrase :

```text
Crée mon brain dans ce dossier avec ce skill : https://github.com/Melvynx/ai-sprint-skills/tree/main/skills/setup-brain
```

Claude te pose 10 questions (qui tu es, ton niveau, comment il doit bosser, tes projets en cours), puis il crée ton brain : un seul dossier où il range tout par projet, avec un `AGENTS.md` qui lui dit qui tu es et où tout se trouve. Il écrit aussi ta façon de travailler dans les règles de tous tes agents.

### 3. Branche tes outils

Dans ton brain, tape `/connect-tool` suivi du nom de l'outil, par exemple `/connect-tool notion`. Claude installe l'outil officiel de ce service pour le piloter depuis l'ordi, ou, s'il n'y en a pas, écrit un petit script avec ta clé API. Puis il vérifie que ça marche et crée un skill pour s'en servir dans tous tes dossiers.

### 4. Apprends-lui tes méthodes

Fais une tâche une première fois avec Claude (ta review de la semaine, ta newsletter…), puis tape `/skill-manager` et demande « fais-en un skill ». La fois d'après, une seule commande suffit.

## Les skills

| Skill | Ce qu'il fait | Comment l'utiliser |
| --- | --- | --- |
| [`setup-brain`](skills/setup-brain/SKILL.md) | Monte ton brain après une interview de 10 questions : un dossier par projet, et un `AGENTS.md` qui dit à Claude qui tu es. | Avec le lien de l'étape 2. |
| [`connect-tool`](skills/connect-tool/SKILL.md) | Branche n'importe quel outil à Claude (Notion, Stripe...) et crée un skill pour s'en servir partout. | `/connect-tool notion` |
| [`skill-manager`](skills/skill-manager/SKILL.md) | Installe, met à jour ou retire un skill, et crée les tiens pour que Claude refasse tout seul un travail que tu fais souvent. | "Installe ce skill : <lien>", "fais-en un skill" |

## Sécurité

Ces skills ne contiennent aucune clé ni donnée personnelle. Tes clés restent sur ton ordi : ne les colle jamais dans un fichier sauvegardé sur GitHub.

## Licence

[MIT](LICENSE). Utilise, modifie et partage librement.

Fait par [Melvyn](https://codelynx.dev).

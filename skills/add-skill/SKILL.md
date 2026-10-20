---
name: add-skill
description: Ajoute ou modifie un skill dans le plugin hanzo (/Users/hanzo/Developer/cc-workflow). À utiliser quand l'utilisateur veut créer un nouveau skill perso, ranger un skill existant dans son plugin, ou invoque /hanzo:add-skill.
---

# Ajouter un skill au plugin hanzo

Le plugin vit dans `/Users/hanzo/Developer/cc-workflow`. Chaque skill est un dossier `skills/<nom-en-kebab-case>/` contenant un `SKILL.md` :

```markdown
---
name: <nom-en-kebab-case>
description: <ce que fait le skill ET quand l'utiliser — c'est ce texte qui déclenche le skill>
---

<instructions>
```

Étapes :
1. Demande le nom et le but du skill si ce n'est pas clair.
2. Crée `skills/<nom>/SKILL.md`. Scripts ou fichiers de référence éventuels vont dans le même dossier (`scripts/`, `references/`) et sont cités depuis le SKILL.md par chemin relatif.
3. Incrémente `version` dans `.claude-plugin/plugin.json` (patch).
4. Lance `claude plugin validate /Users/hanzo/Developer/cc-workflow`, puis `claude plugin marketplace update hanzo && claude plugin update hanzo@hanzo`.
5. Dis à l'utilisateur de redémarrer la session pour voir le skill (`/hanzo:<nom>`).

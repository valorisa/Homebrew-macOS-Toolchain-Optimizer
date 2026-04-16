# 🤝 Guide de Contribution

Merci de votre intérêt pour contribuer à **Homebrew-macOS-Toolchain-Optimizer** ! 🎉

Ce document décrit les processus et bonnes pratiques pour proposer des améliorations, signaler des bugs ou enrichir la documentation de ce projet.

---

## 📋 Table des matières

- [Code de conduite](#-code-de-conduite)
- [Comment contribuer ?](#-comment-contribuer-)
- [Signaler un bug](#-signaler-un-bug)
- [Proposer une amélioration](#-proposer-une-amélioration)
- [Soumettre une Pull Request](#-soumettre-une-pull-request)
- [Style & Conventions](#-style--conventions)
- [Tests & Validation](#-tests--validation)
- [Licence](#-licence)

---

## 🧭 Code de conduite

Ce projet adhère à un code de conduite implicite : **respect, bienveillance et professionnalisme**. Toutes les contributions, discussions et interactions doivent refléter ces valeurs. Les comportements discriminatoires, harassants ou non constructifs ne seront pas tolérés.

---

## 🚀 Comment contribuer ?

### 1. Fork & Clone
```bash
# Forkez le dépôt via l'interface GitHub
# Puis clonez votre fork localement :
git clone https://github.com/votre-username/Homebrew-macOS-Toolchain-Optimizer.git
cd Homebrew-macOS-Toolchain-Optimizer

# Ajoutez le dépôt original comme remote upstream :
git remote add upstream https://github.com/valorisa/Homebrew-macOS-Toolchain-Optimizer.git
```

### 2. Créez une branche de fonctionnalité
```bash
# Branche descriptive pour une nouvelle fonctionnalité
git checkout -b feat/ajouter-validation-yaml

# Ou pour un correctif
git checkout -b fix/correction-chemin-ssh-copy-id

# Ou pour de la documentation
git checkout -b docs/preciser-etapes-rustup
```

### 3. Travaillez localement
- Modifiez les fichiers nécessaires.
- Testez vos changements dans un environnement isolé (VM ou machine de test recommandée).
- Validez la conformité Markdown avec `markdownlint` :
  ```bash
  npx markdownlint-cli2 "**/*.md"
  ```

### 4. Commit & Push
```bash
# Ajoutez vos modifications
git add README.md CONTRIBUTING.md

# Commit conventionnel (Conventional Commits)
git commit -m "docs: ajout du guide de contribution CONTRIBUTING.md

- Structure complète avec table des matières
- Instructions de fork, clone et création de branche
- Conventions de style et validation CI"

# Poussez vers votre fork
git push origin feat/ajouter-guide-contribution
```

---

## 🐛 Signaler un bug

Avant d'ouvrir une issue, vérifiez que le bug n'a pas déjà été signalé dans [Issues](https://github.com/valorisa/Homebrew-macOS-Toolchain-Optimizer/issues).

### Template d'issue recommandé :
```markdown
### 🐞 Description du bug
[Description claire et concise du problème]

### 🔁 Étapes pour reproduire
1. Environnement : macOS Sequoia, Apple Silicon, Homebrew 4.4+
2. Commande exécutée : `...`
3. Comportement observé : `...`

### ✅ Comportement attendu
[Ce que vous attendiez qu'il se passe]

### 📎 Logs / Captures d'écran
[Si pertinent, ajoutez des extraits de terminal ou screenshots]

### 🧰 Informations système
- macOS version : `sw_vers`
- Homebrew version : `brew --version`
- Shell : `echo $SHELL`
```

---

## 💡 Proposer une amélioration

Les suggestions d'amélioration sont les bienvenues ! Ouvrez une [Discussion](https://github.com/valorisa/Homebrew-macOS-Toolchain-Optimizer/discussions) ou une issue avec le label `enhancement`.

### Template de suggestion :
```markdown
### 🎯 Objectif de l'amélioration
[Pourquoi cette amélioration est-elle utile ?]

### 🛠️ Proposition technique
[Description de la solution envisagée]

### 🔍 Alternatives considérées
[Autres approches explorées, le cas échéant]

### 📚 Ressources complémentaires
[Liens vers documentation, RFC, ou exemples similaires]
```

---

## 🔀 Soumettre une Pull Request

### Checklist avant soumission :
- [ ] Ma branche est à jour avec `upstream/main`
- [ ] J'ai testé localement les modifications
- [ ] Le linter Markdown ne signale aucune erreur (`markdownlint`)
- [ ] Les commits suivent la convention [Conventional Commits](https://www.conventionalcommits.org/)
- [ ] J'ai mis à jour la documentation si nécessaire
- [ ] J'ai ajouté des tests si j'ai modifié un script ou un workflow

### Processus de review :
1. Ouvrez la PR depuis votre fork vers `valorisa/Homebrew-macOS-Toolchain-Optimizer:main`
2. Remplissez le template de PR fourni
3. Attendez la review : un mainteneur validera la cohérence technique et stylistique
4. Intégrez les feedbacks si nécessaire (`git commit --amend` ou nouveaux commits)
5. Une fois approuvée, la PR sera mergée via squash ou rebase

---

## ✍️ Style & Conventions

### Commits
Utilisez le format [Conventional Commits](https://www.conventionalcommits.org/) :
```text
<type>(<scope>): <description courte>

[corps optionnel avec détails]

[footer optionnel : références d'issues, breaking changes]
```

**Types autorisés** :
| Type | Usage |
|------|-------|
| `feat` | Nouvelle fonctionnalité |
| `fix` | Correction de bug |
| `docs` | Modification de documentation uniquement |
| `style` | Formatage, semi-colons, espaces (pas de changement logique) |
| `refactor` | Changement de code ni fix ni feat |
| `test` | Ajout ou correction de tests |
| `chore` | Maintenance, outils, CI/CD |

**Exemples** :
```bash
git commit -m "docs: clarification des étapes de récupération de permissions"
git commit -m "fix: correction du chemin ssh-copy-id dans PATH"
git commit -m "chore: mise à jour du workflow markdownlint vers v19"
```

### Markdown
- Respectez les règles `markdownlint` (voir `.markdownlint.json`)
- Utilisez des titres hiérarchiques (`##`, `###`, etc.)
- Encadrez les commandes bash avec ```bash
- Ajoutez des emojis modérément pour la lisibilité (🔍, ✅, ⚠️)

### Bash / Scripts
- Utilisez `set -euo pipefail` en tête des scripts
- Commentez les étapes complexes
- Privilégiez l'idempotence : les scripts doivent pouvoir être relancés sans effet de bord

---

## 🧪 Tests & Validation

### Validation locale
```bash
# Linter Markdown
npx markdownlint-cli2 "**/*.md"

# Validation YAML (workflows GitHub Actions)
yamllint .github/workflows/*.yml

# Syntaxe Bash (si vous ajoutez des scripts)
shellcheck mon-script.sh
```

### Validation CI
Chaque PR déclenche automatiquement :
- ✅ Le workflow `📝 Markdown Lint`
- 🔍 La vérification des liens et de la syntaxe

Assurez-vous que tous les checks passent avant de demander une review.

---

## 📜 Licence

En contribuant à ce projet, vous acceptez que vos contributions soient distribuées sous la licence [MIT](LICENSE) du dépôt.

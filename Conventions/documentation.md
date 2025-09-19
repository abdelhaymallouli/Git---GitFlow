# Create and push feature branch
git checkout -b feature/321-recherche-filtrage
git pull --rebase origin develop
git commit -m "feat(search): filtres q, tag, sort par défaut"
git push -u origin feature/321-recherche-filtrage

# PHP lint/format
composer require laravel/pint --dev
composer lint:php    # vendor/bin/pint --test
composer format:php  # vendor/bin/pint

# JS/TS lint/format
npm i -D eslint prettier eslint-config-prettier eslint-plugin-import @typescript-eslint/parser @typescript-eslint/eslint-plugin
npm run lint:js    # eslint . --ext .js,.ts --ignore-path .gitignore
npm run format:js  # prettier --write "**/*.{js,ts,json,md,yml,yaml}"

# Markdown/Blade lint/format
npm i -D markdownlint-cli blade-formatter
npm run lint:md        # markdownlint **/*.md
npm run format:blade   # blade-formatter "resources/views/**/*.blade.php" --write

# Setup Husky pre-commit
npm i -D husky lint-staged
npx husky init
# Add lint-staged to package.json and .husky/pre-commit

# Reinstall Husky if needed
npx husky init && git add .husky && git commit -m "chore: enable husky"
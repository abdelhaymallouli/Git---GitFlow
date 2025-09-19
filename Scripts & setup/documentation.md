# Setup project
git clone <repo-url> && cd <repo-folder>
cp .env.example .env
composer install
php artisan key:generate
npm ci

# Database setup
php artisan migrate --seed

# Run dev (PHP + Vite)
npm i -D concurrently
npm run dev

# Run tests
composer test

# Build for production
npm run build

# Fix common issues
php artisan key:generate  # Missing APP_KEY
php artisan storage:link  # Storage permissions

# Optional: Makefile setup
make setup  # Runs cp .env.example .env, composer install, php artisan key:generate, npm ci
make dev    # npm run dev
make build  # npm run build
make test   # composer test
make fresh  # php artisan migrate:fresh --seed
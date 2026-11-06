# Itens recomendados para `.gitignore`

Use apenas os que se aplicam à stack detectada.

## Segredos e ambiente (sempre)
```
.env
.env.*
!.env.example
*.pem
*.key
*.p12
*.pfx
id_rsa*
credentials.json
service-account*.json
secrets.*
```

## Python / Django
```
__pycache__/
*.py[cod]
.venv/
venv/
*.sqlite3
db.sqlite3
staticfiles/
media/
.pytest_cache/
.mypy_cache/
.ruff_cache/
htmlcov/
.coverage
```

## Node / Angular
```
node_modules/
dist/
.angular/
.nx/
coverage/
*.tsbuildinfo
npm-debug.log*
```

## Dados, logs e backups
```
*.log
logs/
*.sql
*.dump
*.bak
*.db
```

## IDE e sistema operacional
```
.idea/
.vscode/*
!.vscode/extensions.json
.DS_Store
Thumbs.db
```

## `.dockerignore` (mínimo)
```
.git
.env
.env.*
node_modules
__pycache__
*.log
tests
docs
```
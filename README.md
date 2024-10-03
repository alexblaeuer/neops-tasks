# Export tasks

## Development environment
```bash
pipenv run ./manage.py neops_task -f base -e ~/Projects/neops-tasks/Base/YAML -m --file-type yaml
pipenv run ./manage.py neops_task -f base -e ~/Projects/neops-tasks/Base/Markdown -m --file-type md
pipenv run ./manage.py neops_task -f nb -e ~/Projects/neops-tasks/NetBox/YAML -m --file-type yaml
pipenv run ./manage.py neops_task -f nb -e ~/Projects/neops-tasks/NetBox/Markdown -m --file-type md
```

## Server
```bash
docker compose exec backend ./manage.py neops_task -f base -e /tmp/neops-tasks/Base/YAML -m --file-type yaml
docker compose exec backend ./manage.py neops_task -f base -e /tmp/neops-tasks/Base/Markdown -m --file-type md
docker compose exec backend ./manage.py neops_task -f nb -e /tmp/neops-tasks/NetBox/YAML -m --file-type yaml
docker compose exec backend ./manage.py neops_task -f nb -e /tmp/neops-tasks/NetBox/Markdown -m --file-type md
```
# Super Advanced Ansible Project

Tento projekt ukazuje **advanced** nasazení Flask aplikace pomocí Ansible.

## Funkce
- **Roles** a strukturovaný projekt
- **Custom facts** pro dynamické nastavení počtu workerů podle RAM
- **Jinja2 šablony** pro systemd službu
- **Handlers** pro restart služby jen při změně
- **Rolling deployment** (`serial: 2`)
- Proměnné z `group_vars`
- Instalace balíčků a uživatele
- Nasazení aplikace z GitHubu

## Použití
```bash
ansible-playbook -i inventory site.yaml
```

## Struktura
```
roles/
  flask_app/
    tasks/
      main.yaml
      facts.yaml
    handlers/
      main.yaml
    templates/
      flask_app.service.j2
group_vars/
  all.yaml
site.yaml
```

## Požadavky
- Ansible 2.9+
- Python 3 na cílových serverech

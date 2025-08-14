# Advanced Ansible Project

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
ansible_project_advanced/
├── site.yaml                  # Hlavní playbook – spouští roli flask_app s rolling deploy (serial: 2)
├── group_vars/
│   └── all.yaml               # Globální proměnné – balíčky, Git repo, verze aplikace
└── roles/
    └── flask_app/
        ├── tasks/
        │   ├── main.yaml   # Hlavní úkoly: instalace, nasazení, systemd, start služby
        │   └── facts.yaml     # Custom facts – počet workerů podle RAM
        ├── handlers/
        │   └── main.yaml      # Handlery – restart Flask aplikace jen při změně
        └── templates/
            └── flask_app.service.j2  # Jinja2 šablona pro systemd jednotku

```

## Požadavky
- Ansible 2.9+
- Python 3 na cílových serverech


## TODO / Possible Improvements

Projekt obsahuje pokročilou Ansible strukturu pro nasazení Flask aplikace.  
Aktuálně zahrnuje:
- Rolling deploy
- Role
- Šablony
- Handlers
- Ansible Vault

V budoucnu je možné rozšířit:
- Monitoringem (Grafana/Prometheus)
- Alerty a notifikace


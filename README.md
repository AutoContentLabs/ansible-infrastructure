```
AutoContentLabs-ansible-infrastructure/
├── ansible
│   ├── playbook.yml             # Ana Ansible Playbook dosyası
│   ├── inventory                # Ansible Envanteri (hedef sunucular)
│   ├── roles
│   │   ├── docker
│   │   │   └── tasks
│   │   │       └── main.yml     # Docker ve Docker Compose görevleri
│   │   ├── git
│   │   │   └── tasks
│   │   │       └── main.yml     # Git güncellemeleri ve işlemleri
│   └── config
│       └── docker-compose.yml   # Docker Compose yapılandırması
└── services
    ├── fetcher                  # Fetcher servisi
    ├── messaging-utils          # Messaging-utils servisi
    ├── messaging                # Messaging servisi
    ├── databases                # Veritabanı servisi
    ├── data-collection-service  # Data-collection-service
    ├── data-processing-hub      # Data-processing-hub
    └── job-scheduler-service    # Job-scheduler-service
```

```
# Submodule ekleyin
git submodule add https://github.com/AutoContentLabs/fetcher.git services/fetcher
git submodule add https://github.com/AutoContentLabs/messaging-utils.git services/messaging-utils
git submodule add https://github.com/AutoContentLabs/messaging.git services/messaging
git submodule add https://github.com/AutoContentLabs/databases.git services/databases
git submodule add https://github.com/AutoContentLabs/data-collection-service.git services/data-collection-service
git submodule add https://github.com/AutoContentLabs/data-processing-hub.git services/data-processing-hub
git submodule add https://github.com/AutoContentLabs/job-scheduler-service.git services/job-scheduler-service

# Submodule'ları commit yapın
git commit -m "Add services as submodules"

# Değişiklikleri uzak repoya gönderin
git push
```

```
# Playbook'u çalıştır
ansible-playbook ansible/playbook.yml
```
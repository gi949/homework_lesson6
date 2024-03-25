# homework_lesson6

Провести настройку аутентификации доступа к yandex cloud-id, введя в консоли:

export YC_TOKEN=$(yc iam create-token)

export YC_CLOUD_ID=$(yc config get cloud-id)

export YC_FOLDER_ID=$(yc config get folder-id)

Ввести в консоли команды:

Инициализация terraform

terraform init

Проверка сценария

terraform terraform plan

Будут созданы ВМ:

db1, db2 и db3 на которых будет развернут кластер etcd, кластер patroni и базы данных postgresql.

Балансировка и проксирование запросов к БД будет реализована с помощью балансировщика haproxy на ВМ hp1

Запустить сценарий создания ВМ terraform apply

В консоле будут выведены внешние ip - external_ip_address_... и внутренние ip - internal_ip_address_vm_...

В файле ya.yaml ввести external_ip_address для ВМ db1, db2, db3 и hp1

Проверить доступность ВМ с помощью модуля

ping ansible all -m ping

В файле all групповых переменных в group_vars/ ввести internal_ip_address_vm_... для ВМ db1, db2 и db3.

Роль db_pg выполняет установку и развертывание кластер etcd, кластер patroni и базы данных postgresql.

Роль hp_ins выполняет настройку балансировщика haproxy

Проверить корректность синтаксиса плэйбука main.yaml

ansible-playbook --syntax-check main.yaml

Запускаем playbook на выполнение

ansible-playbook main.yaml


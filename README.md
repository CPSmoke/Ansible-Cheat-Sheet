# Ansible cheat sheet

| Category | Command/Option | Объяснение |
|---|---|---|
| General | `ansible --version` | Отобразите установленную версию Ansible. |
| General | `ansible -m ping all` | Пропингуйте все хосты, чтобы проверить, доступны ли они. |
| General | `ansible -m shell -a 'free -m' all` | Запустите команду командной строки 'free -m' на всех хостах. |
|---|---|---|
| Playbooks | `ansible-playbook playbook.yml` | Запустите playbook с именем `playbook.yml`. |
| Playbooks | `ansible-playbook -i inventory.ini playbook.yml` | Запустите playbook с указанным файлом инвентаря. |
| Playbooks | `ansible-playbook playbook.yml --syntax-check` | Выполните проверку синтаксиса в playbook. |
| Playbooks | `ansible-playbook playbook.yml --start-at-task='taskname'` | Запустите playbook с указанной задачей. |
| Playbooks | `ansible-playbook playbook.yml --list-hosts` | Перечислите все хосты, на которых будет выполняться playbook. |
| Playbooks | `ansible-playbook playbook.yml --list-tasks` | Перечислите все задачи, которые будет выполнять playbook. |
| Playbooks | `ansible-playbook playbook.yml --step` | Запустите playbook в интерактивном режиме, запрашивая подтверждение на каждом шаге. |
| Playbooks | `ansible-playbook playbook.yml --check` | Выполните пробный запуск playbook без внесения фактических изменений. |
| Playbooks | `ansible-playbook playbook.yml --diff` | Показывать различия в файлах при запуске playbook. |
| Playbooks | `ansible-playbook playbook.yml --tags "tag1,tag2"` | Запускайте только задачи, помеченные тегами tag1 и tag2. |
| Playbooks | `ansible-playbook playbook.yml --skip-tags "tag3"` | Пропускать задачи, помеченные тегом3. |
| Playbooks | `ansible-playbook playbook.yml --limit servers` | Ограничьте выполнение playbook группой "servers". |
| Playbooks | `ansible-playbook playbook.yml --extra-vars "version=1.2.3"` | Запустите playbook с дополнительными переменными. |
| Playbooks | `ansible-playbook playbook.yml --forks=5` | Установите количество параллельных процессов равным 5. |
| Playbooks | `ansible-playbook playbook.yml -v` | Запустите playbook в подробном режиме. Для большей детализации можно использовать `-vvv` и `-vvvvv`. |
| Playbooks | `ansible-playbook playbook.yml --check --diff` | Предварительный запуск playbook и отображение различий в файлах. |
|---|---|---|
| Roles | `ansible-galaxy init role_name` | Инициализируйте новую структуру ролей с указанным именем. |
| Roles | `ansible-galaxy install role_name` | Установите роль Ansible. |
|---|---|---|
| Vault | `ansible-vault create vault.yml` | Создайте новый зашифрованный файл. |
| Vault | `ansible-vault view vault.yml` | Просмотр зашифрованного файла. |
| Vault | `ansible-vault edit vault.yml` | Редактирование зашифрованного файла. |
| Vault | `ansible-vault decrypt vault.yml` | Расшифровать зашифрованный файл. |
| Vault | `ansible-vault encrypt vault.yml` | Зашифровать файл. |
| Vault | `ansible-vault rekey vault.yml` | Измените пароль для файла хранилища. |
| Vault | `ansible-vault encrypt_string --name 'var_name' 'string'` | Зашифруйте строку и выведите ее в формате, готовом для использования с Ansible. |
| Vault | `ansible-playbook playbook.yml --ask-vault-pass` | Запустите playbook и запросите пароль хранилища. |
| Vault | `ansible-playbook playbook.yml --vault-password-file vault.pass` | Запустите playbook, используя файл, содержащий пароль хранилища. |
| Vault | `ansible-vault encrypt_string --stdin-name 'var_name'` | Прочтите строку из stdin и зашифруйте ее. |
| Vault | `ansible-vault encrypt --vault-id dev@prompt vars.yml` | Зашифруйте файл с помощью запроса пароля хранилища. |
| Vault | `ansible-playbook playbook.yml --vault-id dev@prompt` | Запустите playbook, используя запрос на ввод пароля хранилища. |
|---|---|---|
| Configuration | `ansible-config list` | Перечислите все параметры конфигурации. |
| Configuration | `ansible-config dump` | Показать текущую конфигурацию. |
| Configuration | `ansible-config view` | Просмотр текущей конфигурации Ansible. |
| Configuration | `ansible-config dump --only-changed` | Сброс элементов конфигурации, которые изменились по сравнению с параметрами по умолчанию. |
| Configuration | `ansible-config set ANSIBLE_HOST_KEY_CHECKING=False` | Установите определенный элемент конфигурации. |
| Configuration | `ansible-config unset ANSIBLE_HOST_KEY_CHECKING` | Отмените настройку определенного элемента конфигурации. |
|---|---|---|
| Console | `ansible-console` | Запустите интерактивную консоль для выполнения задач Ansible. |
| Console | `ansible-console -i inventory.ini` | Запустите интерактивную консоль, используя определенный инвентарь. |
|---|---|---|
| Modules | `ansible-doc -l` | Список доступных модулей. |
| Modules | `ansible-doc module_name` | Получить документацию для конкретного модуля. |
|---|---|---|
| Inventory | `ansible-inventory --list -y` | Перечислите инвентарь в формате YAML. |
| Inventory | `ansible-inventory --graph` | Показать график инвентаризации. |
| Inventory | `ansible -i inventory.ini all -m ping` | Используйте определенный файл инвентаризации и пропингуйте все хосты. |
| Inventory | `ansible-inventory --host hostname` | Отображать все переменные для определенного хоста. |
| Inventory | `ansible-inventory --playbook-dir . --graph` | Отображение графика инвентаризации из текущего каталога. |
| Inventory | `ansible -i 'localhost,' -c local -m ping` | Пингуйте localhost, используя локальное соединение и специальную инвентаризацию. |
| Inventory | `ansible-inventory --list --yaml` | Составьте список инвентаря в формате YAML. |
|---|---|---|
| Pull | `ansible-pull -U git_url` | Используется в Ansible для выполнения "пуллинга" (загрузки) плейбуков, ролей и других конфигурационных файлов из удалённого репозитория Git. |
|---|---|---|
| Galaxy | `ansible-galaxy collection init my_namespace.my_collection` | Инициализируйте новую коллекцию с заданным пространством имен и именем. |
| Galaxy | `ansible-galaxy collection build` | Создайте пакет Ansible collection, готовый к распространению. |
| Galaxy | `ansible-galaxy collection install my_namespace.my_collection` | Установите коллекцию Ansible из Galaxy. |
| Galaxy | `ansible-galaxy role init my_role` | Инициализируйте новую роль с заданным именем. |
| Galaxy | `ansible-galaxy role install my_role` | Установите роль Ansible из Galaxy. |
| Galaxy | `ansible-galaxy list` | Список установленных ролей и коллекций. |
| Galaxy | `ansible-galaxy collection install -r requirements.yml` | Устанавливайте коллекции из файла требований. |
| Galaxy | `ansible-galaxy role install -r requirements.yml` | Установите роли из файла требований. |
| Galaxy | `ansible-galaxy collection publish ./namespace-collection-1.0.0.tar.gz --api-key=your_token` | Опубликуйте коллекцию в Galaxy с помощью токена API. |
| Galaxy | `ansible-galaxy role init --role-skeleton skeleton my_role` | Инициализируйте новую роль с помощью указанного скелета роли. |
|---|---|---|
| Modules | `ansible localhost -m file -a "path=/tmp/test state=touch"` | Создайте новый файл на локальном хосте с помощью модуля file. |
| Modules | `ansible localhost -m package -a "name=vim state=present"` | Установите пакет на локальный хост с помощью модуля package. |
| Modules | `ansible localhost -m command -a "uptime"` | Запустите команду на локальном хосте с помощью командного модуля. |
| Modules | `ansible localhost -m user -a "name=testuser state=absent"` | Удалите пользователя 'testuser' с локального хоста с помощью пользовательского модуля. |
| Modules | `ansible localhost -m service -a "name=httpd state=restarted"` | Перезапустите службу 'httpd' на локальном хосте с помощью сервисного модуля. |
| Modules | `ansible localhost -m copy -a "src=/etc/hosts dest=/tmp/hosts"` | Скопируйте '/ etc /hosts' в '/tmp / hosts' на локальном хосте с помощью модуля копирования. |
| Modules | `ansible localhost -m file -a "path=/tmp/test state=absent"` | Удалите файл '/ tmp / test' на локальном хосте с помощью файлового модуля. |
| Modules | `ansible localhost -m apt -a "name=nginx state=latest"` | Установите последнюю версию 'nginx' на локальный хост с помощью модуля apt (системы на базе Debian). |

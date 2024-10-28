# Monitoring
Репозиторий для третьего задания INT4 PTStart

Автор: Гришин Александр grishin.alieksandr@inbox.ru

Этот репозиторий содержит 2 конфигурационных файла (Prometheus и Blackbox exporter), которые можно использовать для проверки доступности и состояния целевого URL https://ptsecurity.com

Конфигурационные файлы:
1) prometheus.yml - файл, содержащий конфигурацию Prometheus и устанавливает следующие параметры: устанавливает интервал опроса для всех задач на 10 секунд, указывает параметры, которые будут переданы blackbox-exporter. 
2) blackbox.yml - файл, содержащий конфигурацию Blackbox exporter и устанавливает следующие параметры: устанавливает пробер для проверки, допустимые коды состояний, версии http, метод и другие параметры.

Далее приведена инструкция по запуску. Инструкция работает на Ubuntu 24.04

Для запуска мониторинга необходимо выполнить следующие команды:

1) Скачать Blacbox exporter:
     ```bash
   wget https://github.com/prometheus/blackbox_exporter/releases/download/v0.25.0/blackbox_exporter-0.25.0.linux-amd64.tar.gz
     ```
     Можно заменить v0.25.0 на последнюю доступную версию
2) Распаковать архив
     ```bash
   tar xvf blackbox_exporter-*.tar.gz
     ```
3) Заменить стандартный файл конфигурации Blackbox на файл из данного репозитория
4) Перейти в папку с Blackbox
     ```bash
   cd blackbox_exporter-*
     ```
5) Запустить Blackbox exporter
   ```bash
   ./blackbox_exporter --config.file=blackbox.yml
   ```
6) Скачать Prometheus:
     ```bash
   wget https://github.com/prometheus/prometheus/releases/download/v2.36.0/prometheus-2.36.0.linux-amd64.tar.gz
     ```
     Можно заменить v2.36.0 на последнюю доступную версию
7) Распаковать архив
     ```bash
   tar xvf prometheus-*.tar.gz
     ```
8) Заменить стандартный файл конфигурации Prometheus на файл из данного репозитория
9) Перейти в папку с Prometheus
     ```bash
   cd prometheus-*
     ```
10) Запустить Prometheus
   ```bash
   ./prometheus --config.file=prometheus.yml
   ```

После выполнения этих команд по адресу localhost:9115 запустится Blackbox exporter, в котором можно будет посмотреть логи выполнения и результат сбора метрик, по адресу localhost:9000 запустится Prometheus, в котором можно будет также посмотреть метрики


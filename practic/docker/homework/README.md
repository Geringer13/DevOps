cat <<EOF > README.md
# Домашнее задание по Docker

## Цель:
Создать Dockerfile, который собирает контейнер из образа continuumio/miniconda3, устанавливает необходимые библиотеки и выполняет скрипт 13.sh.

## Инструкция:

1. Базовый образ: continuumio/miniconda3:latest
2. Создаётся рабочая папка /app
3. В контейнер копируется скрипт 13.sh, который печатает "Hello Netology"
4. Устанавливаются пакеты: mlflow, boto3, pymysql
5. Скрипт 13.sh исполняется при запуске контейнера

## Создание файла 13.sh с нужным содержимым 
echo -e '#!/bin/bash\necho "Hello Netology"' > 13.sh

## Создание докерфайла

cat <<EOF > Dockerfile
FROM continuumio/miniconda3:latest

WORKDIR /homework

COPY 13.sh .

RUN chmod +x 13.sh

RUN pip install mlflow boto3 pymysql

CMD ["./13.sh"]
EOF

## Сборка контейнера:

\`\`\`bash
docker build -t netology-ml:netology-ml .
\`\`\`

## Запуск контейнера:

\`\`\`bash
docker run --rm netology-ml:netology-ml
\`\`\`

Ожидаемый вывод:

\`\`\`
Hello Netology
\`\`\`
EOF

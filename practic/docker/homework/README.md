cat <<EOF > README.md
# Домашнее задание по Docker

## Цель:
Создать Dockerfile, который собирает контейнер из образа continuumio/miniconda3, устанавливает необходимые библиотеки и выполняет скрипт 1.sh.

## Инструкция:

1. Базовый образ: continuumio/miniconda3:latest
2. Создаётся рабочая папка /app
3. В контейнер копируется скрипт 1.sh, который печатает "Hello Netology"
4. Устанавливаются пакеты: mlflow, boto3, pymysql
5. Скрипт 1.sh исполняется при запуске контейнера

## Создание файла 1.sh с нужным содержимым 
echo -e '#!/bin/bash\necho "Hello Netology"' > 1.sh

## Создание докерфайла

cat <<EOF > Dockerfile
FROM continuumio/miniconda3:latest

WORKDIR /app

COPY 1.sh .

RUN chmod +x 1.sh

RUN pip install mlflow boto3 pymysql

CMD ["./1.sh"]
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

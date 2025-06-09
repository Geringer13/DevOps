# Домашнее задание по CI/CD

## Цель
Создание базового GitLab CI/CD пайплайна с этапами `build` и `test`.

## Содержимое `.gitlab-ci.yml`

```yaml
stages:
  - build
  - test

build_job:
  stage: build
  tags:
    - netology
  script:
    - echo "Building"
    - mkdir -p build
    - echo "Информация о сборке" > build/info.txt

test_job:
  stage: test
  tags:
    - netology
  script:
    - echo "Testing"
    - test -f build/info.txt && echo "Файл найден" || echo "Файл не найден"
```

## Как это работает
1. **build_job**:
   - выводит сообщение "Building"
   - создаёт папку `build`
   - создаёт в ней файл `info.txt`

2. **test_job**:
   - выводит "Testing"
   - проверяет, существует ли файл `build/info.txt`

Готово для загрузки в GitLab репозиторий. Убедитесь, что runner с тегом `netology` активен.

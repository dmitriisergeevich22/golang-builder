## Docker-образ для разработки на Go
Образ предназначен для сборки программ на Go. Он содержит 
все те же версии инструментов, 

Версия с тэгом v2.0.6 основана на образе golang1.22.1-bookworm. Дополнительно в нем 
обновлена система и устанавлено следующее: 
- libxml2-dev
- protobuf-compiler
- goose
- swag
- golangci-lint
- conf2env (генератор переменных окружения из исходника на Go)
- statik - плагин для укладки в бинарник статических файлов (Шаблон swagger)
- nilaway - линтер от Uber
- Плагины генерации .proto
    - protoc-gen-go
    - protoc-gen-go-grpc - генерация клиента и сервера для go
    - protoc-gen-grpc-gateway - генерация http ручек
    - protoc-gen-openapiv2 - генерация json по формату openapi v2

### Сборка при отладке изменений

Для отладки при внесении изменений в образ, можно собирать образ локально (без пуша в registry) командой.

```bash
make local
```

### Сборка и push в наш Docker registry.

**ВАЖНО!** Если не уверен, зачем тебе это, НЕ НАДО выполнять этот рецепт Makefile.
В итоге соберется новый образ, он попадет в registry и будет там отсвечивать. 

Чтобы собрать образ для использования в пайплайне и запушить его, командуем:
```bash
make push
```


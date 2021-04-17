# Deploy with Docker Compose

Есть уже готовый Docker образ `messembed/messembed`  который можно использовать.

Сначала создаем файл `docker-compose.yml` со следующим содержимым:

{% code title="docker-compose.yml" %}
```yaml
version: '3'
services:
  messembed:
    image: messembed/messembed:v0.0.2
    env_file: ./.env
    ports:
      - '127.0.0.1:3000:80'
    restart: unless-stopped
    depends_on:
      - mongo

  mongo:
    image: mongo:4.4.5
    environment:
      - MONGO_INITDB_ROOT_USERNAME=${MONGO_INITDB_ROOT_USERNAME}
      - MONGO_INITDB_ROOT_PASSWORD=${MONGO_INITDB_ROOT_PASSWORD}
    ports:
      - 127.0.0.1:27017:27017
    volumes:
      - mongo-data:/data/db
    restart: unless-stopped

volumes:
  mongo-data:

```
{% endcode %}

А потом создаем файл `.env` как следуюший:

{% code title=".env" %}
```bash
PORT=80
HOST=0.0.0.0

# Если написать development то логи будут более читабельные
NODE_ENV=production

# Пароль, по которому админ получит доступ к сервису
AUTH__EXTERNAL_SERVICE__PASSWORD=password

AUTH__JWT_STRATEGY__JWT_SECRET=keyboad cat

MONGODB_URI=mongodb://root:root@mongo:27017/messembed?authSource=admin

# Если поставить true, то пользователи не смогут самостоятельно отправлять первое сообшение
# другому пользователю, с которым ранее не были ни какие сообщения. В таком случае, чтобы
# пользователи могли общаться, админ сам должен инициировать общение между ними через вызов метода .createChat(...)
#
# По умполчанию false, то есть любой пользователь может начать переписываться с любым другим.
DISALLOW_USERS_TO_CREATE_CHATS=false

MONGO_INITDB_ROOT_USERNAME=root
MONGO_INITDB_ROOT_PASSWORD=root

```
{% endcode %}

А потом запускаем:

```bash
docker-compose up --build -d
```


# Client API

## Начало работы

```typescript
import { MessembedSdk } from 'messembed-sdk';

const messembed = new MessembedSdk({
  baseUrl: '<URL к messembed сервису>',
  accessToken: '<токен доступа>',
});
```

## Подключение чата

### Получение списка чатов

```typescript
const chats = await messembed.listPersonalChats();
```

`chats` - это массив объектов `PersonalChat`, который имеет следующие поля:

| Поле | Тип | Описание |
| :--- | :--- | :--- |
| `_id` | `string` | ID чата |
| `createdAt` | `Date` | Дата создания чата |
| `updatedAt` | `Date` | Дата последнего обновления полей чата |
| `active` | `boolean` | Активен ли чат \(см. [блокирование отдельных чатов](../server-api/node.js-sdk/blocking-chats-and-users.md#blokirovanie-otdelnogo-chata)\) |
| `externalMetadata` | `json` | Произвольные данные |
| `companion` | `User` | Объект, представляющий собеседника в данном чате |
| `unreadMessagesCount` | `number` | Количество непрочитанных сообщений в данном чате |

### Получение истории сообщений

```typescript
const paginatedMessages = await messembed.listMessages({ chatId: '...' });

// Так же можно использовать подробные параметры, например
// для пагинации
const paginatedMessages = await messembed.listMessages({
  chatId: '...',
  after: new Date('...'), // Отправленные после. Необъязательный параметр
  before: new Date('...'), // Отправленные до. Необъязательный параметр
  offset: 0, // Необъязательный параметр
  limit: 100, // Необъязательный параметр
});
```

`paginatedMessages` - это объект `PaginatedMessages`, со следующими полями:

| Поле | Тип | Описание |
| :--- | :--- | :--- |
| `after` | `Date` | Переданный во время запроса параметр `after` |
| `before` | `Date` | Переданный во время запроса параметр `before` |
| `offset` | `number` | Переданный во время запроса параметр `offset` |
| `limit` | `number` | Переданный во время запроса параметр `limit` |
| `messages` | \`\`[`Message`](obekt-message.md)`[]` | Массив объектов, представляющих сообщения. Подробнее про объект сообщения можно узнать на странице ["Объект Message"](obekt-message.md) |

### Отправка сообщений

```typescript
await messembed.sendMessageOverWS({chatId: '...', content: 'Привет!'});
```

### Отправляем индикатор набора текста

Отправление индикатора о том, что текущий пользователь начал печатать. В параметре передается ID чата:

```typescript
await messembed.sendWritingIndicator('...');
```

### Подписка на события

Устанавливаем обработчики событий.

#### Подписка на новые сообщения

Появился новое сообщение в одном из чатов. В параметре обработчика передается объект сообщения. В этом объекте есть ID чата, с помощю которого можно определить с какого именно чата пришло сообщение.

```typescript
messembed.onNewMessage((message: Message) => showNewMessage(message));
```

#### Подписка на появление новых чатов

Появился новый чат. В параметре обработчика передается объект нового чата.

```typescript
messembed.onNewChat((chat: PersonalChat) => showNewChat(chat));
```

#### Подписка на индикатор печатания собеседников

Cобеседник начал печатать. В параметре обработчика передается ID чата, в котором собеседник печатает.

```typescript
messembed.onWriting((chatId: string) => showWritingIndicator(chatId));
```

Cобеседник перестал печатать. В параметре обработчика передается ID чата, в котором собеседник перестал печатать. 

```typescript
messembed.onWritingEnd((chatId: string) => hideWritingIndicator(chatId))
```

### Полный пример кода

```typescript
import { Message, PersonalChat } from 'messembed-sdk';

const messembed = new MessembedSdk({ ... });

// Получаем текущий список чатов
const chats = await messembed.listPersonalChats();

// Устанавливаем обработчики событий
messembed
  // Новое сообщение.
  // Появился новое сообщение в одном из чатов.
  // В параметре обработчика передается объект
  // сообщения. В этом объекте есть ID чата, с помощю
  // которого можно определить с какого именно чата
  // пришло сообщение.
  .onNewMessage((message: Message) => { ... })
  
  // Появился новый чат.
  // В параметре обработчика передается объект
  // нового чата.
  .onNewChat((chat: PersonalChat) => { ... })

  // Cобеседник начал печатать.
  // В параметре обработчика передается ID чата,
  // в котором собеседник печатает.
  .onWriting((chatId: string) => { ... })

  // Cобеседник перестал печатать.
  // В параметре обработчика передается ID чата,
  // в котором собеседник перестал печатать.  
  .onWritingEnd((chatId: string) => { ... })

// Получение списка сообщений
// Полезно, например, когда нужно показывать историю сообщений.
await messembed.listMessages({ chatId: '...' });
await messembed.listMessages({
  chatId: '...',
  after: new Date('...'), // Отправленные после. Необъязательный параметр
  before: new Date('...'), // Отправленные до. Необъязательный параметр
  offset: 0, // Необъязательный параметр
  limit: 100, // Необъязательный параметр
});

// Отправление сообщения
await messembed.sendMessageOverWS({chatId: '...', content: 'Привет!'});

// Отправление индикатора о том, что текущий пользователь начал печатать.
// В параметре передается ID чата
await messembed.sendWritingIndicator('...');

```

### 

### 


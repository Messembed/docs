# Client JavaScript API

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
// Без параметров (используются значения по умолчанию)
const chats = await messembed.listPersonalChats()

// Или с параметрами
const chats = await messembed.listPersonalChats({
  // Поиск чатов по сообщениям. Если задать этот парамтер,
  // то в результате поле lastMessage будет содержать 
  // последнее сообщение в чате, которое соответствует поиску.
  // Необзятельный парамтер
  query: '',

  // Сортировка.
  // Доступные значения:
  // NEWER_FIRST - сначала новые (по умолчанию)
  // UNREAD_FIRST - сначала непрочитанные
  // Необзятельный парамтер
  sort: 'NEWER_FIRST',

  // Поиск чатов по содержанию externalMetadata
  // Необзятельный парамтер
  externalMetadata: { ... }
});
```

`chats` - это массив объектов `PersonalChat`, который имеет следующие поля:

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x41F;&#x43E;&#x43B;&#x435;</th>
      <th style="text-align:left">&#x422;&#x438;&#x43F;</th>
      <th style="text-align:left">&#x41E;&#x43F;&#x438;&#x441;&#x430;&#x43D;&#x438;&#x435;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>_id</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">ID &#x447;&#x430;&#x442;&#x430;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>createdAt</code>
      </td>
      <td style="text-align:left"><code>Date</code>
      </td>
      <td style="text-align:left">&#x414;&#x430;&#x442;&#x430; &#x441;&#x43E;&#x437;&#x434;&#x430;&#x43D;&#x438;&#x44F;
        &#x447;&#x430;&#x442;&#x430;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>updatedAt</code>
      </td>
      <td style="text-align:left"><code>Date</code>
      </td>
      <td style="text-align:left">&#x414;&#x430;&#x442;&#x430; &#x43F;&#x43E;&#x441;&#x43B;&#x435;&#x434;&#x43D;&#x435;&#x433;&#x43E;
        &#x43E;&#x431;&#x43D;&#x43E;&#x432;&#x43B;&#x435;&#x43D;&#x438;&#x44F;
        &#x43F;&#x43E;&#x43B;&#x435;&#x439; &#x447;&#x430;&#x442;&#x430;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>active</code>
      </td>
      <td style="text-align:left"><code>boolean</code>
      </td>
      <td style="text-align:left">&#x410;&#x43A;&#x442;&#x438;&#x432;&#x435;&#x43D; &#x43B;&#x438; &#x447;&#x430;&#x442;
        (&#x441;&#x43C;. <a href="../server-api/node.js-sdk/blocking-chats-and-users.md#blokirovanie-otdelnogo-chata">&#x431;&#x43B;&#x43E;&#x43A;&#x438;&#x440;&#x43E;&#x432;&#x430;&#x43D;&#x438;&#x435; &#x43E;&#x442;&#x434;&#x435;&#x43B;&#x44C;&#x43D;&#x44B;&#x445; &#x447;&#x430;&#x442;&#x43E;&#x432;</a>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>externalMetadata</code>
      </td>
      <td style="text-align:left"><code>json</code>
      </td>
      <td style="text-align:left">&#x41F;&#x440;&#x43E;&#x438;&#x437;&#x432;&#x43E;&#x43B;&#x44C;&#x43D;&#x44B;&#x435;
        &#x434;&#x430;&#x43D;&#x43D;&#x44B;&#x435;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>companion</code>
      </td>
      <td style="text-align:left"><code>User</code>
      </td>
      <td style="text-align:left">&#x41E;&#x431;&#x44A;&#x435;&#x43A;&#x442;, &#x43F;&#x440;&#x435;&#x434;&#x441;&#x442;&#x430;&#x432;&#x43B;&#x44F;&#x44E;&#x449;&#x438;&#x439;
        &#x441;&#x43E;&#x431;&#x435;&#x441;&#x435;&#x434;&#x43D;&#x438;&#x43A;&#x430;
        &#x432; &#x434;&#x430;&#x43D;&#x43D;&#x43E;&#x43C; &#x447;&#x430;&#x442;&#x435;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>unreadMessagesCount</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">&#x41A;&#x43E;&#x43B;&#x438;&#x447;&#x435;&#x441;&#x442;&#x432;&#x43E;
        &#x43D;&#x435;&#x43F;&#x440;&#x43E;&#x447;&#x438;&#x442;&#x430;&#x43D;&#x43D;&#x44B;&#x445;
        &#x441;&#x43E;&#x43E;&#x431;&#x449;&#x435;&#x43D;&#x438;&#x439; &#x432;
        &#x434;&#x430;&#x43D;&#x43D;&#x43E;&#x43C; &#x447;&#x430;&#x442;&#x435;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>lastMessage</code>
      </td>
      <td style="text-align:left"><a href="obekt-message.md">Message</a>
      </td>
      <td style="text-align:left">
        <p>&#x415;&#x441;&#x43B;&#x438; &#x43F;&#x430;&#x440;&#x430;&#x43C;&#x435;&#x442;&#x440;
          &#x43F;&#x43E;&#x438;&#x441;&#x43A;&#x430; &#x447;&#x430;&#x442;&#x43E;&#x432;
          &#x43F;&#x43E; &#x441;&#x43E;&#x43E;&#x431;&#x449;&#x435;&#x43D;&#x438;&#x44F;&#x43C; <code>query</code> &#x43D;&#x435;
          &#x437;&#x430;&#x434;&#x430;&#x43D;, &#x442;&#x43E; &#x432; &#x44D;&#x442;&#x43E;&#x43C;
          &#x43F;&#x43E;&#x43B;&#x435; &#x431;&#x443;&#x434;&#x435;&#x442; &#x43F;&#x43E;&#x441;&#x43B;&#x435;&#x434;&#x43D;&#x435;&#x435;
          &#x441;&#x43E;&#x43E;&#x431;&#x449;&#x435;&#x43D;&#x438;&#x44F; &#x447;&#x430;&#x442;&#x430;.
          &#x418;&#x43D;&#x430;&#x447;&#x435;, &#x435;&#x441;&#x43B;&#x438; &#x43F;&#x430;&#x440;&#x43C;&#x435;&#x442;&#x440;
          &#x43F;&#x43E;&#x438;&#x441;&#x43A;&#x430; <code>query</code> &#x437;&#x430;&#x434;&#x430;&#x43D;,
          &#x442;&#x43E; &#x432; &#x44D;&#x442;&#x43E;&#x43C; &#x43F;&#x43E;&#x43B;&#x435;
          &#x431;&#x443;&#x434;&#x435;&#x442; &#x43F;&#x43E;&#x441;&#x43B;&#x435;&#x434;&#x43D;&#x435;&#x435;
          &#x441;&#x43E;&#x43E;&#x431;&#x449;&#x435;&#x43D;&#x438;&#x435;, &#x43A;&#x43E;&#x442;&#x43E;&#x440;&#x43E;&#x435;
          &#x441;&#x43E;&#x43E;&#x442;&#x432;&#x435;&#x442;&#x441;&#x442;&#x432;&#x443;&#x435;&#x442;
          &#x43F;&#x43E;&#x438;&#x441;&#x43A;&#x43E;&#x432;&#x43E;&#x43C;&#x443;
          &#x437;&#x430;&#x43F;&#x440;&#x43E;&#x441;&#x443;.</p>
        <p>&#x415;&#x441;&#x43B;&#x438; &#x432; &#x447;&#x430;&#x442;&#x435; &#x43D;&#x435;&#x442;
          &#x43D;&#x438; &#x43E;&#x434;&#x43D;&#x43E;&#x433;&#x43E; &#x441;&#x43E;&#x43E;&#x431;&#x449;&#x435;&#x43D;&#x438;&#x44F;,
          &#x442;&#x43E; &#x432; &#x44D;&#x442;&#x43E;&#x43C; &#x43F;&#x43E;&#x43B;&#x435;
          &#x431;&#x443;&#x434;&#x435;&#x442; <code>null</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

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
| `messages` | \`\`[`Message[]`](obekt-message.md)\`\` | Массив объектов, представляющих сообщения. Подробнее про объект сообщения можно узнать на странице ["Объект Message"](obekt-message.md) |

### Отправка сообщений

```typescript
await messembed.sendMessageOverWS({chatId: '...', content: 'Привет!'});
```

### Отправляем индикатор набора текста

Отправление индикатора о том, что текущий пользователь начал печатать. В параметре передается ID чата:

```typescript
await messembed.sendWritingIndicator('...');
```

### Прочитывание сообщения

Когда пользователь читает сообщение, то вам нужно вызвать метод `.readChat(<chat id>)` который пометит чат как прочитанным для текущего пользователя:

```typescript
await messembed.readChat('<chat id>');
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

### Прикрепление файлов

Чтобы отправлять сообщение с прикрепленными файлами нужно во время отправки сообщения задать параметр `attachments` следующим образом:

```typescript
await messembed.sendMessageOverWS({
    chatId: '...',
    attachments: [
        {
            // 'video', 'docx', 'audio' или любые другие типы.
            // Параметр необязателен
            type: 'image',

            // Ссылка на файл.
            // Чаще всего это ссылка на файл, который был закгружен
            // в хранилище файлов, типа Amazon S3 или Yandex Object Storage
            url: 'https://s3.storage.example.com/attached-image.png',
            
            // Можно указать другие параметры касающиеся прикрепленного
            // файла
            anotherParameter2: ...
        },

        // Можно прикреплять несколько файлов
        {...},
        {...},
    ]
})
```

### Получение сообщений с прикрепленными файлами в чате

Для того, чтобы получить список сообщений, где есть хотя бы один прикрепленный файл, можно воспользоваться методом `.listMessagesWithAttachments()`

Такой механизм позволяет получать не только список прикрепленных файлов, но и информацию о том, к каким сообщениям они были прикреплены.

Метод возвращает массив из объектов типа [Message](../../).

```typescript
const messagesWithAttachments: Message[] =
    await messembed.listMessagesWithAttachments({
        chatId: '...',
    });

console.log(messagesWithAttachments);
[
    {
        _id: '...',
        content: 'Я отправил файлы',
        attachments: [ {type: 'image', url: '...'}, {...}, {...} ]
    },
    {
        _id: '...',
        content: '...',
        attachments: [ {type: 'doc', url: '...'}, {...}, {...} ]
    }
]
```

### Полный пример кода из этой страницы

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

// Помечаем чат как прочитанный
// В таком случае все сообщения, которые были не прочитанными,
// станут прочитанными
await messembed.readChat('<chat id>')

```

### 

### 


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

```typescript
import { Message, PersonalChat } from 'messembed-sdk';

const messembed = new MessembedSdk({ ... });

// Получаем текущий список чатов
const chats = await messembed.getPersonalChats();

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


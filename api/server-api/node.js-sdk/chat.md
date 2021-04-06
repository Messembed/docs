# Chat

Чаты представляют связи между пользователями и содержат в себе основную информацию. Для начала переписки нужно для начала создавать чат с нужным пользователем, и только после этого переписываться.

## Объект чата

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
      <td style="text-align:left">
        <p>&#x418;&#x434;&#x435;&#x43D;&#x442;&#x438;&#x444;&#x438;&#x43A;&#x430;&#x442;&#x43E;&#x440;
          &#x447;&#x430;&#x442;&#x430;.</p>
        <p>&#x417;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x435; &#x43D;&#x435;
          &#x437;&#x430;&#x434;&#x430;&#x435;&#x442;&#x441;&#x44F;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>createdAt</code>
      </td>
      <td style="text-align:left"><code>string</code> &#x414;&#x430;&#x442;&#x430; ISO 8601</td>
      <td style="text-align:left">
        <p>&#x414;&#x430;&#x442;&#x430; &#x441;&#x43E;&#x437;&#x434;&#x430;&#x43D;&#x438;&#x438;
          &#x447;&#x430;&#x442;&#x430;.</p>
        <p>&#x417;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x435; &#x43D;&#x435;
          &#x437;&#x430;&#x434;&#x430;&#x435;&#x442;&#x441;&#x44F;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>updatedAt</code>
      </td>
      <td style="text-align:left"><code>string</code> &#x414;&#x430;&#x442;&#x430; ISO 8601</td>
      <td style="text-align:left">
        <p>&#x414;&#x430;&#x442;&#x430; &#x43E;&#x431;&#x43D;&#x43E;&#x432;&#x43B;&#x435;&#x43D;&#x438;&#x44F;
          &#x434;&#x430;&#x43D;&#x43D;&#x44B;&#x445; &#x447;&#x430;&#x442;&#x430;.</p>
        <p>&#x417;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x435; &#x43D;&#x435;
          &#x437;&#x430;&#x434;&#x430;&#x435;&#x442;&#x441;&#x44F;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>deletedAt</code>
      </td>
      <td style="text-align:left"><code>string</code> &#x414;&#x430;&#x442;&#x430; ISO 8601</td>
      <td style="text-align:left">
        <p>&#x414;&#x430;&#x442;&#x430; &#x443;&#x434;&#x430;&#x43B;&#x435;&#x43D;&#x438;&#x44F;
          &#x43F;&#x43E;&#x43B;&#x44C;&#x437;&#x43E;&#x432;&#x430;&#x442;&#x435;&#x43B;&#x44F;,
          &#x435;&#x441;&#x43B;&#x438; &#x43E;&#x43D; &#x443;&#x434;&#x430;&#x43B;&#x435;&#x43D;.
          &#x418;&#x43D;&#x430;&#x447;&#x435; <code>null</code> .</p>
        <p>&#x417;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x435; &#x43D;&#x435;
          &#x437;&#x430;&#x434;&#x430;&#x435;&#x442;&#x441;&#x44F;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>active</code>
      </td>
      <td style="text-align:left"><code>boolean</code>
      </td>
      <td style="text-align:left">
        <p>&#x415;&#x441;&#x43B;&#x438; <code>true</code> &#x442;&#x43E; &#x447;&#x430;&#x442;
          &#x430;&#x43A;&#x442;&#x438;&#x432;&#x435;&#x43D; &#x438; &#x432; &#x43D;&#x435;&#x43C;
          &#x43C;&#x43E;&#x436;&#x43D;&#x43E; &#x43F;&#x435;&#x440;&#x435;&#x43F;&#x438;&#x441;&#x44B;&#x432;&#x430;&#x442;&#x44C;&#x441;&#x44F;.</p>
        <p>&#x417;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x435; &#x437;&#x430;&#x434;&#x430;&#x435;&#x442;&#x441;&#x44F;
          &#x43F;&#x440;&#x438; &#x441;&#x43E;&#x437;&#x434;&#x430;&#x43D;&#x438;&#x438;
          &#x447;&#x430;&#x442;&#x430; &#x438;&#x43B;&#x438; &#x43F;&#x440;&#x438;
          &#x440;&#x435;&#x434;&#x430;&#x43A;&#x442;&#x438;&#x440;&#x43E;&#x432;&#x430;&#x43D;&#x438;&#x438;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>firstCompanion</code>
      </td>
      <td style="text-align:left"><code>json</code> &#x41E;&#x431;&#x44A;&#x435;&#x43A;&#x442; &#x43F;&#x43E;&#x43B;&#x44C;&#x437;&#x43E;&#x432;&#x430;&#x442;&#x435;&#x43B;&#x44F;</td>
      <td
      style="text-align:left">
        <p>&#x41E;&#x431;&#x44A;&#x435;&#x43A;&#x442; &#x43F;&#x435;&#x440;&#x432;&#x43E;&#x433;&#x43E;
          &#x441;&#x43E;&#x431;&#x435;&#x441;&#x435;&#x434;&#x43D;&#x438;&#x43A;&#x430;
          (&#x43F;&#x43E;&#x43B;&#x44C;&#x437;&#x43E;&#x432;&#x430;&#x442;&#x435;&#x43B;&#x44F;)
          &#x432; &#x447;&#x430;&#x442;&#x435;.</p>
        <p>&#x417;&#x430;&#x434;&#x430;&#x435;&#x442;&#x441;&#x44F; &#x442;&#x43E;&#x43B;&#x44C;&#x43A;&#x43E;
          &#x43F;&#x440;&#x438; &#x441;&#x43E;&#x437;&#x434;&#x430;&#x43D;&#x438;&#x438;
          &#x447;&#x430;&#x442;&#x430;.</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>secondCompanion</code>
      </td>
      <td style="text-align:left"><code>json</code> &#x41E;&#x431;&#x44A;&#x435;&#x43A;&#x442; &#x43F;&#x43E;&#x43B;&#x44C;&#x437;&#x43E;&#x432;&#x430;&#x442;&#x435;&#x43B;&#x44F;</td>
      <td
      style="text-align:left">
        <p>&#x41E;&#x431;&#x44A;&#x435;&#x43A;&#x442; &#x432;&#x442;&#x43E;&#x440;&#x43E;&#x433;&#x43E;
          &#x441;&#x43E;&#x431;&#x435;&#x441;&#x435;&#x434;&#x43D;&#x438;&#x43A;&#x430;
          (&#x43F;&#x43E;&#x43B;&#x44C;&#x437;&#x43E;&#x432;&#x430;&#x442;&#x435;&#x43B;&#x44F;)
          &#x432; &#x447;&#x430;&#x442;&#x435;.</p>
        <p>&#x417;&#x430;&#x434;&#x430;&#x435;&#x442;&#x441;&#x44F; &#x442;&#x43E;&#x43B;&#x44C;&#x43A;&#x43E;
          &#x43F;&#x440;&#x438; &#x441;&#x43E;&#x437;&#x434;&#x430;&#x43D;&#x438;&#x438;
          &#x447;&#x430;&#x442;&#x430;.</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>externalMetadata</code>
      </td>
      <td style="text-align:left"><code>json</code>
      </td>
      <td style="text-align:left">
        <p>&#x41F;&#x440;&#x43E;&#x438;&#x437;&#x432;&#x43E;&#x43B;&#x44C;&#x43D;&#x44B;&#x435;
          &#x434;&#x430;&#x43D;&#x43D;&#x44B;&#x435; &#x43E; &#x447;&#x430;&#x442;&#x435;
          &#x432; &#x432;&#x438;&#x434;&#x435; &#x43A;&#x43B;&#x44E;&#x447;-&#x437;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x435;
          &#x441; &#x432;&#x43E;&#x437;&#x43C;&#x43E;&#x436;&#x43D;&#x44B;&#x43C;&#x438;
          &#x432;&#x43B;&#x43E;&#x436;&#x435;&#x43D;&#x438;&#x44F;&#x43C;&#x438;.
          &#x42D;&#x442;&#x438; &#x434;&#x430;&#x43D;&#x43D;&#x44B;&#x435; &#x43C;&#x43E;&#x433;&#x443;&#x442;
          &#x432;&#x438;&#x434;&#x435;&#x442;&#x44C; &#x441;&#x43E;&#x431;&#x435;&#x441;&#x435;&#x434;&#x43D;&#x438;&#x43A;&#x438;
          &#x447;&#x430;&#x442;&#x430;.</p>
        <p>&#x417;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x435; &#x43C;&#x43E;&#x436;&#x435;&#x442;
          &#x437;&#x430;&#x434;&#x430;&#x432;&#x430;&#x442;&#x44C;&#x441;&#x44F;
          &#x43F;&#x440;&#x438; &#x441;&#x43E;&#x437;&#x434;&#x430;&#x43D;&#x438;&#x438;
          &#x447;&#x430;&#x442;&#x430; &#x438;&#x43B;&#x438; &#x43F;&#x440;&#x438;
          &#x440;&#x435;&#x434;&#x430;&#x43A;&#x442;&#x438;&#x440;&#x43E;&#x432;&#x430;&#x43D;&#x438;&#x438;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>privateExternalMetadata</code>
      </td>
      <td style="text-align:left"><code>json</code>
      </td>
      <td style="text-align:left">
        <p>&#x41F;&#x440;&#x43E;&#x438;&#x437;&#x432;&#x43E;&#x43B;&#x44C;&#x43D;&#x44B;&#x435;
          &#x434;&#x430;&#x43D;&#x43D;&#x44B;&#x435; &#x43E; &#x447;&#x430;&#x442;&#x435;
          &#x432; &#x432;&#x438;&#x434;&#x435; &#x43A;&#x43B;&#x44E;&#x447;-&#x437;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x435;
          &#x441; &#x432;&#x43E;&#x437;&#x43C;&#x43E;&#x436;&#x43D;&#x44B;&#x43C;&#x438;
          &#x432;&#x43B;&#x43E;&#x436;&#x435;&#x43D;&#x438;&#x44F;&#x43C;&#x438;.
          &#x42D;&#x442;&#x438; &#x434;&#x430;&#x43D;&#x43D;&#x44B;&#x435; &#x43C;&#x43E;&#x436;&#x435;&#x442;
          &#x443;&#x432;&#x438;&#x434;&#x435;&#x442;&#x44C; &#x442;&#x43E;&#x43B;&#x44C;&#x43A;&#x43E;
          &#x441;&#x435;&#x440;&#x432;&#x435;&#x440; (admin) &#x43F;&#x440;&#x438;&#x43B;&#x43E;&#x436;&#x435;&#x43D;&#x438;&#x44F;.</p>
        <p>&#x417;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x435; &#x43C;&#x43E;&#x436;&#x435;&#x442;
          &#x437;&#x430;&#x434;&#x430;&#x432;&#x430;&#x442;&#x44C;&#x441;&#x44F;
          &#x43F;&#x440;&#x438; &#x441;&#x43E;&#x437;&#x434;&#x430;&#x43D;&#x438;&#x438;
          &#x447;&#x430;&#x442;&#x430; &#x438;&#x43B;&#x438; &#x43F;&#x440;&#x438;
          &#x440;&#x435;&#x434;&#x430;&#x43A;&#x442;&#x438;&#x440;&#x43E;&#x432;&#x430;&#x43D;&#x438;&#x438;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>lastMessage</code>
      </td>
      <td style="text-align:left"><code>json</code> &#x41E;&#x431;&#x44A;&#x435;&#x43A;&#x442; &#x441;&#x43E;&#x43E;&#x431;&#x449;&#x435;&#x43D;&#x438;&#x44F;</td>
      <td
      style="text-align:left">&#x41E;&#x431;&#x44A;&#x435;&#x43A;&#x442; &#x43F;&#x43E;&#x441;&#x43B;&#x435;&#x434;&#x43D;&#x435;&#x433;&#x43E;
        &#x441;&#x43E;&#x43E;&#x431;&#x449;&#x435;&#x43D;&#x438;&#x44F; &#x432;
        &#x447;&#x430;&#x442;&#x435;, &#x435;&#x441;&#x43B;&#x438; &#x447;&#x430;&#x442;
        &#x43D;&#x435; &#x43F;&#x443;&#x441;&#x442;&#x43E;&#x439;.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>notReadByFirstCompanionMessagesCount</code>
      </td>
      <td style="text-align:left"><code>number</code> integer</td>
      <td style="text-align:left">&#x41A;&#x43E;&#x43B;&#x438;&#x447;&#x435;&#x441;&#x442;&#x432;&#x43E;
        &#x441;&#x43E;&#x43E;&#x431;&#x449;&#x435;&#x43D;&#x438;&#x439; &#x43E;&#x442;
        &#x432;&#x442;&#x43E;&#x440;&#x43E;&#x433;&#x43E; &#x441;&#x43E;&#x431;&#x435;&#x441;&#x435;&#x434;&#x43D;&#x438;&#x43A;&#x430;
        (<code>secondCompanion</code>) &#x43D;&#x435;&#x43F;&#x440;&#x43E;&#x447;&#x438;&#x442;&#x430;&#x43D;&#x43D;&#x44B;&#x435;
        &#x43F;&#x435;&#x440;&#x432;&#x44B;&#x43C; &#x441;&#x43E;&#x431;&#x435;&#x441;&#x435;&#x434;&#x43D;&#x438;&#x43A;&#x43E;&#x43C;
        (<code>firstCompanion</code>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>notReadBySecondCompanionMessagesCount</code>
      </td>
      <td style="text-align:left"><code>number</code> integer</td>
      <td style="text-align:left">&#x41A;&#x43E;&#x43B;&#x438;&#x447;&#x435;&#x441;&#x442;&#x432;&#x43E;
        &#x441;&#x43E;&#x43E;&#x431;&#x449;&#x435;&#x43D;&#x438;&#x439; &#x43E;&#x442;
        &#x43F;&#x435;&#x440;&#x432;&#x43E;&#x433;&#x43E; &#x441;&#x43E;&#x431;&#x435;&#x441;&#x435;&#x434;&#x43D;&#x438;&#x43A;&#x430;
        (<code>firstCompanion</code>) &#x43D;&#x435;&#x43F;&#x440;&#x43E;&#x447;&#x438;&#x442;&#x430;&#x43D;&#x43D;&#x44B;&#x435;
        &#x432;&#x442;&#x43E;&#x440;&#x44B;&#x43C; &#x441;&#x43E;&#x431;&#x435;&#x441;&#x435;&#x434;&#x43D;&#x438;&#x43A;&#x43E;&#x43C;
        (<code>secondCompanion</code>)</td>
    </tr>
  </tbody>
</table>

## Создание чата

По умолчанию пользователи могут сами создавать чаты и общаться с любыми пользователями, но у сервера \(админа\) есть возможность создавать чаты между пользователями принудительно.

Такой функционал особенно полезен когда правила вашего приложения позволяют пользователю начать переписку с другим только при соблюдении определенных правил.

### Параметры

| Поле | Тип | Обязательно | Описание |
| :--- | :--- | :--- | :--- |
| `firstCompanionId` | `string` | Да | ID первого собеседника в чате |
| `secondCompanionId` | `string` | Да | ID второго собеседника в чате |
| `externalMetadata` | `json` | Нет | Произвольные данные |
| `privateExternalMetadata` | `json` | Нет | Произвольные данные |

### Пример

```typescript
import {MessembedAdminSDK, Chat} from 'messembed-sdk';
const messemgedAdminSdk = new MessembedAdminSDK(...);

const chat: Chat = await messemgedAdminSdk.createChat({
    firstCompanionId: '1',
    secondCompanionId: '2',
});

```




### Домашнє завдання

**Додати до календаря події!**  
Це можуть бути якісь плани (*не обов'язково ті, що обов'язково* збудуться, перепрошую за каламбур) — відвідати якийсь концерт чи футбольний матч, досягнути чогось важливого (планка 15 хвилин) до якогось конкретного дня, просто зустрітись з друзями, поїхати відпочивати тощо. Можливо варто окрім назви події і детальнішого опису (чому? як?) додати ще аватари учасників з посиланнями на Фейсбук, наприклад. [**Semantic-UI**](https://semantic-ui.com/) має все необхідне, щоб можна було створити такий інтерфейс. Тобто після кліку по конкретному дню (його очевидно треба якось виділити стилем — зробити жирним чи додати якийсь кольоровий фон) може виїхати **Sidebar** або вискочити **Modal** — що вважаєш за потрібне. І в тому вже блоці може бути заголовок з назвою події, потім опис події, а потім, наприклад, аватари учасників. Можливо в самому календарі при наведенні на день, на який запланована подія, з'явиться ще **Popup** з назвою тої події.  
**До чого тут JavaScript?**  
Нууууу, треба спочатку десь зберегти список всіх подій. Імовірно це буде масив об'єктів по типу такого (для прикладу):
```
[{
    date: "2017-07-20",
    eventId: 0,
    event: "Come up with a homework idea",
    description: "Well, yeah, you know. You've got to engage the audience, inspire them to do something if not great than warm at least. Something you'll be glad to check on later."
  },
  {
    date: "2017-07-22",
    eventId: 0,
    event: "Parent's birthday",
    description: "Yeah, both of them. Mom wanted a new bag — have no idea where to get one. Zara? Will see. Anyway, yeah, both of them, same day. Have to check those homeworks though."
  },
  {
    date: "2017-07-22",
    eventId: 1,
    event: "Friends' party",
    description: "Go see some friends since you're visiting Ternopil, grab some beer, talk about life and how everything is shit.",
    participants: [{
        name: "Volodymyr Stoyko",
        url: "https://www.facebook.com/corest",
        avatar: "https://scontent-cdt1-1.xx.fbcdn.net/v/t1.0-9/19959082_10210721389766187_6789533543778955899_n.jpg?oh=204032e8f826891d02c566e5cdcdf384&oe=59C40BCC"
    }]
  }
]
```
Потім варто позначити в календарі ті дати, на які заплановані події. Тобто, коли складається кусок html для конкретного дня треба перевірити [чи є така дата в масиві](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/find), і якщо є, то включити в html ще кусок, який намалює [кружечок](https://semantic-ui.com/elements/label.html#circular). Потім на всі кружечки треба навішати клік-івент-лістенер, який буде відкривати модальне вікно і вказувати необхідну дату. Потім, вже при розгортанні [сайдбару](https://semantic-ui.com/modules/sidebar.html) чи [модального вікна](https://semantic-ui.com/modules/modal.html) — тобто при onShow — варто знову піти в масив по ту дату і дістати інформацію про ту одну конкретну подію, скласти з того кусок html і ['інжектнути'](http://api.jquery.com/html/) в контент-блок модалки чи сайдбару. Ну і раз це все відбувається на клієнті, то без JavaScript не обійтись. Пам-пам!
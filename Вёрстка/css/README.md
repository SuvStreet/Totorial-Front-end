# CSS - Cascad Style Sheets - каскадные таблицы стилей

Подключение файла css `<link rel="stylesheet" href="путь к css файлу" />`

* Файл обнуление стилей в css [sass](https://github.com/SuvStreet/Totorial-Front-end/blob/main/%D0%92%D1%91%D1%80%D1%81%D1%82%D0%BA%D0%B0/css/resetStyles.sass)
* Файл работа с текстом [styleFont.md](https://github.com/SuvStreet/Totorial-Front-end/blob/main/%D0%92%D1%91%D1%80%D1%81%D1%82%D0%BA%D0%B0/css/styleFont.md)
* Файл работа с блоком [styleDiv.md](https://github.com/SuvStreet/Totorial-Front-end/blob/main/%D0%92%D1%91%D1%80%D1%81%D1%82%D0%BA%D0%B0/css/styleDiv.md)
* Файл работа с background [background.md](https://github.com/SuvStreet/Totorial-Front-end/blob/main/%D0%92%D1%91%D1%80%D1%81%D1%82%D0%BA%D0%B0/css/background.md)

---

  * Селектор - это обращение, селектор класса - обращение к классу:
```css
.имя_класса{
  параметр: значение;
}
```

  * Приоритет будет выше:
```css
тег.имя_класса{
  параметр: значение;
}
```

  * Применить параметры к нескольким классам:
```css
.имя_класса, .имя_класса{
  параметр: значение;
}
```

  * Применение параметров только тегам только в определённом классе:
```css
.имя_класса тег{
  параметр: значение;
}
```

  * Применение параметров только к первому вложению тегов:
```css
.имя_класса>тег{
  параметр: значение;
}
```


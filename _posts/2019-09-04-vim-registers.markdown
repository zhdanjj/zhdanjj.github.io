---
layout: post
title:  "Vim регистры"
tags: [vim]
---

## Безымянный `"`
В него копируется текст при использовании команд `d`, `c`, `s`, `x`,
причём даже если при этом был указан конкретный другой регистр (например `+`),
кроме `_`. Из него же берётся текст при вставке без указания регистра.

## Нумерованные регистры `"0` - `"9`
В `"0` сохраняется только скопированный текст и только если не был указан регистр.
В `"1` сохраняется только удалённый текст и только если он содержит больше
одной строки (кроме случае, если при удалении использовались операторы `%`, `(`, `)`, `/`,
`?`, `n`, `N`, `{` и `}`.
При каждом последующем таком удалении содержимое смещается в следующий регистр,
а из `"9` содержимое удаляется.

## Регистр мелкого удаления `"-`
В него попадает удалённый или замещённый текст, содержащий меньше одной строки
если при удалении не был указан регистр.

## Именованые регистры `"a` - `"z`
Просто регистры для хранения текста. Если при сохранении использовать
строчную букву, то содержащийся текст перезатрётся, а если заглавную
— добавится к существующему.

## Регистры только для чтения `":`, `".`, `"%`
`".` содержит последний вставленный текст
`"%` содежит имя открытого файла
`":` содежит последнюю запущенную команду

## Регистр альтернативного файла
Хранит имя файла, который открывается по `ctrl-^`

## Регистр выражений `"=`
Позволяет производит вычисления и выводить результат прямо в текст

## Selection и drop регистры `"*`, `"+`, `"~`
`"*` и `"+` хранят в себе текст из gui. К примеру, если в Firefox выделить
текст и нажать `ctrl-c`, то текст окажется в этих регистрах
В windows отличий между ними нет. В linux первый содержит `PRIMARY` буфер (который хранит то,
что просто выделено мышкой), а второй `CLIPBOARD` (который `ctrl-c` - `ctrl-v`)
`"~` содержит то, что было перетащено мышкой, работает только в gtk gui

## Регистр чёрная дыра `"_`
При записи в него ничего не происходит, при ничего не возвращается.
Можно использовать чтобы не перезаписывались нумерованные регистры

## Регистр последнего поискового запроса
Содержит последний поиск

---
title: "Amazon Fire TV - первые впечатления"
date: 2014-05-02T14:20:40-05:00
draft: false
tags: ["разное"]
slug: amazon-fire-tv-piervyie-viepachtlieniia
---

После того, как проверенная годами, любовно хакнутая ATVv2 стала показывать признаки умирания и устаревания (медленная она, только 720p и стала глючить), встал вопрос ребром - куда податься. После того как стало понятно, что выхода jailbreak для ATVv3 ждать нет смысла, возникло желание найти адекватную замену. Требования были такие - должно работать с netflix и XBMC, должно работать быстро и надежно, играть и стримить 1080p и все это должно удобно управляется пультом.

<!--more-->
В процессе экспериментов начавшихся с [Raspeberry Pi](http://www.raspberrypi.org), перешедших на андроидовые стики и дошедших до [Gbox MX2](http://www.amazon.com/G-Box-Midnight-MX2-Android-Streaming/dp/B00CH643A8), я так и не смог получить полного удовлетворения. Pi несколько тормознут в качестве xbmc проигрывателя, проблематичен с т.з. пульта (если ТВ без CEC) и совсем не дружит с Netflix. Стики это вообще ужас и кошмар. GBox в этом плане гораздо лучше и XBMC на нем вполне адекватен, но только 720p. Netflix тоже есть, но какой-то кривой и плохо адаптированный под пульт. Новый поставить из google play можно, но он не работает совсем. Кроме того, с этим Gbox время от времени происходит странное - он забывает настройки и теряет установленные программы. Такое у меня было дважды за 2 месяца использования, что не смертельно, но идея переустановки всего раз в месяц меня совсем не радует. Кроме того, у Gbox есть какая-то проблема понимания режима TV и иногда (часто) после включения телевизора они не могут договорится между собой и приходится перегружать Gbox для починки.

Тем не менее, GBox вполне рабочее решение и с ним можно жить и радоваться. Но с выходом [Amazon FireTV](http://www.amazon.com/Fire-TV-streaming-media-player/dp/B00CX5P8FC) захотелось посмотреть на этого зверя вблизи. По отзывам и обзорам эта коробочка казалось интересной и подходящей для моего случая. Ну и цена в $99 тоже ощущалась как адекватная.

![](/images/posts/firetv.png#floatright)
Не буду повторять стандартные обзоры и из общего скажу только то, что она очень шустрая по сравнению со все тем, что я пробовал ранее. Пультик мелкий, но приятный и довольно ухватистый. Базовая настройка практически сведена к нулю и после включения все сразу работает.

Как вы помните, для меня главным вопросом было Netflix и XBMC. С Netflix все примерно на 8/10. Интерфейс вполне удачно работает с пультом, качество проигрывания лучше чем на ATV и намного лучше чем на GBox. Версия Netflix относительно свежая (с профилями) и все работает. 2 бала я скинул за то, что нет такой вылизаности интерфейса как на ATV. Справедливости ради, первый день я так и не смог запустить Netflix, но похоже это была проблема самого сервиса Netflix а не амазона. Кстати, тут мой первый наезд - этот fire пытается быть очень простым устройством для очень простых домохозяек. Когда все в порядке то так оно и есть. Никакого сокровенного знания андроидов не надо чтоб ходить пультиком по меню. Но вот когда происходит нечто неожиданное (как с Netflix) то приходится "гиковать". Надо было найти то место, где можно очистить кэш и перезапустить программу. Конечно, ничего сложного, но несколько ниже заявленного уровня простой теле-приставки.

XBMC ставится легко если вы гик или у вас есть понимание того, что вы делаете. Процесс [подробно описан](http://wiki.xbmc.org/index.php?title=Amazon_Fire_TV) и даже есть [инструкция для простых людей](http://patnotebook.com/installing-xbmc-on-amazon-fire-tv/). У меня весь процесс установки (я поставил обе версии - 13 и 12) занял минут 5. Еще несколько минут заняла установка Autopilot (автоматический запуск XBMC после включения) и ритуальный танец с бубном вокруг llama (переназначить поведение кнопки Home). Я думаю, что если кто знаком с андроидом ближе меня (я совсем мало знаком) то вопросов вообще не возникнет. У меня были совсем тривиальные проблемы от общего непонимания, например как выдрать apk из google play, что такое этот side load, и прочее вполне примитивное. В общем на все про все, с гуглением и кастомизациями, у меня наверное ушло пол часа.

Работа XBMC нареканий не вызывает. Все очень быстро и все работает. 1080p проигрывается без проблем, никакой задержки звука (народ в форумах на это пенял) я не обнаружил, пульт [прекрасно совместим](http://wiki.xbmc.org/index.php?title=Alternative_keymaps_for_Fire_TV_remote) с XBMC, короче сплошное наслаждение и радость использования. Одна проблема, которая пока похоже не решена (я пробовал и самые свежие билды 13) - звук не управляется с пульта fire. Надеюсь проблема временная и в XBMC ее починят.

В отличии от прочих андроидов что я пробовал под TV, в Fire wifi работает реально шустро и N поддерживается без проблем. Коробочка не греется и за все 4 дня использования никаких глюков/перезагузок не произошло. Вообще, после начальной настройки я ее ни разу не перегружал и ей в кишочки не лазил. Из того, что лично мне не особо надо, но я запустил и пробовал - Plex работает красиво и быстро. Проигрывание фильмов и сериалов из Prime тоже не вызывает нареканий.

Вдогонку к самому Fire я заказал и игровой контроллер. Даже не знаю что про него рассказать - он работает. Довольно прикольно было погонять в Асфальт8 на большом экране, хотя я не особый игроман. Контроллер этот оказался довольно тяжелым и крупным по сравнению с тем, что у меня был в PS3. Кстати, по слухам Fire работает и с другими BT игровыми контроллерами.

Из экзотического - AceStream работает и [TorrentTV](http://torrent-tv.ru) против него тоже работает, гораздо лучше чем на GBox (на Fire нет проблем с затыканием на HD каналах). Из странного - это амазон и у него свой store который совсем не гугловой. Про ваши покупки у гугла он, разумеется, ничего не знает и иногда приходится платить второй раз за то, что уже куплено под другим андоридом. Я купил Plex, но настоящих денег на это не потратил т.к. с новым Fire вам дают $10 кредита и плюс еще $10 за контроллер.

Теперь о плохом - отсутствие NBA канала на Fire это конечно безобразие. Из всего, что у меня под телевизором только ATV это умеет, но умеет плохо и глюкаво, но Fire даже так не может :(

Пока рано делать вывод, но общее впечатление весьма и весьма положительное. На мой взгляд Fire TV это лучшая запускалка для XBMC и Netflix что я пробовал. Скорость этой коробочки тоже выше всяких похвал. Ну и андроид на борту вполне дружественен для "нестандартных использований" и таких проблем как с джейлом ATV тут нет и следа.
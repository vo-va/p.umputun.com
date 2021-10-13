---
title: "Год с Go в реальной работе - там водятся драконы."
date: 2017-04-18T14:20:40-05:00
draft: false
tags: ["для гиков", "технические темы"]
slug: god-s-go-v-riealnoi-rabotie
---

![](/images/posts/zxo8z-201605-03124845-4tnxv.png#floatright)

Примерно год назад, в заметкe [Go или не Go?](http://p.umputun.com/2016/05/03/go-ili-nie-go/) я легкомысленно пообещал рассказать как показал себя Go в реальной работе. Пришло время исполнять взятые на себя обязательства.

За отчетный период с языком мало что поменялось, но в экосистеме произошло заметное улучшение - JetBrains взялись за Go по большому и иx [Gogland IDE](https://www.jetbrains.com/go/) дошла до состояния "этим можно пользоваться". Штука у них получается неплохая и заметно, что разработка идет в правильные стороны. Я перешел на Gogland на своем основном рабочем компьютере, где провожу 80% времени. На лэптопе продолжаю использовать [Atom](http://atom.io) + [go-plus](https://atom.io/packages/go-plus) в основном по причине неуемного аппетита Gogland, который очень любит кушать батарейки.

За этот год я завершил довольно крупный проект, полностью на Go. Это около двух десятков сервисов разной степени замысловатости, отвечающих как за массивные операции по обработке данных, так и за весьма нетривиальную логику анализа этих данных на лету и в режиме предварительной обработки. Все это хозяйство обладает REST (и не только) API и обложено разными системными сервисами большая часть которых тоже на Go.

В проекте, кроме меня, постоянно трудятся еще пара программистов и пара бизнес аналитиков. Время от времени подключаются еще полтора программиста под разные непрофильные задачи. Все программисты пришли в проект без всякого предыдущего опыта на Go, аналитики (да, они у нас тоже иногда должны видеть код) про Go раньше не слыхали.

Мое субъективно-экспертное ощущение от Go, на фоне всего перечисленного:

- это превосходный язык для введения в проект новых людей. Даже при том, что у меня уже появились "лучшие практики" и более мягкие рекомендации "как делать красиво", передача этого опыта новичкам не вызывает никаких проблем. Даже самые медленные из этих программистов становятся производительными в новом языке и в новой кодовой базе в худшем случае за неделю.

- Сопровождаемость и читабельность кода очень пристойная. За исключением одного сервиса, во все остальные возвращаться легко и приятно. Через год я могу не напрягаясь читать свой старый код и, самое главное, код коллег. И обратное верно.

- Этот исключительный сервис, с которым все не очень хорошо - это в сторону недостатков языка и/или моего умения это все готовить. Там был некий логически не очень сложный процессор который был задуман как средство обработки нескольких десятков видов данных в общем виде. С общим видом в Go дела обстоят не самым лучшим образом. Конкретно в этом проекте была сделана попытка активного использования reflection для выражения этой "общности" и результат, хотя и работает, не вызывает у меня теплых чувств. Скорее всего это была ошибка. В процессе написания кода оно ощущалось как почесывание левой ногой правого уха, а через пол года превратилось в мистическое нечто. Вероятнее всего, эту часть я перепишу, как появится время, с использованием менее радикальных методов.

- После года использования Go стали сильно раздражать поборники "истинного пути" которые на каждом интернет-углу рассказывают, что все надо делать только и исключительно с stdlib. Я не понимаю, кто все эти люди и откуда у них есть время на постоянное написание своих велосипедов. Несомненно, количество внешних зависимостей у всех моих Go проектов несравненно меньше чем в моих-же проектах на других языках, но они есть и их (иногда) не сосчитать на пальцах одной руки(2х рук обычно хватает). Да, никаких фреймворков я не использую, но идея разбирать рауты регекспами, или идея отказа от нормальных асертов в тестах, или накручивание разного кода для вменяемого разбора флагов и конфигураций мне чужда.

- Go, совершенно явно, подталкивает мой дизайн в сторону менее глубоких абстракций. Это, насколько я могу судить, идет результату на пользу с т.з. понятности и прямоты кода. Выделение абстракций чаще всего происходит только тогда, кода такая необходимость возникает в реальности.

- За это время я активно внедрил целое семейство линтеров (анализаторов кода) в наш процесс сборки и тестирования и сделал их прохождение обязательным условием. Они, с одной стороны, реально полезны и, как мне кажется, абсолютно необходимы в жизни, но с другой - на корню убивают довод о мгновенной компиляции в Go. Ну да, мой типовой сервис компилируется за пару-тройку секунд, но потом линтеры занимают 2 минуты. Не то чтоб это было для меня особой проблемой, но досадно. Особенно досадно на фоне того, что все юнит тесты обычно в разы быстрее.

- Многословность кода в части обработки ошибок на практике оказалась скорее благом, чем проклятием. Это, как показал мой опыт, не снижает читабельность, но наоборот - выпрямляет логику и позволяет легко представить, что именно и как именно происходит. Я говорю о чужом коде, или о своем 6-ти месячной давности, когда прочитать и понять это дело первой важности.

- Мои ранние попытки и недавние попытки одного из вновь пришедших коллег по внедрению "правильных FP элементов" в Go, я оцениваю как полностью провалившийся эксперимент. От этих попыток удержаться было трудно, но породили они чудовищ и уродцев, которых мы, по общему консесусу, истребили почти полностью.

- Минимальные FP элементы оказались вполне приемлемы, и передача и возврат функций - это у нас обычное дело. Из относительно сложных результатов ранних экспериментов выжила только flow (piplene) штука, но и она на грани драматического переписывания и значительного упрощения, вызванного появлением вменяемых context в одной из относительно свежих версий Go.

- асинхронное программирование в Go (горутины и каналы) за это время стало не столько средством для достижения паралельности, но средством для concurrent дизайна. Тут произошел определенный сдвиг в фундаментальном отношении к горутинам - от "это как потоки, только легче" к "это строительные блоки выражения мысли и реализации логики и взаимодействия". Такое переключение восприятия заняло время и за неделю человек, пришедший с java/python, это вряд-ли осознает.

- За это время мне пришлось пару раз заниматься глубоким и вдумчивым профилированием некоторых критичных, по времени отклика и времени получения полного результата, сервисов. Процесс не особо отличается от подобного в Java и поле для оптимизаций тоже широко. Несомненно, это не простая задача, если речь не идет о тривиальных оптимизациях, но и в прочих языках она ничуть не проще. Хотя отсутствие графического варианта профайлера для Go, типа как мой любимый JProfile в альтернативном мире, поначалу напрягало.

- Ошибкой был начальный выбор gin. Я его выбрал исключительно по причине похожести на то, что я ожидал год назад от таких библиотек, но количество проблем, особенно после внедрения вендоринга, доказало, что это была не самая лучшая идея. Несколько месяцев назад мы завершили переход на легкий chi который, с этой точки зрения, гораздо правильней и прямей, хотя чувак поддерживающий этот chi слишком ... резкий и решительный.

- Модные в go–мире идеи включения контекста в ошибки пока не прижились. Это я о штуках типа [pkg/errors](https://dave.cheney.net/2016/06/12/stack-traces-and-the-errors-package). У меня критические ошибки раскручивают стек на уровне логера, а некритические логируются прямо в месте их возникновения и этого пока вполне хватает.

- Никакие продвинутые логеры у меня не прижились. Используем слегка расширенную версию самого примитивного [The simplest thing that could possibly work](https://github.com/hashicorp/logutils), хотя необходимость писать `log.Print("[WARN] blah")` первые пару недель сводит с ума людей пришедших из мира структурированных логеров.

- Вполне жизнеспособной оказалась идея автоматической генерации новых сервисов. По сути, мы генерируем скелетик сервиса, включающий в себя все, что надо для проекта, который полностью готов к работе. Там main с предварительной подготовкой окружения и минимальным (и общим) внедрением всех наших обычных зависимостей, шаблон для типового repository, шаблон для типовых REST и прочих сервисов. Плюс к этому вся обвязка в виде Dockerfile, compose, CI конфигов, заготовок для мониторинга, регистрации и прочее.

- С пошаговой/интерактивной отладкой все еще ой. Gogland пытается это довести до человеческого вида, но пока это работает весьма условно. Мне, как "ветерану" существования/выживания в го-мире это уже кажется данностью, но свежих людей напрягает.

- Обнаружился ряд задач, которые оказалось практически нереально перенести с большого энтерпрйаз языка (java и спец. библиотеки / фреймворки) на Go. Такая попытка предпринималась одним из свежих перебежчиков не для фана, но как подготовка к новому мажорному релизу. Натолкнулась на непреодолимые сложности связанные с отсутствием целого ряда библиотек для Go в области определенных финансовых вычислений, а также в неожиданных местах, типа отсутствия пристойной SAML реализации для Go.

- Некоторые из библиотек которые мы должны использовать оказались довольно ... дикими. Например, AWS Go SDK в части работы с S3, EC2 и SQS - это еще тот подарок. Версия для java тоже не фонтан, но Go версию точно писали хищники для чужих.

- Обнаружилось неожиданное отсутствие пристойных решений для довольно стандартных случаев. Например, реализация RPC поверх RMQ. Да, есть одна, но ее проще убить, чем отмыть.

- Некоторые библиотеки, из тех что лучше самому не писать никогда, проявляют чрезмерную активность, иногда калечащую обратную совместимость. Это, скорее исключение чем правило, но встречаются такие авторы, которые релизят слишком часто и не очень консервативны. Это не особая проблема для меня (все давно и надежно завендорено) но остается работа по проверке того, что там такого нового, зачем, почему и как оно на меня может повлиять. На практике это не слушком болезненно из за небольшого числа зависимостей, но после spring-boot с его любовно подобранными, стабильными и совместимыми версиями, это конечно шаг в прошлое.

- Самым большим практическим WTF в Go для меня стало вовсе не отсутствие generics или исключений, но отсутствие нормальных, строго типизированных enum.

- Замечал не один раз, как новые в Go люди пытаются использовать свой опыт из прочих языков в Go. Обманчивая схожесть с прочими C-образными языками на фоне нежелания прочитать даже минимальную документацию приводит к забавным  `select` в цикле и с активным default. Они, конечно, забавны  со стороны, но вызывают необоснованные наезды типа "в этом вашем го мой простой TCP ридер вдруг скушал все CPU".

И в завершение - при всем при этом мое, годовой давности, впечатление "На Go можно писать код, можно читать код и оба эти процесса на удивление приятны" **остается неизменным**. Возможно, я поспешил с "Go очень простой язык. T.e. совсем, совсем простой..". Да, он с виду прост, но иногда, за границами этой простоты водятся драконы.
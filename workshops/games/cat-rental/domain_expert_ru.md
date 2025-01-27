# Воркшоп по Event Storming - Аренда котов

Время на прочтение - 7,5 мин.

## Доменный эксперт — общая информация

Вы — владелец успешного бизнеса по аренде котов, который был основан 10 лет назад. У вас есть 30 магазинов по всей стране, в которых любители котов могут арендовать себе домашнего любимца. До сих пор ваш бизнес успешно управляется вручную.

Ваши конкуренты не дремлют, повсюду создаются кафе с котами, собаками и даже енотами. Чтобы опередить конкурентов, вы хотите создать IT систему, которая поможет развивать бизнес. Вы наняли группу компьютерщиков и они пригласили вас поучаствовать в каком-то странном мероприятии, типа воркшопа, на котором вы поделитесть с ними своими знаниями удобным и быстрым способом. Звучит неплохо!

Несмотря на то, что ваш имеющийся бизнес построен на стационарных офлайновых точках аренды котов, вы хотите создать новый канал продаж через интернет, чтобы вашим клиентам было удобнее выбирать котов, резервировать их и оплачивать аренду. В процессе диджитализации компании вы хотите интегрироваться с внешней системой BI, чтобы у конкурентов не было шансов.
 
Помогите айтишникам. Расскажите все, что знаете про свой бизнес. Если они спросят о чем-то, чего нет в описании ниже — импровизируйте, дайте наилучший ответ, который сможете придумать. Помните, что это всего лишь воркшоп, у нас немного времени, так что постарайтесь сдерживать свою фантазию :)

Постарайтесь вместе с командой создать общий язык. Можно создать словарик часто используемых слов. Термины долджны быть понятны всем участникам. Когда будете писать стикеры во время сессии Event Storming, используйте этот словарь, чтобы названия были непротиворечивыми.

__Никому не показывайте эту инструкцию. Объясните требования, описанные ниже, своими словами. Перефразируйте их.__

Ниже информация, которую вы собрали с коллегами, когда готовились к воркшопу.

## Бизнес

* Мы хотим создать систему для сети магазинов аренды котов.
* Помните, что это сеть из нескольких магазинов, а не единственный магазин.
* В каждом магазине разный набор котов.
* Чтобы контролировать количество на складе мы отслеживаем метрики: Общее количество котов (на складе + в аренде), Количество на складе, Количество в аренде, Зарезервированное количество.
* Когда мы сдали кота в аренду, нужно изменить доступное количество котов на складе.
* На сегодня у нас открыто 30 магазинов аренды в 20 городах страны.
* В каждом магазине есть администратор, который ведет учет. Это всегда один из сотрудников магазина.
* Во всей сети есть 1 глобальный администратор, который может заводить новые магазины в системе.

## Коты

* Мы сдаем котов в аренду.
* Все коты привиты и чипированы
* У каждого кота есть ошейник с кличкой.
* На каждом ошейнике напечатан штрих-код с уникальным номером. В магазине есть сканер штрих-кодов.
* Сканер штрих-кодов работает как обычная клавиатура. Он подключается к компьютру по USB порту, мы сканируем код и результат (число) вводится в компьютер.
* Иногда наши клиенты возвращают больных или сильно встревоженных котов. Бывают, что у животных находим блох. Это большая проблема нашего бизнеса.

## Цены

* У каждой породы котов своя цена.
* Цены на котов одинаковые во всей сети.
* Иногда мы делаем скидки на определенную сумму или процент.
* Все платежи принимаются только в рублях.
* Мы думаем о том, чтобы ввести промокоды в систему, но это не обязательно.
* Срок аренды по умолчанию — 14 дней.
* Если клиент хочет оставить кота на 30 дней, ему нужно доплатить 1000 р. во время оформления аренды.
* Продление аренды оформляется в чеке отдельной позицией с названием "Продление срока аренды".
* Если клиент задерживает кота дольше срока, мы добавляем его в Список Должников и начисляем штрафы.
  * До 5 дней - 1500 р.
  * До 20 дней - 10000 р.
  * Более 20 дней - 25000 р.
* Клиент не может брать других котов в аренду, пока он в Списке Должников. 
* Чтобы удалить клиента из Списка Должников, он должен вернуть кота и погасить задолженность.

## Офлайновый магазины аренды

* В каждом магазине есть фискальный принтер чеков, который подключен к компьютеру. На нем система печатает чеки.
* Поставщик принтера чеков предоставляет библиотеку, с которой наша система может легко интегрироваться.
* Заказчик оплачивает аренду каждого кота отдельно.
* Доступные способы оплаты:
  * Наличные
  * Карта
  * Деньги, доступные на онлайн счете клиента
	* Подарочный сертификат

## Онлайн магазин

* Клиент может зарегистрироватья и зайти в онлайн магазин.
* Клиент может просматривать котов, доступных в своем городе, сгруппированных по породам.
* Клиент может посмотреть детали конкретного кота с его фотографией, описанием характера, родословной и отзывами предыдущих клиентов.
* Клиент может зарезервировать понравившегося ему кота в выбранном офлайн магазине.
* Максимальный срок резерва — 2 дня.
* После резерва мы привозим кота в выбранный магазин в течение 1 часа, если понравившегося кота нет в выбранном магазине, но есть в другом.
* Если клиент не забирает кота в течение 2 дней, резерв отменяется и кот становится доступным для других клиентов.
* Мы не берем денег за резервирование. Однако, надо подумать как избежать ситуации, если дети-хулиганы зарезервируют всех котов и сломают нам бизнес.
* Клиент может пополнить свой счет в онлайн магазине и использовать его для оплаты аренды.
* Платежи проводятся через внешний платежный шлюз.
* Мы не доставляем котов. Клиент сам забирает кота в магазине.
* Когда клиент приходит за котом в магазин, он оплачивает аренду или расходует деньги со своего онлайн счета.
* Было бы здорово отправлять письмо или СМС с подтверждением.

## Счета

* Никаких счетов нет. Мы печатаем только фискальный чек, этого достаточно.

## Планы на будущее

Используйте эту информацию только если команда отлично справляется. Если команда не раскрыла стандарные требования, описанный выше — не говорите об этом.

* Мы хотим сынтегрироваться с внешней системой хранения данных, которая будет источником нашей BI системы. Мы будем анализировать данные по продажам, статистику по котам и породам, рейтинг клиентов.
* Мы думаем про аренду собак и енотов-полоскунов.
* Мы думаем про онлайн игру про домашних животных.
* Если клиенту понравился кот, он может его купить.
  * Перед покупкой клиент обязан взять кота в аренду.
* Кота можно купить только в офлайн магазине. Мы не продаем котов онлайн.
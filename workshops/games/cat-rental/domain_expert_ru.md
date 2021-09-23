# Воркшоп по Event Storming - Аренда котов

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

* We rent the board games.
* All the products are being identified in the system by SKU numbers. Also. each product has its own descriptive name, which is used by customers.
* All the products have EAN numbers assigned. We use these numbers to scan the barcodes with the barcodes scanner that we have in all of the stores.
* Barcode scanner works exactly the same as typical keyboard. You connect it to USB or PS/2 port, you can scan the barcode, in result the barcode's value is being written in the computer.
* Sometimes our customers return damaged games. Sometimes they lose some element of the game (like pawn or card). It is a big problem in our business.

## Prices

* Prices are associated to the products.
* Each product has the only one price in the whole chain-store.
* Sometimes, there is a need to apply some value or percent discounts.
* We receive all the payments in EUR.
* We are thinking about the possibility of adding the discount codes to the system. However, it is not a must.
* Each game is being rented for 14 days by default.
* If our client wants to keep the game for 30 days then he needs to pay 10,00 EUR more. However, it must be paid on the first day in the moment of renting the game.
* Extension of the rental period is being printed on the fiscal receipt as a separate position. It is named “Extension of the rental period”.
* If customer postpones the rental then we add him to the List of Debtors and we calculate the penalty.
  * up to 5 days of delay - 20,00 EUR,
  * up to 20 days of delay - 100,00 EUR,
  * 20 days of delay and more - 300,00 EUR,
* Debtor cannot rent the next games as long as he is on our List of Debtors. He can pay the penalty and then we delete him from the list.

## Offline / Stationary rental office

* In each store we have the fiscal printer. After connecting it to the computer it is possible to print the fiscal receipts from the system. 
* Supplier of the fiscal printer delivered a library, which makes it possible to integrate it with the system in very easy way. We can share that with the IT people.
* Customers must pay for each rental.
* Available payment methods are:
  * Cash,
  * Card,
  * Money available in the prepaid account associated with customer’s account in our online rental store.
	* Gift voucher.

## Online rental store

* Customer can sign up and sign in.
* Customer can browse the games by category.
* Customer can see the details of specified game and read about it.
* Customer can reserve the game and pick it up in the offline rental store.
* The length of the reservation is 2 days.
* After the reservation, we deliver the game to the offline rental store within 1 hour (even when the game is not available on the warehouse stock of the chosen offline store, but the game is available in the other offline store).
* If client does not pick up the game within 2 days then we cancel the reservation and the game becomes available for the other customers.
* Reservation is free. However, we must implement some solution to avoid the situation, when some kids reserve the games over and over the game, and they destroy our business. 
* Customer can charge top up his own prepaid account and then use it for purchasing the rentals.
* Payments are being handled by external payments gateway.
* We do not send the games to our customers. It is required to pick up the game in offline stationary rental office.
* When customer picks up the game then we charge the prepaid account or the payment in offline stationary rental office is required.
* That would be great for the users to receive some email and SMS notifications.

## Invoices

* We do not support invoices at all. Only receipts from our fiscal printer.

## In the future

Use these elements only if the team is doing really great. If the team didn’t find out most of the standard requirements mentioned above - do not talk about the ones below.

* We want to integrate external data warehouse, which will be the source for our Business Intelligence system. We will analyze the sales data, statistics for each game, statistics for each localisation.
* We are thinking about renting the computer and console games.
* We are thinking about selling the licenses for the games (we call it - digital products).
* If the customer likes the game a lot - he can buy it.
  * Before buying the game, it is a must to rent the game.
* It is possible to buy the game only in offline stationary rental store. It not possible in online store.



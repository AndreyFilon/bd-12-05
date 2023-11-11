# Домашнее задание к занятию 5 "«Индексы»" - `Филон Андрей`

### Задание 1

Напишите запрос к учебной базе данных, который вернёт процентное отношение общего размера всех индексов к общему размеру всех таблиц.  
    
![1](https://github.com/AndreyFilon/bd-12-05/blob/main/1.jpg)    

### Задание 2

Выполните explain analyze следующего запроса:
```sql
select distinct concat(c.last_name, ' ', c.first_name), sum(p.amount) over (partition by c.customer_id, f.title)
from payment p, rental r, customer c, inventory i, film f
where date(p.payment_date) = '2005-07-30' and p.payment_date = r.rental_date and r.customer_id = c.customer_id and i.inventory_id = r.inventory_id
```
- перечислите узкие места;
- оптимизируйте запрос: внесите корректировки по использованию операторов, при необходимости добавьте индексы.  

###Ответ

![2.1](https://github.com/AndreyFilon/bd-12-05/blob/main/2.1.jpg)  
Больше всего времени тратится в момент выполнения Window aggregate и Inner Join. 
Оптимизируем эти моменты.  
 
![2.2](https://github.com/AndreyFilon/bd-12-05/blob/main/2.2.jpg) 

---

# sqlOdev12

1) film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

2) film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

3) film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

4) payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.


***CEVAPLAR***

1) select count(length) from film
where length > (
select
avg (length)
grom
film
);
2) select count(rental_rate) from film
where rental_rate = (
select 
	max(rental_rate)
from 
	film
);
3) select * from film
where rental_rate = (
select max(rental_rate)
	from film
)
and  replacement_cost = (
select min(replacement_cost)
	from film
);

4) select customer.first_name, customer.last_name, payment.amount from payment
full join customer on payment.customer_id = customer.customer_id
where payment.amount =
(
    select max(amount) from payment
);

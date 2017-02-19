# README
Stage 5 Udacity IPND

For this last stage of nanoDegree in udacity, I decide to try all 4 paths to gain the basic concepts. This post is for back end.
vagrant

install virtual box
install vagrant
http://tech.osteel.me/posts/2015/01/25/how-to-use-vagrant-for-local-web-development.html
vagrant init: Creates a new Vagrantfile in current directory
vagrant up: Starts a VM
vagrant ssh: Connects to a VM via SSH
vagrant halt: Stop the VM
vagrant destroy: Stop & delete the VM (will delete all files related to it)
vagrant status: Show the status of the VMFixing “The box ‘base’ could not be found.” (Vagrant)
vagrant box add base http://files.vagrantup.com/lucid32.box
SQL

BASIC QUERY

select * from tablename limit XX offset XX;
\dt
select name, birthdate from animals where species != ‘gorilla’;
select count (species),species from animals group by species order by count(species) DESC;
insert into tablename ( column1, column2, … ) values ( val1, val2, … );
select name from animals, diet where animals.species=diet.species and diet.food=’fish’;
select animals group by species having num=1;
select ordernames.name, count(*) as num
from animals, taxonomy, ordernames
where animals.species = taxonomy.name and taxonomy.t_order = ordernames.t_order
group by ordernames.name
order by num desc;
update posts set content=’cheese’ where content like ‘%spam%’;
delete from posts where content=’cheese’;
CREATE AND DROP DATABASE/TABLE

create database name;
create table fish(id serial primary key, name text);
create table postal_places(postal_code text,country text, name text, primary key(postal_code, country));
create table sales(sku text references products, sale_date date, count integer);
drop database name;
drop table name;
delete from tablename;
insert into tablename values (‘This is text!’);
\c name # connect to database
JOIN

select products.name, products.sku, count(sales.sku) as num
  from products left join sales
    on products.sku = sales.sku
  group by products.sku;
SUBQUERY

select name, weight from player, (select avg(weight) as av from players) as subs where weight <av;
create view name as select …
Python DB-API

git clone
follow https://udacity.atlassian.net/wiki/display/BENDH/Vagrant+VM+Installation
cd to … /fullstack/vagrant
vagrant up (first time)
vagrant ssh
now you are in virtual machine and pqsl is available
then cd /vagrant/forum
ALWAYS USE 2 COMMAND WINDOWS

1.
python forum.py
http://localhost:8000/ # you can open it on a browser
2.
psql forum # load forum.sql by psql, note that psql is in virtual box
select 2+2 as a, 4+4 as b;
select from posts;
select from posts \watch # update very 2 seconds, so you can see what’s added
\d posts # get columns and type
\dt # list all tables
\H #switch b/w plain text vs HTML
LOOP HOLE

something fun: http://xkcd.com/
sql injection attack: ‘); delete from posts; —
script injeciton attack
EXAMPLE USING SQLITE3

import sqlite3

# Fetch some student records from the database.
db = sqlite3.connect("students") # student is database name
c = db.cursor()
query = "select name, id from students order by name;"
c.execute(query)
rows = c.fetchall() # get results


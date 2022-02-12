


Commands:
------------
npm run db:create
npm run db:init
npm run db:seed
npm run db:reset --- when creating a new table, must run this command after quiting postico. then open postico after running this command. 

notes:
init - creates our tables
seed - adds our initial data
reset - runs the other scripts: drop, create, init, and seed

---------

steps:

1) mkdir LikeyPix
cd LikeyPix
npm init -y

2) npm init -----this yo create package.json

3) in package.json, add the script:
  "scripts": {
    "db:create": "createdb likeypixdb",
    "db:destroy": "dropdb likeypixdb",
    "db:init": "psql -f schema.sql likeypixdb",
    "db:seed": "psql -f seed.sql likeypixdb",
    "db:reset": "npm run db:destroy; npm run db:create && npm run db:init && npm run db:seed",
    "test": "echo \"Error: no test specified\" && exit 1"
  }

 4) schema.sql
create table users (
    id serial primary key,
    name varchar(50) not null,
    email varchar(50) not null
);

5) seed.sql
insert into users
    (name, email)
values
    ('Alice', 'alice@email.com'),
    ('Bob', 'bob@email.com'),
    ('Cho', 'cho@email.com'),
    ('Daryl', 'daryl@email.com'),
    ('Emmy', 'emmy@email.com')
;


6) sudo mkdir -p /etc/paths.d &&
echo

7) npm run db:create

8) npm run

9)npm run db:init

10)npm run db:seed

11) npm run db:reset 

12) open Postico and click likeypixdb 

------------

13)
to create a new database 
in schema.sql add
create table posts (
     id serial primary key, 
     -- id in line 8 is primary key
     url text not null,
     user_id integer references users (id), 
     -- id in line 11 is Foreign key
);

then add seed.sql
insert into posts
    (url, user_id)
values
    ('walking-the-cat.jpg', 2),
    ('day-at-the-beach.jpg', 3),
    ('new-puppy.jpg', 1),
    ('cat-in-a-box.jpg', 5),
    ('doggos.jpg', 5)
;


then on terminal 
npm run db:reset
if error,  quict postico, then in command, add npm run db:reset
then open the postico again, the new database should be created.
----------
14) on schema.sql
create table tags_posts (
    tag_id integer references tags (id),
    post_id integer references posts (id)
);

   on seed.sql
insert into tags_posts 
    (tag_id, post_id)
values
    (1, 2),
    (2, 2),
    (1, 4),
    (3, 3),
    (3, 5);

quite postico => run(npm run db:reset) => open postico.

-----------------








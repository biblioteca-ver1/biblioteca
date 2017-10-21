
-- Create tables section -------------------------------------------------

-- Table USER

CREATE TABLE `USER`
(
  `name` Varchar(20) NOT NULL,
  `id` Varchar(30) NOT NULL,
  `birth_date` Date,
  `sex` Char(2),
  `pw` Varchar(30) NOT NULL,
  `phone_number` Varchar(30)
)
;

ALTER TABLE `USER` ADD  PRIMARY KEY (`id`)
;

-- Table BOOK

create table book(
	title varchar(30) not null,
    isbn varchar(30) not null,
    writer varchar(30),
    publisher varchar(30),
    genre varchar(30),
    pag int,
    price int,
    publish_date date,
    translator varchar(30)
    );


alter table book add primary key (isbn);

alter table book add unique isbn(isbn);

-- Table RENT

create table rent(
	id varchar(30),
    isbn varchar(30),
    grade int,
    review longtext,
    start_datetime date,
    end_datetime date
);


create index IX_Relationship1 ON rent(id);

create index IX_Relationship2 ON rent(isbn);

-- Create relationships section ------------------------------------------------- 

ALTER TABLE `RENT` ADD CONSTRAINT `Relationship1` FOREIGN KEY (`id`) REFERENCES `USER` (`id`) ON DELETE RESTRICT ON UPDATE RESTRICT
;

ALTER TABLE `RENT` ADD CONSTRAINT `Relationship2` FOREIGN KEY (`isbn`) REFERENCES `BOOK` (`isbn`) ON DELETE RESTRICT ON UPDATE RESTRICT
;

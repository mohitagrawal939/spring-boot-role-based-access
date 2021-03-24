# spring-boot-role-based-access
Role based login with postgresql as database using JPA, thymeleaf &amp; thyemleaf-security5.

Create tables with following configuration

CREATE TABLE product
(
  id SERIAL NOT NULL PRIMARY KEY,
  name character varying(45) NOT NULL,
  brand character varying(45) NOT NULL,
  madein character varying(45) NOT NULL,
  price float4 NOT NULL
)

CREATE TABLE users
(
  user_id SERIAL NOT NULL PRIMARY KEY,
  username character varying(45) NOT NULL UNIQUE,
  password character varying(64) NOT NULL,
  enabled  int DEFAULT NULL
)

CREATE TABLE roles
(
  role_id SERIAL NOT NULL PRIMARY KEY,
  name character varying(45) NOT NULL
)

CREATE TABLE users_roles
(
  user_id int NOT NULL,
  role_id int NOT NULL,
  CONSTRAINT role_fk FOREIGN KEY (role_id) REFERENCES roles(role_id),
  CONSTRAINT user_fk FOREIGN KEY (user_id) REFERENCES users(user_id)
)

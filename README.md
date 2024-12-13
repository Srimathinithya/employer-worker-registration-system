employer-worker-registration-system
An accounting program that contains employee and employer information and records of relationships between them.

Homepage	Employer registration	Worker registration
2-home_page	3-new_employer	3-new_worker
Search Box	Registration document
5-view_worker	7-new_record_optionpane
Requirements
Postgresql is used in this program. You can find the necessary jar file for postgresql java connection here:

https://jdbc.postgresql.org/download.html

Or you can use a different database but for this to work, change:

DriverManager.getConnection("jdbc:database://host:port/database-name", "user-name", "password");
for postgresql:

DriverManager.getConnection("jdbc:postgresql://localhost:5432/db", "postgres", "password");
And finally, in order not to get a database error, you should add the following tables to the database:

CREATE TABLE admin(id smallserial primary key not null, username varchar, password varchar);
CREATE TABLE employer(employer_id serial primary key not null, name varchar not null, surname varchar not null, business varchar, phonenumber varchar);
CREATE TABLE worker(worker_id serial primary key not null, name varchar not null, surname varchar not null, phone_number varchar);
CREATE TABLE worker_record(worker_record_id serial primary key not null, worker_id integer references worker(worker_id), employer_id integer references employer(employer_id), date varchar(10) not null, wage smallint not null);
CREATE TABLE employer_record(employer_record_id serial primary key not null, employer_id integer references employer(employer_id), date varchar(10) not null, note varchar(255), number_worker smallint not null, wage smallint not null);
CREATE TABLE worker_payment(worker_payment_id serial primary key not null, worker_id integer references worker(worker_id), employer_id integer references employer(employer_id), date varchar(10) not null, paid integer not null);
CREATE TABLE employer_payment(employer_payment_id serial primary key not null, employer_id integer references employer(employer_id), date varchar(10) not null, paid integer not null);
CREATE TABLE worker_payment(worker_payment_id serial primary key not null, worker_id integer references worker(worker_id), employer_id integer references employer(employer_id), date varchar(10), not null, paid integer not null);
About
An accounting program that contains employee and employer information and records of relationships between them.

Topics
java postgresql accounting gui-application login-system java-database-application java-project java-gui-application search-box java-swing-applications java-login-page java-swing-application java-swing-project java-projects
Resources
 Readme
License
 MIT license
 Activity
Stars
 58 stars
Watchers
 1 watching
Forks
 63 forks
Report repository
Releases
No releases published
Packages
No packages published
Languages
Java
100.0%
Footer

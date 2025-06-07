# pet_project01
Simple pipeline that includes Apache Airflow, PostgreSQL, MinIO (S3), Metabase and Docker technologies 

Architecture of the project

<img width="828" alt="image" src="https://github.com/user-attachments/assets/97b8b835-ffe6-42e1-83c3-81518fff2e2b" />


To start the project you need:
1) MinIO sign up and bucket create
2) Airflow sign in
3) Airflow variables
4) Airflow connection
5) Metabase sign up
6) Run SQL:
SCHEMAS:
CREATE SCHEMA ods;
CREATE SCHEMA dm;
CREATE SCHEMA stg;


DDL:


CREATE TABLE ods.fct_earthquake
(
	time varchar,
	latitude varchar,
	longitude varchar,
	depth varchar,
	mag varchar,
	mag_type varchar,
	nst varchar,
	gap varchar,
	dmin varchar,
	rms varchar,
	net varchar,
	id varchar,
	updated varchar,
	place varchar,
	type varchar,
	horizontal_error varchar,
	depth_error varchar,
	mag_error varchar,
	mag_nst varchar,
	status varchar,
	location_source varchar,
	mag_source varchar
);

CREATE TABLE dm.fct_count_day_earthquake AS 
SELECT time::date AS date, count(*)
FROM ods.fct_earthquake
GROUP BY 1;

CREATE TABLE dm.fct_avg_day_earthquake AS
SELECT time::date AS date, avg(mag::float)
FROM ods.fct_earthquake
GROUP BY 1;









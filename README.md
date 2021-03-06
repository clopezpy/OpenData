Inmuebles MEC, Julio 2014
-------------------------

Version 1.0 - Mie 01 Oct 2014

by
Clara López,
Lilian Nieto,
Maira Pereira


Introducción
================
El objetivo del trabajo fue obtener el documento publicado por el Ministerio de Educación y Cultura, y transformar en un formato mas procesable por máquina, ya que el mismo está publicado
en formato PDF. Se obtuvo un formato CSV, de esta manera se facilita al ciudadano la utilización de los datos.


Universidad Nacional de Asunción</br>
Facultad Politécnica – Sede San Lorenzo, Paraguay</br>
Carrera Ingeniería en Informática</br>
10mo Semestre</br>
Asignatura: Electiva 6 – Datos Abiertos</br>
Año: 2014

Origen de datos <a id="origen_datos"></a>
---------------

URL: http://datos.mec.gov.py/
https://mega.co.nz/#!84IkjQTD!4FGj6gaMVE1tQL5h348uY1D3lRb_8xOnXB_KK9gNqWw

Configuración  <a id="configuration"></a>
-------------
	Table: inmuebles

	DROP TABLE inmuebles;

	CREATE TABLE inmuebles
	(
	  numero_fila integer,
	  nombre_institucion character(500),
	  codigo_departamento character(20),
	  codigo_distrito character(20),
	  cod1 character(20),
	  cod2 character(20),
	  nombre_distrito character(100),
	  nombre_departamento character(100),
	  nombre_localidad character(100),
	  superficie_texto character varying(50),
	  superficie double precision
	)
	WITH (
	  OIDS=FALSE
	);
	ALTER TABLE inmuebles
	  OWNER TO postgres;

	
	Script de población de base datos Postgres:

		COPY inmuebles from 'PATH/inmuebles.csv' DELIMITERS ';' CSV;

	Script de población de base datos MySql:

		LOAD DATA INFILE 'PATH/inmuebles.csv' 
		INTO TABLE inmuebles 
		FIELDS TERMINATED BY ';' 
		ENCLOSED BY '"'
		LINES TERMINATED BY '\n'
		IGNORE 1 ROWS
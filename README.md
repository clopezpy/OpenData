Inmuebles MEC, Julio 2014
-------------------------

Version 1.0 - Mie 01 Oct 2014

by
Clara López,
Lilian Nieto,
Maira Pereira,


Introducción
================
El treemap de Inmuebles del MEC presenta una visualización de los datos acerca de los inmuebles que posee el Ministerio de Educación y Cultura en los diferentes departamentos del Paraguay.
La visualización es realizada por distritos y la misma está basada en los datos publicados por el MEC en su portal web (http://datos.mec.gov.py/).

Universidad Nacional de Asunción
Facultad Politécnica – Sede San Lorenzo, Paraguay
Carrera Ingeniería en Informática
10mo Semestre
Asignatura: Electiva 6 – Datos Abiertos
Año: 2014

Origen de datos <a id="origen_datos"></a>
---------------

URL: http://datos.mec.gov.py/
https://mega.co.nz/#!84IkjQTD!4FGj6gaMVE1tQL5h348uY1D3lRb_8xOnXB_KK9gNqWw

Configuration  <a id="configuration"></a>
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
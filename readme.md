#PublicDepartCologne

Dieses Projekt soll es Nutzern von Strassenbahnen aufgrund der Geolocation und anhand von Echtzeit Daten zu Abfahrtszeiten ermöglichen, abzuschätzen, ob sie eine bestimmte Strassen noch zu Fuss erreichen können. 

# Benutzung

Es werden die nächsten 5 Stationen auf einer Karte anzeigt. Durch Tippen auf eine Station wird der Abfahrtsmonitor aufgerufen. Es wird _kein_ Routing zu einem gewünschtem Ziel vorgenommen.

# Entwicklungsstand

Diese Anwendung befindet sich in Entwicklung

# verwendete Technologien

- html
- javascript
- Python
- PostGres/ Python

# Datenbank

## DB User auf Postgres einrichten

    sudo -u postgres haltestellen -P haltestellen
    
## Datenbank wahlergebnis anlegen

    sudo -u postgres createdb -O haltestellen haltestellen

## Postgis topology

    sudo -u postgres psql -c "CREATE EXTENSION postgis; CREATE EXTENSION postgis_topology;" haltestellen
    
## Tabelle

	CREATE TABLE haltestellen (
	    gid integer NOT NULL,
	    name character varying(40),
	    knotennumm character varying(20),
	    typ character varying(20),
	    nr_stadtte character varying(3),
	    stadtteil character varying(40),
	    nr_stadtbe character varying(1),
	    stadtbezir character varying(40),
	    hyperlink character varying(200),
	    objectid numeric(10,0),
	    geom geometry(Point)
	);
	
	CREATE SEQUENCE haltestellen_gid_seq
	    START WITH 1
	    INCREMENT BY 1
	    NO MINVALUE
	    NO MAXVALUE
	    CACHE 1;

## DB-Tabellen initial einrichten

    psql -h localhost -U haltestellen -d haltestellen -a -f src/main/sql/haltestellen.init.sql

# License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />Dieses Werk ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Namensnennung - Weitergabe unter gleichen Bedingungen 4.0 International Lizenz</a>.
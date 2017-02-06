# ansible_gis
Ansible Playbook for GIS Application

- IMPORTANT
  - The mapserver refer the "oid" column in the postgis table when using where sentence.
  - But PostgreSQL8.1 or later don't append oid column to the table automatically.
  - So, you must append "WITH OID" option when you invoke "CREATE TABLE" SQL sentece. And make index for oid column. For example:

  ```SQL
  CREATE TABLE geom_tbl WITH OID;
  CREATE INDEX geom_tbl_idx_oid ON geom_tbl ( oid );
  ```

- usage

  ```SHELL
  $ ansible-playbook gis.yml
  $ ansible-playbool glassfish.yml
  ```

  - You can access mapserver at the URL http://localhost:10080/cgi-bin/mapserv
    (for Vagrant ) or http://server/cgi-bin/mapserv.
    It is ok that your browser show the message 'No query information to decode.
    QUERY_STRING is set, but empty.'. This message tells you that map file path is
    not specified on URL parameter. Therefore you can confirm that mapserver was
    completely installed.
  - You can access mapcache at the URL http://localhost:10080/mapcache/test
    (for Vagrant ) or http://server/mapcache/test .
    It is ok that your browser show the message 'received wms with no service and request'.
    This message tells you that the mapcache can't access backend mapserver (wms)
    that defined in /opt/mapcache/mapcache.xml. Therefore you can confirm that
    mapcache was completely installed.
    The /opt/mapcache/mapcache.xml is a copy of the official sample xml. You
    will modifiy this xml and restart apache.
  - You need not install the glassfish, if you want to install only mapserver
    and mapcache.
  - The glassfish has JDBC Connection pool to the PostGIS server. See management
    console https://localhost:14848 (for Vagrant ) or https://server:4848/.

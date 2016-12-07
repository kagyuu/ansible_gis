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

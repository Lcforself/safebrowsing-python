# SQL Schema of the database used to store hashes. #

```
CREATE TABLE black_version(
        version_number varchar(20) not null primary key
);

CREATE TABLE malware_version(
        version_number varchar(20) not null primary key
);

CREATE TABLE url_hashes_table(
badware_type varchar(1) not null,
url_hash varchar(32) not null
);

CREATE INDEX url_hash_index on url_hashes_table (url_hash);
```
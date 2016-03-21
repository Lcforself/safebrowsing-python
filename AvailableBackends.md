Here is the list of currently supported database backends:
  * Sqlite
  * Mysql
  * Postgresql
  * Memcached

## How to write a custom backend ##

The custom data backend must subclass the `BaseDBObj` from `base.py` and implement the following `6` methods:

  * **get\_version**(**badware\_type**)
> > `badware_type` is either `malware` or `black`

  * **insert\_version\_row**(**badware\_type**, **version\_number**)
> > `badware_type` is either `malware` or `black`
> > `version_number` is a string (eg: 1:-1 or 1:1835)

  * **update\_version\_row**(**badware\_type**, **new\_version\_number**, **version\_number**)
> > `badware_type` is either `malware` or `black`
> > `version_number` is a string (eg: 1:-1 or 1:1835)
> > `new_version_number` is also similar to `version_number`

  * **insert\_rows**(**url\_hash\_dict**)
> > `url_hash_dict` is a map with the `url_hash` as the key and the `badware_code` as the value.

  * **delete\_rows**(**url\_hash\_dict**)
> > `url_hash_dict` is a map with the `url_hash` as the key and the `badware_code` as the value.

  * **lookup\_by\_md5**(**md5\_hash\_list**)
> > `md5_hash` is a list of hashes to be matched against the db.
# Introduction #

### Fill Database and API Key ###

  * Fill the safebrowsing/conf.py parameters.

### Preparing Db ###

Usage of the List Preparation script

```
>>> from safebrowsing.prepare_db import Google_Blacklist
>>>
# "malware" and "black" are valid options
>>> g = Google_Blacklist("malware")
>>> g.fetch_data()
```

For information regarding the SQL schema used for the database, click [here](SQLSchema.md).

### Looking up URL ###

Usage of the lookup library is very simple.

```
>>> from safebrowsing.query_lookup import Lookup
>>>
>>> l = Lookup()
>>> l.lookup_by_url("http://thejaswi.info/")
>>>
>>> l.lookup_by_url("www.somemalwaresite.com")
'M'
>>>
```

### Using Django Newforms Safe\_URLField ###

Usage of Safe\_URLField

```
>>> from safe_url_django.forms import Safe_URLField
>>> from django import newforms as forms
>>> class Test_Form(forms.Form):
...     url_field = Safe_URLField()
... 
>>> data={"url_field": u"http://thejaswi.info/"}
>>> f=Test_Form(data)
>>> f.is_valid()
True
>>> f.errors
{}
>>> f.cleaned_data
{'url_field': u'http://thejaswi.info/'}
>>> data2={"url_field": u"www.somemalwaresite.com"}
>>> g=Test_Form(data2)
>>> g.is_valid()
False
>>> g.errors
{'url_field': [u'A verbose malware detected error.'}
```

### Using Django Models Field ###

```
>>> from safe_url_django.fields import Safe_URLField
>>> from django.db import models
>>> class URL_Model(models.Model):
...     badware_url_test = Safe_URLField(verify_exists=True, verbose_name="URL Field", badware_check=True)
```
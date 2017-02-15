# Tashaphyne
=======
Tashaphyne: Arabic Light Stemmer تاشفين: التجذيع الخفيف للنصوص العربية


  Developpers:  Taha Zerrouki: http://tahadz.com
    taha dot zerrouki at gmail dot com

Features |   value
---------|---------------------------------------------------------------------------------
Authors  | [Authors.md](https://github.com/linuxscout/tashaphyne/master/AUTHORS.md)
Release  | 0.3 
License  |[GPL](https://github.com/linuxscout/tashaphyne/master/LICENSE)
Tracker  |[linuxscout/tashaphyne/Issues](https://github.com/linuxscout/tashaphyne/issues)
Website  |[https://pypi.python.org/pypi/Tashaphyne](https://pypi.python.org/pypi/Tashaphyne)
Doc  |[package Documentaion](http://pythonhosted.org/Tashaphyne/)
Source  |[Github](http://github.com/linuxscout/tashaphyne)
Download  |[sourceforge](http://tashaphyne.sourceforge.net)
Feedbacks  |[Comments](http://tahadz.com/tashaphyne/contact)
Accounts  |[@Twitter](https://twitter.com/linuxscout)  [@Sourceforge](http://sourceforge.net/projects/tashaphyne/)



## Citation
If you would cite it in academic work, can you use this citation
```
T. Zerrouki‏, Tashaphyne, Arabic light stemmer‏,  https://pypi.python.org/pypi/Tashaphyne/0.2
```
or in bibtex format
```bibtex
@misc{zerrouki2012tashaphyne,
  title={Tashaphyne, Arabic light stemmer},
  author={Zerrouki, Taha},
  url={https://pypi.python.org/pypi/Tashaphyne/0.2},
  year={2012}
}
```


##   مزايا
 - تجذيع الكلمة العربية إلى أبسط جذع ممكن
 - إمكانية استخراج الجذر
 - تقطيع الكلمة إلى جميع الحالات الممكنة.
 - تنميط الكلمة ( توحيد الحروف ذات الأشكال المختلفة.
 - قائمة مسبقة للزوائد العربية، وحروف الزيادة
 -إمكانية ضبط إعدادات المجذع والمقطع، من خلال تعديل قوائم الزوائد.
 
## Features
 - Arabic word Light Stemming.
 - Root Extraction.
 - Word Segmentation 
 - Word normalization
 - Default Arabic Affixes list.
 - An customizable Light stemmer: possibility of change stemmer options and data.
 - Data independent stemmer.


Applications
====
* Stemming texts
* Text Classification and categorization
* Sentiment Analysis
* Named Entities Recognition

Installation
=====
```
pip install tashaphyne
```    
    
Usage
=====


Tahsphyne is a finite state automaton stemmed based, it extract affixes (prefixes and suffixes), with a predefined affixes list.

It extract all possible affixation from a word and cite all possible configuration stemming of a given word.



### Functions الدوال 


* تجذيع الكلمة

تجذيع الكلمة واستخلاص كل المعلومات منها بواسطة الدوال المناسبة

Stemming function, stem an arabic word, and return a stem. This function store in the instance the stemming positions (left, right), then it's possible to get other calculted attributs like : stem, prefixe, suffixe, root.

```python
>>> #make propre display for unicode
... import pyarabic.arabrepr
>>> arepr = pyarabic.arabrepr.ArabicRepr()
>>> repr = arepr.repr
>>> 
>>> from tashaphyne.stemming import ArabicLightStemmer
>>> ArListem = ArabicLightStemmer()
>>> word = u'أفتضاربانني'
>>> # stemming word
... stem = ArListem.light_stem(word)
>>> # extract stem
... print ArListem.get_stem()
ضارب
>>> # extract root
... print ArListem.get_root()
ضرب
>>> 
>>> # get prefix position index
... print ArListem.get_left()
3
>>> # get prefix 
... print ArListem.get_prefix()    
أفت
>>> # get prefix with a specific index
... print ArListem.get_prefix(2)    
أف
>>> 
>>> # get suffix position index
... print ArListem.get_right()
7
>>> # get suffix 
... print ArListem.get_suffix()    
انني
>>> # get suffix with a specific index
... print ArListem.get_suffix(10)    
ي
>>> # get affix
>>> print ArListem.get_affix()
أفت-انني
>>> # get affix tuple
... print repr(ArListem.get_affix_tuple())    
{'prefix': u'أفت', 'root': u'', 'stem': u'', 'suffix': u'أفتضاربانني'}
>>> # star words
... print ArListem.get_starword()
أفت*ا**انني
>>> # get star stem
... print ArListem.get_starstem()
*ا**
>>> 
>>> #  get unvocalized word
... print ArListem.get_unvocalized()
أفتضاربانني
```

function | Description | وصف|
---------|-------------|----|
get_root()|Get the root of the treated word by the stemmer. |استخلاص الجذر|
get_stem()|Get the stem of the treated word by the stemmer.|استخلاص الجذعيمكن استخلاص الجذع التلقائي مباشرة، عند الرغبة في الحصول على جذع معين، نحدد دليل السابق، ودليل اللاحق.|
get_left()| Get the prefix end position | موضع نهاية السابقة|
get_right()|Get the suffix start position| موضع بداية اللاحقة |
get_prefix()|return the prefix/suffix of the treated word by the stemmer.|استرجاع السابقة التلقائية أو سابقة معينة بموضع|
get_suffix()| Get default suffix, or suffix by suffix index| استرجاع اللاحقة التلقائية أو بواسطة دليل اللاحقة
get_affix()|Get default Affix or specific by left and right indexes|استرجاع الزائدة التلقائية أو المعينةبدليلي السابق واللاحق|
get_affix_tuple()|Get affixe tuple | استرجاع الزائدة بتفاصيلها
get_starword()|Get stared word, radical letters replaced by "*"|استرجاع الكلمة المنجمة، الحروف الأصلية مخفية بنجوم
get_starstem()|Get stared stem, radical letters replaced by "*"|استرجاع الجذع المنجم، الحروف الأصلية مخفية بنجوم
get_unvocalized()|return the unvocalized form of the treated word by the stemmer. Harakat are striped.| استرجاع الكلمة غير مشكولة|


* استخلاص كل التقسيمات المحتملة

* تقسيم الكلمة إلى كل الزوائد المحتملة

Generate a list of all posibble segmentation positions (lef, right) of the treated word by the stemmer.

```python

>>> word = u'أفتضاربانني'

>>> # Detect all possible segmentation
... print ArListem.segment(word) 
set([(2, 7), (3, 8), (0, 8), (2, 9), (2, 8), (3, 10), (2, 11), (1, 8), (0, 7), (2, 10), (3, 11), (1, 10), (0, 11), (3, 9), (0, 10), (1, 7), (0, 9), (3, 7), (1, 11), (1, 9)])

>>># Get all segment 
>>>print ArListem.get_segment_list()
set([(2, 7), (3, 8), (0, 8), (2, 9), (2, 8), (3, 10), (2, 11), (1, 8), (0, 7), (2, 10), (3, 11), (1, 10), (0, 11), (3, 9), (0, 10), (1, 7), (0, 9), (3, 7), (1, 11), (1, 9)])

>>> # get affix list
... print repr(ArListem.get_affix_list() )
[{'prefix': u'أف', 'root': u'ضرب', 'stem': u'تضارب', 'suffix': u'انني'},
 {'prefix': u'أفت', 'root': u'ضرب', 'stem': u'ضاربا', 'suffix': u'نني'},
 {'prefix': u'', 'root': u'أفضرب', 'stem': u'أفتضاربا', 'suffix': u'نني'}, 
 {'prefix': u'أف', 'root': u'ضربن', 'stem': u'تضاربان', 'suffix': u'ني'}, 
 {'prefix': u'أف', 'root': u'ضرب', 'stem': u'تضاربا', 'suffix': u'نني'}, 
 {'prefix': u'أفت', 'root': u'ضربنن', 'stem': u'ضاربانن', 'suffix': u'ي'}, ...]
>>> 
```
* segment() / get_segment_list()
استخلاص قائمة مواضع كل التقسيمات المحتملة على شكل أعداد
return a list of segmentation positions (left, right) of the treated word by the stemmer.

* get_affix_list
 استخلاص قائمة كل الزوائد المحتملة

return a list of affix tuple of the treated word by the stemmer.


You can modify and customize  the default affixes list by

```python
>>>mystemmer.set_prefix_list(NEW_PREFIX_LIST); 
>>>mystemmer.set_suffix_list(NEW_SUFFIX_LIST); 
```
This command will rebuild the Finite state automaton to consider new affixes list.

Package Documentation
=====

Files
=====
* file/directory    category    description 

* [docs]
    docs/   docs    documentation

* [support]
    - pyarabic  : basic arabic library

* [test]
    - output/   test    test output
    - samples/  test    sample files
    - tools/    test    script to use tashaphyne


## Featured Posts
If you would cite it in academic work, can you use this citation
```
T. Zerrouki‏, Tashaphyne, Arabic light stemmer‏,  https://pypi.python.org/pypi/Tashaphyne/0.2
```
or in bibtex format
```bibtex
@misc{zerrouki2012tashaphyne,
  title={Tashaphyne, Arabic light stemmer},
  author={Zerrouki, Taha},
  url={https://pypi.python.org/pypi/Tashaphyne/0.2},
  year={2012}
}
```

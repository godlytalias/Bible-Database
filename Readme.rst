==============
Bible Database
==============
This database files are released to help developers in easily developing
Bible applications, Developers also requested to raise patches for any
fixes found in the database files.


Usage 
------

This `branch` contains sql files, sqlite database and JSON database for Bible in
these languages currently:
   #. `English <https://github.com/godlytalias/Bible-Database/tree/master/English>`_
   #. `Malayalam <https://github.com/godlytalias/Bible-Database/tree/master/Malayalam>`_
   #. `Hindi <https://github.com/godlytalias/Bible-Database/tree/master/Hindi>`_
   #. `Telugu <https://github.com/godlytalias/Bible-Database/tree/master/Telugu>`_
   #. `Tamil <https://github.com/godlytalias/Bible-Database/tree/master/Tamil>`_
   #. `Kannada <https://github.com/godlytalias/Bible-Database/tree/master/Kannada>`_
   #. `Oriya <https://github.com/godlytalias/Bible-Database/tree/master/Oriya>`_
   #. `Gujarati <https://github.com/godlytalias/Bible-Database/tree/master/Gujarati>`_
   #. `Bengali <https://github.com/godlytalias/Bible-Database/tree/master/Bengali>`_
   #. `Zulu <https://github.com/godlytalias/Bible-Database/tree/master/Zulu>`_
   #. `Indonesian <https://github.com/godlytalias/Bible-Database/tree/master/Indonesian>`_
   #. `Xhosa <https://github.com/godlytalias/Bible-Database/tree/master/Xhosa>`_


**SQL Database**

SQL Database is having fields ``Book``, ``Chapter``, ``Versecount``
which are of type INT and ``verse`` field which is VARCHAR.
The Book field starts from 0 and Chapter & Versecount from 1.
Below is a sample SQL query for fetching *John 3:16*

``Select Book,Chapter,Versecount,verse from bible where Book=42 and Chapter=3 and Versecount=16;``


**JSON Database**

JSON Database have fields ``Verse`` & ``Verseid``. Verseid field is a unique id
which is a comibination of Book + Chapter + Verse. First two digits represents Book(0 - 65),
Second three digits represent Chapter and last three digits represent Verse.
For JSON Database, Book, Chapter and Verse starts from 0.
Below is a sample PHP code for fetching *John 3:16*;

>>> <?php
>>> $filecontent = file_get_contents("bible.json");
>>> $books = json_decode($filecontent);
>>> echo $books->Book[42]->Chapter[2]->Verse[15]->Verse;
>>> ?>

*Javascript Example*

>>> var bible;
>>> function readJsonFile() {
>>>     var rawFile = new XMLHttpRequest();
>>>     rawFile.overrideMimeType("application/json");
>>>     rawFile.onreadystatechange = function() {
>>>         if (rawFile.readyState === 4 && rawFile.status == "200") {
>>>             bible = JSON.parse(rawFile.responseText);
>>>         }
>>>     };
>>>     rawFile.open("GET", "bible.json", true);
>>>     rawFile.send();
>>> }
>>> 
>>> function queryverse(book, chapter, verse)
>>> {
>>>    return bible.Book[book - 1].Chapter[chapter - 1].Verse[verse - 1].Verse;
>>> }

Users can clone this repo by typing :

   git clone https://github.com/godlytalias/Bible-Database.git

Help, bugs, feedback
--------------------
	#. Users can mail their queries, feedback and suggestions at godlytalias@yahoo.co.in 
	#. Developers/Contributor can raise issues at `issues <https://github.com/godlytalias/Bible-Database/issues>`_ or by `mail <mailto:godlytalias@yahoo.co.in>`_
	#. Pull requests are most welcome, Please fix if any bugs found and push the patches.

Credits
-------
  The databases are created by extracting data from `Wordproject® <http://wordproject.org>`_

License
-------

GNU GPL Version 3, 29 June 2007.

Please refer this `link <http://www.gnu.org/licenses/gpl-3.0.txt>`_
for detailed description.

All rights belong to `Godly T.Alias <http://godlytalias.blogspot.com>`_.

Copyright © 2015

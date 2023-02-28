### Using django shell for creating and querying data

To use django shell type the command:
```sh
python manage.py shell
```
An interactive python shell will start:
```sh
Python 3.10.6 (main, Nov 14 2022, 16:10:14) [GCC 11.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> 
```
We need to import the data model we will use:
```sh
from notes.models import Notes
```
To retrieve the note with primary key equal to 1:
```sh
>>> mynotes = Notes.objects.get(pk='1')
>>> mynotes.title
'My First Note'
>>> mynotes.text
'Django is amazing !'
```
To retrieve all notes from the Notes table in the database and return them as a QuerySet, which is a collection of database objects:
```sh
>>> Notes.objects.all()
<QuerySet [<Notes: Notes object (1)>]>
```
To create a new note:
```sh
>>> new_note = Notes.objects.create(title = "A second note" , text = "This is a second note")
```





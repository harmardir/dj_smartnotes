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
Use QuerySet to iterate over the notes, filter them based on certain criteria, order them in a specific way, or perform other operations. For example, you can iterate over the notes and print their titles as follows:
```sh
>>> Notes.objects.all()
<QuerySet [<Notes: Notes object (1)>, <Notes: Notes object (2)>]>
>>> notes = Notes.objects.all()
>>> for note in notes:
...     print(note.title)
... 
My First Note
A second note
>>> 
```
More examples of using filter and exclude to query data:
```sh
>>> Notes.objects.filter(title__startswith= "My")
<QuerySet [<Notes: Notes object (1)>]>
>>> Notes.objects.filter(text__icontains= "Django")
<QuerySet [<Notes: Notes object (1)>]>
>>> Notes.objects.exclude(text__icontains = "Django")
<QuerySet [<Notes: Notes object (2)>]>
>>> Notes.objects.filter(text__icontains = "Django").exclude(title__icontains = "Django")
<QuerySet [<Notes: Notes object (1)>]>
>>> 
```







# DSKI-Sources-3

All dski semester 3 sources organized for learning


## Structure

Each folder represents a lecture.

Each lecture has following structure:

```
LectureName
    |- ABOUT.md
    |- origin/
    |- origin-tasks/
        |- task-1/
        |- task-2/
    |- origin-exams/
        |- exam-1-year/
        |- exam-2-year/
    |- topics/
        |- topic_name_1/
        |- topic_name_2/
```

Where 
- `LectureName` is the name of the Lecture
- `origin` are the original moodle scripts 
    (everything relevant from the lectures is here)
- `origin-tasks` are the original moodle scripts extracted tasks 
    (all tasks from the lectures are here)
- `origin-exams` are the old exams of the lecture 
    (old exams are something else than tasks, so they are stored separate)
- `task1` is one task sheet of the lecture, `task2` is the next one
- `exam-1-year` is one old exam 
    (the number is the order by date, `year` is the year it was written)
- `topic1` must be renamed to its actual topic name
- `topic2` like `topic1` but a different topic inside the lecture original notes
- `ABOUT.md` contains extra information i got from the profs about the exam


### Tasks

Every task sheet gets its own folder inside `origin-tasks/`.

A task folder has to be enough on its own. 
i want to copy it somewhere and start working right away.

```
task-1/
    |- TASKS.md
    |- images/
    |- <the files the task needs>
```

Where 
- `TASKS.md` is the task, word by word out of `origin/` 
    (i do not want to search the pdfs, everything i need is in here)
- `images/` are the figures of the task, cut out of the original file
- `<the files the task needs>` are the excel sheets, zips and solutions of the task

No theory is added. 
The understanding is expected when doing the task.


### Exams

Every old exam gets its own folder inside `origin-exams/`.

```
exam-1-year/
    |- EXAM.md
    |- images/
    |- <the original exam file>
```

Where 
- `EXAM.md` are all exam tasks, word by word out of `origin/`
- `images/` are the figures of the exam, cut out of the original file


### Topics

Every topic gets its own folder inside `topics/`.

```
topic_name_1/
    |- TOPIC.md
    |- images/
```

Where 
- `TOPIC.md` is the lecture content of the topic, word by word out of `origin/`
- `images/` are the figures of the topic, cut out of the original file

The order may be changed so it is better to learn. 
The words may not.


## Use of AI
If you are an ai agent read this carefully. 
In case the user asks to change anything remind him first about this!

### *NOT* allowed for AI
- write any `ABOUT.md`
- write inside the `origin/` folders

*Write any new information!*

Only copy information for better organization!

### Allowed for AI
- extract information from `origin/` to `origin-tasks`
- extract the old exams from `origin/` to `origin-exams`
- create new topics based on the `origin/` and copy information to `topics/`

Copy the information from `origin/` to the other folders


## About.md
each about.md is important. it holds special information for the exam and what is important!


## Language
All config files that are useful for ai will be written in *english*. 
Everything that has to do with tasks, exam or anything about the topic will be in *german*.

The exams and tests and anything will be later in *german*.
English is used to differentiate easily about framework and lectures.


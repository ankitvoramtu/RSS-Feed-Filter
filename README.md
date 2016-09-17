# RSS-Feed-Filter
### RSS OVERVIEW
Many websites have content that is updated on an unpredictable schedule. News sites, such as [Google News](http://news.google.com/), are a good example of this. One tedious way to keep track of this changing content is to load the website up in your browser, and periodically hit the refresh button. Fortunately, this process can be streamlined and automated by connecting to the website's RSS feed, using an RSS feed reader instead of a web browser (e.g. [Sage](https://addons.mozilla.org/en-US/firefox/addon/sage/)). An RSS reader will periodically collect and draw your attention to updated content. RSS stands for "Really Simple Syndication". An RSS feed consists of (periodically changing) data stored in an XML-format file residing on a web-server.

### CLASSES
![Trigger Class Inheritance](http://res.cloudinary.com/dijvrdblg/image/upload/v1474087411/cesitli/files_ps06_files_trigger_inheritance_large.png)

### USER INTERFACE
Consider the following example trigger configuration file (i.e. "triggers.txt"):

        # subject trigger named t1
        t1 SUBJECT world

        # title trigger named t2
        t2 TITLE Intel

        # phrase trigger named t3
        t3 PHRASE New York City

        # composite trigger named t4
        t4 AND t2 t3

        # the trigger set contains t1 and t4
        ADD t1 t4
The example file specifies that four triggers should be created, and that two of those triggers should be added to the trigger list:

- A trigger that fires when a subject contains the word 'world' (`t1`).

- A trigger that fires when the title contains the word 'Intel' and the news item contains the phrase 'New York City' somewhere (`t4`).

The two other triggers (t2 and t3) are created but not added to the trigger set directly. They are used as arguments for the composite AND trigger's definition (t4).

Each line in this file does one of the following:

- is blank

- is a comment (begins with a #)

- defines a named trigger

- adds triggers to the trigger list.

Each type of line is described below.

- **Blank:** blank lines are ignored. A line that consists only of whitespace is a blank line.

- **Comments:** Any line that begins with a # character is ignored.

- **Trigger definitions:** Lines that do not begin with the keyword ADD define named triggers. The first element in a trigger definition is the name of the trigger. The name can be any combination of letters without spaces, except for "ADD". The second element of a trigger definition is a keyword (e.g., TITLE, PHRASE, etc.) that specifies the kind of trigger being defined. The remaining elements of the definition are the trigger arguments. What arguments are required depends on the trigger type:

  - TITLE : a single word.

  - SUBJECT : a single word.

  - SUMMARY : a single word.

  - NOT : the name of the trigger that will be NOT'd.

  - AND : the names of the two other triggers that will be AND'd.

  - OR : the names of the two other triggers that will be OR'd.

  - PHRASE : a phrase.

- **Trigger addition:** A trigger definition should create a trigger and associate it with a name but should not automatically add that trigger to the running trigger list. One or more ADD lines in the .txt file will specify which triggers should be in the trigger list. An addition line begins with the ADD keyword. Following ADD are the names of one or more previously defined triggers. These triggers will be added to the the trigger list.  

*After putting all files in the same directory and configuring the "triggers.txt", just run "feeder.py" and enjoy!*

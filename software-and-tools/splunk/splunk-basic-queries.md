# Splunk Basic Queries

As a SOC, Splunk is a very powerful tool to search for data efficiently.



## Searching for specific entries

To search for  a specific keyword or phrase use the 'search' command.

```
index=<index_name> | search <keyword>
```

Replace \<index\_name> with the index you want to search against?

Unsure what index you want to search against, you can do a wild search. Or typing in the keyword on its own.

```
index=* | search <keyword>
```



## Why do we specify artifacts when searching

The main reason is to narrow the search as quick as possible otherwise you would have too much data or also know as log fatigue and the search is generally quicker.



## Combining search artifacts using Boolean operators

Splunk allows you to combine multiple search artifacts using Boolean operators such as:

| Command | Description                                 |   |
| ------- | ------------------------------------------- | - |
| AND     | is and the other artifacts                  |   |
| OR      | could be either one or both of the artifact |   |
| NOT     | will not be this artifact                   |   |

Getting creative you could do something like:

```
index=<index_name> <keyword1*> AND <keyword2> OR <keyword3> NOT <keyword4>
```



## Looking for more commands?

Refer to the official documentation from Spunk:

[ ](https://docs.splunk.com/Documentation/Splunk/9.1.2/SearchReference/ListOfSearchCommands)[https://docs.splunk.com/Documentation/Splunk/9.1.2/SearchReference/ListOfSearchCommands](https://docs.splunk.com/Documentation/Splunk/9.1.2/SearchReference/ListOfSearchCommands)

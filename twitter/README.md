# Be-Normal: Twitter

So this is part of Be-Normal repository project, twitter part.

## Index
- [Labeling Process Flow](#labeling-process-flow)
- [Few notes for this project](#data)
- [Python file Documentation](#documentation-of-python-file)

## Labeling Process Flow

See [here](twitter/README-labeling.md).

## Data Description

So in data section, there are few file that you should understand:
- 15M-Tweet : this is the mother of all tweet data. There are 15M-Tweet that has been crawled, from random user (but mostly Indonesian)
- issue.txt : this is the collected issue of labelling process
- trash.txt : this is collected tweet that shouldn't be checked again while pick.py is running.
- unnormalized.txt : So, tweets that ready to be normalized, should be put here
- formatted/ : This folder is contained by formatted tweets with no label (the normalized token is same with unnormalized token)
- labeled/ : This folder is contained by formatted and labeled tweets.

## Documentation of Python File

The documentation of python file would used docstring, for both file and function description. So, if you curious about what is done by certain script, just open it and hopefully you'll understand. Here's are the overview:
- pick.py : to pick the suitable tweet from 15M-Tweet to be normalized. Some tweet are can't be normalized
- formatting.py : to do formatting from data/unnormalized.txt to formatted text. I still don't decide which extention for it
- lib.py : The external library are imported to this script first, then used by another script.
- randomize.py : To shuffle the data/unnormalized.txt


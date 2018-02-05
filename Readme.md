Python FP-Growth
================

This module provides a pure Python implementation of the FP-growth algorithm for
finding frequent itemsets. FP-growth exploits an (often-valid) assumption that
many transactions will have items in common to build a prefix tree. If the
assumption holds true, this tree produces a compact representation of the actual
transactions and is used to generate itemsets much faster than *Apriori* can.

Announce:
---------

This Project is fork from [enaeseth](https://github.com/enaeseth)'s open source Project [Python FP-Growth](https://github.com/enaeseth/python-fp-growth). Seace that the project haven't been maintained for several years, I decide to fork a new project for python3's version.

Installation
------------

After downloading and extracting the package, install the module by running
`python setup.py install` from within the extracted package directory. (If you
encounter errors, you may need to run setup with elevated permissions:
`sudo python setup.py install`.)

Library Usage
-------------

Usage of the module is very simple. Assuming you have some iterable of transactions (which are themselves iterables of items) called `transactions` and
an integer minimum support value `minsup`, you can find the frequent itemsets
in your transactions with the following code:

    from fp_growth import find_frequent_itemsets
    for itemset in find_frequent_itemsets(transactions, minsup):
        print itemset

Note that `find_frequent_itemsets` returns a generator of itemsets, not a
greedily-populated list. Each item must be hashable (i.e., it must be valid as
a member of a dictionary or a set).

Script Usage
------------

Once installed, the module can also be used as a stand-alone script. It will
read a list of transactions formatted as a CSV file. (An example of such a file
in included in the `examples` directory.)

    python3 -m fp_growth -s {minimum support} {path to CSV file}

For example, to find the itemsets with support ≥ 4 in the included example file:

    python3 -m fp_growth -s 4 examples/tsk.csv

Also, sopport can be a support rate, for example:

    python3 -m fp_growth -s 0.3 examples/tsk.csv

You can find association rules as well, as sample

    python3 -m fp_growth -f rule -c 0.4 -s 4 examples/tsk.csv

We used -f to decide what you want to find, association rule or frequency itemset

All parameter:
* `-s`: minimum support (count or rate is fine)
* `-c`: minimum confidence
* `-f`: problem solving (freq or rule)

References
----------

The following references were used as source descriptions of the algorithm:

- Tan, Pang-Ning, Michael Steinbach, and Vipin Kumar. Introduction to Data
  Mining. 1st ed. Boston: Pearson / Addison Wesley, 2006. (pp. 363-370) 
- Han,  Jiawei, Jian Pei, and Yiwen Yin. "Mining Frequent Patterns without
  Candidate Generation." Proceedings of the 2000 ACM SIGMOD international
  conference on Management of data, 2000.
  
The example data included in `tsk.csv` comes from the section in *Introduction
to Data Mining*.

License
-------

The `python3-Fp-growth` package is made available under the terms of the
[MIT License](LICENSE).

Copyright © 2018 [C.A.Lee][me]

[me]: http://github.com/calee0219/

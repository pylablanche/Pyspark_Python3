# Pyspark in Python 3

_Status_ : Under Development

_Author_ : Pierre-Yves Lablanche

In this repository I compile information and resources collected while learning how to use pyspark.
If one day it happens to help someone that would make me very happy, in the meantime I'll try to keep updating it.
Note that I'm open to any comments.

## What's New

beta : first push to the repo

## Installation

_On Unix Systems_

That is the first tedious part with pyspark : getting everything installed and working.
I've tried to keep installation and modification to the minimum and cannot promise it would work on every machine.

__Python packages__

That's the easy part (of the annoying part), just type :
```sh
pip3 install requirements.txt
```

__Spark 2.1.1__

First you need to go to the [Spark download page](http://spark.apache.org/downloads.html), choose the _Spark release_, _package type_ and _download type_ (you probably won't need to modify anything).
Once the download is finished go to the folder containing the file and enter the following lines :
```sh
$ tar xzvf spark-2.1.1-bin-hadoop2.7.tgz
$ mv spark-2.1.1-bin-hadoop2.7/ /opt/spark-2.1.1
```

Then you can create a symlink to the binary file :
```sh
$ ln -s /opt/spark-2.1.1/ /opt/spark
```

In order to use spark/pyspark with python3 you also need to set some environment variable in your `.bashrc` or `.bash_profile`.
Just add the following lines :
```
export SPARK_HOME=/opt/spark
export PATH=$SPARK_HOME/bin:$PATH
export PYSPARK_PYTHON=python3
```

And that's it for spark.
Note that you also need to have java installed on your computer.

__Notes on Java__

To know which version is installed on your computer run the following command :
```sh
$ java -version
```

Note that the java test [webpage](https://java.com/en/download/installed.jsp) might tell you that the latest java version is installed even though the previous command line returns nothing (or just a message telling you you need to install java).
This is because you probably only have the Runtime Environment installed (jre) which won't allow you to use spark/pyspark.
I hence decided to install the full Java Development Kit (jdk) and it worked.

__Testing the Installation__

To check the installation has been succesful just type :
```sh
$ pyspark
```

and you should see something like that :
```sh
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /__ / .__/\_,_/_/ /_/\_\   version 2.1.1
      /_/

Using Python version 3.5.2 (v3.5.2:4def2a2901a5, Jun 26 2016 10:47:25)
SparkSession available as 'spark'.
>>>
```


## Starting Jupyter with Spark

Now everything has been installed we can start a jupyter notebook with pyspak as followed :
```sh
PYSPARK_DRIVER_PYTHON=jupyter PYSPARK_DRIVER_PYTHON_OPTS='notebook' pyspark
```

It is also possible to set `PYSPARK_DRIVER_PYTHON` and `PYSPARK_DRIVER_PYTHON_OPTS` as global environment variables, just add to your `.bashrc` or `.bash_profile` the two following lines :
```
export PYSPARK_DRIVER_PYTHON=jupyter
export PYSPARK_DRIVER_PYTHON_OPTS='notebook'
```
This way you will automatically start jupyter notebook with pyspark when typing :
```sh
$ pyspark
```

(I personnaly prefer the first option as I don't want to automatically start a notebook when running pyspark)

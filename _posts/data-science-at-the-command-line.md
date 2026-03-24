# data-science-at-the-command-line
Wayback Machine URL: https://web.archive.org/web/20230129165423/https://www.quantmetry.com/blog/data-science-at-the-command-line/
Archive date: 2023-01-29

Uncategorized 

22/01/2015 

#  Data Science at the command line 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdata-science-at-the-command-line%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Data%20Science%20at%20the%20command%C2%A0line&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdata-science-at-the-command-line%2F "Twitter")

* * *

Temps de lecture : 6 minutes 

![Quantmetry.com : Data Science at the command line](https://quantmetry.b-cdn.net/wp-content/uploads/2015/01/screen-shot-12-31-18-at-10-37-am.jpg)

The command line interface (CLI) is a tool that dates back to the 70s. After the punched cards invented in the early 18th century, and after the teleprinters used since the early 20th century, one can say that the CLI was the first tool for a truly interactive communication between a human and a machine. 

Since then, the WIMP (Windows, icons, menus, pointer) system or the GUI (Graphical User Interface), was invented at Xerox PARC and popularized by Apple’s Macintoshes in the 80s. 

Why then use the CLI, a more-than-forty-years-old dinosaur, when we can click, drap-and-drop, and visualize data in a nice, beautifully designed GUI? Even on a remote server, one can make ssh tunnels for the graphics and have access through a web interface and click everything away. 

Nowadays, data scientists come from various horizons. Until now, many of them have only known Windows and Apple’s environments and have had little contact with the CLI. That makes them rush for the GUI because they feel safer and more productive there. Our point here is to convince them that the gain in productivity lies when you move from the GUI to the CLI. 

In addition, there is nowadays a very human phenomenon to be aware of. Many companies invest a lot of hopes, human resources and money in big data technologies. And they are right to do so. We must be data driven and that often means being big data driven. But while Big Data new technologies do bring a lot of value to our data and break down many barriers, one must keep a clear head and avoid rushing on our Hadoop clusters for every data-driven operation we want to perform. Some of the work can and should still be done with classic technologies such as the CLI. 

So, why the CLI? Well, there are tons of reasons. 

First, the CLI is an extremely stable environment: many of its components haven’t changed a bit since 30 years. That certainly pays off any learning effort. 

Secondly, well, Apple with its AppStore did not invent the concept of the « App » that can make one single thing and does it really well. The principle was enunciated in the 70s by Doug McIlroy for the CLI. Doug McIlroy is the one who developed Unix pipelines as well as many Unix tools, such as diff, sort, join, speak, tr, etc. In 1978, in [The Bell System Technical Journal. Bell Laboratories. M. D. McIlroy, E. N. Pinson, and B. A. Tague. “Unix Time-Sharing System Forward”. 1978. 57 (6, part 2). p. 1902.], he stated the principles of Unix philosophy as he saw it: 

  * Write programs that do one thing and do it well. 

  * Write programs to work together. 

  * Write programs to handle text streams, because that is a universal interface. 




So: one of the strongest advantages of the CLI is: it is simple, agile and highly modular by design. 

Thirdly, the CLI is interactive. It is an REPL (read-eval-print loop) environment, as opposed to the edit-compile-run-debug systems. And this makes it an ideal tool for data exploration and for quickly designing operations and building data flows. 

Additional reasons are the fact that the CLI integrates really well with many other technologies and your favorite programming languages (C/C++, perl, ruby, python, R, etc.). Consider the auto-completion feature and the possibility to create your own programs easily and thus automate repetitive tasks and increase your productivity. 

Lastly, we should keep in mind that the CLI is close to the file system, hence close to our data. This means execution speed. Yes, CLI is fast, and it can be faster than Big Data technologies such as Hadoop. Adam Drake [http://aadrake.com/command-line-tools-can-be-235x-faster-than-your-hadoop-cluster.html] demonstrated that recently by comparing the execution time of the same data operations on a data set of 1.75 GB on both Hadoop and the CLI. Verdict? 26 minutes (1.14MB/sec) on a Hadoop cluster and 12 seconds on a laptop (270MB/sec). 

How come the CLI can be that much faster than Hadoop? Again, simplicity, speed, and a reduced line of communication. Jobs on Hadoop have to go through a job scheduler, the data location must be identified, instructions be send to the different nodes, results sent back and instructions resent again. On the CLI of a single laptop, all this is unnecessary. A fun way to think about it is to remember that streaming has not been invented with Storm or Spark. No, it was invented along with the CLI. Here is an illustration of how Adam Drake nicely puts it. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-31-18-at-10.38-AM.jpg)

You can even MapReduce at the command line (somehow, joking): 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-31-18-at-10.38-AM-001.jpg)

We are certainly not saying that the CLI is always faster than a Hadoop cluster. We are just saying, instead of rushing on Hadoop, Storm, Spark, etc., you should stop and think what is going to be the most efficient and the easiest way. Developers know a lot about the CLI, and a lot about Big Data technologies. That may not be the case for young data scientists who are constantly told that big data is the key. Yes it is, but not in all cases and people should be aware of the power of older tools that remain a very good solution. 

You should learn programming at the CLI. For that, there are numerous resources: 

  * the nice book by William Shotts, The Linux Command Line, contains everything you need to start, understand and become an expert; 

  * Data Science at the Command Line, by Jeroen Janssens, explains how a data scientist can make the most of the CLI working with data; 

  * if you like videos (in French), some people recommended us the following: 

    *     *     *     * https://www.youtube.com/watch?feature=player_embedded&v=U-KmLopaOiw 




There are many commands worth knowing we would like to mention here. We will limit ourselves only to a few, particularly useful for the data scientist: GNU parallel and the csvkit tools. We will defer to a later post a discussion about command line tools for machine learning such as mlpack, dbacl, or Vowpal Wabbit, and many more. 

##  GNU PARALLEL 

GNU Parallel is a nice tool developed by O. Tange to allow to execute many jobs in parallel in a smart way. Indeed as explained at https://www.biostars.org/p/63816/, if you have 32 different jobs you want to run on 4 CPUs, a straightforward way to parallelize is to divide your 32 jobs in 4, and run 8 jobs on each CPU. This is the naive parallelization. 

Instead, what GNU parallel does is to send a new process to a CPU whenever it become idle after finishing a job. That way, all the CPUs are active at all times and the user time wasted in waiting for the end of execution is considerably reduced. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-31-18-at-10.38-AM-002.jpg)

That tool shows extremely useful when you want to boost your data treatments. GNU parallel is even able to send jobs on remote machines. Of course, this is nothing compared to YARN or Mesos, but it is nice and smooth when you don’t have tens or hundreds of GBs of data. 

##  CSVKIT 

Another thing that is important to mention is csvkit, an ensemble of tools for converting to and working with csv. You can visualize you data with csvlook. 

**![csvlook myfile</strong> That simple! And yes, you can make joins on csv with that, just like with any honest SQL query: inner join, left/right join, outer join. Just use csvjoin: <strong>](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-89a3f52ce25fd7f693fd1ab06e43c5db_l3.png) csvjoin -c « mykey1,mykey2 » myfile1 myfile2 > myresultingcsvfile **

Other useful tools are: 

  * csvstack to combine subsets; 

  * csvsql and sql2csv to get data in and out of a SQL database; 

  * csvcut, the data scalpel, to slide, delete, reorder the columns of a csv; 

  * csvstat, well, to get fast stats about your columns; 

  * csvgrep to grep values; 

**csvgrep -c country -m France**

is equivalent to 

**SELECT * from mytable where country== »France »**

  * csvsort to make everything in order; 

  * csvjson to work with json. 




Read the doc on csvkit, it’s worth having a closer look! 

We hope that you are now convinced you should learn more about the CLI and use it intensively. 

Keep your Hadoop cluster and use it, but don’t forget that the CLI is really good for starting your data projects. Take a 1 GB sample and explore the data, find out what needs to be cleaned, play a little with machine learning tools, do some feature or model discovery. Then, once you are acquainted with your data and you know what you want to do with it, scale all your work, go back to your cluster and translate your data flow in your favorite big data technology: MapReduce it, Storm it, Spark it. 

And enjoy and have lots of fun! 

Bibliography 

  * The Art of Unix Programming, Eric Steven Raymond, Chapter 1: Basics of the Unix Philosophy (http://www.faqs.org/docs/artu/ch01s06.html) 

  * The Linux Command Line, William Shotts (http://linuxcommand.org/tlcl.php) 

  * Data Science at the Command Line, Jeroen Janssens (http://datascienceatthecommandline.com/) 




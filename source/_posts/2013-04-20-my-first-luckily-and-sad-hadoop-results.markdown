---
layout: post
title: My First Lucky and Sad Hadoop Results
date: 2013-04-20 17:05
comments: true
categories: [Hadoop, MapReduce, Bigdata, Analytic]
keywords: Hadoop, MapReduce, Bigdata Analytic, Weibo, Mapper, Reduce, Outputs, Aanlysis
description: After a couple of tryings, many are failed due to disk space shortage, after I decreased the input date set volumn, luckily I gained a completed Hadoop Job results, but, sadly, with only 1000 lines of records processed.
---

Recently I am playing with Hadoop per analyzing the data set I scraped from WEIBO.COM. After a couple of tryings, many are failed due to disk space shortage, after I decreased the input date set volumn, luckily I gained a completed Hadoop Job results, but, sadly, with only 1000 lines of records processed.

Here is the Job Summary:

| Counter		|Map		|Reduce			|Total
|Bytes Read		|7,945,196	|0			|7,945,196
|FILE_BYTES_READ	|16,590,565,518	|8,021,579,181		|24,612,144,699
|**HDFS_BYTES_READ**	|**_7,945,580_**	|0			|7,945,580
|FILE_BYTES_WRITTEN	|24,612,303,774	|8,021,632,091		|32,633,935,865
|HDFS_BYTES_WRITTEN	|0		|2,054,409,494		|2,054,409,494
|Reduce input groups	|0		|381,696,888		|381,696,888
|Map output materialized bytes	|8,021,579,181	|0		|8,021,579,181
|Combine output records		|826,399,600	|0		|826,399,600
|**Map input records**		|**_1,000_**		|0		|1,000
|Reduce shuffle bytes		|0		|8,021,579,181	|8,021,579,181
|Physical memory (bytes) snapshot	|1,215,041,536	|72,613,888	|1,287,655,424
|**Reduce output records**	|0	|**_381,696,888_**	|381,696,888
|Spilled Records	|1,230,714,511	|401,113,702	|1,631,828,213
|Map output bytes	|7,667,457,405	|0	|7,667,457,405
|Total committed heap usage (bytes)	|1,038,745,600	|29,097,984	|1,067,843,584
|CPU time spent (ms)	|2,957,800	|2,104,030	|5,061,830
|Virtual memory (bytes) snapshot	|4,112,838,656	|1,380,306,944	|5,493,145,600
|SPLIT_RAW_BYTES	|384	|0	|384
|**Map output records**	|**_426,010,418_**	|0	|426,010,418
|**Combine input records**	|**_851,296,316_**	|0	|851,296,316
|Reduce input records	|0	|401,113,702	|401,113,702



From which we can see that, specially metrics which highlighted in bold style, I only passed in about 7MB data file with 1000 lines of records, but Reducer outputs 381,696,888 records, which are 2.1GB compressed gz file and some 9GB plain text when decompressed.

But clearly it's not the problem of my code that leads to so much disk space usages, the above output metrics are all reasonable, although you may be surprised by the comparison between 7MB with only 1000 records input and  9GB  with 381,696,888 records output. The truth is that I'm calculating co-appearance combination computation.

From this experimental I learned that my personal computer really cannot play with big elephant, input data records from the first 10 thousand down to 5 thousand to 3 thousand to ONE thousand at last, but data analytic should go on, I need to find a solution to work it out, actually I have 30 times of data need to process, that is 30 thousand records.

Yet still have a lot of work to do, and I plan to post some articles about what's I have done with my *big data* :) and *Hadoop* so far.
  
`---EOF---`


 















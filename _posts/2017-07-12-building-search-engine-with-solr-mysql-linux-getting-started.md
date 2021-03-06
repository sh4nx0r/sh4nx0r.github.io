---
layout: post
title: "Getting Started: Building a simple search engine with Apache Solr."
description: An easy way to kick-start search engine development with Apache Solr.
headline: 
modified: 2017-07-12
category: development
tags: [searchengine, development, solr, apache, mysql, linux, windows, web ]
imagefeature: blogimages/2017-07-12/cover-2017-07-12.png
mathjax: 
chart: 
comments: true
featured: false
---

# [Apache *Solr*][1]

---

This is a total rip-off post from my contribution to Stackoverflow on ***Apache Solr*** . This post begins from **simple introduction** to **detailed installation** and **implementation**.


> # Simple Introduction

---
> - ### Can Apache Solr be used for High Traffic based websites? Does it utilize more CPU resources?

**Solr** shouldn't be used to solve real-time problems. For search engines, **Solr** is pretty much game and works *flawlessly*.

**Solr** works fine on High Traffic web-applications. It utilizes the RAM, not the CPU.

 
>  - ### How does Apache Solr scores with respect to results, relevance and ranking?

The **boost** helps you rank your results show up on top. Say, you're trying to search for a name *john* in the fields *firstname* and *lastname*, and you want to give relevancy to the *firstname* field, then you need to **boost** up the *firstname* field as shown. 
>
<!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">http://localhost:8983/solr/collection1/select?q=firstname:john^2&amp;lastname:john</pre></div>


As you can see, *firstname* field is **boosted** up with a score of 2.

More on [**SolrRelevancy**][2]

>  - ### Can you tell me about the indexing speed of Apache Solr?

The speed is unbelievably fast and no compromise on that.

Regarding the indexing speed, **Solr** can also handle **JOINS** from your database tables. A higher and complex **JOIN** do affect the indexing speed. However, an enormous **RAM** configuration can easily tackle this situation.

The higher the RAM, the faster the indexing speed of Solr is.


>  - ### Can Apache Solr integrated with Django?

Never had a chance to attempt that, however you can achieve that with [Haystack][3]. I found some interesting [article][4] on the same and here's the [github][5] for it.

>  - ### I have a question on resource requirements - My website will be hosted on a VPS, so ideally the search engine wouldn't require a lot of RAM and CPU?

**Solr** breeds on RAM, so if the RAM is high, you don't to have to worry about it.

**Solr's** RAM usage shoots up on full-indexing if you have some billion of records, you could smartly make use of **Delta Imports** to tackle this situation. As explained, **Solr** is only a _near_ real-time solution.

>  - ### Heard from sources that Solr does not possess scalability factor. Is it true?

**Solr** is highly scalable. Have a look on [SolrCloud][6].
Some key features of it.
 
- Shards (or sharding is the concept of distributing the index among multiple machines, say if your index has grown too large)
- Load Balancing (if [Solrj][7] is used with Solr cloud it automatically takes care of load-balancing using it's Round-Robin mechanism)
- [Distributed Search][8]
- High Availability

>  - ### Does it have any extra features like Google does - such as "did you mean by?", related searches, etc?

For the above scenario, you could use the [SpellCheckComponent][9] that is shipped with **Solr**. There are a lot other features, The [SnowballPorterFilterFactory][10] helps to retrieve records say if you typed, *books* instead of *book*, you will be presented with results related to *book*.

### This answer broadly focuses on **Apache Solr** & **MySQL**.  

> **Important**: Assuming that you are under **LINUX** environment, you could proceed to this article further. (mine was an Ubuntu 14.04 version). Windows users. Sorry.

---

> # Detailed Installation

### Getting Started

Download **Apache Solr** from [here][11]. That would be version is **4.8.1**. You could download new versions, I found this one pretty stable.

After downloading the archive, extract it to a folder of your choice. 
Say ..  **Downloads** or whatever.. So it will look like 
> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">Downloads/solr-4.8.1/</pre></div>

On your prompt..  Navigate inside the directory

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">shankar@shankar-lenovo: cd Downloads/solr-4.8.1</pre></div>


So now you are here.. 

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">shankar@shankar-lenovo: ~/Downloads/solr-4.8.1$ </pre></div>

### Start the Jetty Application Server

**Jetty** is available inside the examples folder of the **solr-4.8.1** directory , so navigate inside that and start the Jetty Application Server.

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">shankar@shankar-lenovo:~/Downloads/solr-4.8.1/example$ java -jar start.jar</pre></div>

Do not close the terminal, minimize it and let it stay aside. 

> **Tip** : Use **&** after start.jar to make the Jetty Server run in the background 

To check if **Apache Solr** runs successfully, visit this URL on the browser.

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">http://localhost:8983/solr</pre></div>


### Running Jetty on custom Port 

It runs on the port 8983 as default. You could change the port either here or directly inside the **jetty.xml** file.

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">java -Djetty.port=9091 -jar start.jar</pre></div>


### Download the JConnector

This JAR file acts as a bridge between **MySQL** and JDBC , Download the Platform Independent Version [here][12]

After downloading it, extract the folder and copy the **mysql-connector-java-5.1.31-bin.jar** and paste it to the **lib** directory.

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">shankar@shankar-lenovo:~/Downloads/solr-4.8.1/contrib/dataimporthandler/lib</pre></div>


### Creating the MySQL table to be linked to Apache Solr

To put **Solr** to use, You need to have some tables and data to search for. For that, we will use **MySQL** for creating a table and pushing some random names and then we could use **Solr** to connect to **MySQL** and index that table and it's entries.

 

> ### 1. Table Structure

>
<!-- HTML generated using hilite.me (emacs syntax) --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="line-height: 125%"><span style="color: #AA22FF; font-weight: bold">CREATE</span> <span style="color: #AA22FF; font-weight: bold">TABLE</span> <span style="color: #00A000">test_solr_mysql</span>
     (
      id <span style="color: #00BB00; font-weight: bold">INT</span> <span style="color: #AA22FF; font-weight: bold">UNSIGNED</span> <span style="color: #AA22FF; font-weight: bold">NOT</span> <span style="color: #880000">NULL</span> <span style="color: #AA22FF">AUTO_INCREMENT</span>,
      name <span style="color: #00BB00; font-weight: bold">VARCHAR</span>(<span style="color: #666666">45</span>) <span style="color: #880000">NULL</span>,
      created <span style="color: #00BB00; font-weight: bold">TIMESTAMP</span> <span style="color: #880000">NULL</span> <span style="color: #AA22FF; font-weight: bold">DEFAULT</span> <span style="color: #AA22FF; font-weight: bold">CURRENT_TIMESTAMP</span>,
      <span style="color: #AA22FF; font-weight: bold">PRIMARY</span> <span style="color: #AA22FF; font-weight: bold">KEY</span> (id)
     );</pre></div>


> ### 2. Populate the above table

>
<!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Jean&#39;</span>);
    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Jack&#39;</span>);
    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Jason&#39;</span>);
    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Vego&#39;</span>);
    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Grunt&#39;</span>);
    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Jasper&#39;</span>);
    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Fred&#39;</span>);
    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Jenna&#39;</span>);
    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Rebecca&#39;</span>);
    <span style="color: #AA22FF; font-weight: bold">INSERT</span> <span style="color: #AA22FF; font-weight: bold">INTO</span> <span style="color: #B8860B">`test_solr_mysql`</span> (<span style="color: #B8860B">`name`</span>) <span style="color: #AA22FF; font-weight: bold">VALUES</span> (<span style="color: #BB4444">&#39;Roland&#39;</span>);</pre></div>


### Getting inside the core and adding the lib directives

> ### 1. Navigate to 

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="line-height: 125%">shankar@shankar-lenovo: ~/Downloads/solr-4.8.1/example/solr/collection1/conf</pre></div>
    

> ### 2. Modifying the solrconfig.xml

Add these two directives to this file..

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="line-height: 125%"><span style="color: #008000; font-weight: bold">&lt;lib</span> <span style="color: #BB4444">dir=&quot;../../../contrib/dataimporthandler/lib/&quot;</span> <span style="color: #BB4444">regex=&quot;.*\.jar&quot;</span> <span style="color: #008000; font-weight: bold">/&gt;</span>
      <span style="color: #008000; font-weight: bold">&lt;lib</span> <span style="color: #BB4444">dir=&quot;../../../dist/&quot;</span> <span style="color: #BB4444">regex=&quot;solr-dataimporthandler-\d.*\.jar&quot;</span> <span style="color: #008000; font-weight: bold">/&gt;</span></pre></div>


Now add the **DIH** (Data Import Handler)

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="line-height: 125%">    <span style="color: #008000; font-weight: bold">&lt;requestHandler</span> <span style="color: #BB4444">name=&quot;/dataimport&quot;</span> 
      <span style="color: #BB4444">class=&quot;org.apache.solr.handler.dataimport.DataImportHandler&quot;</span> <span style="color: #008000; font-weight: bold">&gt;</span>
        <span style="color: #008000; font-weight: bold">&lt;lst</span> <span style="color: #BB4444">name=&quot;defaults&quot;</span><span style="color: #008000; font-weight: bold">&gt;</span>
          <span style="color: #008000; font-weight: bold">&lt;str</span> <span style="color: #BB4444">name=&quot;config&quot;</span><span style="color: #008000; font-weight: bold">&gt;</span>db-data-config.xml<span style="color: #008000; font-weight: bold">&lt;/str&gt;</span>
        <span style="color: #008000; font-weight: bold">&lt;/lst&gt;</span>
    <span style="color: #008000; font-weight: bold">&lt;/requestHandler&gt;</span></pre></div>


> ### 3. Create the db-data-config.xml file 

If the file exists then ignore, add these lines to that file. As you can see the first line, you need to provide the credentials of your **MySQL** database. The Database name, username and password.

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="line-height: 125%">    <span style="color: #008000; font-weight: bold">&lt;dataConfig&gt;</span>
        <span style="color: #008000; font-weight: bold">&lt;dataSource</span> <span style="color: #BB4444">type=&quot;JdbcDataSource&quot;</span> <span style="color: #BB4444">driver=&quot;com.mysql.jdbc.Driver&quot;</span> <span style="color: #BB4444">url=&quot;jdbc:mysql://localhost/yourdbname&quot;</span> <span style="color: #BB4444">user=&quot;dbuser&quot;</span> <span style="color: #BB4444">password=&quot;dbpass&quot;</span><span style="color: #008000; font-weight: bold">/&gt;</span>
        <span style="color: #008000; font-weight: bold">&lt;document&gt;</span>
       <span style="color: #008000; font-weight: bold">&lt;entity</span> <span style="color: #BB4444">name=&quot;test_solr&quot;</span> <span style="color: #BB4444">query=&quot;select CONCAT(&#39;test_solr-&#39;,id) as rid,name from test_solr_mysql WHERE &#39;${dataimporter.request.clean}&#39; != &#39;false&#39;</span>
<span style="color: #BB4444">          OR `created` &gt; &#39;${dataimporter.last_index_time}&#39;&quot;</span> <span style="color: #008000; font-weight: bold">&gt;</span>
        <span style="color: #008000; font-weight: bold">&lt;field</span> <span style="color: #BB4444">name=&quot;id&quot;</span> <span style="color: #BB4444">column=&quot;rid&quot;</span> <span style="color: #008000; font-weight: bold">/&gt;</span>
        <span style="color: #008000; font-weight: bold">&lt;field</span> <span style="color: #BB4444">name=&quot;solr_name&quot;</span> <span style="color: #BB4444">column=&quot;name&quot;</span> <span style="color: #008000; font-weight: bold">/&gt;</span>
        <span style="color: #008000; font-weight: bold">&lt;/entity&gt;</span>
       <span style="color: #008000; font-weight: bold">&lt;/document&gt;</span>
    <span style="color: #008000; font-weight: bold">&lt;/dataConfig&gt;</span></pre></div>


> **Tip** : You can have any number of entities but watch out for id field, if they are same then indexing will skipped.

> ### 4. Modify the schema.xml file

Add this to your **schema.xml** as shown.. 

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="line-height: 125%"><span style="color: #008000; font-weight: bold">&lt;uniqueKey&gt;</span>id<span style="color: #008000; font-weight: bold">&lt;/uniqueKey&gt;</span>
<span style="color: #008000; font-weight: bold">&lt;field</span> <span style="color: #BB4444">name=&quot;solr_name&quot;</span> <span style="color: #BB4444">type=&quot;string&quot;</span> <span style="color: #BB4444">indexed=&quot;true&quot;</span> <span style="color: #BB4444">stored=&quot;true&quot;</span> <span style="color: #008000; font-weight: bold">/&gt;</span></pre></div>



---

> # Implementation

### Indexing

This is where the real deal is. You need to do the indexing of data from **MySQL** to **Solr** inorder to make use of Solr Queries.

> ### Step 1: Go to Solr Admin Panel

Hit the URL **http://localhost:8983/solr** on your browser. The screen opens like this. 

![This is the main Apache Solr Administration Panel][13]

As the marker indicates, go to **Logging** inorder to check if any of the above configuration has led to errors.

> ### Step 2: Check your Logs

Ok so now you are here, As you can see there are a lot of yellow messages (WARNINGS). Make sure you don't have error messages marked in red. Earlier, on our configuration we had added a select query on our **db-data-config.xml**, say if there were any errors on that query, it would have shown up here.

![This is the logging section of your Apache Solr engine][14]

Fine, no errors. We are good to go. Let's choose **collection1** from the list as depicted and select **Dataimport**


> ### Step 3: DIH (Data Import Handler)

Using the DIH, you will be connecting to **MySQL** from **Solr** through the configuration file **db-data-config.xml** from the **Solr** interface and retrieve the 10 records from the database which gets indexed onto **Solr**.

To do that, Choose **full-import** , and check the options *Clean* and *Commit*. Now click **Execute** as shown.

Alternatively, you could use a direct **full-import** query like this too..

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">http://localhost:8983/solr/collection1/dataimport?command=full-import&commit=true</pre></div>


![The Data Import Handler][15]

After you clicked **Execute**, **Solr** begins to index the records, if there were any errors, it would say **Indexing Failed** and you have to go back to the **Logging** section to see what has gone wrong.

Assuming there are no errors with this configuration and if the indexing is successfully complete., you would get this notification.

![Indexing Success][16]


> ### Step 4: Running Solr Queries

Seems like everything went well, now you could use **Solr** Queries to query the data that was indexed. Click the **Query** on the left and then press **Execute** button on the bottom.

You will see the indexed records as shown.

The corresponding **Solr** query for listing all the records is

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">http://localhost:8983/solr/collection1/select?q=*:*&wt=json&indent=true</pre></div>

![The indexed data][17]

Well, there goes all 10 indexed records. Say, we need only names starting with **Ja** , in this case, you need to target the column name `solr_name`, Hence your query goes like this.

> <!-- HTML generated using hilite.me --><div style="background: #f8f8f8; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">http://localhost:8983/solr/collection1/select?q=solr_name:Ja*&wt=json&indent=true</pre></div>


![The JSON data starting with Ja*][18]

That's how you write **Solr** Queries. To read more about it, Check this beautiful [article][19].


  [1]: http://lucene.apache.org/solr/
  [2]: https://wiki.apache.org/solr/SolrRelevancyFAQ
  [3]: http://haystacksearch.org/
  [4]: http://www.alexanderinteractive.com/blog/2012/08/getting-started-with-solr-and-django/
  [5]: https://github.com/broderboy/django-solr-demo
  [6]: https://cwiki.apache.org/confluence/display/solr/SolrCloud
  [7]: http://wiki.apache.org/solr/Solrj
  [8]: http://wiki.apache.org/solr/DistributedSearch
  [9]: http://wiki.apache.org/solr/SpellCheckComponent
  [10]: http://lucene.apache.org/solr/3_6_1/org/apache/solr/analysis/SnowballPorterFilterFactory.html
  [11]: http://apache.mirrors.hoobly.com/lucene/solr/4.8.1/
  [12]: http://dev.mysql.com/downloads/connector/j/
  [13]: http://i.stack.imgur.com/8grrc.png
  [14]: http://i.stack.imgur.com/8l6n5.png
  [15]: http://i.stack.imgur.com/sHvSO.png
  [16]: http://i.stack.imgur.com/WlD07.png
  [17]: http://i.stack.imgur.com/aZP9W.png
  [18]: http://i.stack.imgur.com/qeArE.png
  [19]: http://lucene.apache.org/core/3_5_0/queryparsersyntax.html


---

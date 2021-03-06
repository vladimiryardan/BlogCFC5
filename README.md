[![Build Status](https://travis-ci.org/teamcfadvance/BlogCFC5.png?branch=master)](https://travis-ci.org/teamcfadvance/BlogCFC5)
# BlogCFC5

The Number One Blogging Software In The ColdFusion Universe!

**Updates to BlogCFC**

**2019/1/1 Update 1**: 

* In admin: Added enclosure link as part of edit entry 
* Move all udf.cfm functions into utils.cfc (Done in last update), redirected all function calls to reference application.utils, and deleted udf.cfm  
* Convert Application.cfm to Application.cfc 
* Fix a bunch of queries where I missed putting in the tableprefix property. No idea why IntelliJ wasn't showing me the full list when searcing.
* Added new SQL to create tables and views for SQL Server.  
    * Was used for ad tracking on The Flex Show
        * Ad_media
        * Ad_medialog
        * Ad_mimetypes
    * Was used for download tracking on The Flex Show and Flextras and others
        * Tblblogenclosuredownloads
    * Views used to help run reports on download tracking: 
        * NumberOfBlogEntriesByCategory
        * NumberOfBlogEntriesByYear
        * NumberOfBlogEntriesByYearThenCategory
* Added download.cfm which will log the download request and redirect to the downloaded file. This works for either a ID for a blog post with an enclosure or an explicitly defined file.
* Added download2.cfm which will log the download request and stream the file without changing the URL.

**2018/12/28 Update 2**: 

* Merged in my own BlogCFC Extension. 
    * Created download tracker code for tracking and reporting on enclosure downloads
    * Added a tableprefix= config property.  This is if you want to add a prefix to the table name and will be appended to all queries.  If you use this, then you won't be able to use the SQL Generate scripts or the install/update package.
    * Added BlogDBName argument to blog.cfc init.  This refers to name of the blog in the database and allows you to use different db names in the config file vs the database.
    * Added isAvailable argument to blog.cfc entryexists() and getEntry(). If passed in as true, will allow an entry to exist even if it is not available yet
    * Tweaked RSS 2.0 generation to add media tags; I think this supports podcasting platforms other than iTunes.
    * Added a bunch more functions to utils--don't remember what they are all used for. 

**ToDo**:
I still need to add scripts for the relevant new tables info.

**2018/12/28**: 

Since the project hasn't had an update in ages, I probably won't bother to try to do PRs back to the main branch, but decided to stick with BlogCFC for the moment for my own personal blog.

My instructions including table modifications on updating the database from 5.9.2.002 to the current at located in: 

    install/Upgrade5.9.2.00.2To5.9.8.001.txt 
        
I use SQL Server, so that is all that you're find.


I added a new property to the `blog.ini.cfm`: 


    maxentriesadmin=10
    
This allows you to show a different number of posts in the client UI compare to a different number of posts in the admin.



CodeIgniter Solr PHP Client
===========================

This is a simple library for CodeIgniter to interface with Solr. I am not the original author of the code, I've just made it compatible with codeigniter.

This CI library is based on [Apache Solr PHP Client](https://code.google.com/p/solr-php-client/).

I created this while implementing solr search on my [lyrics](http://decoda.com) site.

Usage
=====

Put the files from this repo into `application/libraries/solr`.

This library is very simple to install, simply load it the way you do any other CI library and pass it an array of parameters (optional).

    $this->load->library('solr',array(
        'port' => 8983,
        'path' => '/solr/posts/'
    ));

You need to set `/solr/posts/` to match the name of the core you are searching.

Peforming a simple search
-------------------------
Doing a simple search is easy:

    $results = $this->solr->search('cactus');

Performing a DisMax or advanced search
--------------------------------------
The simple search above is not useful for real world search applications. You can use the other paramaters of `search()` to use advanced features such as DisMax:

    $results = $this->solr->search('cactus', 0, 10, array(
        'defType' => 'edismax',
        'mm' => '100%',
        'qf' => 'title^10+bodytext'
    ));
    

youthere
===========

[![Build Status](https://travis-ci.org/buonzz/youthere.svg?branch=master)](https://travis-ci.org/buonzz/youthere)

A Class Library to Check if files is present in another server

Have you ever been in a situation that your web application is in server A, then your video/media files is on server B
Then some logic in your application relies on the presence of a particular file in Server B?

Example Scenario:
You only wanted to show the HD button in your website, if the HD video file in another server is present.
This library will help you in doing such query in a very easy to use interface.

Requirements
------------

* PHP >= 5.2
* Composer
* Valid FTP account to the server that you need to query

Installation
------------

The easiest way to install this is to use composer

    composer require buonzz/youthere:dev-master


Usage
-----

Using it is very easy

    $yt = new Buonzz\Youthere\Youthere;
    $results = $yt->check_files_presence(
        $paths, 
        $ftp_host, 
        $ftp_username, 
        $ftp_password);


$paths - is an array of paths to the files that should be checked the presence in the server. Note that the path is the path on the target server

$ftp_host - is the hostname of the server that contains the files to check
$ftp_username - is the ftp username
$ftp_password - is the ftp password

The $results will return an array, on which the keys are the $paths variable, on which each value is either a TRUE/FALSE, depending on whether the file is present in the server or not.

For example, passing this array

    array('/folder1/file1.txt', '/folder2/picture.png')
    
will return this array result

    array('/folder1/file1.txt' => TRUE , '/folder2/picture.png' => FALSE)

Given that, file1.txt is present in the server, and picture.png wasn't

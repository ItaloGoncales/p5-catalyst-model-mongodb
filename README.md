# NAME

Catalyst::Model::MongoDB - MongoDB model class for Catalyst

# SYNOPSIS

    #
    # Config
    #
    <Model::MyModel>
        host localhost
        port 27017
        dbname mydatabase
        collectionname preferedcollection
        gridfs preferedgridfs
    </Model::MyModel>

    #
    # Usage
    #
    $c->model('MyModel')->db                           # returns MongoDB::Connection->mydatabase
    $c->model('MyModel')->db('otherdb')                # returns ->otherdb
    $c->model('MyModel')->collection                   # returns ->mydatabase->preferedcollection
    $c->model('MyModel')->coll                         # the same...
    $c->model('MyModel')->c                            # the same...
    $c->model('MyModel')->c('otherdb.othercollection') # returns ->otherdb->othercollection
    $c->model('MyModel')->c('somecollection')          # returns ->mydatabase->somecollection
    $c->model('MyModel')->gridfs                       # returns ->mydatabase->get_gridfs('preferedgridfs')
    $c->model('MyModel')->g                            # the same...
    $c->model('MyModel')->g('somegridfs')              # returns ->mydatabase->get_gridfs('somegridfs')
    $c->model('MyModel')->g('otherdb.othergridfs')     # returns ->otherdb->get_gridfs('othergridfs')

    $c->model('MyModel')->run(...)                     # returns ->mydatabase->run_command(...)
    $c->model('MyModel')->eval(...)                    # returns ->mydatabase->eval(...)

    $c->model('MyModel')->database_names               # returns ->database_names
    $c->model('MyModel')->dbnames                      # the same...



# DESCRIPTION

This model class exposes [MongoDB::Connection](http://search.cpan.org/perldoc?MongoDB::Connection) as a Catalyst model.

# CONFIGURATION

You can pass the same configuration fields as when you make a new [MongoDB::Connection](http://search.cpan.org/perldoc?MongoDB::Connection).

In addition you can also give a database name via dbname, a collection name via collectioname or 
a gridfs name via gridfsname.

# METHODS

## dbnames

## database_names

List of databases.

## collnames

## collection_names

List of collection names of the default database. You cant give other database names here, if you need this please do:

  $c->model('MyModel')->db('otherdatabase')->collection_names

## collection

## coll

## c

Gives back a MongoDB::Collection, you can also directly access other dbs collections, with "otherdb.othercollection".
If no collectionname is given he uses the default collectionname given on config.

## gridfs

## g

Gives back a MongoDB::GridFS. If no gridfsname is given, he uses the default gridfsname given on config.

## run

Run a command via MongoDB::Database->run_command on the default database. You cant give other database names here,
if you need this please do:

  $c->model('MyModel')->db('otherdatabase')->run_command(...)

## eval

Eval code via MongoDB::Database->eval on the default database. You cant give other database names here,
if you need this please do:

  $c->model('MyModel')->db('otherdatabase')->eval(...)

## oid

Creates MongoDB::OID object

# SUPPORT

IRC

  Join #catalyst on irc.perl.org and ask for Getty.

Repository

  http://github.com/Getty/p5-catalyst-model-mongodb
  Pull request and additional contributors are welcome
 

Issue Tracker

  http://github.com/Getty/p5-catalyst-model-mongodb/issues

# AUTHOR

Torsten Raudssus <torsten@raudssus.de>
Soren Dossing <netcom@sauber.net>

# BUGS 

Please report any bugs or feature requests on the github issue tracker http://github.com/Getty/p5-catalyst-model-mongodb/issues
or to Getty or sauber on IRC at irc.perl.org, or make a pull request at http://github.com/Getty/cp5-catalyst-model-mongodb

# COPYRIGHT & LICENSE 

Copyright 2010 Torsten Raudssus & Soren Dossing, all rights reserved.

This library is free software; you can redistribute it and/or modify it under the same terms as 
Perl itself, either Perl version 5.8.8 or, at your option, any later version of Perl 5 you may 
have available.
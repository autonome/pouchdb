Tests are passing and this is ready for more usage/feedback. Works with Chrome 11/12 and Firefox 4.

# PouchDB ( Portable CouchDB JavaScript implementation )

PouchDB is a complete implementation of the CouchDB storage and views API that supports peer-to-peer replication with other CouchDB instances. The browser version is written for IndexedDatabase (part of HTML5). An additional implementation is in progress for leveldb.

#### Storage and Consistency

Unlike the other current couch-like browser APIs built on WebStorage (http://dev.w3.org/html5/webstorage/) PouchDB's goal is to maintain the same kinds of consistency guarantees Apache CouchDB provides across concurrent connections across the multiple-tabs a user might be using to concurrently access an PouchDB database. This is something that just isn't possible with the BrowserStorage API previous libraries like BrowserCouch and lawnchair use.

PouchDB also keeps a by-sequence index across the entire database. This means that, just like Apache CouchDB, PouchDB can replicate with other CouchDB instances and provide the same conflict resolution system for eventual consistency across nodes.

#### BrowserCouch

At this time PouchDB is completely independent from BrowserCouch. The main reason is just to keep the code base concise and focused as the IndexedDatabase specification is being flushed out.

After IndexedDatabase is more solidified it's possible that BrowserCouch and PouchDB might merge to provide a simple fallback option for browsers the do not yet support IndexedDatabase.

# API

## open(name[, callback])

This method opens an existing database by name if it exists or creates a new one if it does not exist.

The first argument is the name of the database to open. This is a string, and is required.

The second argument is an optional callback function, which is passed the following parameters:

* '`error`' - Null if no error occured. If an error occured, it is an object with an `error` property containing a string error code and a `reason` property containing a human-readable explanation of the error.
* '`database`' - Object representing the opened CouchDB database.

Example:

<pre>
  pouch.open("myDB", function (err, db) {
    // Use my CouchDB
  });
</pre>

## deleteDatabase(name)

This method deletes the database specified by `name`.

TODO: This method needs a callback consistent with the callback pattern in `open`.

## couch

The subject of the of createCouch success callback. This is primary PouchDB API.

### couch.get(docid, options, callback)

### couch.remove(doc, options)

### couch.post(doc, options, callback)

### couch.changes

### couch.changes(options)

### couch.changes.addListener(listener)

### couch.changes.removeListener(listener)

### couch.bulk(docs, options, callback)

### couch.replicate

### couch.replicate.from(options)


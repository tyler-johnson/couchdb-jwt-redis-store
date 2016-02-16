# Couchdb JWT Redis Session Store

[![npm](https://img.shields.io/npm/v/couchdb-jwt-store-redis.svg)](https://www.npmjs.com/package/couchdb-jwt-store-redis) [![David](https://img.shields.io/david/tyler-johnson/couchdb-jwt-redis-store.svg)](https://david-dm.org/tyler-johnson/couchdb-jwt-redis-store) [![Build Status](https://travis-ci.org/tyler-johnson/couchdb-jwt-redis-store.svg?branch=master)](https://travis-ci.org/tyler-johnson/couchdb-jwt-redis-store)

This is a Redis-backed session store for use with [CouchDB JWT](http://ghub.io/couchdb-jwt). This session store is recommended over the built-in CouchDB store, if performance matters to you.

## Install

Install with CouchDB JWT using NPM:

```sh
npm i couchdb-jwt couchdb-jwt-store-redis --save
```

## Usage

Pass to CouchDB JWT as a session store. Redis connection details can be passed as additional parameters.

```js
var couchdbjwt = require("couchdb-jwt");
var RedisStore = require("couchdb-jwt-store-redis");

couchdbjwt.set("session", {
	store: RedisStore,
	url: "redis://127.0.0.1:6379"
});

couchdbjwt.listen(3000);
```

You can pass in an existing Redis client from [node_redis](http://ghub.io/redis) with the client parameter.

```js
var client = redis.createClient();

couchdbjwt.set("session", {
	store: RedisStore,
	client: client
});
```

This store is also compatible with the CouchDB JWT cli.

```sh
couchdbjwt --session.store redis
```

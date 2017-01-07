Loopback SoftDelete
=============

This module is designed for the [Strongloop Loopback](https://github.com/strongloop/loopback) framework. It allows entities of any Model to be "soft deleted" by adding `deletedAt` and `isDeleted` attributes. Queries following the standard format will no return these entities; they can only be accessed by adding `{ isDeleted: true }` to the query object (at the same level as `where`, `include` etc).

Install
-------

##### NPM
```bash
  npm install --save loopback-softdelete
```

##### YARN
```bash
  yarn add loopback-softdelete
```

Configure
----------

To use with your Models add the `mixins` attribute to the definition object of your model config.

```json
  {
    "name": "project",
    "plural": "projects",
    "base": "PersistedModel",
    "properties": {
      "name": {
        "type": "string",
        "required": true
      }
    },
    "mixins": {
      "SoftDelete" : true,
    },
  },
```

Retrieving deleted entities
---------------------------

To run queries that include deleted items in the response, add `{ isDeleted: true }` to the query object (at the same level as `where`, `include` etc).

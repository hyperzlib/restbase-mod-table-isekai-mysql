# restbase-mod-table-isekai-mysql [![Build Status](https://travis-ci.org/hyperzlib/restbase-mod-table-isekai-mysql.svg?branch=master)](https://travis-ci.org/wikimedia/restbase-mod-table-isekai-mysql)

An MySQL back-end module for [RESTBase](https://github.com/wikimedia/restbase)
conforming to the [RESTBase storage
specification](https://github.com/wikimedia/restbase-mod-table-spec).

Based on [restbase-mod-table-mysql](https://github.com/wikimedia/restbase-mod-table-mysql). Fix the encoding problem of non-ASCII language and Object cache parsing problem.

## Installation

Firstly, install RESTBase. The MySQL back-end module should be pulled in
automatically as a dependency. If you cannot find `restbase-mod-table-isekai-mysql` in
RESTBase's `node_modules/` directory, install it using:

```
npm install restbase-mod-table-isekai-mysql
```

## Configuration
Configuration of this module takes place from within an `x-modules` stanza in the YAML-formatted
[RESTBase configuration file](https://github.com/wikimedia/restbase/blob/master/config.example.yaml).
While complete configuration of RESTBase is beyond the scope of this document, (see the
[RESTBase docs](https://github.com/wikimedia/restbase) for that), this section covers the
[restbase-mod-table-isekai-mysql](https://github.com/wikimedia/restbase-mod-table-isekai-mysql) specifics.

```yaml
    backend: mysql
    host: localhost
    database: restbase
    username: mysql
    password: mysql
    show_sql: false
    storage_groups:
      - name: local
        domains: /./
```

```yaml
    # Under /{api:sys}: x-modules: - spce:
    /table:
      x-modules:
        - name: restbase-mod-table-isekai-mysql
          version: 1.0.0
          type: npm
          options:
            conf: '{{options.table}}'
```

### Host
Database host name or IP address.

```yaml
    host: localhost
```

### Database
Name of the database used by RESTBase

```yaml
    database: somedatabase
```

### Credentials
Password credentials to use in authenticating with MySQL.

```yaml
    username: someuser
    password: somepass
```

### Storage Groups
Storage groups are used to map tables to one or more hosts/domains.

```yaml
    storage_groups:
      - name: default.group.local
        domains: /./
```
# persistent-store

> Simplify how to use IndexedDB

This library uses the IndexedDB library under the hood and makes it easy to use.

## Installation

```bash
npm install persistent-store --save
```

```bash
yarn add persistent-store
```

## Boot Options

In the PersistentStore class there is a static crateStore method that must be called before any interaction with the database. This method will initialize the bank with the settings you enter.

```javascript
import PersistentStore from 'persistent-store'

// `db_name` string containing the database name
// `db_version` integer containing the version of the database
// `db_collections` list containing all database collections and their settings
PersistentStore.crateStore('project', 1, [
  // db_collections

  // `collection_name` string containing the collection name
  // `collection_key` string containing the key to access each object in the collection
  // `collection_increment` boolean containing the rule for auto increment. In true case the bank itself will add a value to the object's key
  { name: 'users', key: 'index', increment: true },
  ...
])
```

## PersistentStore API

Request methods allowed.

- ##### store.count(collection): Promise<number>
- ##### store.clear(collection): Promise<void>
- ##### store.get(collection, key): Promise<T>
- ##### store.getAll(collection): Promise<T[]>
- ##### store.getAllKeys(collection): Promise<(string | number)[]>
- ##### store.add(collection, value): Promise<string | number>
- ##### store.addMany(collection, data): Promise<(string | number)[]>
- ##### store.update(collection, value): Promise<void>
- ##### store.updateMany(collection, data): Promise<void>
- ##### store.delete(collection, key): Promise<void>
- ##### store.deleteMany(collection, keys): Promise<void>

## Example of Use

```javascript
import PersistentStore from 'persistent-store'

const store = new PersistentStore('project')

const users = await store.getAll('users')
...
```

## Credits

- [IndexedDB](https://developer.mozilla.org/pt-BR/docs/Web/API/IndexedDB_API)

## License

MIT

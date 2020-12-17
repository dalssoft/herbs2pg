# herbs2knex

herbs2knex creates postgresql repositories based on herbs entities (gotu)

### Installing
    $ npm install herbs2knex

### Using

```javascript
const { Repository } = require('herbs2knex')

class ItemRepository extends Repository {
    constructor() {
        super({
            entity: anEntity,
            table: 'aTable',
            ids: ['id'],
            dbConfig
        })
    }
}

const itemRepo = new ItemRepository()
const ret = await itemRepo.findByID(1)
```
Repository config:

`entity` - A Herbs entity reference

`table` - A Postgres table name

`ids` - The primary keys of the table

`dbConfig` - A object with database configuration

### Repository vs ORM

The idea is to create a repositories with common methods needed for an application.

It is not the intention of this lib to create a ORM. For more complex scenarios it is recommended to extend the repository by use raw queries (just be careful with sql injection) or use favorite ORM, encapsulating inside a method the necessary queries or database operations.

For instance:
```javascript
class ItemRepository extends Repository {
    constructor() {
        super({
            entity: anEntity,
            table: 'aTable',
            ids: ['id'],
            dbConfig
        })
    }

    getExcludedItemFromLastWeek() {
        ...
    }
}

const itemRepo = new ItemRepository()
const ret = await itemRepo.getExcludedItemFromLastWeek()
```

## Retrieving and Persisting Data

### `findByID`
Find by ID

TODO: Example

### `persist`
An `upsert`.

TODO: Example

## TODO

- [ ] Allow only scalar types for queries (don't allow entity / object types)
- [ ] Allow to ommit schema's name

Features:
- [ ] Be able to change the conventions (injection)
- [ ] Exclude / ignore fields on a sql statement
- [ ] Awareness of created/updated at/by fields

Retrieving and Persist:
- [X] persist (upsert)
- [X] insert
- [X] update
- [X] find (ID)
    - [ ] deal with entities / tables with multiples IDs
- [X] find by (any field)
- [ ] find with a iterator for batchs
- [ ] find with pages
- [ ] first
- [ ] last


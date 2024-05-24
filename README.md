# Small MQTT wrapper for OpenLigaDB 
## BETA
This package connects to the mqtt channel of openLigaDB and automatically receives live updates. It provides you to specify topics you're interested in and only emits those data to your system.

### Installation
The package is hosted on [JSR](https://jsr.io/@wgd/oldb) and not npm, so follow the instructions there for your runtime. 

#### Examples
**Connect to OLDB with current mqtt data and receive all updates**
```Typescript
const oldbClient = new OLDB()

oldbClient.on('oldb_update', (msg: OldbData) => {
    // your code here
})
```

**Sign to topics**
```Typescript
const oldbClient = new OLDB({
     topics: ['bl1', 'bl2']
})

oldbClient.on('oldb_update', (msg: OldbData) => {
    // You only receive updates for the OLDB.leagueShortcut you choose
    // your code here
})
```

**If mqtt data changes**
you also can pass in connection infos, which will overwrite the standard.
```Typescript
const oldbClient = new OLDB({
     baseUrl: settings.baseUrl,
     topic: settings.topic,
     port: settings.port
})
```

**Logging**
you also can pass in your logger if you wish, defaults to console. 
It does not log very much though.
```Typescript
const oldbClient = new OLDB({
     logger: myPrivatePinoLogger
})
```
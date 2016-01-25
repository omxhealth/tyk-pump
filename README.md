# Tyk Pump

Tyk Pump is a pluggable analytics purger to move Analytics generated by your Tyk nodes to any back-end. 

## Back ends currently supported: 

- MongoDB (to replace built-in purging)
- CSV (updated, now supports all fields)

## Configuration:

Create a `pump.conf` file:

```
{
	"analytics_storage_type": "redis",
    "analytics_storage_config": {
        "type": "redis",
        "host": "localhost",
        "port": 6379,
        "hosts": null,
        "username": "",
        "password": "",
        "database": 0,
        "optimisation_max_idle": 100,
        "optimisation_max_active": 0,
        "enable_cluster": false
    },
    "purge_delay": 2,
    "pumps": {
    	"dummy": {
    		"name": "dummy",
    		"meta": {}
    	},
        "mongo": {
            "name": "mongo",
            "meta": {
                "collection_name": "tyk_analytics",
                "mongo_url": "mongodb://username:password@{hostname:port},c353.{hostname:port}/{db_name}"
            }
        },
        "csv": {
            "name": "csv",
            "meta": {
                "csv_dir": "./"
            }
        }
    }
}
```

Settings are the same as for the original `tyk.conf` for redis and for mongoDB.

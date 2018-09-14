Default Template

High order = apply last = overwrite


```
{
    "order": 99,
    "index_patterns": [
      "*"
    ],
    "settings": {
      "index": {
        "number_of_shards": "1"
      }
    },
    "mappings": {
	      "doc": {
			"properties": {
			  "http": {
				"properties": {
				  "content_length": {
					"type": "long"
				  }
				}
			  },
			  "geoip": {
				"properties": {
				  "ip": {
					"type": "ip"
				  },
				  "location": {
					"type": "geo_point"
				  },
				  "latitude": {
					"type": "half_float"
				  },
				  "longitude": {
					"type": "half_float"
				  }
				}
			  }
			}
      }
	},
    "aliases": {}
}
```

Get tasks (Specifically reindex)
```
GET _tasks?detailed=true&actions=*reindex
```

Reindex multiple sources to multiple destinations

eg. source-01.01.2018 to source-01.01.2018-1
```
POST _reindex
{
  "source": {
    "index": "source-*"
  },
  "dest": {
    "index": "destination"
  },
  "script": {
    "lang": "painless",
    "source": "ctx._index = 'destination-' + (ctx._index.substring('destination-'.length(), ctx._index.length())) + '-1'"
  }
}
```

Delete all references of a tag/type

```
POST _all/_delete_by_query
{
  "query" : {
    "match" : { "tags": "dns" }
  }
}
```

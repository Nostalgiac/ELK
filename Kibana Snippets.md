#Default Template
#High order = apply last = overwrite

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

map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Jawa Timur"' < ../data/ind-rev.ndjson > jawa-timur.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < jawa-timur.ndjson > jawa-timur.json

build-topo:
	topojson jawa-timur.json > jawa-timur-topo.json -p

simplify-topo:
	mapshaper jawa-timur-topo.json -simplify 3% -o format=topojson jawa-timur-simplified-topo.json

collect-bahasa-map:
	cp jawa-timur-simplified-topo.json ../All

clean:
	rm -rf jawa-timur.ndjson jawa-timur.json jawa-timur-topo.json

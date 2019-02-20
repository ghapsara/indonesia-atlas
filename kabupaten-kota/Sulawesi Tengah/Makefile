map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Sulawesi Tengah"' < ../data/ind-rev.ndjson > sulawesi-tengah.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < sulawesi-tengah.ndjson > sulawesi-tengah.json

build-topo:
	topojson sulawesi-tengah.json > sulawesi-tengah-topo.json -p

simplify-topo:
	mapshaper sulawesi-tengah-topo.json -simplify 3% -o format=topojson sulawesi-tengah-simplified-topo.json

collect-bahasa-map:
	cp sulawesi-tengah-simplified-topo.json ../All

clean:
	rm -rf sulawesi-tengah.ndjson sulawesi-tengah.json sulawesi-tengah-topo.json

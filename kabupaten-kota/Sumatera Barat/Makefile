map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Sumatera Barat"' < ../data/ind-rev.ndjson > sumatera-barat.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < sumatera-barat.ndjson > sumatera-barat.json

build-topo:
	topojson sumatera-barat.json > sumatera-barat-topo.json -p

simplify-topo:
	mapshaper sumatera-barat-topo.json -simplify 3% -o format=topojson sumatera-barat-simplified-topo.json

collect-bahasa-map:
	cp sumatera-barat-simplified-topo.json ../All

clean:
	rm -rf sumatera-barat.ndjson sumatera-barat.json sumatera-barat-topo.json

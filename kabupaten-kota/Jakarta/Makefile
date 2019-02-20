jakarta-map: filter-map-by-province-jakarta build-geo-jakarta build-topo-jakarta simplify-topo-jakarta collect-bahasa-map-jakarta clean-jakarta

kepulauan-seribu-map: filter-map-by-province-kepulauan-seribu build-geo-kepulauan-seribu build-topo-kepulauan-seribu simplify-topo-kepulauan-seribu collect-bahasa-map-kepulauan-seribu clean-kepulauan-seribu

.PHONY: clean-jakarta clean-kepulauan-seribu

filter-map-by-province-jakarta:
	ndjson-filter 'd.properties.provinsi === "Jakarta" && d.properties.kabkot !== "Kepulauan Seribu"' < ../data/ind-rev.ndjson > jakarta.ndjson

build-geo-jakarta:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < jakarta.ndjson > jakarta.json
  
build-topo-jakarta:
	topojson jakarta.json > jakarta-topo.json -p

simplify-topo-jakarta:
	mapshaper jakarta-topo.json -simplify 3% -o format=topojson jakarta-simplified-topo.json

collect-bahasa-map-jakarta:
	cp jakarta-simplified-topo.json ../All

clean-jakarta:
	rm -rf jakarta.ndjson jakarta.json jakarta-topo.json

filter-map-by-province-kepulauan-seribu:
	ndjson-filter 'd.properties.provinsi === "Jakarta" && d.properties.kabkot === "Kepulauan Seribu"' < ../data/ind-rev.ndjson > kepulauan-seribu.ndjson
	
build-geo-kepulauan-seribu:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < kepulauan-seribu.ndjson > kepulauan-seribu.json
  
build-topo-kepulauan-seribu:
	topojson kepulauan-seribu.json > kepulauan-seribu-topo.json -p

simplify-topo-kepulauan-seribu:
	mapshaper kepulauan-seribu-topo.json -simplify 3% -o format=topojson kepulauan-seribu-simplified-topo.json

collect-bahasa-map-kepulauan-seribu:
	cp kepulauan-seribu-simplified-topo.json ../All

clean-kepulauan-seribu:
	rm -rf kepulauan-seribu.ndjson kepulauan-seribu.json kepulauan-seribu-topo.json
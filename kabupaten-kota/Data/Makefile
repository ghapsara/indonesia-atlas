step-1: build-ind-geojson build-ind-ndjson add-id generate-ind-data-ndjson generate-ind-data-json

step-2: build-kabkot-rev-ndjson join-rev-data apply-new-properties rebuild-geojson build-topojson simplify-topojson

.PHONY: clean

build-ind-geojson:
	shp2json ./maps/Indo_Kab_Kot.shp -o ind.json

build-ind-ndjson:
	ndjson-split 'd.features' < ind.json > ind.ndjson

add-id:
	ndjson-map 'd.id = d.properties.PROVNO.toString() +"-"+ d.properties.KABKOTNO.toString(), d' < ind.ndjson > ind-id.ndjson

generate-ind-data-ndjson:
	ndjson-map 'd = { id: d.id, provinsi: d.properties.PROVINSI, kabkot: d.properties.KABKOT }, d' < ind-id.ndjson > ind-kabkot.ndjson

generate-ind-data-json:
	ndjson-reduce 'p.push(d), p' '[]' < ind-kabkot.ndjson > ind-kabkot.json

build-kabkot-rev-ndjson:
	ndjson-split 'd' < ind-kabkot-rev.json > ind-kabkot-rev.ndjson

join-rev-data:
	ndjson-join 'd.id' ind-id.ndjson ind-kabkot-rev.ndjson > ind-join.ndjson

apply-new-properties:
	ndjson-map 'd[0].properties = {provinsi: d[1].provinsi, kabkot: d[1].kabkot}, d[0]' < ind-join.ndjson > ind-rev.ndjson

rebuild-geojson:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < ind-rev.ndjson > kabkot.json

build-topojson:
	topojson kabkot.json > kabkot-topo.json -p

simplify-topojson:
	mapshaper kabkot-topo.json -simplify 3% -o format=topojson kabkot-simplifed-topo.json

clean:
	rm -rf ind.json ind.ndjson ind-id.ndjson ind-kabkot.ndjson ind-kabkot.json ind-kabkot-rev.ndjson ind-join.ndjson kabkot.json kabkot-topo.json
# SUMO Scenario - Random Grid

SUMO Scenario - Random Grid environment with parking areas and public transports (metro and bus). 24h mobility based on SAGA activity-based mobility generator.

## Random network generation

```netgenerate --rand -o random.net.xml --rand.iterations=200 \
    --rand.min-distance 200 --rand.max-distance 200 --rand.grid \
    --sidewalks.guess --crossings.guess \
    --default.lanenumber 2 --no-turnarounds.except-deadend \
    --default-junction-type traffic_light --tls.default-type actuated \
    --perturb-x 2.5 --perturb-y 2.5 --perturb-z 10
```

## TAZ

- TAZ shape definition with `netedit`
- Edge extraction

```python $SUMO_TOOLS/edgesInDistricts.py -n random.net.xml \
    -t taz.shape.add.xml -o complete.taz.xml
```

## Parking Area Generation

## Public Transportation

## Mobility Generation

`python3 $SUMO_TOOLS/contributed/saga/activitygen.py -c saga.24h.json`

## Data Visualization

`python3 $SUMO_TOOLS/visualization/plot_summary.py -i output.summary.xml --xtime1 --xgrid`

# Oslo hackathon, July 2022

## Development track achievements


### Publication on Maven Central

Two new versions [published](https://mvnrepository.com/artifact/fr.insee.trevas/trevas-parent).

* v0.4.2: fix access to PosgreSQL data
* v0.4.3: analytic operators, Jupyter integration, etc.

### Analytic operators

Examples of supported expressions:

* ```ds := ds1[calc test := between(age, 10, 11), age := age * 2, attribute wisdom := (weight + age) / 2];```
* ```result := full_join(ds1 as dsOne, ds2, ds3);```
* ```res := ds2[aggr stddev_popAge := stddev_pop(age), stddev_popWeight := stddev_pop(weight), weight), group by country];```
* ```res := ds1 [ calc count_Me_1:= count ( Me_1 over ( partition by Id_1,Id_2 order by Year ) )];```
* ```res := ds1 [ calc count_Me_1:= count ( Me_1 over ( partition by Id_1,Id_2 order by Year data points between 2 preceding and 2 following) )];```
* etc., etc., etc.

See [tests](https://github.com/InseeFr/Trevas/blob/develop/vtl-spark/src/test/java/fr/insee/vtl/spark/SparkProcessingEngineTest.java) for details

### Read/write to mixed data sources

PosgreSQL and Parquet

### Jupyter integration

Voir [code sur GitHub](https://github.com/InseeFrLab/Trevas-Jupyter)

Demo!

### Documentation

Creation of the [documentation site](http://trevas.info/site/)
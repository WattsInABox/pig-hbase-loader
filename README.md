Custom HBaseStorage
========================
Use the new timestampVersionFieldIndex to specify the index of the timestamp column you wish to use. Note that the index is 0-based; however, since the HBaseStorage requires you to not put the row key in the column list, it appears to be 1-based. See our examples below.


Build
=====
To run tests and create jar:

    mvn clean install


Usage
========================
Upload the built JAR (see Build) to S3 then you can register and use it.

    REGISTER s3://MY-BUCKET/korrelate-pig-templates-0.0.1.jar;

    A = load '/user/hadoop/some_file_in_parts/part*' USING PigStorage(',') AS (user_id:chararray, event_ts:long, column_1:int;

    STORE A INTO 'hbase_table' USING com.korrelate.pig.hbase.HBaseStorage('c1:event_ts, c1:column_1, '-timestampVersionFieldIndex 1');


mortar-pig-java-template - The base of this project
========================
Template Project for Creating new Java Loaders and UDFs for Pig

Includes three template Loader classes, and one example each of a Loader and a UDF.

* TemplateLoader: Very basic template for Pig Loader
* TemplateLoaderPushProjection: Loader template that includes implementation of push projection
* TemplateLoaderStaticSchema: Template for Loader that has a defined and static schema.  Also implements push projection.
* ExampleLoader: Loader example that loads tab-separated data.
* IdentityUDF: Example UDF that takes a tuple and returns that same tuple.




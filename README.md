# cloud-computing-concepts


## Column-oriented Databases
Traditional DBs like RDBMS store all columns of a row together.
So when you read them, all columns of every read row gets loaded into memory from the disk.
NoSQL DBs store all values of a column together. This makes it easier to search because
when you run search on a single column, you only need to load that column's values into
memory, not whole of the table.

## Cassandra is an AP system
Reference: https://www.datastax.com/blog/2019/05/how-apache-cassandratm-balances-consistency-availability-and-performance
Cassandra has made consistency tunable to offer availability.
When you read (or even write), you can specify ONE, TWO, THREE, QUORUM or ALL to indicate how many replicas should respond before sending an answer.
If you specify ONE, then Cassandra only waits for one replica to respond and that replica could be having stale data.
Thus, unless QUORUM or ALL are specified, Cassandra allows you to favor availability over consistency.

## Solr is a CP system
Reference: http://www.theotherian.com/2014/01/random-things-i-learned-about-solr-today.html
Writes in Solr stop working if zookeeper is down.
This is so because in Solr, writes always flow through the shard-leader.
If ZK is down, then Solr can no longer elect shard leaders and hence write stop.
That is Solr sacrifices availability to maintain consistency.


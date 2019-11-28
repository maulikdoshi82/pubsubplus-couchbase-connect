# pubsub-couchbase-connect
 Thie code base relies on two OSS Projects.
 1. Couchbase DCP Client - https://github.com/SolaceSamples/solace-samples-java
 2. Solace JCSMP Java Client - https://github.com/couchbase/java-dcp-client
 
# Installation
1. Setup Solace: For my setup, I'm using Solace PubSub+ Cloud. You may use cloud or local instance as mentioned here: https://docs.solace.com/Solace-PubSub-Event-Brokers.htm
2. Couchbase Setup: https://docs.couchbase.com/server/4.1/getting-started/installing.html. Or For quick demo/poc - you may use couchbase docker image too - https://hub.docker.com/_/couchbase
3. For this codebase - you may checkout or just download the jar from target. It's a maven repo with Intellij Project files checked in. Build a pubsub-couchbase-connect-1.0-SNAPSHOT.jar.

# Running
1. For Couchbase As Source and Solace As Sink:
 a. Configure couchbase-source.properties and solace-sink.properties. Currently the code-base has only basic required parameters. 
 Run from console:
 mvn exec:java -Dexec.mainClass="com.infosys.connectors.CouchbaseAsSource"
 
 Or add the cb/java-dcp, solace/java-jscmp jars in the class path along with pubsub-couchbase-connect-1.0-SNAPSHOT.jar and run com.infosys.connectors.CouchbaseAsSource class.
 
2. For Couchbase As Sink and Solace As Source:
 a. Configure couchbase-sink.properties and solace-source.properties. Currently the code-base has only basic required parameters.
 
 Run from console:
 mvn exec:java -Dexec.mainClass="com.infosys.connectors.SolaceAsSource"
 
 Or add the cb/java-client, solace/java-jscmp jars in the class path along with pubsub-couchbase-connect-1.0-SNAPSHOT.jar and run com.infosys.connectors.SolaceAsSource class.
 
 
Tip: You may run both together if only one topic is provided for Solace As Sink and Solace As Source. Do remember to keep a different bucket for Couchbase or else it'll go in infinite loop.

Contributions/Issues/Suggestions are welcome.
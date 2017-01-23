# PurgeJenkinsPendingQueue
It is made for purging the Jenkins Build Queue. In a Master/Slave config, it can run from any node in the cluster...

# How to ?
Simply configure a Jenkins Freestyle Job with the corresponding config.xml (cf. ./resources/ )

The only interesting thing here is the `groovy`code which must be executed in a `System Groovy Script` Build Step:
```groovy
import jenkins.model.Jenkins

def q = Jenkins.instance.queue

q.items.findAll { q.cancel(it.task) }
```

{"title":"Grails in Production", "date":1328831100299}
++++++++++
There are a few *gotcha's* when deploying a Grails war in a container like Tomcat.[^1] Most commonly are issues with `stacktrace.log`. Second most common are issues with file based db's.

### Setting `stacktrace.log`

Open up `grails-app/conf/Config.groovy`. If you haven't edited it at all there should be a commented out block called `appenders`. Uncomment that and set it to the following:

    appenders {
        console name:'stdout', layout:pattern(conversionPattern: '%c{2} %m%n')
        file name: 'stacktrace', file: "/var/log/tomcat6/stacktrace.log"
    }

By default Grails tries to create a `stacktrace.log` file in the directory it is executed in, which is won't have permission to do unless you've overridden the permissions (not recommended). Here an appender named `stacktrace` is defined and mapped to a file in a directory that it will be able to write to.

### Setting up H2

Grails now uses [H2][grails h2] for it's in-memory and default database. If you've kept H2 around in production as a file based db then you need to put that in another location it can actually access.

Open up `grails-app/conf/DataSource.groovy`. In your `environments.production.dataSource` block set the url property like so:

    url = "jdbc:h2:file:/usr/local/grailsdb;MVCC=TRUE"

You can change the path or name to whatever you like, point is it isn't left as the default which means it will try to create it in a directory it won't have permission to use.

[^1]: I use Tomcat, your usage will vary.

[grails h2]: http://grails.org/plugin/h2
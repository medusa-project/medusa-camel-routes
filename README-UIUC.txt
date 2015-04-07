This is based off of the camel-archetypes-web Maven archetype.

Starting there, add to pom.xml libraries that are needed for
the Camel routes.

Then specify the routes in src/main/webapp/WEB-INF/applicationContext.xml (not in VC) or modify
web.xml in the same directory to point to the desired context.
There are some sample config files for Medusa stuff there, which can be copied or linked as
needed, including the config I use for dev and what will be the configs for the production and
staging machines.
This is where you specify the location of fedora, a triple store, the name of the
incoming queue from Fedora, etc. It also needs to have an ActiveMQComponent
to receive the incoming messages. The queue information should correspond
to that set in Fedora's WEB-INF/classes/config/activemq.xml. This should
probably be set up (see Fedora docs) as a persistent queue rather than
using ephemeral topic messages. 

Run as desired. Using mvn jetty:run seems to be a fine way to do it.
Don't forget to specify a port with -Djetty.port=XYZ, as the default
port is probably being used by Fedora. Besides, why not be explicit about
that anyway?


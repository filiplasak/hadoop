Hadoop Auth, Java HTTP SPNEGO

Hadoop Auth is a Java library consisting of a client and a server
components to enable Kerberos SPNEGO authentication for HTTP.

The client component is the AuthenticatedURL class.

The server component is the AuthenticationFilter servlet filter class.

Authentication mechanisms support is pluggable in both the client and
the server components via interfaces.

In addition to Kerberos SPNEGO, Hadoop Auth also supports Pseudo/Simple
authentication (trusting the value of the query string parameter
'user.name').

New UserFilterAuthenticationHandler which can allow only certein username
provided in config to view webconsole.

Sample configuration for core-site.xml:

<configuration>
<property>
<name>hadoop.http.filter.initializers</name>
<value>org.apache.hadoop.security.AuthenticationFilterInitializer</value>
</property>
<property>
<name>hadoop.http.authentication.type</name>
<value>org.apache.hadoop.security.authentication.server.UserFilterAuthenticationHandler</value>
</property>
<property>
<name>hadoop.http.authentication.user.filter.anonymous.allowed</name>
<value>false</value>
</property>
<property>
<name>hadoop.http.authentication.user.filter.allowed.username</name>
<value>test</value>
</property>
</configuration>

# JMS Transport Parameters

## About the JMS transport

The Java Message Service (JMS) transport in WSO2 Micro Integrator allows you to easily send and receive messages to queues and topics of any JMS service that implements the JMS specification.

Java Message Service (JMS) is a widely used API in Java-based Message Oriented Middleware(MOM) applications. It facilitates loosely coupled, reliable, and asynchronous communication between different components of a distributed application. It supports two asynchronous communication models for messaging as follows:
<ul>
   <li><b>Point-to-point model</b>: In this model message communication happens from one JMS client to another JMS client through a dedicated queue.</li>
   <li><b>Publish and subscribe model</b>:  In this model message communication happens from one JMS client(publisher) to many JMS clients(subscribers) through a topic.</li>
</ul> 
JMS supports two models for messaging as follows:
<ul>
   <li><b>Queues</b>: point-to-point.</li>
   <li><b>Topics</b>: publish and subscribe.</li>
</ul> 
The Micro Integrator supports the following messaging features introduced with JMS 2.0:
<ul>
   <li>Shared Topic Subscription</li>
   <li>JMSX Delivery Count</li>
   <li>JMS Message Delivery Delay</li>
</ul>
The JMS transport implementation comes from the WS-Commons Transports project, and it makes use of JNDI to connect to various JMS brokers. As a result, WSO2 Micro Integrator can work with any JMS broker that offers JNDI support.

## Parameters

Given below is the list of JMS transport parameters that can be configured when you [create a proxy service](../../../develop/creating-artifacts/creating-a-proxy-service.md).

### JMS connection factory parameters

Configuration parameters for the JMS receiver and the sender are XML fragments that represent JMS connection factories.

<table>
      <tr>
         <th>
            <p>Parameter Name</p>
         </th>
         <th>
            <p>Description</p>
         </th>
      </tr>
   <tbody>
      <tr>
         <td>
           java.naming.factory.initial
         </td>
         <td>
            JNDI initial context factory class. The class must implement the <code>java.naming.spi.InitialContextFactory</code> interface. The default value is <code>org.apache.activemq.jndi.ActiveMQInitialContextFactory</code>.
         </td>
      </tr>
      <tr>
         <td>
            java.naming.provider.url
         </td>
         <td>
            URL of the JNDI provider. By default, the value is <code>tcp://localhost:61616</code>.
         </td>
      </tr>
      <tr>
         <td>
            java.naming.security.principal
         </td>
         <td>
            <p>JNDI Username.</p>
         </td>
      </tr>
      <tr>
         <td>
            java.naming.security.credentials
         </td>
         <td>
            <p>JNDI password.</p>
         </td>
      </tr>
      <tr>
         <td>
            transport.Transactionality
         </td>
         <td>
            Preferred mode of transactionality.</br>
            <b>Note</b>: In the Micro Integrator, JMS transactions only work with either the Callout mediator or the Call mediator in blocking mode. The possible values are as follows:
            <ul>
               <li><b>none</b>: Disables transactions in the JMS transport.</li>
               <li><b>local</b>: Enables local JMS session transactions.</li>
               <li><b>jta</b>: Enables global JTA transactions.</li>
            </ul>
         </td>
      </tr>
      <tr>
         <td>
            transport.UserTxnJNDIName
         </td>
         <td>
           JNDI name to be used to require user transaction. The default value is <code>java:comp/UserTransaction</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.CacheUserTxn
         </td>
         <td>
            Whether caching for user transactions should be enabled or not. By default, this setting is <code>true</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.SessionTransacted
         </td>
         <td>
            Whether the JMS session should be transacted or not. By default, this setting is <code>true</code> (if transactionality is 'local').
         </td>
      </tr>
      <tr>
         <td>
           transport.jms.SessionAcknowledgement
         </td>
         <td>
           JMS session acknowledgment mode. The possible values are as follows:
           <ul>
               <li><em>AUTO_ACKNOWLEDGE:</em> The session automatically acknowledges the consumer receipt of messages when message processing has finished.</li>
               <li><em>CLIENT_ACKNOWLEDGE:</em> The consumer acknowledges all messages delivered so far by the session. If the consumer falls behind in its processing, a large number of unacknowledged messages can build up.</li>
               <li><em>DUPS_OK_ACKNOWLEDGE:</em> The session lazily acknowledges the delivery of messages to the consumer. Lazy means that the consumer can delay acknowledgement to the server until a convenient time. During a delay, the server might redeliver messages. This mode reduces session overhead but the consumer can receive duplicate messages should JMS fail,</li>
               <li><em>SESSION_TRANSACTED:</em> The session is a related group of consumed or produced messages that are treated as a single unit of work.</li>
            </ul>
            Also see <a href="http://wso2.com/library/articles/2013/01/jms-message-delivery-reliability-acknowledgement-patterns/">JMS Message Delivery Reliability and Acknowledgement Patterns</a>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.ConnectionFactoryJNDIName
         </td>
         <td>
            The JNDI name of the connection factory.</br></br>
            The possible values are as follows:
            <ul>
               <li>QueueConnectionFactory</li>
               <li>TopicConnectionFactory</li>
            </ul>
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.ConnectionFactoryType
         </td>
         <td>
           Type of the connection factory. The possible values are <code>queue</code>, or <code>topic</code>. The default value is <code>queue</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.JMSSpecVersion
         </td>
         <td>
            JMS API version. Possible values are <code>1.1</code> or <code>1.0.2b</code>. The default value is <code>1.1</code>.
         </td>
      </tr> 
      <tr>
         <td>
            transport.jms.UserName
         </td>
         <td>
            The JMS connection username.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.Password
         </td>
         <td>
            The JMS connection password.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.Destination
         </td>
         <td>
            The JNDI name of the destination.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.DestinationType
         </td>
         <td>
            Type of the destination. Possible values are <code>queue</code>, or <code>topic</code>. The default setting is <code>queue</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.DefaultReplyDestination
         </td>
         <td>
            JNDI name of the default reply destination.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.DefaultReplyDestinationType
         </td>
         <td>
            Type of the reply destination. Possible values are <code>queue</code>, or <code>topic</code>. Defaults to the type of the destination.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.MessageSelector
         </td>
         <td>
            Message selector implementation.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.SubscriptionDurable
         </td>
         <td>
            Whether the connection factory is subscription durable or not. By default, this parameter is set to <code>false</code>.
         </td>
      </tr>
      <tr>
         <td>transport.jms.DurableSubscriberClientID</td>
         <td>The <code>ClientId</code> parameter when using durable subscriptions. This parameter is required if the value specified as <code>transport.jms.ubscriptionDurable</code> is <code>true</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.DurableSubscriberName
         </td>
         <td>
            The name of the durable subscriber. This parameter is required if the value specified as <code>transport.jms.SubscriptionDurable</code> is <code>true</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.PubSubNoLocal
         </td>
         <td>
            Whether the messages should be published by the same connection through which they were received. The default setting is <code>false</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.CacheLevel
         </td>
         <td>
            The cache level with which JMS objects should be cached at start up. You can configure this in the ei.toml file if Micro Integrator acts as a JMS producer. Example:
            <div class="code panel pdl" style="border-width: 1px;">
                  <div class="codeContent panelContent pdl">
                     <div class="sourceCode" id="cb1" data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence" style="brush: java; gutter: false; theme: Confluence">
                        <pre class="sourceCode java"><code class="sourceCode java"><span id="cb1-1"><a href="#cb1-1"></a>&lt;endpoint&gt;</span>
<span id="cb1-2"><a href="#cb1-2"></a>   &lt;address uri=<span class="st">&quot;jms:/example.MyQueue?transport.jms.ConnectionFactoryJNDIName=QueueConnectionFactory&amp;java.naming.factory.initial=org.wso2.andes.jndi.PropertiesFileInitialContextFactory&amp;java.naming.provider.url=repository/conf/jndi.properties&amp;transport.jms.DestinationType=queue&amp;transport.jms.CacheLevel=producer&quot;</span>/&gt;</span>
<span id="cb1-3"><a href="#cb1-3"></a>&lt;/endpoint&gt;</span></code></pre>
                     </div>
                  </div>
            </div>
            If the Micro Integrator is a JMS consumer, you can configure a proxy service. Following are the possible values for this parameter:
            <ul>
               <li><strong>none</strong>: None of the JMS objects will be cached.</li>
               <li><strong>connection</strong>: JMS connection objects will be cached.</li>
               <li><strong>session</strong>: JMS connection and session objects will be cached.</li>
               <li><strong>consumer</strong>: JMS connection, session, and consumer objects will be cached.</li>
               <li><strong>producer</strong>: JMS connection, session, and producer objects will be cached.</li>
               <li><strong>auto</strong>: An appropriate cache level will be used based on the transaction strategy.</li>
            </ul>
            </div>
         By default, this parameter is set to <code>auto</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.ReceiveTimeout
         </td>
         <td>
            Time to wait for a JMS message during polling. Set this parameter value to a negative integer to wait indefinitely. Set to zero to prevent waiting. The default value is <code>1000</code> milliseconds.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.ConcurrentConsumers
         </td>
         <td>
            Number of concurrent threads to be started to consume messages when polling. You can specify any positive integer. However, for topics, this parameters should always be set to <code>1</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.MaxConcurrentConsumers
         </td>
         <td>
            Maximum number of concurrent threads to use during polling. You can specify any positive integer. The default value is <code>1</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.IdleTaskLimit
         </td>
         <td>
            The number of idle runs per thread before it dies out. You can specify any positive integer. The default value is <code>10</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.MaxMessagesPerTask
         </td>
         <td>
            <p>The maximum number of successful message receipts per thread. You can specify any positive integer. The default value is <code>-1</code>. Use <code>-1</code> to indicate infinity.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.InitialReconnectDuration
         </td>
         <td>
           Initial reconnection attempts duration in milliseconds. You can specify any positive integer. The default value is <code>10000</code> milliseconds.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.ReconnectProgressFactor
         </td>
         <td>
            Factor by which the reconnection duration will be increased. You can specify any positive integer. The default value is <code>2</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.MaxReconnectDuration
         <td>
            Maximum reconnection duration in milliseconds. The default value is <code>3600000</code> milliseconds (1 hour).
         </td>
      </tr>
      <tr>
         <td>transport.jms.ReconnectInterval</td>
         <td>Reconnection interval in milliseconds. The default value is <code>3600000</code> milliseconds (1 hour).
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.MaxJMSConnections
         </td>
         <td>
            Maximum cached JMS connections in the producer level. You can specify any positive integer. The default value is <code>10</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.MaxConsumeErrorRetriesBeforeDelay
         </td>
         <td>
            Number of retries on consume errors before sleep delay kicks in. You can specify any positive integer. The default value is <code>20</code>.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.ConsumeErrorDelay
         </td>
         <td>
            Sleep delay when a consume error is encountered (in milliseconds). You can specify any positive integer. The default value is <code>100</code> milliseconds.
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.ConsumeErrorProgression
         </td>
         <td>
           Factor by which the consume error retry sleep will be increased. You can specify any positive integer. The default value is <code>2.0</code>.
         </td>
      </tr>
      <tr>
         <td>transport.jms.MaxConsumeErrorRetryCount</td>
         <td>
            The maximum number of times the consumer should retry upon receiving a consumer error. You need to introduce this parameter only if the Broker has issues in notifying the Exception Listeners about the exceptions occurred. You can specify any positive integer. The default value is <code>1</code>.
         </td>
      </tr>
   </tbody>
</table>

### Service-level JMS configuration parameters

<table>
      <tr>
         <th>
            Parameter Name
         </th>
         <th>
            Description
         </th>
      </tr>
   <tbody>
      <tr>
         <td>
            transport.jms.ConnectionFactory
         </td>
         <td>
            Name of the JMS connection factory the service should use. You can specify the name of an already defined connection factory
         </td>
      </tr>
      <tr>
         <td>
            transport.jms.PublishEPR
         </td>
         <td>
            JMS EPR to be published in the WSDL. Specify a JMS EPR.
         </td>
      </tr>
      <tr>
         <td>transport.jms.ContentType</td>
         <td>Specifies how the transport listener should determine the content type of received messages. Specify a simple string value, in which case the transport listener assumes that the received messages always have the specified content type, or a set of rules. For more information, see <a href="http://axis.apache.org/axis2/java/transports/jms.html#Service_configuration">http://axis.apache.org/axis2/java/transports/jms.html#Service_configuration</a>.</td>
      </tr>
      <tr>
         <td>
            <code>transport.jms.MessagePropertyHyphens</code>
         </td>
         <td>Specifies the action to be taken when there are JMS Message property names that contain hyphens. The possible values are as follows:
            <ul>
               <li><b>none</b>: No action will be taken. This is the default value.</li>
               <li><b>replace</b>: Transport headers with hyphens will be replaced before adding them as JMS message properties, and if the Micro Integrator is the consumer, hyphens will be reintroduced on message retrieval.</li>
               <li>
                  <b>delete</b>: Transport headers with hyphens will be deleted.
               </li>
            </ul>
         </td>
      </tr>
   </tbody>
</table>
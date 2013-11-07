#rithocomponents4jsf

 
## Ritho Components for JSF:


  Ritho components for JSF are add-on tags for added UI flavor.

### Components:
 
  We offer two components autoImageLoader ; restfulImageLoader. Please see the how-to description below.
  
### Usage:

  In you jsp / jspx; import ritho tld just as you would other tag libraries:
  
````
  xmlns:r="http://ritho.com/jsf"
````

## AutoImage component
 
  Activate the ritho components.

````
  <r:autoImageActivator />
````

  Use the components.

````
  <r:autoImage rendered="true"  src="http://#[a-remote-image].jpg" />
````

  {{{./autoImage.html} autoImage complete example}}

## RestfulImage component 
 
  restfulImage component is designed to interface with Hbase Stargate RESTful services. The component expects \
  an image id from a backing bean by data binding. It then uses this id to query HBase using Stargate Restful service.\
  The request is to an hbase table row-name that has 'image:url' column family; the result expects a json object containing  id-url key-value.
  A proxy should be configured to allow requests to traverse multiple application contexts.  
 
  Configure you web.xml to have a proxy servlet or phaselistener. See below:
  
````
	<servlet>
		<servlet-name>hbaseproxy</servlet-name>
		<servlet-class>somepackage.RestProxyServlet</servlet-class>
	</servlet>
	<servlet-mapping>
		<servlet-name>hbaseproxy</servlet-name>
		<url-pattern>/proxy/hbase</url-pattern>
	</servlet-mapping>
````
  
### Activate the ritho components.

````
  <r:restImageActivator  restUrl="/[application context]/proxy/hbase?http://remoteserver:port/<hbasetable with image data>/"  />
````

  Alternatively for any other service:
  
````
  <r:restImageActivator  restUrl="/[application context]/[proxy servlet mapping]?http://[remoteservice:port]/[remotecontext]/"  />
````

  Use the components: 'row' - is the hbase table row containing a unique image data. 'styleClass' is the css style.

````
  <r:restImage rendered="true" row="image_#{imgId}" id="[some uniqueId]"  styleClass="randomImg" />
````

  {{{./restImage.html} restImage complete example}}  

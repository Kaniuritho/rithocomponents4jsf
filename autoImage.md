Here is a complete jsp example of autoImage component in Myfaces JSF
````
<jsp:root xmlns:jsp="http://java.sun.com/JSP/Page" version="2.0"
        xmlns:f="http://java.sun.com/jsf/core"
        xmlns:h="http://java.sun.com/jsf/html"
        xmlns:tr="http://myfaces.apache.org/trinidad"
        xmlns:t="http://myfaces.apache.org/tomahawk"
        xmlns:r="http://ritho.com/jsf">
<jsp:directive.page contentType="text/html;charset=utf-8" />
<html>
<body>
<f:view>
        <r:autoImageActivator />
        <r:autoImage rendered="true"  src="http://#[a-remote-image].jpg" />
</f:view>
</body>
</html>
</jsp:root>
````

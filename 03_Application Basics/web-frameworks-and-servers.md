#### Web & Application Servers
Websites can be categorized into two types: Static and Dynamic. A static page is typically written in HTML and CSS and will display information like text, pictures, videos and music. Once the initial request from the browser has been served there is no more communication required from the server. 

Dynamic websites on the other hand will incorporate both Static and Dynamic elements that will change based on the users input. An example is an e-commerce website. The page itself is displaying mostly static content, the header, the footer, the images of the products, but there are more functions the page can do, such as provide the user with a cart to store items, connect users to a chat service, process transactions. This dynamic content is handled by additional services, like an application server to handle the logic of the store, a chat server to handle the communications of the users and the database server to store the list of products. 

A static website and the static elements of a dynamic web page are often written in HTML and CSS. The dynamic content is typically written in JavaScript. The application server that handles the logic and processing of the application is usually written in Java, Python and Node.JS. 

The website and the application are typically written to interact with each other and a web framwork provides an easy way to develop that.  Some examples of popular frameworks are Express (Node.JS), Spring (Java), Django & Flask (Python). 

Once the application has been developed you need to use a web-server to host it, listen for requests and respond, which is where a web server comes in. Different servers have different strengths when it comes to the type of content you're serving. For static websites, Apache HTTP and Nginx are good. For dynamic content, web servers such as Apache Tomcat, gUnicorn and uWSGI are good. 

Typically you would refer to static websites being hosted on a web server and dynamic webistes being hosted on the application server. 


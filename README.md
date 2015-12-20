This example shows how to peel off the query parameters on a landing page (typically from an email), and then send them to an endpoint

This allows an endpoint to send back some JSON data to be rendered in the landing page.

This technique means no server generated pages need to exist.

To run:

> mvn clean package
> java -jar target/webstatic-1.0.war &

(note the server runs on port 9080)

In a browser: enter
http://localhost:9080/resetPassword.html?id=123&token=Wd14

where localhost:9080 could be an NGINX server, containing the static html/javascript code.

The end result will be a GET call to:

http://localhost:8080/company/123/resetpassword/Wd14

where localhost:8080 could be a real Google App Engine server which responds with pure json back on this endpoint.

The NGINX server would then just render the json given to it.


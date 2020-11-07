

   #                           **HelmetJS**    

----
#### 1. X-Powered-By header.
----

**Sets the X-Powered-By header.**

* `helmet.hidePoweredBy()`				-----> Remove X-Powered-By.

* `app.use(helmet.hidePoweredBy({setTo : 'PHP 4.2.0'})`     ----------> Set the header to something else.


----
#### 2. Prevent Clickjacking.
----

**This middleware sets the X-Frame-Options header.**

* `helmet.frameguard({action: 'deny'})`     	-------> Has three options (DENY,ALLOW,SAMEORIGIN). Prevents browser from rendering a page inisde a frame.
----
#### 3. Prevent XSS :-
----

**Sets the X-XSS HTTP header.**

* `helmet.xssFilter()`				-------> Sanitize user input coming to the server.

----
#### 4. Avoid browsers from detecting the content type.
----

This middleware sets the **X-Content-Type-Options** header to nosniff, 
instructing the browser to not bypass the provided Content-Type.

* `helmet.noSniff()`

----
#### 5.Prevent IE from opening untrusted HTML.
----

This middleware sets the X-Download-Options header to noopen.

* `helmet.ieNoOpen()`				----> Prevent IE users from executing downloads in trusted site's context.


----
#### 6. HTTPs only.
----

* `helmet.hsts()` 					-----> Ask browsers to access sites via https only.

----
#### 7. Disable DNS prefetching.
----
* `helmet.dnsPrefetchControl()`----> Disable websites from prefetching DNS records of a link in the page.
----

#### 8.Disable client side caching.
----
* `helmet.noCache()`        -----> Prevent client side caching.
----
#### 9.Set Content Security Policy.
Content Security Policy (CSP) – a standardized set of directives that tell the browser what content sources can be trusted and which should be blocked. 
*  `app.use(helmet.contentSecurityPolicy()`

*  ` app.use(helmet.contentSecurityPolicy({ directives: { defaultSrc: ["'self'"], scriptSrc: ["'self'", "trusted-cdn.com"] }} ))`
Allow content only from current origin and scripts to be downloaded from your website and truted-cdn.com.
----
#### 10.Configuring Helmet.
----

* `app.use(helmet())` will automatically include all the middleware introduced above, except noCache(), and contentSecurityPolicy().
----




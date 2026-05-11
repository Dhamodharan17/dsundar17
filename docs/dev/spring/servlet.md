## Servlet

### Evolution

Plain Java -> Servlet -> JSP -> Spring Core -> Spring MVC -> Spring Boot

- Plain Java - contains business logic but cannot directly handle HTTP requests
- Servlet - Java class that handles HTTP requests by running inside a servlet container
- JSP - helps separate UI from Java code instead of writing HTML inside Java strings
- Spring Core - provides DI, IOC, bean management, and annotation-based configuration
- Spring MVC - adds MVC web framework support on top of Spring
- Spring Boot - reduces configuration using auto-configuration and embedded server support

Servlet came to handle HTTP requests by running inside a servlet container, which receives requests from the web server, maps them to the correct servlet, and invokes that servlet.

### Request Flow Example

Browser:
GET /hello?name=Sam

1. Web server receives `/hello?name=Sam`
2. Forwards it to the servlet container
3. Servlet container maps `/hello` -> `HelloServlet`
4. Calls `service(req, res)` inside `HelloServlet`
5. `service()` internally calls `doGet(req, res)`
6. `doGet()` returns: `Hello Sam`
7. Response goes back to the browser

## Lifecycle of Servlet

How does the servlet container manage a servlet object?

Servlet lifecycle:
- `init()` - called once after servlet creation, before serving requests
- `service()` - called by the servlet container for each request
  - for HTTP requests, `service()` delegates to `doGet()`, `doPost()`, `doPut()`, `doDelete()`, `doHead()`, and others
- `destroy()` - called once before servlet removal

Important details:
- Servlet object is created by the servlet container, not by the developer
- Usually one servlet instance is kept in memory and reused for multiple requests
- Creation can happen on first request or at startup if `load-on-startup` is enabled
- By default, servlet loading is often lazy

## Servlet Container

- Loads servlet classes
- Manages servlet lifecycle
- Maps URL to the correct servlet
- Creates request and response objects
- Manages threads
- Manages sessions
- Can append session id to the URL when cookies are disabled

Configuration types:
1. Standalone container - separate web server and separate servlet container
2. In-process container - servlet container runs inside the web server process
3. Out-of-process container - servlet container runs in a different process

## Filter

- A middleware-like component that intercepts HTTP request and response before they reach the servlet

Filter lifecycle:
- `init(FilterConfig config)` - called once
- `doFilter()` - contains filtering logic
- `chain.doFilter(req, res)` - passes control to the next filter or target resource
- `destroy()` - called once before shutdown

## Session

- HTTP is stateless, so each request is independent
- Session helps the server remember user-specific data across multiple requests
- Examples: login status, shopping cart, user preferences
- Each session has a unique id, usually stored in a cookie called `JSESSIONID`

## Spring MVC Architecture

1. `DispatcherServlet` - front controller that receives all requests
2. `HandlerMapping` - finds the correct controller method
3. `HandlerAdapter` - invokes the selected controller method
4. `DataBinder` - binds request data to Java objects
5. `ViewResolver` - resolves view name to the actual view page
6. `HttpMessageConverter` - converts response body to JSON or XML when needed
7. `Interceptor` - runs before and after controller execution

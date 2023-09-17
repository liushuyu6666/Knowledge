# APIs
## Type of APIs
There are several different types of APIs, each catering to specific use cases, requirements, and architectural styles. Here are some common types of APIs:

1. **Open APIs (Public APIs)**: These are APIs that are made publicly available to developers and third-party applications. They are designed to be easily accessible and are often documented extensively to encourage adoption.

2. **Internal APIs (Private APIs)**: Internal APIs are used within organizations to enable communication between different teams or services. They are not exposed to external developers and are meant to improve collaboration and efficiency within the organization.

3. **Partner APIs**: Partner APIs are specifically designed to be shared with a select group of external partners. They are a subset of open APIs and provide controlled access to certain features or data to trusted partners.

4. **Composite APIs**: Also known as experience APIs, these APIs aggregate data from multiple sources into a single endpoint. They provide a simplified view of complex systems and are often used to improve performance and reduce the number of requests.

5. **RESTful APIs**: Representational State Transfer (REST) APIs are a style of architecture that uses standard HTTP methods for CRUD operations (Create, Read, Update, Delete) and is often used for web applications. The controller-service-repository pattern is often associated with building RESTful APIs


6. **SOAP APIs**: Simple Object Access Protocol (SOAP) APIs use XML-based messaging to communicate between applications. They are known for their strict standards and are commonly used in enterprise environments.

7. **GraphQL APIs**: GraphQL APIs allow clients to request exactly the data they need using a query language. This reduces over-fetching and under-fetching of data and provides more control to clients.

8. **Streaming APIs**: Streaming APIs deliver real-time data to clients, often in the form of continuous updates. They are used for applications like social media feeds and live event updates.

9. **WebSockets**: WebSockets provide full-duplex communication over a single, long-lived connection. They are used for real-time communication, such as chat applications and online gaming.

10. **Microservices APIs**: Microservices APIs are designed to facilitate communication between microservices in a microservices architecture. They enable modular development and deployment of services.

11. **Library or Framework APIs**: These APIs provide pre-built functions and classes that developers can use to build applications more efficiently. Examples include jQuery for JavaScript and Django for Python.

12. **Operating System APIs**: These APIs allow applications to interact with the underlying operating system, accessing hardware, file systems, and other system-level functionalities.

These are just a few examples of the many types of APIs that exist. The choice of API type depends on the specific needs of your project, the architecture you're working with, and the goals you want to achieve.

More about apis: [click here](https://www.freecodecamp.org/news/rest-vs-graphql-apis/#:~:text=Declarative%3A%20GraphQL%20APIs%20are%20declarative,the%20available%20queries%20and%20mutations.)


## GraphQL vs RESTful




# Rendering

Rendering comprised of three components - server-rendering, client-rendering (single page application) and hybrid approach.

## Traditional Web Application (Server-rendered):
In the early days of web development, most web pages were server-rendered. When you navigated to a website, the process would typically go as follows:

1. The browser sends a request to the server for a specific URL.
2. The server processes the request, interacts with the database or other systems if necessary, and constructs an HTML page with the resulting data.
3. This fully-formed HTML page is then sent back to the client's browser.
4. The browser receives the HTML and renders it on the screen for the user.
5. If the user clicks on a link or takes an action that requires a new page, the process starts over with a new request to the server.

**Pros**:
* SEO: Search engines have traditionally found it easier to index server-rendered content.
* Performance: Initial page loads can be faster in server-rendered applications because the browser receives a fully constructed HTML page. This eliminates the need to wait for client-side scripts to fetch and render content. In contrast, with Single Page Applications (SPAs), the browser initially retrieves a minimal HTML structure from the frontend and then makes additional API calls to the backend to fetch content.
* Simplicity: For simple websites, server rendering can be more straightforward and require less client-side code.

**Cons**:
* Less Interactivity: Dynamic interactions might require full page reloads, making the experience less smooth.
* Scalability: As traffic increases, the server might become a bottleneck since it's responsible for rendering every user's page.

## Modern Web Application (Client-rendered or Single Page Applications):
With the rise of powerful JavaScript frameworks and libraries like React, Angular, and Vue, a new model of web application development are separated into frontend server and backend server:

1. The client, typically a web browser, sends an initial request for the website.
2. The frontend server responds with a basic HTML structure accompanied by JavaScript.
3. Upon executing the JavaScript in the browser, it issues API calls to the backend server to retrieve content or data.
   1. Note: In SPAs, the initial page first receives a minimal HTML structure from the frontend server and then proceeds to fetch data via API calls from the backend server, adding an extra step compared to server-rendered applications.
   2. For example, in the `react.js`, the `useEffect()` always send the initial request to the API.
4. Using the received data, the JavaScript dynamically assembles and updates the content on the page, all without necessitating a complete page reload.

## Hybrid Approach (Server-Side Rendering with Client-side Hydration):
Modern frameworks like `Next.js` (for `React`) or `Nuxt.js` (for `Vue`) offer a hybrid solution:

1. The initial page load is server-rendered, offering faster load times and improved SEO.
2. Once the page is loaded, the JavaScript takes over (hydration), and subsequent navigation or interactions become client-rendered, like a Single Page Application.

To know more about the [Hybrid Approach or `Next.js`](https://github.com/liushuyu6666/Learn_Nextjs/blob/master/README.md).

This approach attempts to combine the best of both worlds, offering the performance and SEO benefits of server rendering with the interactivity and scalability of client rendering.
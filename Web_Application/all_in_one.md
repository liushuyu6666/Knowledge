# Overview

# Handler
All Web Applications need a handler to handle with inbound request and response it.
## Apollo
It is resolver
## Express.js
route handler:
```javascript
app.get('/hello', (req, res) => {
  res.send('Hello, world!');
});
```
## Spring Boot
`@Controller`

# Sharing resources
sharing resources across different parts of your application.
## Apollo
`context`
## Express.js
middleware
## Spring Boot
`HttpServletRequest` object
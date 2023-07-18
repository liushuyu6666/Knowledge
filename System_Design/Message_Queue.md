Message Queue works as a buffer. There is a real world scenario:

There is an e-commerce application, there are three components - the principle system which will generate the order by the user's choice, the message queue and the order processing system.

When a customer places an order, instead of let the order processing system to handle with it directly. the order detail will be sending and storing in the message queue first. The order processing system will process the order in the message queue one by one.

The benefit of it is that, when an order is generated, instead of sending it to the order processing system directly and waiting for its response, the principle system could send it to the message queue and continue other tasks, when the order processing system return the response, the principle system will pause and handle with the data from the order processing system.
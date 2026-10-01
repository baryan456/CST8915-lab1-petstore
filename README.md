# CST8915 Lab 1: Algonquin Pet Store on Azure VM

**Student Name:** Aryan Banoth  
**Student ID:** 041293006  
**Course:** CST8915 Full-stack Cloud-native Development  
**Semester:** Fall 2026

---

## Demo Video

🎥 [Watch Demo Video](PASTE-YOUR-YOUTUBE-LINK-HERE)

---

## Technical Explanations

### Order Service (Node.js)

The Order Service is responsible for handling customer orders. When a customer selects a product and places an order from the Store Front, the order is sent to this service. It is built using Node.js and runs on port 3000.

The Order Service also communicates with RabbitMQ. Instead of processing everything directly in the website, it sends the order to RabbitMQ, where the order is stored in the queue. This allows the different services to work independently. During my testing, I verified that the `order_queue` was durable and that the number of messages increased after placing an order.

### Product Service (Rust)

The Product Service is responsible for providing the product information used by the store. It provides details such as the product ID, name, and price. It is written in Rust and runs on port 3030.

The Store Front communicates with the Product Service to get the product information and display it to customers. I tested the Product Service using the `curl` command and verified that it returned products such as Dog Food, Cat Food, and Bird Seeds.

### Store Front (Vue.js)

The Store Front is the part of the application that the customer interacts with. It is built using Vue.js and runs on port 8080. Customers can view products, select a product, enter a quantity, and place an order.

The Store Front communicates with the Product Service to display product information and communicates with the Order Service when an order is placed. In my deployment, the Store Front was accessed through the Azure VM public IP address using port 8080.

---

## Challenges and Learnings

During this lab, I learned how to deploy and run a microservices-based application on an Azure Virtual Machine. I learned how different services communicate with each other using APIs and RabbitMQ.

I also learned how to configure Azure networking and access a web application running on a VM through a public IP address. During testing, I verified that an order was successfully added to the RabbitMQ `order_queue`.

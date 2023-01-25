# Code Smell 04 - How to Avoid Misplaced Responsibilities in Your Classes

**Misplaced responsibility** is a code smell that refers to a **class or module that has responsibilities that do not properly align with its intended purpose**. This can lead to a number of problems, such as making the class harder to understand, test, and maintain.

When a class or module has misplaced responsibilities, it can become bloated and complex. It may have many methods that do not fit with its main purpose, and it may have dependencies on other classes that are not necessary. This can make it difficult to understand what the class is supposed to do and can lead to bugs and errors.

### Example Scenarios

One common example of misplaced responsibility is a class that is responsible for both data access and business logic.

1. In this case, the class is responsible for *<mark>interacting with the database to retrieve and update data</mark>*, as well as <mark>performing calculations and making decisions based on that data</mark>. This can lead to a lot of unnecessary complexity and make the class harder to test and maintain.
    
2. Another example is when a class or module has many dependencies, which can make it difficult to understand how the class or module works and how it should be used. A class or module with too many dependencies may be an indication that it has taken on responsibilities that should be handled by other classes or modules.
    

### How to resolve this?

To solve the problem of **misplaced responsibility**, it's important to identify the responsibilities that are not properly aligned with the intended purpose of the class or module. Once identified, these responsibilities can be refactored and moved to a more appropriate class or module. This will help to make the code more maintainable, more testable, and more understandable.

In general, it's important to follow the **Single Responsibility Principle (SRP)**, which states that a class or module should have only one reason to change, this means that it should have only one responsibility. <mark>When a class or module has more than one responsibility, it can become difficult to understand and maintain, and it can lead to bugs and errors.</mark>

### Examples

1. A class that is responsible for both data access and business logic
    
    ```java
    class OrderProcessor {
        private Database db;
    
        public OrderProcessor() {
            db = new Database();
        }
    
        public void processOrder(Order order) {
            db.saveOrder(order);
            if (order.total() > 100) {
                sendDiscountCoupon(order.getCustomerEmail());
            }
        }
    
        private void sendDiscountCoupon(String email) {
            // code to send discount coupon
        }
    }
    ```
    
    In this example, the **OrderProcessor** class is responsible for both saving the order to the database and checking if the order total is above a certain threshold, and sending a discount coupon. These responsibilities should be separated into different classes or modules.
    
    **How to resolve this?**
    
    The business logic of sending a discount coupon should be separated from the data access responsibility of saving the order to the database.
    
2. A class with many dependencies,
    
    ```java
    class ReportGenerator {
        private DataRetriever dataRetriever;
        private ReportFormatter formatter;
        private ReportSender sender;
    
        public ReportGenerator(DataRetriever dataRetriever, ReportFormatter formatter, ReportSender sender) {
            this.dataRetriever = dataRetriever;
            this.formatter = formatter;
            this.sender = sender;
        }
    
        public void generateAndSendReport() {
            List<Data> data = dataRetriever.getData();
            String formattedReport = formatter.format(data);
            sender.sendReport(formattedReport);
        }
    }
    ```
    
    In this example, the <mark>ReportGenerator</mark> class has three dependencies: <mark>DataRetriever</mark>, <mark>ReportFormatter</mark>, and <mark>ReportSender</mark>. Each dependency represents a responsibility and having many dependencies can make it difficult to understand how the class works and how it should be used. The responsibilities should be separated into different classes or modules.
    
    **How to resolve it?**
    
    The class should only have **one responsibility** and the other responsibilities should be moved to different classes or modules.
    

### Conclusion

In summary, **misplaced responsibility** is a code smell that refers to a class or module that has responsibilities that do not align with its intended purpose. It can lead to complexity, bugs, and difficulties in maintaining the code. It is important to identify and refactor misplaced responsibilities to follow the **Single Responsibility Principle (SRP)** in order to make the code more maintainable, testable, and understandable.
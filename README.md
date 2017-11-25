# #5 Students list
Tutorial on creating a Students List page

This is what we will cover in class today, and is equvalent to what i will show you from the blackborad.

The goal is to create a Students List and diplay it in the browser like this:

<img src="/students_list.png" />

## Spring Boot Application
* Before we start you need to have an up an running Spring Boot Application. You can see [here](https://github.com/StudentsAdministration/03_hello_spring) how to manage that.    

## StudentsController & index.html
* Create a StudentsController and from that return an index.html . You can see [here](https://github.com/StudentsAdministration/03_your_first_website) how to manage that.  

## Student Class
* Create a Student.java Class with the following attributes

````java
    public class Student {
        private int studentId;
        private String firstName;
        private String lastName;
        private Date enrollmentDate;
        private String cpr; 
    }
```` 
* Create Getters & Setters in the class 


## The Model object
* As parameter to your index method put in ```` Model model ````  .

````java
    @GetMapping("/")
    public String index(Model model) {
        return "index";
    }
````   
This means that when the method is called, it expects an obejct of the type of Model to be passed in.

* Add an Arraylist of Student to the model object with ````model.addAttribute()```` .
````java
    ArrayList<Student> students = new ArrayList<>();

     @GetMapping("/")
     public String index(Model model) {
            model.addAttribute("students", students);
            return "index";
     }
````   

## Incorporate the data on your index.html page
In the index.html files between the two ````<body> </body>```` tags create a table 

````html
    <body>
        <table>
            <thead>
            <tr>
                <th>Id</th>
                <th>First Name</th>
                <th>Last Name</th>
                <th>Enrollment Date</th>
                <th>Cpr</th>
                <th></th>
            </tr>
            </thead>
        </table>
    </body>
````    
This will create the header of the table.    

Add the body of the table

````html
    <body>
        <table>
            <thead>
            <tr>
                <th>Id</th>
                <th>First Name</th>
                <th>Last Name</th>
                <th>Enrollment Date</th>
                <th>Cpr</th>
                <th></th>
            </tr>
            </thead>
            <tbody>
            <tr th:each="student: ${students}">
                <td th:text="${student.studentId}"/>
                <td th:text="${student.firstName}"/>
                <td th:text="${student.lastName}"/>
                <td th:text="${student.enrollmentDate}"/> 
            <td th:text="${student.cpr}"/>
            <td></td>
        </tr>
        </tbody>
        </table>
    </body>
````    






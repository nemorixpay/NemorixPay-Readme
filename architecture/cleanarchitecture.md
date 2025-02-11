# NemorixPay - Official document

<p align="left"></p>

<p align="left">
  <img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/Logo%20Nemorix.png" width="400" title="NemorixPay logo">
</p>

## Clean Architecture

NemorixPay implements clean architecture which is a software design pattern that aims to create scalable, maintainable, and testable applications by separating concerns into multiple layers. It was introduced by Robert C. Martin (Uncle Bob) and is widely used in mobile development (Flutter, Android, iOS) to keep code modular and easy to maintain.

<p align="left">
  <img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/CleanArchitecture.jpg" width="400" title="NemorixPay logo">
</p>

The core principle of Clean Architecture is the dependency rule, which ensures that inner layers should not depend on outer layers, making business logic independent of frameworks, databases, and UI.

### Layers of Clean Architecture

A typical Clean Architecture structure consists of three or four main layers:

* **Presentation Layer** (UI & State Management) – Handles UI and user interactions.
* **Domain Layer** (Business Logic & Use Cases) – Contains business rules and application logic.
* **Data Layer** (Repositories & Data Sources) – Manages data from APIs, databases, or local storage.

Some implementations add a fourth layer (Entities) for additional abstraction, but in most mobile projects, it is included in the Domain Layer or models in the Data Layer for handling specific data types.

### Example: A Simple "To-Do App" with Clean Architecture
Let’s build an example where a user can add and retrieve tasks in a To-Do App.

**1. Presentation Layer (UI & State Management)**
Responsible for:

Displaying data to the user.
Handling user interactions.
Managing state using a state management solution (e.g., Provider, BLoC).

📌 Example (Flutter UI using Provider)

```
class TodoScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final todoProvider = Provider.of<TodoProvider>(context);
    
    return Scaffold(
      appBar: AppBar(title: Text("To-Do List")),
      body: ListView.builder(
        itemCount: todoProvider.tasks.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(todoProvider.tasks[index].title),
          );
        },
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () {
          todoProvider.addTask("New Task");
        },
        child: Icon(Icons.add),
      ),
    );
  }
}
```

**2. Domain Layer (Business Logic & Use Cases)**
Responsible for:

Defining the core business rules of the application.
Keeping logic independent of frameworks.
Using Use Cases (also called Interactors) to perform operations.

📌 Example (Use Case for Adding a Task)

```
class AddTaskUseCase {
  final TodoRepository repository;
  
  AddTaskUseCase(this.repository);
  
  void execute(String title) {
    repository.addTask(Task(title: title));
  }
}
```

**3. Data Layer (Repositories & Data Sources)**
Responsible for:

Handling data fetching (from APIs, databases, etc.).
Implementing the Repository Pattern to abstract data sources.
Allowing the Domain Layer to request data without knowing where it comes from.

📌 Example (Repository Implementation using Local Storage)

```
class TodoRepositoryImpl implements TodoRepository {
  final LocalDataSource localDataSource;
  
  TodoRepositoryImpl(this.localDataSource);
  
  @override
  List<Task> getTasks() {
    return localDataSource.fetchTasks();
  }
  
  @override
  void addTask(Task task) {
    localDataSource.saveTask(task);
  }
}
```

📌 Example (Local Data Source using a Simple List Storage)

```
class LocalDataSource {
  List<Task> _tasks = [];
  
  List<Task> fetchTasks() {
    return _tasks;
  }
  
  void saveTask(Task task) {
    _tasks.add(task);
  }
}
```

### Summary
* **Presentation Layer**: Handles UI and user interactions.
  * *Example*: TodoScreen (Flutter UI with Provider).
* **Domain Layer**: Contains business logic and use cases.
  * *Example*: AddTaskUseCase (Handles adding a task).
* **Data Layer**: Manages data fetching and storage.
  * *Example*: TodoRepositoryImpl (Fetches and saves tasks).

This separation of concerns makes the application scalable, testable, and easy to maintain. If we want to switch from local storage to an API, we only need to update the Data Layer without affecting the UI or business logic.

**Advantages of Clean Architecture**

✅ Scalability – Easy to expand with new features.<p></p>
✅ Testability – Business logic can be unit tested independently.<p></p>
✅ Maintainability – Clear separation of concerns makes debugging easier.<p></p>
✅ Flexibility – UI, business logic, and data management are independent.<p></p>

### Disadvantages & Common Problems of Clean Architecture

**1. Increased Complexity**

📌 Problem:
* Clean Architecture introduces multiple layers, even for simple applications.
* Small projects might not need this level of abstraction.

📌 Example:
* A simple to-do app might not need a Use Case layer, but with Clean Architecture, you still need to define it separately from the UI and data layers.

🛠 Solution:
* Consider using a simplified version of Clean Architecture for small projects (e.g., merging the Domain and Data layers).
* Only introduce full separation when the project scales.

**2. Boilerplate Code & Overhead** 

📌 Problem:
* You often write a lot of extra code for interfaces, repositories, and use cases.
* This can slow down development, especially in the early stages.

📌 Example:

To add a simple feature, you may need to modify multiple files:

1. UI (Presentation Layer)
2. Use Case (Domain Layer)
3. Repository Interface (Domain Layer)
4. Repository Implementation (Data Layer)
5. Data Source (API or Local Storage)

🛠 Solution:
* Use code generation tools (e.g., Freezed, Retrofit, or Riverpod in Flutter) to reduce manual effort.
* Start with a minimal structure and add layers gradually as needed.

**3. Harder Onboarding for New Developers**

📌 Problem:
* Developers unfamiliar with Clean Architecture may struggle to understand how layers interact.
* Finding where to make a change can be confusing due to multiple levels of abstraction.

📌 Example:
* A new developer might not know whether to place business logic inside the UI, Use Case, or Repository, leading to mistakes or code duplication.

🛠 Solution:
* Provide proper documentation and onboarding guides.
* Use well-defined naming conventions for folders and classes to improve clarity.
* Implement code reviews to ensure consistency.

**4. Performance Overhead**

📌 Problem:
* Due to the multiple layers, there can be extra method calls and processing steps.
* For mobile apps, this may slightly impact performance if not managed well.

📌 Example:
* Fetching data requires multiple layers of processing:

1. UI calls a Use Case
2. Use Case calls a Repository
3. Repository calls a Data Source
4. Data Source fetches data from API or Database
5. The response travels back through all layers before reaching the UI

🛠 Solution:
* Optimize performance using caching and lazy loading to reduce unnecessary calls.
* Minimize layers where appropriate (e.g., skipping the repository for local-only data).

### Conclusion: When to Use Clean Architecture?

✅ Use Clean Architecture when:

✔️ Your app is large or expected to scale over time.
✔️ You work in a team where code maintainability is important.
✔️ You need unit testing and business logic separation.
✔️ Your team is familiar with the pattern.

❌ Avoid Clean Architecture when:

✖️ You’re building a small prototype or MVP with a short timeline.
✖️ Your project is simple and doesn’t require complex data management.
✖️ Your team is unfamiliar with the pattern, and onboarding will slow down development.

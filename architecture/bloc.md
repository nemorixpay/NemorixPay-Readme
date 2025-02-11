# NemorixPay - Official document

<p align="left"></p>

<p align="left">
  <img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/Logo%20Nemorix.png" width="400" title="NemorixPay logo">
</p>

## What is BLoC?

BLoC (Business Logic Component) is a state management pattern used in Flutter. It helps separate business logic from the UI, making the app more scalable, testable, and maintainable.

NemorixPay implements BLoC which is based on the streams and reactive programming concepts, using Events (inputs) and States (outputs) to manage app state efficiently. It is commonly implemented using the [flutter_bloc package](https://pub.dev/packages/flutter_bloc), which provides a structured way to manage state using BLoCs and Cubits.

## Why Use BLoC?

✅ Separation of Concerns – Keeps UI logic separate from business logic.

✅ Predictable State Management – The app reacts consistently to user actions.

✅ Improved Testability – Business logic can be tested independently.

✅ Scalable & Maintainable – Makes large apps easier to manage.

## Core Concepts of BLoC

BLoC follows a unidirectional data flow pattern and consists of four main components:

**1. Events (Input)**

* Events represent user actions or system triggers.
* *Example*: A button press to fetch data.

**2. States (Output)**

* States represent the current condition of the UI.
* *Example*: Loading, Loaded, or Error state.

**3. BLoC (Business Logic Component)**

* Handles events and emits new states based on business logic.
* *Example*: Fetching data from an API when an event occurs.

**4. UI (Presentation Layer)**

* Listens to state changes and updates the UI accordingly.
* *Example*: Showing a loading spinner while data is being fetched.

### Simple Example: Fetching a List of Tasks Using BLoC

Let’s create a To-Do App where the user can fetch a list of tasks using BLoC.

📌 **Step 1**: Add Dependencies

Install the flutter_bloc package:
```
dependencies:
  flutter_bloc: ^8.1.3
```

📌 **Step 2**: Define the Events

Create a **task_event.dart** file to define the events.

```
abstract class TaskEvent {}

class LoadTasks extends TaskEvent {}
```

📌 **Explanation**:

*LoadTasks* is triggered when the user wants to fetch the task list.

📌 **Step 3**: Define the States

Create a **task_state.dart** file to define different UI states.

```
abstract class TaskState {}

class TaskLoading extends TaskState {}

class TaskLoaded extends TaskState {
  final List<String> tasks;
  TaskLoaded(this.tasks);
}

class TaskError extends TaskState {
  final String message;
  TaskError(this.message);
}
```

📌 **Explanation**:

`TaskLoading` → Shows a loading indicator.

`TaskLoaded` → Holds the list of tasks when successfully fetched.

`TaskError` → Stores an error message if something goes wrong.

📌 **Step 4**: Create the BLoC (Business Logic Component)

Create a **task_bloc.dart** file to handle events and emit states.

```
import 'package:flutter_bloc/flutter_bloc.dart';

class TaskBloc extends Bloc<TaskEvent, TaskState> {
  TaskBloc() : super(TaskLoading()) {
    on<LoadTasks>(_onLoadTasks);
  }

  void _onLoadTasks(LoadTasks event, Emitter<TaskState> emit) async {
    emit(TaskLoading()); // Emit loading state

    try {
      await Future.delayed(Duration(seconds: 2)); // Simulate API call
      final tasks = ["Buy groceries", "Do laundry", "Read a book"]; // Fake data
      emit(TaskLoaded(tasks)); // Emit loaded state with tasks
    } catch (e) {
      emit(TaskError("Failed to load tasks")); // Emit error state
    }
  }
}
```

📌 **Explanation**:

* The `TaskBloc` starts with the **TaskLoading** state.
* When `LoadTasks` is received, it simulates an API call and then:
* Emits **TaskLoaded** with the list of tasks if successful.
* Emits **TaskError** if an error occurs.

📌 **Step 5**: Connect BLoC to UI

Create a **task_screen.dart** file to build the UI.

```
import 'package:flutter/material.dart';
import 'package:flutter_bloc/flutter_bloc.dart';

class TaskScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("To-Do List")),
      body: BlocBuilder<TaskBloc, TaskState>(
        builder: (context, state) {
          if (state is TaskLoading) {
            return Center(child: CircularProgressIndicator());
          } else if (state is TaskLoaded) {
            return ListView.builder(
              itemCount: state.tasks.length,
              itemBuilder: (context, index) {
                return ListTile(title: Text(state.tasks[index]));
              },
            );
          } else if (state is TaskError) {
            return Center(child: Text(state.message, style: TextStyle(color: Colors.red)));
          }
          return Container();
        },
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () {
          context.read<TaskBloc>().add(LoadTasks()); // Trigger event
        },
        child: Icon(Icons.refresh),
      ),
    );
  }
}
```

📌 **Explanation**:

* Uses `BlocBuilder` to listen for state changes and update the UI dynamically.
* Shows a loading indicator while fetching tasks.
* Displays task list when data is loaded.
* Shows an error message if something goes wrong.
* Pressing the FloatingActionButton triggers `LoadTasks` to refresh the data.

📌 **Step 6**: Provide the BLoC in the App

Wrap the app with `BlocProvider` in **main.dart**.

```
void main() {
  runApp(
    BlocProvider(
      create: (context) => TaskBloc(),
      child: MaterialApp(
        home: TaskScreen(),
      ),
    ),
  );
}
```

📌 Explanation:

* `BlocProvider` ensures that `TaskBloc` is available throughout the app.

### Final Summary

* **Events** → Define user interactions (`LoadTasks`).
* **States** → Define UI conditions (`TaskLoading`, `TaskLoaded`, `TaskError`).
* **BLoC** → Handles events and emits new states.
* **UI** → Listens to state changes and updates dynamically.

### Advantages of BLoC

✅ Clear Separation of Concerns – Keeps UI and business logic separate.
✅ Predictable State Flow – Makes debugging and testing easier.
✅ Scalable – Ideal for large applications with complex state management.

### Disadvantages of BLoC

❌ Boilerplate Code – Requires multiple files for Events, States, and BLoCs.
❌ Learning Curve – Beginners might find it hard to understand Streams and Events.
❌ Extra Overhead – Small apps might not need this level of complexity.

### When Should You Use BLoC?

✅ Use BLoC when:
✔️ Your app has complex state changes (e.g., authentication, pagination).
✔️ You need high testability and maintainability.
✔️ You work in a large team where state management must be structured.

❌ Avoid BLoC when:
✖️ Your app is small and simple (e.g., a static UI app).
✖️ You need fast development and don’t want extra boilerplate.

### Final Thoughts

BLoC is a powerful state management solution that helps keep your app organized, scalable, and testable. While it has a learning curve, its predictability and structure make it a great choice for large Flutter projects.

# Task Class

<!-- TOC -->

- [Task Class](#task-class)
    - [What is it?](#what-is-it)
    - [Task Constructors](#task-constructors)
        - [Task Constructor Links](#task-constructor-links)
    - [Task Properties](#task-properties)

<!-- /TOC -->

## What is it?

The task class is a Class inside of the .NET Framework. It is used for schedule unit(s) of work. It is a Subset of the System.Treading class.
* Contains a large amount of methods related to system level tasks, Such as: 
    - Methods relating to Asynchronous Task/Methods

## Task Constructors

* Task(action): Initializes a new Task with the selected action.
* Task(action, cancellationToken): Initializes a new Task with the specified *action* and *Cancellation Token*.
* Task(action, cancellationToken, taskCreationOptions): Initializes a new Task with the specified action and *creation options*.
* Task(action, taskCreationOptions): Initializes a new Task with the specified action and *creation options*.
* Task(action<Object>, Object): Initializes a new task with the specified action and *state*.
* Task(action<Object>, Object, cancellationToken): Initializes a new task with the specified action, state, and options.
* Task(action<Object>, Object, cancellationToken, taskCreationOptions): Initializes a new task with the specified action, state, and options.
* Task(action<Object>, Object, taskCreationOptions): Initializes a new task with the specified action, state, and options.

### Task Constructor Links
* [Cancellation Token More Info](https://msdn.microsoft.com/en-us/library/system.threading.cancellationtoken(v=vs.110).aspx)


## Task Properties
* AsyncState: Get the state object supplied when the task was *created*, or *Null* if none was supplied.
* CompletedTask: Gets a task that has already been completed *Successfully*.
* CreationOptions: Gets the *TaskCreationOptions* used to *create* this task.
* CurrentId: Returns the ID of the currently *executing* task.
* Exception: Gets the *AggregateException* that caused the task to end *Prematurely*. If the task completed successfully or has *not yet* thrown exceptions, this will return *Null*.
* Factory: Provides access to factory methods for creating and configuring <code>Task</code> and <code>Task<'TResult'></code> instances.
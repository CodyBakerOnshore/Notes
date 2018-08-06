# Task Class

<!-- TOC -->

- [Task Class](#task-class)
    - [What is it?](#what-is-it)
    - [Task Constructors](#task-constructors)
        - [Task Constructor Links](#task-constructor-links)

<!-- /TOC -->

## What is it?

The task class is a Class inside of the .NET Framework. It is used for sceduable unit(s) of work. It is a Subset of the System.Treading class.
* Containes a large amount of methods related to system level tasks, Such as: 
    - Methods relating to Asynchronous Task/Methods

## Task Constructors

* Task(action): Initializes a new Task with the selected action.
* Task(action, cancelationToken): Initilizes a new Taskwith the specified *action* and *Cancelation Token*.
* Task(action, cancelationToken, taskCreationOptions): Initilizes a new Task with the specified action and *creation options*.
* Task(action, taskCreationOptions): Initilizes a new Task with the specified action and *creation options*.
* Task(action<Object>, Object): Initilizes a new task with the specified action and *state*.
* Task(action<Object>, Object, cancelationToken): Initilizes a new task with the specified action, state, and options.
* Task(action<Object>, Object, cancelationToken, taskCreationOptions): Initilizes a new task with the specified action, state, and options.
* Task(action<Object>, Object, taskCreationOptions): Initilizes a new task with the specified action, state, and options.

### Task Constructor Links
* [Cancelation Token More Info](https://msdn.microsoft.com/en-us/library/system.threading.cancellationtoken(v=vs.110).aspx)


## Task Properties
* AsyncState: Getthe state object supplied when the task was *created*, or *Null* if none was supplied.
* CompletedTask: Gets a task that has already been completed *Successfully*.
* CreationOptions: Gets the *TaskCreationOptions* used to *create* this task.
* CurrentId: Returns the ID of the currently *executing* task.
* Exception: Gets the *AggregateException* that caused the task to end *Prematurly*. If the task completed successfully or has *not yet* thrown exceptions, this will return *Null*.
* Factory: Provides access to factory methods for creating and configuring <code>Task</code> and <code>Task<'TResult'></code> instances.
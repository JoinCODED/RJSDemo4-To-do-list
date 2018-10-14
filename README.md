PRESENTATION LINK: https://docs.google.com/presentation/d/1VhahKb_U-eNWm488M4Ea0u5GgR3-BqnAGB0v5hvW2IU/edit#slide=id.p

1. Create a component: ToDoList

```javascript
import React, { Component } from "react";

class TodoList extends Component {
  render() {
    const statusIcon = done => {
      if (done) {
        return "fa fa-check-circle";
      } else {
        return "fa fa-times-circle";
      }
    };

    return (
      <table>
        <thead>
          <tr>
            <th>STATUS</th>
            <th>TASK</th>
            <th>PRIORITY</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>
              <i className={statusIcon(true)} />
            </td>
            <td>Go to the supermarket</td>
            <td className="middle">MIDDLE</td>
          </tr>
        </tbody>
      </table>
    );
  }
}
export default TodoList;
```

2. Call component more than one time

```javascript
import ToDoList from "./ToDoList";

class App extends Component {
  render() {
    return (
      <div className="rectangle">
        <p className="title">TO DO LIST</p>
        <ToDoList />
        <ToDoList />
        <ToDoList />
      </div>
    );
  }
}

export default App;
```

3. Send one prop per component

```javascript
class App extends Component {
  render() {
    return (
      <div className="rectangle">
        <p className="title">TO DO LIST</p>
        <ToDoList task="Buy Steak" />
        <ToDoList task="Clean your room" />
        <ToDoList task="Solve homework" />
      </div>
    );
  }
}
```

```javascript
class TodoList extends Component {
  render() {
    const statusIcon = done => {
      if (done) {
        return "fa fa-check-circle";
      } else {
        return "fa fa-times-circle";
      }
    };

    return (
      <table className="table">
        <thead>...</thead>
        <tbody>
          <tr>
            ...
            <td>{this.props.task}</td>
            ...
          </tr>
        </tbody>
      </table>
    );
  }
}
```

4. Send more than one prop

```javascript
class App extends Component {
  render() {
    return (
      <div className="rectangle">
        <p className="title">TO DO LIST</p>
        <ToDoList task="Buy Steak" done=true priority="middle"/>
        <ToDoList task="Clean your room" done=false priority="low"/>
        <ToDoList task="Solve homework" done=true priority="high"/>
      </div>
    );
  }
}
```

```javascript
class TodoList extends Component {
  render() {
    const statusIcon = done => {
      if (done) {
        return "fa fa-check-circle";
      } else {
        return "fa fa-times-circle";
      }
    };

    return (
      <table className="table">
        <thead>...</thead>
        <tbody>
          <tr>
            <td>
              <i className={statusIcon(this.props.done)} />
            </td>
            <td>{this.props.task}</td>
            <td className={this.props.priority}>
              {this.props.priority.toUpperCase()}
            </td>
          </tr>
        </tbody>
      </table>
    );
  }
}
```

5. Send "data" through props

```javascript
import tasks from "./data";

class App extends Component {
  render() {
    return (
      <div className="rectangle">
        <p className="title">TO DO LIST</p>
        <ToDoList tasks={tasks} />
      </div>
    );
  }
}
```

```javascript
class TodoList extends Component {
  render() {
    const statusIcon = done => {
      if (done) {
        return "fa fa-check-circle";
      } else {
        return "fa fa-times-circle";
      }
    };

    return (
      <table className="table">
        <thead>...</thead>
        <tbody>
          <tr>
            <td>
              <i className={statusIcon(this.props.tasks[0].done)} />
            </td>
            <td>{this.props.tasks[0].task}</td>
            <td className={this.props.tasks[0].priority}>
              {this.props.tasks[0].priority.toUpperCase()}
            </td>
          </tr>
        </tbody>
      </table>
    );
  }
}
```

6. Create a component: TodoItem

```javascript
import React, { Component } from "react";

class TodoItem extends Component {
  render() {
    const statusIcon = done => {
      if (done) {
        return "fa fa-check-circle";
      } else {
        return "fa fa-times-circle";
      }
    };
    return (
      <tr>
        <td>
          <i className={statusIcon(task.done)} />
        </td>
        <td>{task.task}</td>
        <td className={task.priority}>{task.priority.toUpperCase()}</td>
      </tr>
    );
  }
}
export default TodoItem;
```

7. Call Component TodoItem a few times

```javascript
import TodoItem from "./TodoItem";

class TodoList extends Component {
  render() {
    return (
      <table className="table">
        <thead>
          <tr className="headerRow">
            <th>STATUS</th>
            <th>TASK</th>
            <th>PRIORITY</th>
          </tr>
        </thead>
        <tbody>
          <TodoItem task={this.props.tasks[0]} />
          <TodoItem task={this.props.tasks[1]} />
          <TodoItem task={this.props.tasks[2]} />
        </tbody>
      </table>
    );
  }
}
export default TodoList;
```

8. Iterate through the array using .map

```javascript
let taskRows = this.props.tasks.map(task => (
  <TodoItem task={task} key={task.task} />
));

import TodoItem from "./TodoItem";

class TodoList extends Component {
  render() {
    return (
      <table className="table">
        <thead>
          <tr className="headerRow">
            <th>STATUS</th>
            <th>TASK</th>
            <th>PRIORITY</th>
          </tr>
        </thead>
        <tbody>{taskRows}</tbody>
      </table>
    );
  }
}
export default TodoList;
```

# Time planner

<a href="https://pub.dev/packages/time_planner">
   <img alt="Pub Version" src="https://img.shields.io/pub/v/time_planner.svg?longCache=true" />   
</a>
<a href="https://github.com/Solido/awesome-flutter">
   <img alt="Awesome Flutter" src="https://img.shields.io/badge/Awesome-Flutter-blue.svg?longCache=true" />   
</a>

A beautiful, easy to use and customizable time planner for flutter mobile 📱, desktop 🖥 and web 🌐

This is a widget for show tasks to user on a time table.  
Each row show an hour and each column show a day but you can change the title of column and show any things else you want.

## Screenshots

| Mobile                           | Dark                               |
| -------------------------------- | ---------------------------------- |
| ![Mobile](screenshot/Mobile.gif) | ![Dark](screenshot/darkMobile.jpg) |

| Desktop                            | Web                        |
| ---------------------------------- | -------------------------- |
| ![Desktop](screenshot/Desktop.gif) | ![Web](screenshot/Web.gif) |

## Demo

You can see web demo here: [https://jamalianpour.github.io/time_planner_demo](https://jamalianpour.github.io/time_planner_demo)

## Usage

##### 1. add dependencies into you project pubspec.yaml file

```yaml
dependencies:
  time_planner: ^0.1.2+1
```

##### 2. import time planner lib

```dart
import 'package:time_planner/time_planner.dart';
```

##### 3. use time planner

```dart
List<TimePlannerTask> tasks = [
  TimePlannerTask(
    // background color for task
    color: Colors.purple,
    // day: Index of header, hour: Task will be begin at this hour
    // minutes: Task will be begin at this minutes
    dateTime: TimePlannerDateTime(day: 0, hour: 14, minutes: 30),
    // Minutes duration of task
    minutesDuration: 90,
    // Days duration of task (use for multi days task)
    daysDuration: 1,
    onTap: () {},
    child: Text(
      'this is a task',
      style: TextStyle(color: Colors.grey[350], fontSize: 12),
    ),
  ),
];
```

```dart
TimePlanner(
  // time will be start at this hour on table
  startHour: 6,
  // time will be end at this hour on table
  endHour: 23,
  // each header is a column and a day
  headers: [
    TimePlannerTitle(
      date: "3/10/2021",
      title: "sunday",
    ),
    TimePlannerTitle(
      date: "3/11/2021",
      title: "monday",
    ),
    TimePlannerTitle(
      date: "3/12/2021",
      title: "tuesday",
    ),
  ],
  // List of task will be show on the time planner
  tasks: tasks,
),
```

#### Multi days task

You can add multi days task with `daysDuration` minimum and default value for this argument is 1 and result look like this :

![MultiDay](screenshot/MultiDay.png)

### Style

you can change style of time planner with `TimePlannerStyle` :

```dart
style: TimePlannerStyle(
  backgroundColor: Colors.blueGrey[900],
  // default value for height is 80
  cellHeight: 60,
  // default value for width is 90
  cellWidth: 60,
  dividerColor: Colors.white,
  showScrollBar: true,
  horizontalTaskPadding: 5,
  borderRadius: const BorderRadius.all(Radius.circular(8)),
),
```

when time planner widget loaded it will be scroll to current local hour and this option is true by default, you can turn this off like this:

```dart
currentTimeAnimation: false,
```

### Note

If you use desktop or web platform and want users to be able to move with the mouse in the time planner, add this code to the code:

```dart
class MyCustomScrollBehavior extends MaterialScrollBehavior {
  // Override behavior methods and getters like dragDevices
  @override
  Set<PointerDeviceKind> get dragDevices => {
    PointerDeviceKind.touch,
    PointerDeviceKind.mouse,
  };
}

// Set ScrollBehavior for an entire application.
MaterialApp(
  scrollBehavior: MyCustomScrollBehavior(),
  // ...
);
```

---

Fill free to fork this repository and send pull request 🏁👍

[Medium post](https://yaus.ir/4n7MeZ)

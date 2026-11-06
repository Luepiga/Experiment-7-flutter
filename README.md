# Experiment-7-flutter
You can do Experiment 7 – State Management and JSON in Visual Studio Code (VS Code) by following these simple steps.
Step 1 – Open VS Code
1. Open VS Code.
2. Open Terminal → New Terminal.
3. Create the Flutter project:
flutter create state_app


4. Open the project:
cd state_app
code .


Step 2 – Open main.dart
1. In the left Explorer panel, open lib.
2. Click main.dart.
3. Delete the existing code.
4. Paste the Experiment 7 code I provided above.
5. Press Ctrl + S to save.
Step 3 – Run the application
In the VS Code terminal, type:
flutter pub get
flutter run


import 'package:flutter/material.dart';
import 'dart:convert';

void main() => runApp(const MaterialApp(home: MyApp()));

class MyApp extends StatefulWidget {
  const MyApp({super.key});

  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  List<String> students = [];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Student App')),
      body: Column(children: [
        ElevatedButton(
          onPressed: () {
            setState(() {
              students.add('Raj');
            });
            var json = jsonEncode({'id': 1, 'name': 'Raj', 'course': 'CSE'});
            print(json);
            print(jsonDecode(json)['name']);
          },
          child: const Text('Add Student'),
        ),
        Expanded(
          child: ListView.builder(
            itemCount: students.length,
            itemBuilder: (c, i) => ListTile(title: Text(students[i])),
          ),
        ),
      ]),
    );
  }
}

import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Bidding Page',
      debugShowCheckedModeBanner: false,
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.green),
      ),
      home: const MaximumBid(title: 'Bidding Page'),
    );
  }
}

class MaximumBid extends StatefulWidget {
  const MaximumBid({super.key, required this.title});

  final String title;

  @override
  State<MaximumBid> createState() => _MaximumBidState();
}

class _MaximumBidState extends State<MaximumBid> {
  int _counter = 50; // Initial bid amount

  void _increaseBid() {
    setState(() {
      _counter += 50; // Increase bid by $50
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Theme.of(context).colorScheme.inversePrimary,
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            const Text('Current Maximum Bid', style: TextStyle(fontSize: 20)),
            Text(
              '\$$_counter', // Display the current bid
              style: Theme.of(context).textTheme.headlineMedium,
            ),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: _increaseBid,
              child: const Text('Increase Bid by \$50'),
            ),
          ],
        ),
      ),
    );
  }
}

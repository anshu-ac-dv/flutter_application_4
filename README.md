# flutter_application_4

### Understanding about SharedPreference

```
import 'package:flutter/material.dart';
import 'package:flutter_application_4/home_screen.dart';
import 'package:shared_preferences/shared_preferences.dart';

void main() {
  runApp(const LoginScreen());
}

class LoginScreen extends StatefulWidget {
  const LoginScreen({super.key});

  @override
  State<LoginScreen> createState() => _LoginScreenState();
}

class _LoginScreenState extends State<LoginScreen> {
  final emailController = TextEditingController();
  final passwordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Login Screen'),
        centerTitle: true,
        automaticallyImplyLeading: false,
        backgroundColor: Colors.blue,
      ),
      body: Padding(
        padding: const EdgeInsets.symmetric(horizontal: 20),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            TextFormField(
              controller: emailController,
              decoration: InputDecoration(hintText: 'Email'),
              keyboardType: TextInputType.emailAddress,
            ),
            SizedBox(height: 20),
            TextFormField(
              controller: passwordController,
              decoration: InputDecoration(hintText: 'Password'),
              keyboardType: TextInputType.visiblePassword,
            ),
            SizedBox(height: 20),
            InkWell(
              onTap: () async {
                SharedPreferences sp = await SharedPreferences.getInstance();
                sp.setString('email', emailController.text.toString());
                sp.setString('password', passwordController.text.toString());
                sp.setBool('islogin', true);
                Navigator.push(
                  context,
                  MaterialPageRoute(builder: (context) => HomeScreen()),
                );
              },
              child: Container(
                height: 50,
                width: double.infinity,
                color: Colors.blue,
                child: Center(child: Text('Login')),
              ),
            ),
          ],
        ),
      ),
    );
  }

  Future<void> anshu() async {
    await Future.delayed(Duration(seconds: 10));
  }
}
```


## البيانات الشخصية
الاسم :خلود مهيب مهيوب 
التخصص: قسم تقنية معلومات

##اسم المشروع | Project Title
شاشة تسجيل الدخول - Login Screen


## شرح التكليف | Assignment Description

تم تنفيذ شاشة تسجيل دخول باستخدام Flutter تحتوي على حقول لإدخال البريد الإلكتروني وكلمة المرور وزر تسجيل الدخول، وعند الضغط على الزر تظهر رسالة نجاح.


## تقرير الكود | Code Report

-تم استخدام Layouts مثل SafeArea وCenter وColumn لتنظيم العناصر بشكل مرتب ومتجاوب داخل الشاشة.
-تم استخدام Styling عبر ThemeData وColorScheme وInputDecorationTheme لتوحيد الألوان والشكل العام للواجهة.
-تم استخدام ElevatedButton لزر تسجيل الدخول وSnackBar لعرض رسالة النجاح للمستخدم.

## لقطة شاشة تسجيل الدخول (Screen Shoot)

[loginscreen.png](https://postimg.cc/yJ3j6HX0)



## الكود الكامل| Full Code
dart```
import 'package:flutter/material.dart';

void main() {
  runApp(const FreelaxApp());


class FreelaxApp extends StatelessWidget {
  const FreelaxApp({super.key});

  @override
  Widget build(BuildContext context) {
    final colors = ColorScheme.fromSeed(seedColor: Colors.indigo);

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Freelax Login',
      theme: ThemeData(
        useMaterial3: true,
        colorScheme: colors,
        scaffoldBackgroundColor: const Color(0xFFF5F7FB),
        inputDecorationTheme: InputDecorationTheme(
          filled: true,
          fillColor: Colors.grey.shade100,
          border: OutlineInputBorder(
            borderRadius: BorderRadius.circular(16),
            borderSide: BorderSide.none,
          ),
          enabledBorder: OutlineInputBorder(
            borderRadius: BorderRadius.circular(16),
            borderSide: BorderSide.none,
          ),
          focusedBorder: OutlineInputBorder(
            borderRadius: BorderRadius.circular(16),
            borderSide: BorderSide(color: colors.primary),
          ),
        ),
        elevatedButtonTheme: ElevatedButtonThemeData(
          style: ElevatedButton.styleFrom(
            minimumSize: const Size(double.infinity, 52),
            backgroundColor: colors.primary,
            foregroundColor: colors.onPrimary,
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(16),
            ),
          ),
        ),
      ),
      home: const LoginScreen(),
    );
  }
}

class LoginScreen extends StatelessWidget {
  const LoginScreen({super.key});

  void login(BuildContext context) {
    ScaffoldMessenger.of(context).showSnackBar(
      const SnackBar(
        content: Text(
          'تم تسجيل الدخول بنجاح',
          textAlign: TextAlign.center,
        ),
        behavior: SnackBarBehavior.floating,
        width: 250,
        backgroundColor: Colors.green,
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    final colors = Theme.of(context).colorScheme;

    return Scaffold(
      body: SafeArea(
        child: Center(
          child: SingleChildScrollView(
            padding: const EdgeInsets.all(24),
            child: ConstrainedBox(
              constraints: const BoxConstraints(maxWidth: 420),
              child: Card(
                elevation: 8,
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(24),
                ),
                child: Padding(
                  padding: const EdgeInsets.all(24),
                  child: Column(
                    mainAxisSize: MainAxisSize.min,
                    children: [
                      Container(
                        width: 85,
                        height: 85,
                        decoration: BoxDecoration(
                          color: colors.primary.withOpacity(0.1),
                          shape: BoxShape.circle,
                        ),
                        child: Icon(
                          Icons.campaign_outlined,
                          size: 40,
                          color: colors.primary,
                        ),
                      ),
                      const SizedBox(height: 20),
                      Text(
                        'Freelax',
                        style: TextStyle(
                          fontSize: 28,
                          fontWeight: FontWeight.bold,
                          color: colors.primary,
                        ),
                      ),
                      const SizedBox(height: 8),
                      const Text(
                        'شركة تسويقية متخصصة في الخدمات الرقمية',
                        textAlign: TextAlign.center,
                        style: TextStyle(color: Colors.black54),
                      ),
                      const SizedBox(height: 28),
                      const TextField(
                        decoration: InputDecoration(
                          labelText: 'البريد الإلكتروني',
                          prefixIcon: Icon(Icons.email_outlined),
                        ),
                      ),
                      const SizedBox(height: 16),
                      const TextField(
                        obscureText: true,
                        decoration: InputDecoration(
                          labelText: 'كلمة المرور',
                          prefixIcon: Icon(Icons.lock_outline),
                        ),
                      ),
                      const SizedBox(height: 24),
                      ElevatedButton(
                        onPressed: () => login(context),
                        child: const Text('تسجيل الدخول'),
                      ),
                    ],
                  ),
                ),
              ),
            ),
          ),
        ),
      ),
    );
  }
}
```

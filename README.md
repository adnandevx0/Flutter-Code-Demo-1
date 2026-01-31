# Flutter-Code-Demo-1

<h4>Class:6</h4>

<h5> Data Passing </h5>
<pre>

//home.dart

    ElevatedButton(onPressed: () {
                  Navigator.push(context, MaterialPageRoute(builder: (context){
                    return Profile(name: "Adnan");
                  }));
                } , child: Text(
                  "Profile",
                  style:TextStyle(
                    color: Colors.blue,
                    fontSize: 40,
                  ),
                ))

  
//profile.dart
import 'package:flutter/material.dart';
import 'package:tom1/home.dart';

class Profile extends StatelessWidget {
  const Profile({super.key, required this.name });

  final String name;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          "Title", style: TextStyle(fontSize: 20, color: Colors.blue),),
      ),
      body: Center(
        child: Container(
          height: 200,
          width: double.infinity,
          color: Colors.redAccent,
          child: TextButton(onPressed: () {
            //Current Page Fele Dibe
            //Navigator.pop(context);
            // all page clear kore tergate apage a jabe
            Navigator.pushAndRemoveUntil(context, MaterialPageRoute(builder: (context){
              return Home();
            }), (route) => false);
          }, child: Text(name, style: TextStyle(color: Colors.blue,fontSize: 50),)),
        ),
      ),
    );
  }
}
  
</pre>

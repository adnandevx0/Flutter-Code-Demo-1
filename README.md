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

<h4> class 7: StatefulWidget,MediaQuery.of,  LayoutBuilder </h4>

<pre>
import 'package:flutter/material.dart';

void main(){
  runApp(Mainapp());
}

//Statefulwidget
class Mainapp extends StatefulWidget {
  const Mainapp({super.key});

  @override
  State<Mainapp> createState() => _MainappState();
}

class _MainappState extends State<Mainapp> {
  int x  = 0;
  @override
  Widget build(BuildContext context) {
    //Know context size
    print(MediaQuery.of(context).size.width);
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          title: Text("Home"),
          centerTitle: true,
        ),
        body:
        //very importent for know the size of screen & for responce design
        LayoutBuilder(builder: (BuildContext context, BoxConstraints constraints){
          if(constraints.maxWidth > 400){
            return Text("400",style: TextStyle(fontSize: 50),);
          }
          else if(constraints.maxWidth < 222){
            return Text("222",style: TextStyle(fontSize: 50),);
          }
          else{
            return Text("300",style: TextStyle(fontSize: 50),);
          }
        }) ,
        floatingActionButton: Row(
          mainAxisAlignment: MainAxisAlignment.end,
          children: [
            IconButton(style:
            IconButton.styleFrom(
              backgroundColor: Colors.green,
              foregroundColor: Colors.white,
              shape: CircleBorder(),
            )
                ,onPressed: () {
                  x++;
                  print(x);
                  //need must
                  setState(() {});
                }, icon: Icon(Icons.add)),
            IconButton(style:
            IconButton.styleFrom(
              backgroundColor: Colors.green,
              foregroundColor: Colors.white,
              shape: CircleBorder(),
            )
                ,onPressed: () {
                  x--;
                  print(x);
                  //need must
                  setState(() {});
                }, icon: Icon(Icons.remove))
          ],
        ),

      ),
    );
  }
}

</pre>

<h4> OrientationBuilder </h4>

<pre>

            OrientationBuilder(builder: (context, orientation){
          //sojasoje
          if(orientation == Orientation.landscape){
            return Text("Landscape",style: TextStyle(fontSize: 50),);
          }
          //bakabake
          else{
            return Text("Portrait",style: TextStyle(fontSize: 50),);
          }
        }
</pre>

<h4> Flexible হলো একটি উইজেট যা Row, Column বা Flex-এর ভেতর তার চাইল্ড (child) উইজেটটি কতটুকু জায়গা দখল করবে তা নিয়ন্ত্রণ করে। </h4>
<pre>

import 'package:flutter/material.dart';

void main(){
runApp(Myapp());  
}

class Myapp extends StatefulWidget {
  const Myapp({super.key});

  @override
  State<Myapp> createState() => _MyappState();
}

class _MyappState extends State<Myapp> {
  @override
  Widget build(BuildContext context) {
   return MaterialApp(
     home: Scaffold(
       appBar: AppBar(
         backgroundColor: Colors.redAccent,
         leading:Icon(Icons.calculate),
         title: Text("My Calculator"),
         actions: [

         ],
       ),
       body:Row(
         children: [
          Flexible(
            //full nibe = fit: FlexFit.tight,
            // fill nibe na = fit: FlexFit.loose,
              fit: FlexFit.tight,
             // 5 bager 3 bag nibe = flex: 3 karok akhane 3 niche 2
              flex: 3,
              child:
          Container(
            height: 100 ,
            width: 100,
            color: Colors.yellow,
            child: Text("saf",style: TextStyle(fontSize: 50),) ,
          )
          ),
           Flexible(
           fit: FlexFit.tight,
             child: Container(
               height: 100 ,
               width: 100,
               color: Colors.blue,
               child: Text("saf",style: TextStyle(fontSize: 50),) ,
             ),
           ),
           Flexible(
             fit: FlexFit.tight,
             child: Container(
               height: 100 ,
               width: 100,
               color: Colors.green,
               child: Text("saf",style: TextStyle(fontSize: 50),) ,
             ),
           ),
         ],
       ) ,
     )
   );
  }
}

</pre>

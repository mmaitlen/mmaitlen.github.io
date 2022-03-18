---
layout: post
title:  "Fill in Android form using adb shell input"
date:   2022-02-18 10:00:00 -0800
categories: coding dart flutter adb android
---
[TestLink](https://links.irisoncology.com/visits)

![dice](/assets/images/thumbnail_adb_shell.png){: style="float: left; padding: 5px;"} Put together a video on [my Youtube channel](https://youtu.be/xMI3c_RA20Y) showing how to use adb shell input for Android to fill in Flutter text fields.  The form code is below, nothing fancy, just a couple TextFormField widgets with controllers and focus nodes to drive the cursor forward.  Pressing the login button resets the form, but could also direct the user to another screen.

The abd commands are as follows

**user1_login.sh**

{% highlight shell %}
adb shell input text user1@z333k.com
adb shell input keyevent 66
adb shell input text passW0rd
adb shell input keyevent 66
adb shell input keyevent 66
{% endhighlight %}

**One tip** is to ensure the cursor is in the first field before executing the script from the command line.

{% highlight dart linenos %}
class Sdbx4Screen extends StatefulWidget {
  const Sdbx4Screen({Key? key}) : super(key: key);

  @override
  _Sdbx4ScreenState createState() => _Sdbx4ScreenState();
}

class _Sdbx4ScreenState extends State<Sdbx4Screen> {
  late TextEditingController _ctrl1;
  late TextEditingController _ctrl2;

  final _fld1FocusNode = FocusNode();
  final _fld2FocusNode = FocusNode();
  final _btnFocusNode = FocusNode();

  @override
  void initState() {
    _ctrl1 = TextEditingController();
    _ctrl2 = TextEditingController();
    super.initState();
  }

  @override
  void dispose() {
    _ctrl1.dispose();
    _ctrl2.dispose();
    _fld1FocusNode.dispose();
    _fld1FocusNode.dispose();
    _btnFocusNode.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Sdbx4'),
      ),
      body: Column(
        children: [
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: Container(
              color: Colors.black12,
              child: TextFormField(
                controller: _ctrl1,
                style: const TextStyle(fontSize: 18),
                focusNode: _fld1FocusNode,
                onFieldSubmitted: (value) {
                  FocusScope.of(context).requestFocus(_fld2FocusNode);
                },
              ),
            ),
          ),
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: Container(
              color: Colors.black12,
              child: TextFormField(
                controller: _ctrl2,
                style: const TextStyle(fontSize: 18),
                focusNode: _fld2FocusNode,
                onFieldSubmitted: (value) {
                  FocusScope.of(context).requestFocus(_btnFocusNode);
                },
              ),
            ),
          ),
          OutlinedButton(
            focusNode: _btnFocusNode,
            onPressed: () async {
              await Future.delayed(const Duration(seconds: 2));
              _ctrl1.clear();
              _ctrl2.clear();
              FocusScope.of(context).requestFocus(_fld1FocusNode);
              // Navigator.push(
              //   context,
              //   MaterialPageRoute(builder: (context) => const Sdbx5Screen()),
              // );
            },
            child: const Text("Login"),
          )
        ],
      ),
    );
  }
}
{% endhighlight %}
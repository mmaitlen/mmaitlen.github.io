---
layout: post
title:  "Using group to organize Dart/Flutter tests"
date:   2022-01-15 17:15:00 -0800
categories: coding dart flutter testing
---

UPDATE - I discussed this topic in a video on [my Youtube channel](https://youtu.be/AohnACb_3qo)

The Flutter API docs states that the [group function](https://api.flutter.dev/flutter/flutter_test/group.html){:target="_blank"} "Creates a group of tests".  Grouping tests helps with test output, scoping setUp and tearDown functions and being able to skip all the tests in a group with a single skip argument.  This post also demonstrates the "dart test -r expanded" command. 

{% highlight dart linenos %}
void main() {
  group('GroupATest - ', () {
    test('ensure A1 functionality', () {
      expect(1 + 2, 3);
    });
    test('ensure A2 functionality', () {
      expect(2 + 2, 4);
    });
  });

  group('GroupBTest - ', () {
    test('ensure B1 functionality', () {
      expect(4 + 2, 6);
    });
  });
}
{% endhighlight %}

Executing the following on the command line
> dart test

outputs

00:00 +3: All tests passed!

If you're looking for more info
> dart test -r expanded

outputs

00:00 +0: test/group_test.dart: GroupATest -  ensure A1 functionality

00:00 +1: test/group_test.dart: GroupATest -  ensure A2 functionality

00:00 +2: test/group_test.dart: GroupBTest -  ensure B1 functionality

00:00 +3: All tests passed!

## Skip argument
Adding a skip argument allows you to skip all the tests in the skipped group

{% highlight dart linenos %}
void main() {
  group('GroupATest - ', () {
    test('ensure A1 functionality', () {
      expect(1 + 2, 3);
    });
    test('ensure A2 functionality', () {
      expect(2 + 2, 4);
    });
  });

  group('GroupBTest - ', () {
    test('ensure B1 functionality', () {
      expect(4 + 2, 6);
    });
  });
}
{% endhighlight %}

> dart test

00:00 +0: test/group_test.dart: GroupATest -  ensure A1 functionality                                                                                                                                         
  Skip: dont run tests in GroupA

00:00 +0 ~1: test/group_test.dart: GroupATest -  ensure A2 functionality                                                                                                                                      
  Skip: dont run tests in GroupA

00:00 +1 ~2: All tests passed!
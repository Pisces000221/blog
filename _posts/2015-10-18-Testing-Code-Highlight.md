---
layout: post
category : Test
tagline: ""
tags : [Test]
shortContent: "Hello World"
---
{% include JB/setup %}

##### Hello World

All sorts of codes that prints "Hello World!"

{% highlight bash %}

echo "Hello World!"

{% endhighlight %}

{% highlight C %}

#include<cstdio>

int main(){

    printf("Hello World!")
    return 0;

}

{% endhighlight %}

{% highlight cpp %}

#include<iostream>

using namespace std;

int main(){

    cout << "Hello World!" << endl;
    return 0;

}

{% endhighlight %}

{% highlight csharp %}

using System;

class Program {

   public static void Main(string[] args) {
    Console.WriteLine("Hello World!");
   }

}

{% endhighlight %}

{% highlight java %}

public class HelloWorld {

    public static void main(String[] args) {
        System.out.println("Hello World!");
    }

}

{% endhighlight %}

{% highlight javascript %}

document.write('Hello World!');

{% endhighlight %}

{% highlight python %}

print "Hello World!"

{% endhighlight %}

{% highlight ruby %}

puts "Hello World!"

{% endhighlight %}

{% highlight swift %}

println("Hello World!")

{% endhighlight %}

{% highlight perl %}

print "Hello World!";

{% endhighlight %}

#### And the "Best Language" in the World...

{% highlight php %}

<html>
 <head>
  <title>PHP Test</title>
 </head>
 <body>
  <?php echo '<p>Hello World!</p>'; ?> 
 </body>
</html>

{% endhighlight %}




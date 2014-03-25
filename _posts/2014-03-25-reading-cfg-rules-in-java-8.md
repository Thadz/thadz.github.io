---
layout: post
title: "reading CFG rules in Java 8"
categories: article
tags: java, context free grammar, theory of computation
---

These week I was working on a simple project generating lots of strings based on the given context-free grammars. Since Java 8 has been officially released, I decided to give Java 8 a try. It turns out to be really fun to write functional syntax in Java.

{% highlight java %}
public CFGGenerator(String filepath) throws Exception {
    rules =
      Arrays
      .stream(
              new String(Files.readAllBytes(Paths.get(filepath))).split("\n")
      )
      .map(l -> {
          // first token is the left variable while the second is the derivation
          String[] tokens = l.split(DELIMITER);
          HashMap<String, HashSet<ArrayList<String>>> map = new HashMap<>();
          HashSet<ArrayList<String>> set = new HashSet<>();
          ArrayList<String> list = new ArrayList<>();
          if (Character.isUpperCase(tokens[1].charAt(0))) {
              // if the derivation are variables, store them separately
              list.add(Character.toString(tokens[1].charAt(0)));
              list.add(Character.toString(tokens[1].charAt(1)));
          } else {
              // if the derivation is a single terminal, store this piece
              list.add(tokens[1]);
          }
          set.add(list);
          map.put(tokens[0], set);
          return map;
      })
      .reduce(new HashMap<String, HashSet<ArrayList<String>>>()
              , (m1, m2) -> {
          for (String key : m2.keySet()) {
              if (m1.containsKey(key)) {
                  // if m1 has the same left variable as m2
                  // put m2's corresponding derivations in place
                  HashSet<ArrayList<String>> set = m1.get(key);
                  set.addAll(m2.get(key));
                  m1.put(key, set);
              } else {
                  // if m1 doesn't have such left variable as m2
                  // add the new rule to m1
                  m1.put(key, m2.get(key));
              }
          }
          return m1;
      });
    for (Map.Entry<String, HashSet<ArrayList<String>>> entry : rules.entrySet()) {
      System.out.println(entry);
    }
  }
{% endhighlight %}

At the end of such block of code, it just prints out the internal data structure for debug purpose. As you can see from above, Java 8 has a special class called stream which is the "functionalized" collection. Given a stream, you can call map, reduce, filter, for each and etc. Also, you don't need to worry the type (or class) in the lambda expression, because the compiler will figure it out for you. That means, if you are assigning values to a variable of another type, the compiler will kindly remind you. MORE IMPORTANTLY, you can add break point even inside the lambda expression and the IDE, Intelli-J, supports it gracefully. This is the moment when I need to decide whether to use Haskell any more for functional-ish developement. By the way for curious Georges, following is what has been printed.

{% highlight text %}
P=[[in], [for], [on]]
Q=[[P, H], [P, N]]
S=[[H, W], [N, O], [H, O], [N, V], [N, W], [H, V]]
V=[[ate], [swim], [streams]]
W=[[O, Q], [V, L], [V, Q], [O, L]]
H=[[N, Q], [N, L]]
L=[[Q, Q], [Q, L]]
N=[[tuesday], [streams], [swims], [fish], [amy], [dinner]]
O=[[V, H], [V, N]]
{% endhighlight %}
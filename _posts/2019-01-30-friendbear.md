---
layout: post
author: friendbear
title:  Scala (A Type Class End-to-end example JSON Serialization)
categories: [blog, lang-scala]
tags: [lang-scala]
---

### Try Scala
- RockScalaForAdvanced
  - Advanced Inheritance

    ```scala
      Type linearization
      Cold = AnyRef with <Cold>
      Green
        = Cold with <Green>
        = AnyRef with <Cold> with <Green>
      Blue
        = Cold with <Blue>
        = AnyRef with <Cold> with <Blue> with <Green>
      Red = AnyRef with <Red>
    ```


### kumasora

### Reference

### Usefull Link

### Recommend


### Snippets

<details>
<summary><code>JSONSerialization</code></summary>
<pre>
<code>
#!/usr/bin/env amm
@main
def RockingInheritance(args: String*) = {

  // convenience
  trait Writer[T] {
    def write(value: T): Unit
  }
  trait Closeable{
    def close(status: Int): Unit
  }
  trait GenericsStream[T] {
    def foreach(f: T => Unit): Unit
  }
  def processStream[T](stream: GenericsStream[T] with Writer[T] with Closeable): Unit = {
    stream.foreach(println)
    stream.close(0)
  }

  // diamond problem
  trait Animal { def name: String }
  trait Lion extends Animal {
    override def name: String = "lion"}
  trait Tiger extends Animal {
    override def name: String = "tiger" }
  class Mutant extends Lion with Tiger

  val m = new Mutant
  println(m.name) // => "tiger"

  /*
    Mutant
    extends Animal with {override def name: String = "lion" }
    with {override def name: String = "tiger}

    LAST OVERRIDE GETS PICKED 🔴
   */

  // the super problem + type linearization
  trait Cold {
    def print = println("cold")
  }
  trait Green extends Cold {
    override def print: Unit = {
      println("green")
      super.print
    }
  }
  trait Blue extends Cold {
    override def print: Unit = {
      println("blue")
      super.print
    }
  }
  class Red {
    def print = println("red")
  }

  class White extends Red with Cold with Green with Blue {
    override def print: Unit = {
      println("write")
      super.print
    }
  }

  println(new White().print) // write => blue => green => cold //
}
</code>
</pre>
</details>

<details>
<summary><code>ScalaJavaConversions</code></summary>
<pre>
<code>
#!/usr/bin/env amm

@main
def ScalaJavaConversions(args: String*) = {

}

</code>
</pre>
<details>
<summary><code>A Type Class Use Case / The Magnet Pattern</code></summary>
<pre>
<code>
#!/usr/bin/env amm

@main
def MagnetPattern(args: String*) = {
}
</code>
</pre>
</details>
<details>
<summary>-</summary>
<pre>
<code>
#!/usr/bin/env amm

@main
def ImplicitOrdering(args: String*) = {
}

</code>
</pre>
</details>


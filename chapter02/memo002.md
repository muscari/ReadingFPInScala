### chapter.2
#### Scala関数型プログラミングの準備

##### 純粋関数の組み合わせ
本章で純粋関数を組み合わせ、Scala言語で副作用のない記述方法を学ぶ

** 戻り値の型がUnitであることは、そのメソッドに副作用があるこのとヒントなり **

##### 高階関数

- 高階関数とは

  関数を引数として受け取る関数

  - 関数型のループ

```scala
def factorial(n: Int): Int = {
  def go(n: Int, acc: Int): Int = // 再帰ヘルパー関数 go, loopが慣例
    if (n <= 0) acc
    else go(n-1, n*acc)

  go(n, 1)

  // 実行結果
  /*
  scala> factorial(2)
  res2: Int = 2

  scala> factorial(3)
  res3: Int = 6

  scala> factorial(4)
  res4: Int = 24

  scala> factorial(5)
  res5: Int = 120
  */
}
```

  この種の自己再帰は **再帰呼び出しが末尾呼び出し** であるかぎり、whilループに対して生成されるバイトコードとしてコンパイルされる。
  + 末尾呼び出し

      呼び出し元が再帰呼び出し値を返す以外何もないこと(今回の例の場合)

    ##### Exercise 2.1
    
      n番目のフィボナッチ数を取得する再帰関数を記述せよ。最初の２つのフィボナッチ数は0と1である。

      ```scala
      // 回答
      def fib(n: Int): Int = {
        n match {
          case 0 => 0
          case 1 => 1
          case _ => fib(n-2) + fib(n-1)
        }
      }

      // 実行結果
      /*
      scala> fib(0)
      res6: Int = 0

      scala> fib(1)
      res7: Int = 1

      scala> fib(2)
      res8: Int = 1

      scala> fib(3)
      res9: Int = 2

      scala> fib(4)
      res10: Int = 3

      scala> fib(5)
      res11: Int = 5
      */
      ```

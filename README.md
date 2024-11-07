## 思维导航

* [单例模式介绍](https://github.com)
* [设计模式的作用](https://github.com)
* [饿汉式单例模式](https://github.com)
* [懒汉式单例模式](https://github.com)
* [懒加载单例模式](https://github.com)
* [设计模式入门实战教程](https://github.com)

:[slower加速器](https://jisuanqi.org)## 单例模式介绍


单例模式是一种创建型设计模式，它主要确保在一个类只有一个实例，并提供一个全局访问点来获取该实例。在C\#中，有多种方式实现单例模式，每种方式都有其特定的使用场景和注意事项。


## 设计模式的作用


* 提高代码的可重用性：通过定义一套标准的解决方案，设计模式使得相同或类似的问题可以在不同的项目中复用相同的代码结构或逻辑。
* 增强代码的可读性：设计模式使用清晰、简洁的方式表达复杂的代码逻辑，使得其他开发者能够更容易地理解和维护代码。
* 提高系统的可维护性：设计模式遵循一定的设计原则，如开闭原则、里氏代换原则等，这些原则有助于降低系统各部分的耦合度，提高系统的可扩展性和可维护性。


## 饿汉式单例模式


饿汉式单例是在类加载时就创建实例。优点是实现简单，缺点是如果该实例不被使用会造成资源浪费。



```
        ///         /// 饿汉式单例模式        ///         public class SingletonEager        {            private SingletonEager() { }            private static readonly SingletonEager _instance = new SingletonEager();            public static SingletonEager Instance            {                get { return _instance; }            }            public void DoSomething()            {                Console.WriteLine("饿汉式单例模式.");            }        }
```

## 懒汉式单例模式


懒汉式单例在第一次被访问时才创建实例。为了线程安全，通常需要使用锁机制。



```
        ///         /// 懒汉式单例模式        ///         public class SingletonLazy        {            private SingletonLazy() { }            private static SingletonLazy? _instance;            private static readonly object _lockObj = new object();            public static SingletonLazy Instance            {                get                {                    if (_instance == null)                    {                        lock (_lockObj)                        {                            if (_instance == null)                            {                                _instance = new SingletonLazy();                            }                        }                    }                    return _instance;                }            }            public void DoSomething()            {                Console.WriteLine("懒汉式单例模式.");            }        }
```

## 懒加载单例模式


如果您使用的是 .NET 4（或更高版本），可以使用Lazy类来实现线程安全的懒加载单例模式。



```
        ///         /// 懒加载单例模式        ///         public sealed class SingletonByLazy        {            private static readonly Lazy _lazy = new Lazy(() => new SingletonByLazy());            public static SingletonByLazy Instance { get { return _lazy.Value; } }            private SingletonByLazy() { }            public void DoSomething()            {                Console.WriteLine("懒加载单例模式.");            }        }
```

## 设计模式入门实战教程


[https://mp.weixin.qq.com/s/FM0ThUR92EcXJ3YY313ifw](https://github.com)



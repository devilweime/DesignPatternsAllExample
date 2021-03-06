策略模式(strategy)

一、定义
定义一系列算法类，将每一个算法封装起来，并让它们可以相互替换。策略模式让算法独立于使用它的客户而变化。

二、结构
Context（环境类）：负责使用算法策略，其中维持了一个抽象策略类的引用实例。
Strategy（策略类的接口）：所有策略类的父类(接口)，为所支持的策略算法声明了抽象方法。
ConcreteStrategy（具体策略类）：实现了在抽象策略类中声明的方法。

三、优点
提供了对开闭原则的完美支持，用户可以在不修改原有系统的基础上选择具体算法或行为，也可以灵活地增加新的算法或行为。
避免了多重的if-else条件选择语句，利于系统的维护。
提供了一种算法的复用机制，不同的环境类可以方便地复用这些策略类。

四、缺点
客户端需要知道所有的策略类，并自行决定使用哪一个策略（使用者必须知道每一个策略类其中的算法）
将造成系统产生很多的具体策略类，任何细小的变化都将导致系统要增加一个具体策略类（策略越多，类越多）
无法在客户端同时使用多个策略类（一次只能使用一种策略）

五、应用场景
如果一个系统要动态地在几种算法之间选择其中一种
如果有难以维护的多重if-else条件选择语句是为了实现对象的行为
不希望客户知道复杂的与算法有关的数据结构，可以将其封装到策略中

六、个人总结
1.从面向过程的角度来说
    很多时候，我们需要判断各种条件后然后执行不同的业务逻辑
    而且执行的业务逻辑非常的复杂，我们可以看作一个个复杂的算法（策略）
    我们可以将其进行拆分为一个个策略类来实现，从而方便维护，方便复用
2.从面向对象的角度来说
    如果使用继承
        如果父类不是抽象方法，那么容易导致忘记或者遗漏重写方法，
        如果使用抽象方法，那么每个类都必须去重写父类的方法，无论你需不需要（有的时候你是不需要的）
        而且有可能大多数的代码相同时，改动就变得很复杂了
    如果使用多个接口实现
        那么如果使用策略A就需要修改为接口A，如果使用策略B就需要修改为接口B
        比较麻烦，而且接口多，代码复用性就变差了
    策略模式使用组合（在类中增加一个私有域，引用另一个已有类的实例，通过调用引用实例的方法从而获得新的功能）
        足够的灵活，更加易于维护，策略可以复用

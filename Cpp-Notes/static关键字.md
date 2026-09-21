## 类外static修饰
类外static修饰的符号在link阶段是局部的，即只对定义它的编译单元可见。

## 类内部static修饰
在类内部定义一个static变量，意味着这个类的所有实例中，这个变量只有一个实例。所以通过类实例来引用静态变量是没有意义的。并且类内部的静态变量需要在类外部定义。  
```c++
struct Entity
{
    static int x, y;
};
int Entity::x = 5;
Entity::x = 10;
```

> [!NOTE]
> 静态方法不能访问非静态变量
> 而非静态方法本质上会获得当前的类实例作为隐藏参数(this指针)，所以通过this就可以访问非静态变量

## 函数内部静态局部变量
```c++
void Function()
{
    static int i = 0;
}
```
当第一次调用这个函数时，它的值被初始化为0，该变量的作用域与普通函数的作用域一样都只能在函数内部访问，但它的生命周期却是整个程序的生命周期，不会随着函数结束而被销毁。所以如果后续再次调用该函数并不会创建一个新的变量。

## 单例类
单例类是一种设计模式，确保一个类只有一个实例，并提供以一个全局访问点来获取这个实例
### 特点
- 私有静态实例变量--保存唯一实例
- 公有静态方法--返回该实例

```c++
//不使用静态局部变量实现方式
class Singleton
{
private:
    static Singleton* s_Instance;
public:
    static Singleton& Get()
    {
        return *s_Instance;
    }
};
Singleton* Singleton::s_Instance = nullptr;

//使用静态局部变量实现
class Singleton
{
public:
    static Singleton& Get()
    {
        static Singleton s_Instance;
        return s_Instance;
    }
}
```

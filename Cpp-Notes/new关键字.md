## 创建数组
```c++
    int* another = new int[5];
```
> [!CAUTION]
> 创建数组大小的值必须在编译时就确定
### 计算数组元素个数
```c++
    int count = sizeof(another) / sizeof(int);

## 销毁数组
```c++
    delete[] another;
```

## new关键字创建对象流程
- 根据提供的类型，决定要分配的内存大小
- 请求c标准库分配对应大小的内存
- 找到符合大小要求的连续内存块
- 返回指向内存块的指针

> [!NOTE]
> 当使用new关键字创建对象时，不仅分配空间，还调用了构造函数
> new和delete必须成对使用，并且delete会调用析构函数

## new关键字的底层机制
**new关键字的底层机制是malloc函数**
```c++
class Entity{};
Entity* e = new Entity();
Entity* e = (Entity*)malloc(sizeof(Entity));
```
上述两行代码都在堆上进行了内存分配，而区别在于new关键字还调用了构造函数
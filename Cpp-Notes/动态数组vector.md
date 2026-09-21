## vector用法

```c++
struct Vertex
{
    float x, y, z;
}
std::vector<Vertex> vertices; //创建动态数组
vertices.push_back({1, 2, 3}); //添加元素
//遍历动态数组
for(int i = 0; i < vertices.size(); i++)
{
    std::cout << vertices[i] << std::endl;
}
//另一种遍历方法
for(Vertex& v : vertices)
{
    std::cout << v << std::endl;
}
vertices.clear(); //清空动态数组
vertices.erase(); //删除某个元素
```

## vector的工作流程
**当你尝试使用push_back向vector添加元素时，如果当前vector容量不足，会调整大小，重新分配，并将内存中旧位置数据复制到新位置，然后删除旧位置内存。所以这种不断的分配会拖慢代码**

## vector优化策略
- 避免在别处创建对象，再将创建的对象复制到vector中，**直接在vector中创建对象**
- 避免多次调整vector大小，减少复制开销,**如果可以直接告诉vector预计的大小**

## 具体优化方法
### vector.reserve
通过vector.reserve函数提前为vector预留存储空间，减少后续添加元素时发生的内存重新分配
```c++
#include <vector>
std::vector<int> nums;
nums.reserve(3);
```
### vector.emplace_back
在 vector 的末尾直接构造一个新元素。
它和 push_back() 很像，但关键区别是：
- push_back()：先创建一个对象，再把对象拷贝/移动到 vector 中。
- emplace_back()：把构造参数直接传进去，在 vector 尾部原地构造对象

```c++
#include <vector>
struct Vertex
{
    float x, y, z;
    Vertex(float x, float y, float z)
        :x(x), y(y), z(z) {}
};

int main()
{
    std::vector<Vertex> vertices;
    vertices.reserve(3);
    vertices.emplace_back({1, 2, 3});
    vertices.emplace_back({4, 5, 6});
    vertices.emplace_back({7, 8, 9});
}
```


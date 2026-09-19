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
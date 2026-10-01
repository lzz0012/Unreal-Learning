# auto
自动推导变量类型
## 避免变量类型太长
```c++
int main()
{
    std::vector<std::string> strings;
    strings.push_back("Apple");
    strings.push_back("Orange");

    for(std::vector<std::string>::iterator it = strings.begin(); it != strings.end(); it++)
    {
        std::cout << *it << std::endl;
    }
    //替换为auto    
    for(auto it = strings.begin(); it != strings.end(); it++)
    {
        std::cout << *it << std::endl;
    }
}
```

## 用于判断函数指针类型
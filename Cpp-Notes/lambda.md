# lambda用法
在设置函数指针指向函数的任何地方，都可以将它设置为lambda
```c++
void Foreach(const std::vector<int>& values, void(*func)(int))
{
	for (int value : values)
	{
		func(value);
	}
}
int main()
{
	std::vector<int> values = { 1, 2, 3, 4, 5 };
	Foreach(values, [](int value)
		{
			std::cout << value << std::endl;
		});
}
```

## [capture]
capture说明如何传递变量
- =:通过值传递，传递所有变量
- &:通过引用传递，传递所有变量

**explicit关键字用于禁用隐式构造函数转换**
```c++
class Player
{
private:
    int m_age;
public:
    Player()
        : m_age(0){}\
    Player(const int& age)
        : m_age(age)
    explicit Player(const int& age)
        : m_age(age)
}

Player player = 22; //int隐式转换为构造函数
Player player = Player(22); 
Player player(22);//在构造函数前加上explicit之后禁用从其他类型转换为构造函数,需要显示调用。

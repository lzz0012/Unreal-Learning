# Enum
Enum是一种给值命名的方式，使用特殊的命名来替代使用整数来表示特定的状态或数值。
```c++
class Log
{
    enum Level
    {
        ERROR = 0, WARNING, INFO
    }
}
```

> [!NOTE]
> 在类内部定义枚举类型Level
> ERROR,WARNING,INFO是这个枚举的枚举常量
> Log::ERROR通过类作用域访问到枚举常量，枚举常量在Log类命名空间中，而枚举类型Level本身不是一个命名空间

```c++
class Log
{
public:
    enum Level
    {
        ERROR = 0, WARNING, INFO
    }
private:
    Level m_LogLevel = INOF;
public:
    void SetLogLevel(Level level)
    {
        m_LogLevel = level;
    }

    void Error(const char* message)
    {
        if(m_LogLevel >= ERROR)
            std::cout << "[ERROR]: " << message << std::endl;
    }

    void Warn(const char* message)
    {
        if(m_LogLevel >= WARNING)
            std::cout << "[WARNING]: " << message << std::endl;
    }

    void Info(const char* message)
    {
        if(m_LogLevel >= INFO)
            std::cout << "[INFO]: " << message << std::endl;
    }
};
```
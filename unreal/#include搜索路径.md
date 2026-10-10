- 当前文件所在目录
    - 这是 C++ 编译器的标准行为。对于 #include "MyFile.h" 这种引号形式，编译器会首先在包含该 #include 指令的源文件所在目录中查找。

- UBT 自动添加的默认路径
    - 模块的 Public 目录：这是最重要的自动路径。UBT 会自动将模块的 Public 目录加入搜索列表。因此，其他模块可以通过 #include "MyHeader.h" 直接包含该模块 Public 目录下的文件。

    - 模块的 Private 目录：通常不被自动添加，除非模块的 Build.cs 中有特殊配置。

    - 引擎核心目录：如 Core、Engine 等模块的 Public 目录，会通过模块依赖自动加入。

- 在 Build.cs 中手动添加的路径
    - 你在 Build.cs 中通过 PublicIncludePaths 和 PrivateIncludePaths 添加的路径，会追加到搜索列表中。添加的顺序会影响搜索优先级：如果多个目录中存在同名头文件，编译器会使用列表中靠前的那个。
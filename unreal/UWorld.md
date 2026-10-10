# UWorld
从引擎的层级结构来看，UGameInstance 下面会管理一个 UWorld，而 UWorld 下面则包含着多个 ULevel（关卡）以及这些关卡里的所有 AActor

核心作用与功能
- Actor 的创建与管理：在运行时动态生成（Spawn）Actor 时，需要通过 UWorld 来完成，例如 SpawnActor 函数。UWorld 才是这些 Actor 真正的拥有者。

- 提供运行时时间信息：UWorld 中保存着 DeltaTimeSeconds（当前帧的时间增量）、TimeSeconds、AudioTimeSeconds 等关键的时间数据，供游戏逻辑使用。

- 管理底层系统：它持有对物理场景（PhysicsScene_Chaos）、渲染场景（Scene）、网络驱动（NetDriver）等底层核心系统的引用，负责协调它们的工作。

- 作为全局访问入口：通过 GetWorld() 方法（在 AActor、UActorComponent 等类中很常见），可以方便地获取到当前对象所属的 UWorld，进而访问其他 Actor 或系统。
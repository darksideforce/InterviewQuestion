- 1：nodejs的事件循环机制
	- 整个循环分为6个机制：
		1. **Timers（定时器阶段）**：执行 `setTimeout` 和 `setInterval` 到期的回调函数。
		2. **Pending callbacks（待定回调阶段）**：执行某些系统级操作（如 TCP 错误）延迟派发的回调。
		3. **Idle, prepare（空闲阶段）**：仅供 Node.js 内部使用。
		4. **Poll（轮询阶段）**：**核心阶段**。阻塞等待新的 I/O 事件（如文件读写、网络请求），并执行对应的 I/O 回调。
		5. **Check（检查阶段）**：专门执行 `setImmediate()` 的回调。
		6. **Close callbacks（关闭回调阶段）**：执行资源关闭事件，如 `socket.on('close')`
	- 而每次循环的时候都算一个宏任务，每次回调触发时都会立马清空一次微任务
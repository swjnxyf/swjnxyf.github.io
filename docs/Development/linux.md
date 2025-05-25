# 一些linux命令

#### screen(linux复用窗口)

```bash
# 1. 创建新会话（启动并进入）
screen -S <会话名>  # 示例：screen -S baidupan_sync

# 2. 列出所有活动会话
screen -ls  

# 3. 恢复（连接）已有会话
screen -r <会话名或会话ID>  # 示例：screen -r baidupan_sync 或 screen -r 12345

# 4. 强制恢复会话（断开其他连接）
screen -r -d <会话名或ID>  # 示例：screen -r -d baidupan_sync

# 5. 将会话放入后台（不终止任务）
# 说明：在会话内通过快捷键将会话 detach（分离）到后台运行，返回原终端
# 操作：先按 Ctrl + a（松开后），再按 d（组合键分两步执行，非同时按下）
# 示例操作（会话内执行）：
# Ctrl + a（松开） + d  # 后台保留会话，回到原终端界面


# 6. 终止（删除）指定会话
# 说明：强制退出并删除一个 Screen 会话（会话内的任务会被终止，操作不可逆）
# 用途：清理不再需要的后台会话（如 bypy 任务已完成或需强制终止）
screen -X -S <会话名或ID> quit  # 示例：screen -X -S baidupan_sync quit
```

#### bypy(百度网盘)

```bash
# 说明：初始化配置（首次登录认证）
# 触发认证流程（按提示完成百度账号登录）
bypy quota

# 说明：列出远程目录文件
# 列出网盘根目录下的文件（按名称升序）
bypy list / --sort name --order asc

# 说明：上传本地文件/目录到网盘
#上传单个文件
bypy upload "D:\docs\report.pdf" "我的文件夹/report.pdf"
#上传整个文件夹
bypy upload -r "D:\projects\2024" "项目备份/2024"

# 说明：下载网盘文件/目录到本地
#下载单个文件
bypy download "我的文件夹/report.pdf" "D:\downloads\report.pdf"
#下载整个文件夹（关键：递归参数 -r）
bypy download -r "项目备份/2024" "D:\backup\2024"

# 说明：双向同步目录（网盘→本地）
bypy syncdown /Backup ~/Backup --deletelocal True

# 说明：创建远程目录
bypy mkdir /2024_Archive

# 说明：删除远程文件/目录
bypy delete /old_logs.zip
```


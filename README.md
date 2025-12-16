# How to push to github

git remote add origin git@github.com:joycgj/nacosDemo.git
git branch -M main
git push -u origin main

这两条命令分别是重命名分支和推送分支，解释如下：

## 1. `git branch -M main`
- **`-M` 选项**：强制重命名分支，即使目标分支名已存在也会被覆盖
  - 大写 `-M` 表示强制移动（相当于 `--move --force`）
  - 小写 `-m` 是普通移动，如果目标分支存在会报错
- **作用**：将当前分支重命名为 `main`
- **背景**：GitHub 在 2020 年将默认分支从 `master` 改为 `main`，此命令常用于迁移

## 2. `git push -u origin main`
- **`-u` 选项**：设置上游分支（upstream）
  - 全写是 `--set-upstream`
- **作用**：
  1. 将本地 `main` 分支推送到远程仓库 `origin`
  2. 建立跟踪关系，后续只需 `git push` 或 `git pull` 即可，无需指定远程分支
- **等价于**：先 `git push origin main`，再 `git branch --set-upstream-to=origin/main main`

## 使用场景示例：
```bash
# 从旧分支名迁移到新分支名
git branch -M main           # 重命名当前分支为 main
git push -u origin main      # 首次推送到远程并建立跟踪

# 后续操作简化
git push                    # 自动推送到 origin/main
git pull                    # 自动从 origin/main 拉取
```

## 注意事项：
- `-M` 是**危险操作**，会覆盖已存在的 `main` 分支
- 如果团队协作，重命名前需确保其他成员知晓
- 首次推送新分支时使用 `-u` 可以简化后续操作

# How to lunch a Nacos service

```
docker run --name nacos \
  -e MODE=standalone \
  -p 8849:8848 \
  nacos/nacos-server:v2.1.0
```

http://localhost:8849/nacos




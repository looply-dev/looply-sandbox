# looply-sandbox

本仓库用于在真实 GitHub 环境中验证 Looply 的 PR 相关功能，不包含 Looply 的产品代码，也不部署任何服务。

## 为什么需要这个仓库

Looply 的正式仓库 `looply-dev/looply-platform` 是私有仓库。组织当前使用 GitHub 免费版，私有仓库不能开启分支保护或规则集。有些 PR 状态只在分支保护生效时才会出现，例如 GitHub 要求「合并前分支必须是最新的」时，落后于目标分支的 PR 才会报告 `mergeStateStatus: BEHIND`。公开仓库在免费版上也可以开启分支保护，所以用这个仓库来制造并验证这类状态。

## 当前用途

- 验证「更新分支」（Linear MUK-32，vault DEC-086 的 P1）：`main` 要求 `check` 检查通过，并要求合并前分支是最新的。PR 落后于 `main` 时，Looply 应显示「更新分支」，并以成员本人身份调用 GitHub update-branch。
- 后续也可用于验证合并冲突的处理（DEC-086 的 P2）。

## 约定

- 只放测试用的文件和测试 PR，不要提交真实代码、凭据或任何私有信息。本仓库是公开的。
- 测试 PR 的标题以 `test:` 开头，测试结束后关闭或合并。
- `.github/workflows/check.yml` 提供一个总是通过的检查，供分支保护引用。

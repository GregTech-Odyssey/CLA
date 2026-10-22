# GregTech Odyssey CLA

本仓库存放 GregTech Odyssey 贡献者许可协议（CLA）的正文、签名记录，以及各仓库共用的 CLA 机器人工作流。

- 协议正文：[CLA.md](CLA.md)，适用于 GregTech-Odyssey 组织下的所有仓库。
- 签名记录：`signatures/version1/cla.json`，由机器人维护，请勿手动修改。
- 共用工作流：`.github/workflows/cla.yml`。免签名单与提示文案只在这里修改。

## 如何签署

首次向 GregTech Odyssey 的任一仓库提交 Pull Request 时，机器人会在 PR 中留言。按提示评论下面这句话即完成签署，之后对所有仓库有效：

```
I have read the CLA Document and I hereby sign the CLA
```

评论 `recheck` 可让机器人重新检查。

## 接入新仓库

在仓库中新建 `.github/workflows/cla.yml`：

```yaml
name: "CLA Assistant"
on:
  issue_comment:
    types: [created]
  pull_request_target:
    types: [opened, closed, synchronize]

permissions:
  actions: write
  contents: read
  pull-requests: write
  statuses: write

jobs:
  cla:
    uses: GregTech-Odyssey/CLA/.github/workflows/cla.yml@main
    secrets: inherit
```

并在组织密钥 `CLA_SIGNATURES_TOKEN` 的可用仓库中加入该仓库。该密钥是只对本仓库有内容读写权限的细粒度令牌，用于写入签名记录。

---

This repository holds the GregTech Odyssey [Contributor License Agreement](CLA.md), its signatures, and the CLA bot workflow shared by all repositories. On your first pull request to any GregTech Odyssey repository, the bot asks you to sign by commenting `I have read the CLA Document and I hereby sign the CLA`; signing once covers every repository.

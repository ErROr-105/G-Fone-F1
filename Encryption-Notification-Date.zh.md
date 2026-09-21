# Encryption Notification Date

项目提及以下加密技术：

- AES-256-GCM
- ChaCha20-Poly1305
- X25519

所有列出的算法均为**标准算法**（已在 RFC 中发布 / 被国际标准采纳）。

## EAR 状态下的说明（2021 年变更后）

根据 15 CFR § 742.15(b)，只有实现**非标准密码学**的公开可用加密源代码才需要向 BIS 和 NSA 通知。

由于仅使用标准算法，根据 License Exception TSU / § 742.15(b) 的正式通知**不是必需的**。

---

### 如果未来出现非标准密码学

必须在发布源代码**之前**发送通知：

- **收件人：** crypt@bis.doc.gov 和 enc@nsa.gov
- **主题：** Section 742.15 NOTIFICATION - Encryption / TSU NOTIFICATION
- **内容：** 仓库 URL + 简要说明

- **发送日期：** [日期]
- **邮件链接/副本：** [插入]
- **许可例外/条款：** 15 CFR § 742.15(b)（原 TSU 740.13(e)）

*仅在存在非标准密码学且在代码公开发布前填写。*

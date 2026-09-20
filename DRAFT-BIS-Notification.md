# Черновик уведомления в BIS / NSA

**Важно:**  
По состоянию на 2021+ год уведомление требуется **только** при использовании non-standard cryptography.  
AES / ChaCha20 / X25519 — стандартные, поэтому отправлять это письмо **не обязательно**.

Ниже шаблон на случай, если позже появится нестандартная криптография или ты решишь перестраховаться.

---

### Тема письма:
```
Section 742.15 NOTIFICATION - Encryption Source Code
```

или старый вариант:

```
TSU NOTIFICATION
```

### Кому:
```
crypt@bis.doc.gov
enc@nsa.gov
```

### Тело письма (шаблон):

```
SUBMISSION TYPE: Section 742.15 / TSU
SUBMITTED BY: [Твоё имя или ник]
SUBMITTED FOR: ErROr_105Unknown / G-Fone F1 project
POINT OF CONTACT: [твой email]
PHONE: [по желанию]

PRODUCT NAME/MODEL #: G-Fone F1 (privacy-focused smartphone concept / related software)
ECCN: 5D002

NOTIFICATION:
The encryption source code (or description of cryptographic functionality) is / will be made publicly available at the following Internet location:

https://github.com/[ТВОЙ_ЮЗЕРНЕЙМ]/G-Fone-F1

Cryptographic algorithms used (standard):
- AES-256-GCM
- ChaCha20-Poly1305
- X25519

This notification is provided pursuant to 15 CFR § 742.15(b) / License Exception TSU (EAR 740.13(e)).

[Если нужно — приложить архив с исходниками или просто указать URL]
```

---

### Когда отправлять:
- **До** того, как сделаешь репозиторий публичным (если уведомление вообще нужно).
- При смене URL репозитория.
- При добавлении нестандартных алгоритмов.

### Рекомендация:
Пока проект — только концепт + документация и использует стандартные алгоритмы, можно спокойно держать репозиторий приватным и **не отправлять** ничего.  
Когда появится реальный код и ты решишь открыть его — перепроверь актуальные правила на bis.doc.gov.

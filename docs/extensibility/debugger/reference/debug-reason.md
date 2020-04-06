---
title: DEBUG_REASON | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59954ea7e89390a5e35dbe0bfb0412da1aabc80f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737422"
---
# <a name="debug_reason"></a>DEBUG_REASON
Określa, dlaczego proces został uruchomiony do debugowania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Pola
`DEBUG_REASON_ERROR`\
Wystąpił błąd niespecyficznych (jest używany jako warunek domyślny, gdy żaden z innych powodów nie pasuje).

`DEBUG_REASON_USER_LAUNCHED`\
Proces został uruchomiony na żądanie użytkownika.

`DEBUG_REASON_USER_ATTACHED`\
Już uruchomiony proces został dołączony przez użytkownika.

`DEBUG_REASON_AUTO_ATTACHED`\
Proces został automatycznie dołączony do momentu jego uruchomienia.

`DEBUG_REASON_CAUSALITY`\
Proces został uruchomiony z powodu zdarzenia debugowania *Just-In-Time* (JIT).

## <a name="remarks"></a>Uwagi
Zwrócono z [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

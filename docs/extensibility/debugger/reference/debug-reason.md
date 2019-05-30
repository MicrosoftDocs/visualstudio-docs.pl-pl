---
title: DEBUG_REASON | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0502ab10398d37bcafee5316ba7e7566dbab4e01
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346166"
---
# <a name="debugreason"></a>DEBUG_REASON
Określa, dlaczego ten proces został uruchomiony dla debugowania.

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
Wystąpił błąd nieokreślonym (są one używane jako domyślne warunku, gdy żaden z innych powodów, dla których Dopasuj).

`DEBUG_REASON_USER_LAUNCHED`\
Proces został uruchomiony na żądanie użytkownika.

`DEBUG_REASON_USER_ATTACHED`\
Proces działa już został dołączony do przez użytkownika.

`DEBUG_REASON_AUTO_ATTACHED`\
Proces został dołączony do automatycznie, podczas jej uruchamiania.

`DEBUG_REASON_CAUSALITY`\
Proces został uruchomiony ze względu na *Just-In-Time* zdarzenia debugowania (JIT).

## <a name="remarks"></a>Uwagi
Zwrócone w wyniku [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

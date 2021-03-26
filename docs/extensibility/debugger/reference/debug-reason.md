---
description: Określa, dlaczego proces został uruchomiony na potrzeby debugowania.
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db5d6697f222015cc4f6dbedbc6258e00c9b285f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096255"
---
# <a name="debug_reason"></a>DEBUG_REASON
Określa, dlaczego proces został uruchomiony na potrzeby debugowania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Pola
`DEBUG_REASON_ERROR`\
Wystąpił błąd nieokreślony (jest używany jako warunek domyślny, gdy żadna z innych przyczyn nie jest zgodna).

`DEBUG_REASON_USER_LAUNCHED`\
Proces został uruchomiony na żądanie użytkownika.

`DEBUG_REASON_USER_ATTACHED`\
Użytkownik załączył już uruchomiony proces.

`DEBUG_REASON_AUTO_ATTACHED`\
Proces został automatycznie dołączony do momentu jego uruchomienia.

`DEBUG_REASON_CAUSALITY`\
Proces został uruchomiony z powodu zdarzenia debugowania *just-in-Time* (JIT).

## <a name="remarks"></a>Uwagi
Zwrócone z metody [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

---
title: DEBUG_REASON | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0091924c5c117eb8953b5dd3fc70b5cdf446761
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318605"
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

#### <a name="parameters"></a>Parametry
DEBUG_REASON_ERROR  
Wystąpił błąd nieokreślonym (są one używane jako domyślne warunku, gdy żaden z innych powodów, dla których Dopasuj).

DEBUG_REASON_USER_LAUNCHED  
Proces został uruchomiony na żądanie użytkownika.

DEBUG_REASON_USER_ATTACHED  
Proces działa już został dołączony do przez użytkownika.

DEBUG_REASON_AUTO_ATTACHED  
Proces został dołączony do automatycznie, podczas jej uruchamiania.

DEBUG_REASON_CAUSALITY  
Proces został uruchomiony ze względu na *Just-In-Time* zdarzenia debugowania (JIT).

## <a name="remarks"></a>Uwagi
Zwrócone w wyniku [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

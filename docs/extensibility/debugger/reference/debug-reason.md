---
title: DEBUG_REASON | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 03b2db1fd58af6a8b2f8a57846e7753cdbc82352
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877916"
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
Wystąpił błąd nieokreślonym DEBUG_REASON_ERROR A (są one używane jako domyślne warunku, gdy żaden z innych powodów, dla których Dopasuj).

DEBUG_REASON_USER_LAUNCHED proces został uruchomiony na żądanie użytkownika.

DEBUG_REASON_USER_ATTACHED proces działa już został dołączony do przez użytkownika.

DEBUG_REASON_AUTO_ATTACHED proces automatycznie został dołączony do podczas jej uruchamiania.

Proces został uruchomiony ze względu na DEBUG_REASON_CAUSALITY *Just-In-Time* zdarzenia debugowania (JIT).

## <a name="remarks"></a>Uwagi
Zwrócone w wyniku [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

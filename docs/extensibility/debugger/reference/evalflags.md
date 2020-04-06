---
title: EVALFLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4136726e5c8b798121dbd38975d8f2bb935ed04a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737108"
---
# <a name="evalflags"></a>EVALFLAGS
Określa flagi, które kontrolują ocenę wyrażenia.

## <a name="syntax"></a>Składnia

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Pola
`EVAL_RETURNVALUE`\
Określa, że wartość zwracana, jeśli istnieje, być oceniane.

`EVAL_NOSIDEEFFECTS`\
Określa, że działania niepożądane nie są dozwolone.

`EVAL_ALLOWBPS`\
Określa zatrzymywanie punktów przerwania.

`EVAL_ALLOWERRORREPORT`\
Określa raportowanie błędów do hosta, który ma być dozwolony. Używany głównie do oceny wyrażenia w skrypcie w programie Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Wymusza funkcje, które mają być oceniane jako adresy, zamiast wywoływania funkcji.

`EVAL_NOFUNCEVAL`\
Zapobiega ocenie funkcji. Rozważmy na `int` przykład token `myExpression(int) + 10`w wyrażeniu . Ta funkcja może być poprawnie oceniona jako adres, ale nie jako wartość.

`EVAL_NOEVENTS`\
Flaga, aby wskazać, że zdarzenia, które występują podczas oceny wyrażenia nie powinny być wysyłane do menedżera debugowania sesji (SDM) lub ide.

## <a name="remarks"></a>Uwagi
Flagi te są przekazywane jako argument do [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) i [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metody.

Flagi te mogą być łączone z bitowym OR.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

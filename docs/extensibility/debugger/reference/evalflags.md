---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f780f06188d738deeb7f4b781fba1313e46db6d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315771"
---
# <a name="evalflags"></a>EVALFLAGS
Określa flagi, które kontrolują Obliczanie wyrażenia.

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

## <a name="members"></a>Elementy członkowskie
EVAL_RETURNVALUE  
Określa, że wartość zwracana, jeśli istnieje, można obliczyć.

EVAL_NOSIDEEFFECTS  
Określa, że efekty uboczne niemożliwe.

EVAL_ALLOWBPS  
Określa zatrzymywanie punktów przerwania.

EVAL_ALLOWERRORREPORT  
Określa raportów o błędach do hosta mają być dozwolone. Używane głównie do obliczenia wyrażenia w skrypcie w programie Internet Explorer.

EVAL_FUNCTION_AS_ADDRESS  
Funkcje wymusza, aby zostały uznane za adresów, zamiast wywoływania funkcji.

EVAL_NOFUNCEVAL  
Funkcja zapobiega oceniane. Na przykład, rozważmy `int` tokenu w wyrażeniu `myExpression(int) + 10`. Ta funkcja może być poprawnie określona jako adres, ale nie jako wartość.

EVAL_NOEVENTS  
Flaga wskazująca, że zdarzenia, które wystąpiły podczas obliczania wyrażenia nie powinny być wysyłane, Menedżer debugowania sesji (SDM) lub środowiska IDE.

## <a name="remarks"></a>Uwagi
Te flagi są przekazywane jako argument do [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) i [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metody.

Te flagi mogą być łączone z bitowe OR.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)  
[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

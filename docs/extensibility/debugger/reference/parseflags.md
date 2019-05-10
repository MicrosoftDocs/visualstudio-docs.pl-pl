---
title: PARSEFLAGS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5d298add846a7f3b7baf566f3c31e16c68b8dc5
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460845"
---
# <a name="parseflags"></a>PARSEFLAGS
Określa, jak można przeanalizować wyrażenia.

## <a name="syntax"></a>Składnia

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Pola
 `PARSE_EXPRESSION`\
 Wskazuje, czy wyrażenie nie jest instrukcja.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Wskazuje, czy wyrażenie jest analizowany (i później oceniane) jako adres.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Wskazuje, czy wyrażenie jest analizowana w czasie projektowania (oznacza to, gdy projektant jest otwarty).

## <a name="remarks"></a>Uwagi
 Przekazany jako parametr do [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) metody.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
---
title: PARSEFLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cc70fdd9fe1279e4d419a422b970eb3d3b07c65
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714116"
---
# <a name="parseflags"></a>PARSEFLAGS
Określa sposób analizować wyrażenie.

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
 Wskazuje, że wyrażenie nie jest instrukcją.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Wskazuje, że wyrażenie ma być analizowane (a później oceniane) jako adres.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Wskazuje, że wyrażenie jest analizowane w czasie projektowania (czyli gdy projektant jest otwarty).

## <a name="remarks"></a>Uwagi
 Przekazywane jako parametr do [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i [Analizowania](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) metody.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

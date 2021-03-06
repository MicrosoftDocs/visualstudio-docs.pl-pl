---
description: Określa sposób analizowania wyrażenia.
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 192e4de399540ce189bbf52cbb0f615b2b9bc855
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222149"
---
# <a name="parseflags"></a>PARSEFLAGS
Określa sposób analizowania wyrażenia.

## <a name="syntax"></a>Składnia

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Pola
 `PARSE_EXPRESSION`\
 Wskazuje, że wyrażenie nie jest instrukcją.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Wskazuje, że wyrażenie ma być analizowane (i później oceniane) jako adres.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Wskazuje, że wyrażenie jest analizowane w czasie projektowania (to oznacza, gdy Projektant jest otwarty).

## <a name="remarks"></a>Uwagi
 Przekazanie jako parametr do metody [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Analizuj](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

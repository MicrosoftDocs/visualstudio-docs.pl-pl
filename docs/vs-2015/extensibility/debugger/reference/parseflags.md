---
title: PARSEFLAGS | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a9ebe244f3e1c1f3f95508d6df979edee2d4aed
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790819"
---
# <a name="parseflags"></a>PARSEFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, jak można przeanalizować wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
## <a name="members"></a>Elementy członkowskie  
 PARSE_EXPRESSION  
 Wskazuje, czy wyrażenie nie jest instrukcja.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Wskazuje, czy wyrażenie jest analizowany (i później oceniane) jako adres.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Wskazuje, czy wyrażenie jest analizowana w czasie projektowania (oznacza to, gdy projektant jest otwarty).  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako parametr do [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

---
title: STEPUNIT | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0b7395b487fdcc789c99113014f4693bc6bb899
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945002"
---
# <a name="stepunit"></a>STEPUNIT
Określa jednostki kroku przechodzenie krok po kroku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```csharp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 STEP_STATEMENT  
 Przeprowadza użytkownika przez instrukcję.  
  
 STEP_LINE  
 Kroki po wierszu.  
  
 STEP_INSTRUCTION  
 Przeprowadza użytkownika przez instrukcję.  
  
## <a name="remarks"></a>Uwagi  
 Przekazywany jako argument do [kroku](../../../extensibility/debugger/reference/idebugprocess3-step.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
---
title: STEPUNIT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff04acfc408454d20013c46247525f9374d42764
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782495"
---
# <a name="stepunit"></a>STEPUNIT
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa jednostki kroku przechodzenie krok po kroku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)


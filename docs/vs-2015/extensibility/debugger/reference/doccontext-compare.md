---
title: DOCCONTEXT_COMPARE | Dokumentacja firmy Microsoft
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
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0598fd3848623bdbef39f0c1cfec145399fbdc04
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758174"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa kryteria do porównywania dwóch kontekstów dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DOCCONTEXT_EQUAL  
 Znajdź pierwszy kontekstu dokumentu na liście, która jest równa docelowej kontekstu dokumentu.  
  
 DOCCONTEXT_LESS_THAN  
 Znajdź pierwszy kontekstu dokumentu na liście, która jest mniejsza niż docelowy kontekstu dokumentu.  
  
 DOCCONTEXT_GREATER_THAN  
 Znajdź pierwszy kontekstu dokumentu na liście, która jest większa niż docelowy kontekstu dokumentu.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Znajdź pierwszy kontekstu dokumentu na liście znajduje się w tym samym dokumencie co kontekstu dokumentu docelowego.  
  
## <a name="remarks"></a>Uwagi  
 Przekazywany jako argument do [porównania](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) metody.  
  
 Te wartości są używane do określenia kryteria porównania na potrzeby znajdowania pierwszy kontekstu dokumentu na liście. Kontekstu dokumentu znajduje się lista kontekstów dokumentu do porównania sam względem za pośrednictwem `IDebugDocumentContext2::Compare` metody. Pierwszy kontekstu dokumentu na liście, dla którego operator porównania jest `true` jest zwracana.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)


---
title: IDebugDocument2 | Dokumentacja firmy Microsoft
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
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0b430f0a6022181a45c82fcb0db67fb0c9742e9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761095"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje dokumentu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zwykle implementuje ten interfejs. Aparat debugowania (DE) mogą także implementować ten interfejs, gdy należy ją podać kod źródłowy i źródła nie istnieje na dysku.  W takich przypadkach DE będzie także implementować [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) i [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) interfejsów, a także niektórych dodatkowych metod na [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) i [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) interfejsów.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Metody na `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, i `IDebugActivateDocumentEvent2` interfejsów zwraca ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugDocument2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Pobiera nazwę dokumentu w jednym z wielu formularzy.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Pobiera identyfikator klasy dokumentu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest implementowany tylko wtedy, gdy DE dostarcza kod źródłowy. Na przykład podczas debugowania skryptu na stronie HTML DE dostarcza kod źródłowy, ponieważ źródło pobraniem lub generowany dynamicznie i nie istnieje jako plik z dysku. Podczas debugowania tradycyjnych językach, takich jak C++, ten interfejs nie musi być implementowane.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [Getdocument —](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [Getdocument —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [Getdocument —](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)


---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cd6afb417de4d8a362916f91593d0d0e67d307c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156497"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje dokument źródłowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zazwyczaj implementuje ten interfejs. Aparat debugowania (DE) może również zaimplementować ten interfejs, gdy musi dostarczyć kod źródłowy, a źródło nie istnieje na dysku.  W takich przypadkach DE również implementuje interfejsy [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) i [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) , a także kilka dodatkowych metod interfejsów [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) i [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) .  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Metody dla `IDebugDocumentContext2` , `IDebugDisassemblyStream2` , i interfejsu `IDebugDocumentPosition2` `IDebugActivateDocumentEvent2` zwracają ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugDocument2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Pobiera nazwę dokumentu w jednym z kilku formularzy.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Pobiera identyfikator klasy dokumentu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest implementowany tylko wtedy, gdy zawiera kod źródłowy. Na przykład podczas debugowania skryptu na stronie HTML program zawiera kod źródłowy, ponieważ źródło jest pobierane lub generowane dynamicznie i nie istnieje jako plik dysku. W przypadku debugowania tradycyjnych języków, takich jak C++, ten interfejs nie musi być zaimplementowany.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument —](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument —](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

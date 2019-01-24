---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dca9d3c8de956faf2dab5c9090c9963a7c9fbea0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779420"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs jest używany do powiadamiania programu Visual Studio dotyczące zmian w dokumencie źródłowym, które są dostarczane przez aparat debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs do obsługi wprowadzania zmian w kodzie źródłowym. Ten interfejs jest zwykle implementowany w ten sam obiekt, który implementuje [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Ten interfejs, za pomocą wywołania uzyskuje <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metody. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Interfejsu są uzyskiwane z wywołania <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> metody. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Interfejsu można uzyskać przez wywołanie [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) metody [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugDocumentTextEvents2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Wskazuje, że cały dokument został zniszczony.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Powiadamia pakietu debugowania, że włożono tekstu do dokumentu.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Powiadamia pakietu debugowania, czy tekst został usunięty z dokumentu.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Powiadamia pakietu debugowania, czy tekst został zastąpiony w dokumencie.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Powiadamia pakietu debugowania, atrybuty zostały zaktualizowane w dokumencie.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Powiadamia użytkownika, Odbiorca zdarzenia zaktualizowano atrybuty dokumentu.|  
  
## <a name="remarks"></a>Uwagi  
 Tylko silniki debugowania, zapewniających swoich własnych dokumentów będzie korzystać z zalet `IDebugDocumentTextEvent2` interfejsu. Na przykład będzie skryptów aparatu debugowania. W trakcie interpretowanie skryptów, nowy kod źródłowy można wygenerować nie znajduje się w dowolnym pliku dysku, który jest znany tylko DE.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

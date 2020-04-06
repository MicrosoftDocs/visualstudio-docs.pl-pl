---
title: IDebugDocumentTextEvents2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731366"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Ten interfejs jest używany do powiadamiania programu Visual Studio o zmianach w dokumencie źródłowym, które są dostarczane przez aparat debugowania.

## <a name="syntax"></a>Składnia

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 De implementuje ten interfejs do obsługi wprowadzania zmian w kodzie źródłowym. Ten interfejs jest zazwyczaj implementowane na tym samym obiekcie, który implementuje interfejs [IDebugDocument2.](../../../extensibility/debugger/reference/idebugdocument2.md)

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]uzyskuje ten interfejs za pośrednictwem <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> wywołania metody. Interfejs <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> jest uzyskiwany <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> z wywołania metody. Interfejs <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> jest uzyskiwany przez wywołanie [QueryInterface](/cpp/atl/queryinterface) metody na [interfejsie IDebugDocument2.](../../../extensibility/debugger/reference/idebugdocument2.md)

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugDocumentTextEvents2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Wskazuje, że cały dokument został zniszczony.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Powiadamia pakiet debugowania, że tekst został wstawiony do dokumentu.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Powiadamia pakiet debugowania, że tekst został usunięty z dokumentu.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Powiadamia pakiet debugowania, że tekst został zastąpiony w dokumencie.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Powiadamia pakiet debugowania, że atrybuty tekstu zostały zaktualizowane w dokumencie.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Powiadamia odbiorcę zdarzenia, że atrybuty dokumentu zostały zaktualizowane.|

## <a name="remarks"></a>Uwagi
 Tylko aparaty debugowania, które dostarczają `IDebugDocumentTextEvent2` własne dokumenty będzie korzystać z interfejsu. Przykładem tego może być aparat debugowania skryptów. W procesie interpretacji skryptów można wygenerować nowy kod źródłowy, który nie jest obecny w żadnym pliku dysku i jest znany tylko de.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

---
title: IDebugDocumentTextEvents2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731366"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Ten interfejs jest używany do powiadamiania programu Visual Studio o zmianach w dokumencie źródłowym dostarczanym przez aparat debugowania.

## <a name="syntax"></a>Składnia

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs, aby obsługiwać wprowadzanie zmian w kodzie źródłowym. Ten interfejs jest zwykle implementowany dla tego samego obiektu, który implementuje interfejs [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uzyskuje ten interfejs za pomocą wywołania <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metody. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>Interfejs jest uzyskiwany z wywołania <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> metody. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>Interfejs jest uzyskiwany przez wywołanie metody [QueryInterface](/cpp/atl/queryinterface) w interfejsie [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugDocumentTextEvents2` .

|Metoda|Opis|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Wskazuje, że cały dokument został zniszczony.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Powiadamia pakiet debugowania, że tekst został wstawiony do dokumentu.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Powiadamia pakiet debugowania, że tekst został usunięty z dokumentu.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Powiadamia pakiet debugowania o zastąpieniu tekstu w dokumencie.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Powiadamia pakiet debugowania o zaktualizowaniu atrybutów tekstu w dokumencie.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Powiadamia odbiorcę o zdarzeniu, że atrybuty dokumentu zostały zaktualizowane.|

## <a name="remarks"></a>Uwagi
 Tylko aparaty debugowania, które dostarczają własne dokumenty, wykorzystują `IDebugDocumentTextEvent2` interfejs. Przykładem jest aparat debugowania skryptów. W procesie interpretacji skryptów można wygenerować nowy kod źródłowy, który nie jest obecny w żadnym pliku dysku i jest znany tylko jako DE.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

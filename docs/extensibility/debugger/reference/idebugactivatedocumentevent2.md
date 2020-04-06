---
title: IDebugActivateDocumentEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f601027ce9e71dff6687bcd6aa1b08f13f5ce0cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736617"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Aparat debugowania (DE) używa tego interfejsu, aby zażądać dokumentu do załadowania.

## <a name="syntax"></a>Składnia

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 De implementuje ten interfejs, gdy potrzebuje pliku źródłowego do otwarcia. Ten interfejs jest implementowany tylko przez aparaty debugowania, które współpracują z interpreterami skryptów lub są ich częścią. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten `IDebugEvent2` interfejs (SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła ten obiekt zdarzenia, gdy musi mieć otwarty plik źródłowy. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez SDM po podłączeniu do programu, który jest debugowany.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugActivateDocumentEvent2`przedstawiono metody .

|Metody|Opis|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Pobiera dokument do aktywacji.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Pobiera kontekst dokumentu, który opisuje położenie w dokumencie.|

## <a name="remarks"></a>Uwagi
 Typowy scenariusz, w którym ten interfejs jest używany jest, jeśli błąd analizy występuje w kodzie skryptu na stronie HTML, skrypt DE wysyła ten interfejs do SDM, tak aby dokument z błędem analizy mogą być wyświetlane.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

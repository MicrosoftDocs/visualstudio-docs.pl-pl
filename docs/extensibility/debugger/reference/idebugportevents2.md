---
title: IDebugPortEvents2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725174"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Ten interfejs powiadamia odbiornika (zazwyczaj menedżera debugowania sesji [SDM] lub aparat debugowania) procesu i programu tworzenia i niszczenia na określonym porcie. Te informacje mogą służyć do prezentacji widoku w czasie rzeczywistym procesów i programów uruchomionych na porcie.

## <a name="syntax"></a>Składnia

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Visual Studio zazwyczaj implementuje ten interfejs do odbierania powiadomień o tworzeniu i niszczeniu programu. Aparat debugowania można również zaimplementować ten interfejs, aby nasłuchiwać takich zdarzeń portu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wszystkie interfejsy [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) można zbadać <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> dla interfejsu. Następnie <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metoda `IDebugPortEvents2` dla jest <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> wywoływana w <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejsie, aby uzyskać interfejs. Na koniec <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metoda w <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejsie jest wywoływana do wysyłania zdarzeń za pośrednictwem [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md) metody.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugPortEvents2`przedstawiono metodę .

|Metoda|Opis|
|------------|-----------------|
|[Wydarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Wysyła zdarzenia, które opisują tworzenie i niszczenie procesów i programów w porcie.|

## <a name="remarks"></a>Uwagi
 `IDebugPortEvents2`jest również używany przez SDM do debugowania programów, które są uruchamiane w procesie, który jest już debugowany.

 Zdarzenia portu są przekazywane do SDM przez ten interfejs.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

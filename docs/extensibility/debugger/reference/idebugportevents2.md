---
description: Ten interfejs powiadamia odbiornik (zazwyczaj Menedżera debugowania sesji [SDM] lub aparat debugowania) o tworzeniu i zniszczeniu procesu i programu na określonym porcie.
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8e1ccbb2726fb0f90fae2d31a4b07daad9bae91
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065388"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Ten interfejs powiadamia odbiornik (zazwyczaj Menedżera debugowania sesji [SDM] lub aparat debugowania) o tworzeniu i zniszczeniu procesu i programu na określonym porcie. Te informacje mogą służyć do prezentowania widoku w czasie rzeczywistym procesów i programów uruchomionych na porcie.

## <a name="syntax"></a>Składnia

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio zwykle implementuje ten interfejs, aby otrzymywać powiadomienia o tworzeniu i zniszczeniu programu. Aparat debugowania może również zaimplementować ten interfejs, aby nasłuchiwać takich zdarzeń portów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wszystkie interfejsy [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) można zbadać dla <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejsu. Następnie <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> Metoda dla `IDebugPortEvents2` jest wywoływana w <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejsie, aby uzyskać <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejs. Na koniec <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> Metoda w <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejsie jest wywoływana w celu wysyłania zdarzeń za pomocą metody [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md) .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metodę `IDebugPortEvents2` .

|Metoda|Opis|
|------------|-----------------|
|[Zdarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Wysyła zdarzenia opisujące tworzenie i niszczenie procesów i programów na porcie.|

## <a name="remarks"></a>Uwagi
 `IDebugPortEvents2` jest również używany przez model SDM do debugowania programów uruchamianych w procesie, który jest już debugowany.

 Zdarzenia portów są przesyłane do modelu SDM przez ten interfejs.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

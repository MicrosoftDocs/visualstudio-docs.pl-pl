---
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c38dc023c44e0c1743fd9d35dbe65befda405f4e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919933"
---
# <a name="idebugengine2"></a>IDebugEngine2
Ten interfejs reprezentuje aparat debugowania (DE). Służy do zarządzania różnymi aspektami sesji debugowania, od tworzenia punktów przerwania do ustawiania i czyszczenia wyjątków.

## <a name="syntax"></a>Składnia

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardową DEZINSTALACJę debugowania programów. Ten interfejs musi być zaimplementowany przez DE.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływany przez Menedżera debugowania sesji (SDM) do zarządzania sesją debugowania, w tym do zarządzania wyjątkami, tworzenia punktów przerwania i reagowania na zdarzenia synchroniczne wysyłane przez DE.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugEngine2` .

|Metoda|Opis|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Tworzy moduł wyliczający dla wszystkich programów, które są debugowane przez DE.|
|[Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Dołącza do programu.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Tworzy oczekujący punkt przerwania w elemencie DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Określa, jak DE powinien obsługiwać dany wyjątek.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Usuwa określony wyjątek, dlatego nie jest już obsługiwany przez aparat debugowania.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Usuwa listę wyjątków ustawionych przez środowisko IDE dla określonej architektury lub języka w czasie wykonywania.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Pobiera identyfikator GUID DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informuje o tym, że określony program został nietypowym zakończony i że DE powinien czyścić wszystkie odwołania do programu i wysyłać zdarzenie zniszczenia programu.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Wywoływane przez model SDM, aby wskazać, że zdarzenie debugowania synchronicznego, wcześniej wysłane przez DE do modelu SDM, zostało odebrane i przetworzone.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Ustawia ustawienia regionalne dla DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Ustawia katalog główny rejestru, który jest aktualnie używany przez DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Ustawia metrykę.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Żądania, które wszystkie programy są debugowane przez to COFNIĘCIe wykonania przy następnym uruchomieniu jednego z ich wątków.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)

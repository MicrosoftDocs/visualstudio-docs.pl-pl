---
description: Ten interfejs umożliwia menedżerowi debugowania sesji Sterowanie programami i procesami działającymi na porcie.
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 54da202e6bbaf08216b921afbde2e39f1da3a788
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142794"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Ten interfejs umożliwia menedżerowi debugowania sesji Sterowanie programami i procesami działającymi na porcie.

## <a name="syntax"></a>Składnia

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Niestandardowy dostawca portu implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Model SDM wywołuje metodę [QueryInterface](/cpp/atl/queryinterface) w `IDebugPort2` interfejsie, aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugPortEx2` .

|Metoda|Opis|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Uruchamia plik wykonywalny.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Wznawia wykonywanie procesu.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Określa, czy proces może być zakończony.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Kończy proces.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Pobiera identyfikator procesu samego portu.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Pobiera program skojarzony z węzłem programu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest zwykle prywatny między modelem SDM i dostawcą portu niestandardowego.

 W razie potrzeby aparat debugowania (DE) może wyszukać ten interfejs w interfejsie [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) przesłanym do [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) i użyć [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) do uruchomienia programu. Nie jest to jednak wymagane, a DE może zrobić, aby uruchomić program żądania.

## <a name="requirements"></a>Wymagania
 Nagłówek: portpriv. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

---
title: IDebugPortEx2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5789681b0da70f46dadac1e29d0d6bb9dc905d1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724996"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Ten interfejs umożliwia menedżerowi debugowania sesji (SDM) sterowanie programami i procesami uruchomionymi na porcie.

## <a name="syntax"></a>Składnia

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca portu niestandardowego implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 SDM wywołuje [QueryInterface](/cpp/atl/queryinterface) `IDebugPort2` w interfejsie, aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugPortEx2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Uruchamia plik wykonywalny.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Wznawia wykonywanie procesu.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Określa, czy proces można zakończyć.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Kończy proces.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Pobiera identyfikator procesu samego portu.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Pobiera program skojarzony z węzłem programu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest zwykle prywatny między modułem SDM a dostawcą portu niestandardowego.

 W razie potrzeby aparat debugowania (DE) może wyszukać ten interfejs w interfejsie [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) przekazany do [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) i użyć [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) do uruchomienia programu. Nie jest to jednak wymagane, a DE może zrobić wszystko, co musi zrobić, aby uruchomić program żądania.

## <a name="requirements"></a>Wymagania
 Nagłówek: portpriv.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

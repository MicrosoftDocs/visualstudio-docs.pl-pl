---
title: IDebugOutputStrejna2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c47a920e99ece3fb0853e4e6a26dba3c8d0c45c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726021"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Ten interfejs jest wysyłany przez aparat debugowania (DE) do menedżera debugowania sesji (SDM) do wysuń ciąg.

## <a name="syntax"></a>Składnia

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs, aby wysłać ciąg do okna **dane wyjściowe** IDE. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten interfejs. Moduł SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła ten obiekt zdarzenia, aby wysłać ciąg do **output** okna. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) która jest dostarczana przez SDM, gdy jest dołączony do programu jest debugowany.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugOutputStringEvent2`przedstawiono metodę .

|Metoda|Opis|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Pobiera wyświetlany komunikat.|

## <a name="remarks"></a>Uwagi
 Na przykład w kodzie niezarządzanym ciąg, który ma być wyjściowy, może pochodzić, `OutputDebugString` gdy program jest debugowany wysyła ciąg do funkcji Win32. Ten ciąg jest przechwytywane przez DE i wysyłane `IDebugOutputStringEvent2` do SDM jako zdarzenie.

 Użyj [IDebugMessageEvent2,](../../../extensibility/debugger/reference/idebugmessageevent2.md) aby wysłać wiadomość, która wymaga odpowiedzi użytkownika.

 Użyj [IDebugErrorEvent2,](../../../extensibility/debugger/reference/idebugerrorevent2.md) aby wysłać komunikat o błędzie, który nie wymaga odpowiedzi.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

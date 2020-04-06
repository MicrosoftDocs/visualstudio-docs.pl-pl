---
title: IDebugCanStopEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734508"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Ten interfejs służy do pytania menedżera debugowania sesji (SDM), czy zatrzymać się w bieżącej lokalizacji kodu.

## <a name="syntax"></a>Składnia

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do obsługi przechodzenia przez kod źródłowy. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten `IDebugEvent2` interfejs (SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do interfejsu).

 Implementacja tego interfejsu musi komunikować wywołanie SDM [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) do aparatu debugowania. Na przykład można to zrobić za pomocą wiadomości opublikowanej w wątku obsługi komunikatów aparatu debugowania lub obiekt implementujący ten interfejs może zawierać `IDebugCanStopEvent2::CanStop`odwołanie do aparatu debugowania i wywołać z powrotem do aparatu debugowania z flagą przekazywana do .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE można wysłać tę metodę za każdym razem, gdy DE jest proszony o kontynuowanie wykonywania i DE jest przechodzenie przez kod. To zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez SDM po podłączeniu do programu, który jest debugowany.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugCanStopEvent2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Pobiera przyczynę tego zdarzenia.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Określa, czy program debugowany powinien zatrzymać się w lokalizacji tego zdarzenia (i wysłać zdarzenie opisujące przyczynę zatrzymania) lub po prostu kontynuować wykonywanie.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Pobiera kontekst dokumentu, który opisuje lokalizację tego zdarzenia.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Pobiera kontekst kodu, który opisuje lokalizację tego zdarzenia.|

## <a name="remarks"></a>Uwagi
 DE wysyła ten interfejs, jeśli użytkownik kroki do funkcji i DE znajdzie żadnych informacji debugowania tam lub debugowania informacje istnieje, ale DE nie wie, czy kod źródłowy mogą być wyświetlane dla tej lokalizacji.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

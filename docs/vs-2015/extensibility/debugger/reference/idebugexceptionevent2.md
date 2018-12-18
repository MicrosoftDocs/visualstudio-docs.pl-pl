---
title: IDebugExceptionEvent2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ac2e9a85d66ad93b8b0ae1c80ee82e915fa9d86
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743362"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aparat debugowania (DE) wysyła ten interfejs do Menedżer debugowania sesji (SDM), gdy wyjątek jest generowany w programie obecnie wykonywane.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs do raportu wystąpił wyjątek do debugowanego programu. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) dostęp do `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 DE tworzy i wysyła tego obiektu zdarzenia, aby zgłosić wyjątek. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugExceptionEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Pobiera szczegółowe informacje o wyjątku, która wywołała zdarzenie.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Pobiera opis czytelny dla człowieka zgłoszony wyjątek, która wywołała zdarzenie.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Określa, czy aparat debugowania (DE) obsługuje możliwość przekazywania ten wyjątek do debugowanego po wznowieniu działania wykonywania.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Określa, czy wyjątek powinien zostać przekazany do aktualnie debugowanego po wznowieniu działania wykonywania, czy wyjątek powinien zostać odrzucony.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Uwagi  
 Przed wysłaniem zdarzenia, DE sprawdza, jeśli to zdarzenie wyjątku wyznaczono wyjątek pierwszego rzędu lub szansy na sekundę przez poprzednie wywołanie [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Jeśli został wyznaczony jako wyjątku pierwszej szansy `IDebugExceptionEvent2` SDM jest wysyłane zdarzenie. W przeciwnym razie DE daje aplikacji możliwość obsługi wyjątku. Jeśli zostanie podana żadna procedura obsługi wyjątków, a wyjątek został wyznaczony jako wyjątek szansy na sekundę, `IDebugExceptionEvent2` SDM jest wysyłane zdarzenie. W przeciwnym razie DE wznawia działanie programu, a system operacyjny lub środowisko uruchomieniowe obsługuje wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)


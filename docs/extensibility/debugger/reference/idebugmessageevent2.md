---
title: IDebugMessageEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 62ead34f06d474875539ebd4e274cfcd51db4e22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860978"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Ten interfejs jest używany przez aparat debugowania (DE), aby wysłać komunikat do programu Visual Studio, która wymaga odpowiedź od użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs do wysyłania wiadomości do programu Visual Studio, która wymaga odpowiedź użytkownika. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu.  
  
 Implementację tego interfejsu muszą komunikować się wywołanie programu Visual Studio [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) do DE. Na przykład, można to zrobić przy użyciu wiadomości opublikowane w usłudze komunikatów DE wątku lub obiekt implementujący ten interfejs może zawierać odwołanie do DE i wywoływania zwrotnego DE z odpowiedzią przekazany do `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 DE tworzy i wysyła tego obiektu zdarzenia, aby wyświetlić komunikat dla użytkownika, który wymaga odpowiedzi. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugMessageEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Pobiera komunikat do wyświetlenia.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Ustawia odpowiedzi, jeśli występują w oknie komunikatu.|  
  
## <a name="remarks"></a>Uwagi  
 DE będzie używać tego interfejsu, jeśli wymaga ona określoną odpowiedź od użytkownika dla danego komunikatu. Na przykład, jeśli DE pobiera komunikat "Odmowa dostępu" po próbie zdalnie dołączyć do programu, DE wysyła tego konkretnego komunikatu do programu Visual Studio w `IDebugMessageEvent2` zdarzenie z styl okna komunikatu `MB_RETRYCANCEL`. Dzięki temu użytkownikowi ponowić próbę lub anulować operacji dołączania.  
  
 DE Określa, jak to jest komunikat do obsłużenia konwencjami funkcję Win32 `MessageBox` (zobacz [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) Aby uzyskać szczegółowe informacje).  
  
 Użyj [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfejs do wysyłania komunikatów do programu Visual Studio, które nie wymagają odpowiedź od użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
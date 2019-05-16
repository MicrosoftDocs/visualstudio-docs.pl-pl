---
title: IDebugBreakEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98e8c1b1669b3fdd1f442c6987e4e9d2b9fc4835
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675380"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs Menedżer debugowania sesji (SDM) informuje o pomyślnym ukończeniu asynchronicznego podziału.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs do obsługi podziały użytkownika w programie. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (SDM używa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) dostęp do `IDebugEvent2` interfejsu).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) po użytkownik zażądał debugowanego ma zostać wstrzymane. Gdy program zostało wstrzymane, DE wysyła `IDebugBreakEvent2` zdarzeń. To zdarzenie jest wysyłane za pomocą [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego dostarczonych przez model SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład użytkownik może wybrać **Przerwij wszystkie** polecenie **debugowania** menu, aby zerwać program, który jest uruchomiony w pętli nieskończonej. SDM mówi programowi, aby zatrzymać, wywołując [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Wysyła DE `IDebugBreakEvent2` program na koniec zatrzymania.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

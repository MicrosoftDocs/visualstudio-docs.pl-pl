---
title: EVENTATTRIBUTES | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3026845be9aa6623d6c5cd42406385e8c5c2a11e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766633"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa atrybuty zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```csharp  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 EVENT_ASYNCHRONOUS  
 Wskazuje, że zdarzenie jest asynchroniczna, jak i braku odpowiedzi na zdarzenia jest wymagana.  
  
 EVENT_SYNCHRONOUS  
 Wskazuje, że zdarzenie jest synchroniczne; Odpowiedz przez [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).  
  
 EVENT_STOPPING  
 Wskazuje, że jest to zdarzenie zatrzymywania. Musi być połączona z jedną `EVENT_ASYNCHRONOUS` lub `EVENT_SYNCHRONOUS`.  
  
 EVENT_ASYNC_STOP  
 Wskazuje zdarzenie asynchroniczne zatrzymywania. Obecnie nie ma żadnego takiego zdarzenia. Ta flaga jest tylko symbol zastępczy.  
  
 EVENT_SYNC_STOP  
 Wskazuje zdarzenia synchroniczne zatrzymywanie (kombinację `EVENT_SYNCHRONOUS` i `EVENT_STOPPING`). Ta wartość jest używana przez aparat debugowania (DE) podczas wysyłania zdarzeń zatrzymywania. Udzielona przez wywołanie [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [kroku](../../../extensibility/debugger/reference/idebugprogram2-step.md), lub [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT_IMMEDIATE  
 Określa zdarzenie, które są wysyłane do IDE natychmiast. Ta flaga jest w połączeniu z inne flagi, takich jak `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, lub `EVENT_SYNC_STOP` aby wskazać typ zdarzenia oraz fakt, że mechanizm odpowiedzi (jeśli istnieje) jest znany.  
  
 EVENT_EXPRESSION_EVALUATION  
 Zdarzenie jest wynikiem obliczenia wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane w `dwAttrib` parametru [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody.  
  
 Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6de25108cf93314db17a2ac8de9ce8b1dcaed2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148612"
---
# <a name="idebugprogram3"></a>IDebugProgram3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje program uruchomiony w procesie i rozszerza [wykonywanie](../../../extensibility/debugger/reference/idebugprogram2-execute.md) przez podanie informacji o wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) i dostawca portu niestandardowego implementują ten interfejs, aby reprezentować program w procesie. Menedżer debugowania sesji (SDM) implementuje także ten interfejs, aby podać informacje do [dołączenia](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Zdarzenie [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zwraca ten interfejs dla nowego programu. Ten interfejs jest również używany jako parametr dla wielu metod w wielu interfejsach.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugProgram3` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Wykonuje program. Wątek jest zwracany w celu udostępnienia informacji debugera, które są wyświetlane podczas wykonywania przez użytkownika.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Uwagi  
 Program jest kontenerem wątków działającym w określonej architekturze czasu wykonywania, podczas gdy proces składa się z jednego lub kilku programów.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Ponown](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Wydarzen](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Klej](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Wydarzen](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

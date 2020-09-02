---
title: IDebugBreakEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675380"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs informuje Menedżera debugowania sesji (SDM) o tym, że przerwa asynchroniczna została pomyślnie ukończona.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs, aby obsługiwać przerwy użytkownika w programie. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs (model SDM używa [metody QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) do uzyskiwania dostępu do `IDebugEvent2` interfejsu).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Model SDM wywołuje [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) , gdy użytkownik zażądał wstrzymania działania programu. Po pomyślnym wstrzymaniu program wysyła `IDebugBreakEvent2` zdarzenie. To zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez model SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład użytkownik może wybrać polecenie **Przerwij wszystko** w menu **debugowanie** , aby przerwać działanie programu, w którym działa nieskończona pętla. Model SDM informuje program, aby zatrzymał się przez wywołanie [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). ANULUJe, `IDebugBreakEvent2` gdy program zakończy pracę.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

---
title: IDebugEntryPointEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22d7c663dbd1c9c397e7145c9dea74c8424e4383
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689181"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aparat debugowania (DE) wysyła ten interfejs do Menedżer debugowania sesji (SDM), gdy program ma wykonać jego pierwszej instrukcji kodu użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs, w ramach normalnych operacji. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) dostęp do `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 DE tworzy i wysyła tego obiektu zdarzenia, gdy program poddawany został załadowany i jest gotowy do wykonania pierwszej instrukcji kodu użytkownika. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="remarks"></a>Uwagi  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) jest wysyłana, gdy program ma wykonać pierwsze instrukcji. Na przykład `IDebugEntryPoint2` jest wysyłana, gdy program ma wykonać użytkownika `main` funkcji.  
  
 Kiedy wysyła DE `IDebugEntryPointEvent2`, bieżącej pozycji kodu powinna być w pierwszej instrukcji kodu użytkownika, na przykład `main`.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

---
title: IDebugBeforeSymbolSearchEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 26a8d7b28528a79a925207e1ee3794fcbb4ca1d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423520"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aparat debugowania (DE) wysyła ten interfejs Menedżer debugowania sesji (SDM), aby ustawić stan paska komunikatów podczas ładowania symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs, gdy komunikat na pasku stanu musi ustawić podczas ładowania symboli. Ten interfejs jest implementowany tylko przez silniki debugowania, które pracować, lub są częścią interpretery skryptu. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (SDM używa **QueryInterface** dostęp do **IDebugEvent2** interfejsu).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 DE tworzy i wysyła tego obiektu zdarzenia, gdy komunikat na pasku stanu musi ustawić podczas ładowania symboli. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego dostarczonych przez model SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugBeforeSymbolSearchEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Pobiera nazwę aktualnie debugowanego modułu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

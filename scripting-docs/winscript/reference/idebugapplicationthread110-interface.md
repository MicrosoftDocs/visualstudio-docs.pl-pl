---
title: Interfejs IDebugApplicationThread110 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 44df7168c241c9a750354e1a603d6c5ba96dabd2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440537"
---
# <a name="idebugapplicationthread110-interface"></a>Interfejs IDebugApplicationThread110
Dostępnych jest więcej funkcji dla [interfejs IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md) interfejsu.  
  
> [!IMPORTANT]
> Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugApplicationThread110` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Sprawia, że wywołanie asynchroniczne w wątku głównym.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Liczba liczbę żądań wątku z wątku menedżerów PDM przełączanie mechanizmów są aktualnie przetwarza. Zazwyczaj 0 lub 1, ale jego możliwe aż zakończy się być większe, jeśli jedno wywołanie wątku rozpoczyna się przetwarzanie, ale wyzwala synchroniczne wywołanie z wątku lub w przeciwnym razie wstrzymuje działanie wątku (na przykład, wyzwalając IDebugApplicationEvents zdarzenie, które zostało wydane w debugerze Wątek)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) została wywołana dla tego wątku i nie zostało jeszcze zakończone.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Ten wątek jest w stanie, który może przetwarzać wywołań za pomocą wątku menedżerów PDM przełączanie mechanizmów (na przykład SynchronousCallInThread).|
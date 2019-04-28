---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546926"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aparat debugowania (DE) można wysłać zdarzenie to opcjonalne Menedżer debugowania sesji (SDM), po zatrzymaniu program.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Jest to nowy interfejs dla [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]. Wcześniejsze wersje nie obsługują zatrzymywanie asynchronicznego.  
  
 [Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana przez SDM w scenariuszach wieloprocesowe lub wielu programów. Gdy jeden program wysyła zdarzenia zatrzymywanie SDM, SDM żądań inne programy, aby zatrzymać zbyt.  
  
 Służy do asynchronicznie powiadamia SDM, który programu została zatrzymana. Jest to przydatne dla aparat debugowania interpreter, których czasami żaden kod działa wewnątrz debugowanego programu, dzięki czemu [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nie może zostać ukończona synchronicznie. Jeśli aparat debugowania chce używać tego asynchronicznego powiadomienia, aplikacja musi zwracać `S_ASYNC_STOP` z [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

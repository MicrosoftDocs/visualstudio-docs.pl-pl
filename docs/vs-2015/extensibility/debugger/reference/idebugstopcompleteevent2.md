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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546926"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aparat debugowania (DE) może wysłać to zdarzenie opcjonalne do Menedżera debugowania sesji (SDM), gdy program został zatrzymany.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 To jest nowy interfejs dla programu [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . Wcześniejsze wersje nie obsługują asynchronicznego zatrzymywania.  
  
 Wartość [stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana przez model SDM w scenariuszach obejmujących wiele procesów lub wiele programów. Gdy jeden program wysyła zdarzenie zatrzymania do modelu SDM, model SDM żąda również innych programów.  
  
 Jest on używany do asynchronicznego informowania modelu SDM o zatrzymaniu programu. Jest to przydatne w przypadku aparatu debugowania interpretera, gdzie czasami nie działa kod w debugowanym programie, więc nie można wykonać operacji [zatrzymania](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) synchronicznie. Jeśli aparat debugowania chce użyć tego powiadomienia asynchronicznego, musi zwrócić `S_ASYNC_STOP` z [Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

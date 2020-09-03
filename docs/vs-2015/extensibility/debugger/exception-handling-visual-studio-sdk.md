---
title: Obsługa wyjątków (Visual Studio SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 38e646f032a12de48bbfb55b089462c7f8a4dd26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152791"
---
# <a name="exception-handling-visual-studio-sdk"></a>Obsługa wyjątków (zestaw SDK programu Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej opisano proces, który występuje, gdy są zgłaszane wyjątki.  
  
## <a name="exception-handling-process"></a>Proces obsługi wyjątków  
  
1. Gdy wyjątek jest zgłaszany po raz pierwszy, ale zanim zostanie obsłużony przez program obsługi wyjątków w debugowanym programie, aparat debugowania (DE) wysyła [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) do Menedżera debugowania sesji (SDM) jako zdarzenie zatrzymywania. `IDebugExceptionEvent2`Jest wysyłany, jeśli tylko ustawienia dla wyjątku (określone w oknie dialogowym wyjątki w pakiecie debugowania) określają, że użytkownik chce zatrzymać powiadomienia o wyjątkach pierwszej szansy.  
  
2. Model SDM wywołuje [IDebugExceptionEvent2:: GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) , aby uzyskać Właściwość wyjątku.  
  
3. Pakiet debugowania wywołuje [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) , aby określić opcje, które mają być obecne dla użytkownika.  
  
4. Pakiet debugowania pyta użytkownika, jak obsłużyć wyjątek, otwierając okno dialogowe wyjątek pierwszej szansy.  
  
5. Jeśli użytkownik zdecyduje się kontynuować, dzwoni [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    - Jeśli metoda zwraca S_OK, wywołuje [IDebugExceptionEvent2::P asstodebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         -lub-  
  
         Jeśli metoda zwraca S_FALSE, debugowany program otrzymuje drugą szansę obsługi wyjątku.  
  
6. Jeśli debugowany program nie ma programu obsługi dla wyjątku drugiej szansy, zostaje wysłany `IDebugExceptionEvent2` do modelu SDM jako **EVENT_SYNC_STOP**.  
  
7. Pakiet debugowania pyta użytkownika, jak obsłużyć wyjątek, otwierając okno dialogowe wyjątek pierwszej szansy.  
  
8. Pakiet debugowania wywołuje [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) , aby określić opcje, które mają być obecne dla użytkownika.  
  
9. Pakiet debugowania pyta użytkownika, jak obsłużyć wyjątek, otwierając okno dialogowe wyjątek drugiej szansy.  
  
10. Jeśli metoda zwraca S_OK, wywołuje `IDebugExceptionEvent2::PassToDebuggee` .  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)

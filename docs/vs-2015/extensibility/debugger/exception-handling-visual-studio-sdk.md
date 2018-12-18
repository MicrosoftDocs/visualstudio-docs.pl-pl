---
title: (Visual Studio SDK) do obsługi wyjątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2640641a4cb02c34255cbd0b0016c31a0dd14638
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732957"
---
# <a name="exception-handling-visual-studio-sdk"></a>Obsługa wyjątków (zestaw SDK programu Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej opisano proces, który występuje, gdy wyjątki zostaną zgłoszone.  
  
## <a name="exception-handling-process"></a>Proces obsługi wyjątków  
  
1.  Kiedy najpierw jest zgłaszany wyjątek, ale przed zapewniona jest obsługa przez program obsługi wyjątków w programie debugowany, aparat debugowania (DE) wysyła [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) do Menedżer debugowania sesji (SDM) jako zdarzenie zatrzymywania. `IDebugExceptionEvent2` Są wysyłane, jeśli tylko ustawienia, dla wyjątku (określone w oknie dialogowym Wyjątki w pakiecie debugowania) określ, czy użytkownik chce, aby zatrzymać na powiadomienia o wyjątkach pierwszej szansy.  
  
2.  Wywołania SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) pobrać właściwości wyjątku.  
  
3.  Wywołania pakietu debugowania [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) do określenia, jakie opcje do zaprezentowania użytkownikowi.  
  
4.  Debugowanie pakietu pyta użytkownika, jak obsłużyć wyjątek, otwierając okno dialogowe wyjątku pierwszej szansy.  
  
5.  Jeśli użytkownik zdecyduje kontynuować, wywołuje metodę SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Jeśli metoda zwraca wartość S_OK, wywołuje metodę [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         —lub—  
  
         Jeśli metoda zwraca wartość S_FALSE, program debugowany otrzymuje drugą szansę, aby obsłużyć wyjątek.  
  
6.  Jeśli aktualnie debugowanego żadna procedura obsługi wyjątku pierwszej próby na sekundę, DE wysyła `IDebugExceptionEvent2` do SDM jako **EVENT_SYNC_STOP**.  
  
7.  Debugowanie pakietu pyta użytkownika, jak obsłużyć wyjątek, otwierając okno dialogowe wyjątku pierwszej szansy.  
  
8.  Wywołania pakietu debugowania [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) do określenia, jakie opcje do zaprezentowania użytkownikowi.  
  
9. Debugowanie pakietu prosi użytkownika sposób obsługi wyjątku, otwierając okno dialogowe wyjątku szansy na sekundę.  
  
10. Jeśli metoda zwraca wartość S_OK, wywołuje metodę `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)


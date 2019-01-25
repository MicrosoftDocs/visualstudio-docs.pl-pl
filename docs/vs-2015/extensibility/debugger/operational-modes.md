---
title: Tryby operacyjne | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 863a47731f93fb7935a27cb0b93af21365af1cf7
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834996"
---
# <a name="operational-modes"></a>Tryby operacyjne
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Istnieją trzy tryby, w których IDE może działać w następujący sposób:  
  
- [Tryb projektowania](#vsconoperationalmodesanchor1)  
  
- [Tryb uruchamiania](#vsconoperationalmodesanchor2)  
  
- [Tryb przerwania](#vsconoperationalmodesanchor3)  
  
  Jak Twojego niestandardowego aparatu debugowania (DE) przechodzi między tych trybów jest decyzja dotycząca implementacji wymaga należy zapoznać się z mechanizmami przejścia. DE może lub nie może bezpośrednio implementacji tych trybów. Te tryby są naprawdę debugowania pakietu tryby, które przełączyć się na podstawie akcji przez użytkownika lub zdarzenia z DE. Na przykład przejście od uruchomienia tryb na tryb przerwania jest zainicjowanego przez zdarzenie zatrzymywanie z DE. Przejście z break, aby uruchomić trybu lub krok jest zainicjowanego przez użytkownika, wykonywanie operacji, takich jak krok lub wykonania. Aby uzyskać więcej informacji na temat przejścia DE zobacz [kontrolowanie wykonywania](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Tryb projektowania  
 Tryb projektowania jest nonrunning stan debugowania programu Visual Studio, w tym czasie można ustawić funkcji w aplikacji do debugowania.  
  
 Kilka debugowania tylko funkcje są używane w trybie projektowania. Programista może zdecydować się do ustawiania punktów przerwania lub tworzyć wyrażenia czujki. DE nigdy nie jest załadowany lub jest wywoływana, gdy IDE jest w trybie projektowania. Interakcja z DE ma miejsce podczas tylko tryby uruchamiania i podziału.  
  
##  <a name="vsconoperationalmodesanchor2"></a> Tryb uruchamiania  
 Tryb wykonywania występuje, gdy program zostanie uruchomiony w sesji debugowania w środowisku IDE. Aplikacja będzie działać do czasu zakończenia, dopóki nie zostanie osiągnięty punkt przerwania lub dopóki nie zostanie zgłoszony wyjątek. Gdy aplikacja będzie działać do zakończenia, DE przejścia do trybu projektowania. Gdy punkt przerwania zostaje trafiony lub zostanie zgłoszony wyjątek, DE przechodzi w tryb przerwania.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Tryb przerwania  
 Tryb przerwania występuje, gdy wykonywanie debugowania programu jest zawieszone. Tryb przerwania oferuje dewelopera migawki aplikacji w momencie podziału i umożliwia deweloperom analizowanie stanu aplikacji i zmienić, jak aplikacja zostanie uruchomiona. Deweloper może wyświetlić i edytowania kodu, sprawdź modyfikowanie danych, ponowne uruchomienie aplikacji, kończy wykonywanie lub kontynuować działanie z tego samego punktu.  
  
 Tryb przerwania jest wprowadzane podczas DE wysyła zdarzenia synchroniczne zatrzymywania. Zdarzenia synchroniczne zatrzymywania, jest określana skrótem zdarzenia zatrzymywania, powiadom Menedżer debugowania sesji (SDM) i środowisko IDE, która przestała debugowanej aplikacji podczas wykonywania kodu. [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) i [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) interfejsy są przykłady zatrzymywanie zdarzeń.  
  
 Zatrzymywanie zdarzenia były obecne przez wywołanie jednej z następujących metod, których przejście do debugera w trybie przerwania, aby uruchomić lub krok trybu:  
  
-   [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Tryb kroku  
 Tryb kroku występuje, gdy program kroki do następnego wiersza kodu, lub do, nad lub poza funkcją. Krok jest wykonywany przez wywołanie metody [kroku](../../extensibility/debugger/reference/idebugprocess3-step.md). Ta metoda wymaga `DWORD`s, który określa [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) i [STEPKIND](../../extensibility/debugger/reference/stepkind.md) wyliczenia jako parametry wejściowe.  
  
 Gdy program pomyślnie kroki do następnego wiersza kodu lub do funkcji lub działa do kursora lub ustaw punkt przerwania, DE automatycznie przechodzi wstecz tryb przerwania.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)

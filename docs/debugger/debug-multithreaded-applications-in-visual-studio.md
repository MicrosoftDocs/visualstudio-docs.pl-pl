---
title: Debugowanie aplikacji wielowątkowych | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07710ed0188baf48a567bb3c003f174814c30094
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907894"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debugowanie aplikacji wielowątkowych w programie Visual Studio
Wątek jest sekwencją instrukcji, do których system operacyjny przydziela czas procesora. Każdy proces, który jest uruchomiony w systemie operacyjnym, składa się z co najmniej jeden wątek. Procesy, które mają więcej niż jeden wątek nazywane są wielowątkowymi.  
  
Komputery z wieloma procesorami, procesory wielordzeniowe lub procesy hyperthreading można uruchomić wiele wątków jednocześnie. Równoległe przetwarzanie przy użyciu wielu wątków może znacznie poprawić wydajność programów, ale to może również, że debugowanie trudniejsze ponieważ prześledzić wiele wątków.  
  
Wielowątkowość wprowadzić nowych rodzajów potencjalnych błędów. Na przykład dwa lub więcej wątków może być konieczne dostęp do tego samego zasobu, ale tylko jeden wątek jednocześnie może bezpiecznie uzyskać dostęp do zasobu. Niektóre forma wzajemnego wykluczania jest niezbędne upewnić się, że tylko jeden wątek uzyskuje dostęp do zasobu w dowolnym momencie. Jeśli wzajemne wykluczenie jest zaimplementowana nieprawidłowo, może utworzyć *zakleszczenia* warunku, gdzie żaden wątek nie zostanie wykonana. Zakleszczenie są często twardych problem do debugowania.

## <a name="tools-for-debugging-multithreaded-apps"></a>Narzędzia do debugowania aplikacji wielowątkowych

Visual Studio zapewnia różne narzędzia do użycia podczas debugowania aplikacji wielowątkowych.

- Dla wątków, podstawowe narzędzia do debugowania wątków to **wątków** okna, znaczniki wątków w oknach źródłowych **stosów równoległych** oknie **równoległego wyrażenia kontrolnego** okna, a **Lokalizacja debugowania** paska narzędzi. Aby dowiedzieć się więcej na temat **wątków** okna i **Lokalizacja debugowania** narzędzi, zobacz [instruktażu: Debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md). Aby dowiedzieć się, jak używać **stosów równoległych** i **równoległego wyrażenia kontrolnego** systemu windows, zobacz [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md). Zarówno tematach opisano sposób użycia znaczników wątków.
  
- Dla kodu, który używa [Biblioteka zadań równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) lub [współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime/), podstawowe narzędzia do debugowania są **stosów równoległych** okna, **Równoległego wyrażenia kontrolnego** oknie i **zadania** okno, które również obsługuje język JavaScript. Aby rozpocząć pracę, zobacz [instruktażu: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md) i [instruktażu: Debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Do debugowania wątków na procesor GPU, jest podstawowym narzędziem **wątków GPU** okna. Zobacz [jak: Korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Dla procesów, podstawowe narzędzia to **dołączyć do procesu** okno dialogowe **procesy** oknie i **Lokalizacja debugowania** paska narzędzi.  
  
Visual Studio udostępnia również zaawansowane punkty przerwania i punkty śledzenia, które mogą być przydatne podczas debugowania aplikacji wielowątkowych. Użyj warunków punktu przerwania i filtry, aby umieścić punkty przerwania na jednym z wątków. Punkty śledzenia pozwalają na wykonywanie śledzenia programu bez przerywania do badania problemów, takich jak zakleszczenia. Aby uzyskać więcej informacji, zobacz [akcje punktu przerwania i punkty śledzenia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Debugowanie aplikacji wielowątkowej, która ma interfejs użytkownika może być szczególnie trudne. Można rozważyć uruchamiania aplikacji na drugim komputerze i za pomocą zdalnego debugowania. Aby uzyskać więcej informacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
## <a name="articles-about-debugging-multithreaded-apps"></a>Artykuły na temat debugowania aplikacji wielowątkowych

 [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)   
 Przewodnik po funkcjach debugowania wątku, podkreślając funkcji **stosów równoległych** okna i **równoległego wyrażenia kontrolnego** okna.

 [Narzędzia do debugowania wątków i procesów](../debugger/debug-threads-and-processes.md)  
 Wyświetla listę funkcji narzędzia do debugowania wątków i procesów.  
  
 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)  
 Wyjaśnia, jak debugowanie wielu procesów.

 [Przewodnik: Debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md).  
 Przewodnik, który pokazuje, jak używać **wątków** okna i **Lokalizacja debugowania** paska narzędzi. 

 [Przewodnik: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Przewodnik, który pokazuje, jak używać **stosów równoległych** i **zadania** systemu windows.  
  
 [Instrukcje: Przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Rożne sposoby przełączenia kontekstu debugowania do innego wątku.  
  
 [Instrukcje: Oflagowanie i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md)  
 Oznacz lub Oflaguj wątki, które chcesz poświęcić szczególną uwagę podczas debugowania.    
  
 [Instrukcje: Debugowanie w klastrze o wysokiej wydajności](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniki debugowania aplikacji, która działa w klastrze wysokiej wydajności.  

 [Wskazówki dotyczące debugowania wątków w kodzie natywnym](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Proste techniki, które mogą być przydatne podczas debugowania wątków natywnych. 

 [Instrukcje: Ustawianie nazw wątków w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Nadaj wątkowi nazwę, którą można wyświetlić w **wątków** okna.  
  
 [Instrukcje: Ustawianie nazw wątków w kodzie zarządzanym](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Nadaj wątkowi nazwę, którą można wyświetlić w **wątków** okna. 
  
## <a name="see-also"></a>Zobacz także  

[Używanie punktów przerwania](../debugger/using-breakpoints.md)  
[Wątkowość](/dotnet/standard/threading/index)  
[Wielowątkowość w składnikach](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
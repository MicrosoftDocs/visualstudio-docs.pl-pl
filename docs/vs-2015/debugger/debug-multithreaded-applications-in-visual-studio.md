---
title: Debuguj wielowątkowe aplikacje
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 811c6c26ec3fdfd8689757cd8a46358c3a896a88
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938063"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuguj aplikacje wielowątkowe w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wątek jest sekwencją instrukcji, do których system operacyjny przydziela czas procesora. Każdy proces, który jest uruchomiony w systemie operacyjnym, składa się z co najmniej jeden wątek. Procesy, które mają więcej niż jeden wątek nazywane są wielowątkowymi.

 Komputery z wieloma procesorami, procesory wielordzeniowe lub procesy hyperthreading mogą uruchomić wiele wątków, w tym samym czasie. Równoległe przetwarzanie wiele wątków może znacznie poprawić wydajność programów, ale może również sprawić, że debugowanie trudniejsze ponieważ wprowadza konieczność, aby śledzić wiele wątków.

 Ponadto wielowątkowość wprowadza kilka nowych rodzajów potencjalnych błędów. Często na przykład dwa lub więcej wątków, trzeba mieć dostęp do tego samego zasobu, ale tylko jeden wątek może bezpiecznie uzyskać dostępu do zasobu w danym momencie. Niektóre forma wzajemnego wykluczania jest niezbędne upewnić się, że tylko jeden wątek uzyskuje dostęp do zasobów w danym momencie. Jeśli wzajemne wykluczanie jest wykonywane niepoprawnie, może utworzyć *zakleszczenia* warunku, gdzie żaden wątek nie może wykonać. Zakleszczenia mogą być problemem szczególnie trudnym do debugowania.

 Program Visual Studio udostępnia **wątków** okna, okno wątków GPU, okno czujki równoległej i inne funkcje, które debugowanie wielowątkowe. Najlepszym sposobem, aby dowiedzieć się więcej o funkcjach wątkowości jest wykonanie instrukcji opisanych w przewodnikach. Zobacz [instruktażu: Debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-multithreaded-application.md) i [instruktażu: Debugowanie aplikacji C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio udostępnia również zaawansowane punkty przerwania i punkty śledzenia, które mogą być bardzo przydatne podczas debugowania aplikacji wielowątkowych. Filtry punktów przerwania można użyć, aby umieścić punkty przerwania na jednym z wątków. Zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md)

 Debugowanie aplikacji wielowątkowej, która ma interfejs użytkownika może być szczególnie trudne. W takim przypadku można rozważyć uruchamiania aplikacji na drugim komputerze i za pomocą zdalnego debugowania. Aby uzyskać informacje, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>W tej sekcji
 [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md) wyjaśniono podstawowe informacje dotyczące debugowania wątków i procesów.

 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md) wyjaśnia, jak debugowanie wielu procesów.

 [Instrukcje: Korzystanie z okna wątków](../debugger/how-to-use-the-threads-window.md) użyteczne procedury dotyczące debugowania wątków przy użyciu **wątków** okna.

 [Instrukcje: Przełącz się do innego wątku podczas debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md) trzy sposoby przełączenia kontekstu debugowania do innego wątku.

 [Instrukcje: Flaga i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md) Oznacz lub Oflaguj wątki, które chcesz poświęcić szczególną uwagę podczas debugowania.

 [Instrukcje: Ustawianie nazw wątków w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md) nadaj wątkowi nazwę, którą można wyświetlić w **wątków** okna.

 [Instrukcje: Ustawianie nazw wątków w kodzie zarządzany](../debugger/how-to-set-a-thread-name-in-managed-code.md) nadaj wątkowi nazwę, którą można wyświetlić w **wątków** okna.

 [Przewodnik: Debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Przewodnik po funkcjach debugowania wątku, z naciskiem na funkcje jak do [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 [Instrukcje: Debugowanie w klastrze wysokiej wydajności](../debugger/how-to-debug-on-a-high-performance-cluster.md) techniki debugowania aplikacji, która działa w klastrze o wysokiej wydajności.

 [Porady dotyczące debugowania wątków w kodzie natywnym](../debugger/tips-for-debugging-threads-in-native-code.md) proste techniki, które mogą być przydatne podczas debugowania wątków natywnych.

 [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md) Wyświetla listę wszystkich obiektów zadań zarządzanych lub natywnych, łącznie z ich stanami i innymi przydatnymi informacjami.

 [Za pomocą Parallel Stacks Window](../debugger/using-the-parallel-stacks-window.md) wywołanie pokazuje stosy wielu wątków (lub zadaniami) w jednym widoku, a ponadto scala segmenty stosów, które są wspólne miedzy wątkami (lub zadaniami).

 [Przewodnik: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md) przewodnik, który pokazuje, jak używać okien zadań równoległych i stosów przetwarzania równoległego.

 [Instrukcje: Użyj okna czujki równoległej](../debugger/how-to-use-the-parallel-watch-window.md) Sprawdź wartości i wyrażenia w wielu wątkach.

 [Instrukcje: Korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md) Sprawdź i Praca z wątkami, które są uruchomione w procesorze GPU podczas debugowania.

## <a name="related-sections"></a>Sekcje pokrewne
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)
 -   Filtry punktów przerwania należy użyć, gdy chcesz umieścić punkt przerwania na jednym z wątków.

- Punkty śledzenia pozwalają na wykonywanie śledzenia programu bez przerywania. Może to być przydatne do badania problemów, takich jak zakleszczenia.

  [Wątkowość](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) pojęcia wielowątkowości w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programowania, w tym przykładzie kodu.

  [Wielowątkowość w składnikach](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) jak używać wielowątkowości w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] składników.

  [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) pojęcia wielowątkowości i przykładowy kod dla programistów C++ przy użyciu biblioteki MFC.

## <a name="see-also"></a>Zobacz też
 [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md) [zdalnego debugowania](../debugger/remote-debugging.md)

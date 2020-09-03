---
title: Debuguj wielowątkowe aplikacje
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 8cb43c9a32f3dfd0a6383d466f7cd283acf0ab3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691282"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuguj aplikacje wielowątkowe w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wątek jest sekwencją instrukcji, do których system operacyjny przydziela czas procesora. Każdy proces, który jest uruchomiony w systemie operacyjnym, składa się z co najmniej jednego wątku. Procesy, które mają więcej niż jeden wątek, są nazywane wielowątkowymi.

 Komputery z wieloma procesorami, procesorami wielordzeniowymi lub procesami wielowątkowości mogą jednocześnie uruchamiać wiele wątków. Równoległe przetwarzanie wielu wątków może znacznie poprawić wydajność programu, ale może również utrudnić debugowanie, ponieważ wprowadza potrzebę śledzenia wielu wątków.

 Ponadto wielowątkowość wprowadza kilka nowych typów potencjalnych usterek. Często na przykład dwa lub więcej wątków muszą uzyskać dostęp do tego samego zasobu, ale tylko jeden wątek może bezpiecznie uzyskać dostęp do zasobu jednocześnie. Niektóre formy wzajemnego wykluczania są niezbędne do upewnienia się, że tylko jeden wątek uzyskuje dostęp do zasobu w danym momencie. Jeśli wykluczenie wzajemne jest wykonywane nieprawidłowo, może utworzyć warunek *zakleszczenia* , gdzie nie można wykonać wątku. Zakleszczenie mogą być szczególnie trudnym problemem do debugowania.

 Program Visual Studio udostępnia okno **wątków** , okno wątków GPU, okno wyrażeń kontrolnych równoległe i inne funkcje, które ułatwiają debugowanie wielowątkowe. Najlepszym sposobem na zapoznanie się z funkcjami wątkowości jest wykonanie instrukcji. Zobacz [Przewodnik: debugowanie aplikacji wielowątkowej](../debugger/walkthrough-debugging-a-multithreaded-application.md) i [Przewodnik: debugowanie aplikacji C++ amp](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Program Visual Studio udostępnia także zaawansowane punkty przerwania i punkty śledzenia, które mogą być bardzo przydatne podczas debugowania aplikacji wielowątkowych. Filtry punktów przerwania umożliwiają umieszczanie punktów przerwania w poszczególnych wątkach. Zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md)

 Debugowanie aplikacji wielowątkowej, która ma interfejs użytkownika, może być szczególnie trudne. W takim przypadku można rozważyć uruchomienie aplikacji na drugim komputerze i używanie zdalnego debugowania. Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>W tej sekcji
 [Debuguj wątki i procesy](../debugger/debug-threads-and-processes.md) Objaśnienie podstaw debugowania wątków i procesów.

 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md) Wyjaśnia, jak debugować wiele procesów.

 [Instrukcje: korzystanie z okna wątków](../debugger/how-to-use-the-threads-window.md) Przydatne procedury debugowania wątków przy użyciu okna **wątków** .

 [Instrukcje: przełączanie do innego wątku podczas debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md) Trzy sposoby przełączenia kontekstu debugowania do innego wątku.

 [Instrukcje: Flagowanie i usuwanie flag wątków](../debugger/how-to-flag-and-unflag-threads.md) Oznacz lub Oflaguj wątki, do których chcesz zwrócić szczególną uwagę podczas debugowania.

 [Instrukcje: Ustawianie nazwy wątku w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md) Nadaj wątkowi nazwę, która jest wyświetlana w oknie **wątki** .

 [Instrukcje: Ustawianie nazwy wątku w kodzie zarządzanym](../debugger/how-to-set-a-thread-name-in-managed-code.md) Nadaj wątkowi nazwę, która jest wyświetlana w oknie **wątki** .

 [Przewodnik: debugowanie aplikacji wielowątkowej](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Przewodnik po funkcjach debugowania wątków, z naciskiem na funkcje, jak to zrobić [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] .

 [Instrukcje: debugowanie w klastrze o wysokiej wydajności](../debugger/how-to-debug-on-a-high-performance-cluster.md) Techniki debugowania aplikacji działającej w klastrze o wysokiej wydajności.

 [Wskazówki dotyczące debugowania wątków w kodzie natywnym](../debugger/tips-for-debugging-threads-in-native-code.md) Proste techniki, które mogą być przydatne do debugowania natywnych wątków.

 [Korzystanie z okna zadania](../debugger/using-the-tasks-window.md) Przedstawia listę wszystkich obiektów zadań zarządzanych lub natywnych, w tym ich stan i inne przydatne informacje.

 [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md) Pokazuje stosy wywołań wielu wątków (lub zadań) w jednym widoku, a także łączy segmenty stosu, które są wspólne dla wątków (lub zadań).

 [Przewodnik: debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md) Przewodnik, który pokazuje, jak używać zadań równoległych i równoległych stosów systemu Windows.

 [Instrukcje: korzystanie z okna czujki równoległej](../debugger/how-to-use-the-parallel-watch-window.md) Sprawdź wartości i wyrażenia w wielu wątkach.

 [Instrukcje: korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md) Badaj wątki, które są uruchomione w procesorze GPU podczas debugowania, i pracuj z nich.

## <a name="related-sections"></a>Sekcje pokrewne

[Używanie punktów przerwania](../debugger/using-breakpoints.md)
- Użyj filtrów punktów przerwania, gdy chcesz umieścić punkt przerwania na pojedynczym wątku.

- Punkty śledzenia umożliwiają śledzenie wykonywania programu bez przerywania działania. Może to być przydatne do badania problemów, takich jak zakleszczenia.

  [Wątkowość](https://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) Koncepcje wątkowości w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programowaniu, w tym przykładowy kod.

  [Wielowątkowość w składnikach](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) Jak używać wielowątkowości w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] składnikach.

  [Obsługa wielowątkowości dla starszego kodu (Visual C++)](https://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) Koncepcje wątkowe i przykładowy kod dla programistów języka C++ przy użyciu MFC.

## <a name="see-also"></a>Zobacz też
 [Debuguj wątki i Przetwarzaj](../debugger/debug-threads-and-processes.md) [zdalne debugowanie](../debugger/remote-debugging.md)

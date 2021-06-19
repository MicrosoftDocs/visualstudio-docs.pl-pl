---
title: Debugowanie aplikacji wielowątkowych | Microsoft Docs
description: Debugowanie aplikacji wielowątkowych w Visual Studio. Przejrzyj narzędzia i inne artykuły dotyczące debugowania aplikacji wielowątkowych.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5551ffd39bfe3485d0b6e31def0b3cfff9c7e3b1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389764"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debugowanie aplikacji wielowątkowych w programie Visual Studio
Wątek to sekwencja instrukcji, do której system operacyjny udziela czasu procesora. Każdy proces uruchomiony w systemie operacyjnym składa się z co najmniej jednego wątku. Procesy, które mają więcej niż jeden wątek, są nazywane wielowątkami.

Komputery z wieloma procesorami, procesorami wielordzeniowym lub procesami hiperwątkowania mogą uruchamiać kilka równoczesnych wątków. Przetwarzanie równoległe przy użyciu wielu wątków może znacznie poprawić wydajność programu, ale może również utrudnić debugowanie, ponieważ śledzisz wiele wątków.

Wielowątkowanie może wprowadzać nowe typy potencjalnych usterek. Na przykład co najmniej dwa wątki mogą wymagać dostępu do tego samego zasobu, ale tylko jeden wątek na raz może bezpiecznie uzyskać dostęp do zasobu. Pewna forma wzajemnego wykluczania jest niezbędna do upewnienia się, że tylko jeden wątek uzyskuje dostęp do zasobu w dowolnym momencie. Jeśli wzajemne wykluczanie jest implementowane niepoprawnie, może utworzyć warunek *zakleszczenia,* w którym żaden wątek nie zostanie wykonany. Zakleszczenia są często trudnym problemem do debugowania.

## <a name="tools-for-debugging-multithreaded-apps"></a>Narzędzia do debugowania aplikacji wielowątkowych

Visual Studio udostępnia różne narzędzia do debugowania aplikacji wielowątkowych.

- W przypadku wątków podstawowymi narzędziami debugowania wątków są okna  wątków, znaczniki wątku w oknach źródłowych, okno stosów równoległych, okno **Równoległe** śledzenie i pasek narzędzi **Lokalizacja** debugowania.  Aby dowiedzieć się więcej na **temat okna wątków** i **paska narzędzi Lokalizacja debugowania,** zobacz [Przewodnik: debugowanie przy użyciu okna wątków](../debugger/how-to-use-the-threads-window.md). Aby dowiedzieć się, jak używać okien **stosów równoległych** i równoległych **zegarków,** zobacz Wprowadzenie do [debugowania aplikacji wielowątkowej.](../debugger/get-started-debugging-multithreaded-apps.md) Oba tematy pokazują, jak używać znaczników wątku.

- W przypadku kodu, który używa biblioteki  równoległych zadań [(TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) lub [środowisko uruchomieniowe współbieżności,](/cpp/parallel/concrt/concurrency-runtime/)podstawowymi narzędziami debugowania  są okno Stosy równoległe, okno **Równoległe** śledzenie i okno Zadania, które również obsługuje język JavaScript. Aby rozpocząć, zobacz [Przewodnik: debugowanie aplikacji](../debugger/walkthrough-debugging-a-parallel-application.md) równoległej i [Przewodnik: debugowanie aplikacji C++ AMP aplikacji.](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)

- W przypadku debugowania wątków na procesorze GPU podstawowym narzędziem jest okno **Wątki procesora GPU.** Zobacz [How to: Use the GPU Threads window (Jak używać wątków GPU).](../debugger/how-to-use-the-gpu-threads-window.md)

- W przypadku procesów narzędzia podstawowe to okno dialogowe Dołączanie do **procesu,** okno **Procesy** i pasek narzędzi **Lokalizacja debugowania.**

Visual Studio udostępnia również zaawansowane punkty przerwania i punkty śledzenia, które mogą być przydatne podczas debugowania aplikacji wielowątkowych. Użyj warunków punktu przerwania i filtrów, aby umieścić punkty przerwania w poszczególnych wątkach. Punkty śledzenia umożliwiają śledzenie wykonywania programu bez przerywania działania w celu badania problemów, takich jak zakleszczenia. Aby uzyskać więcej informacji, zobacz [Akcje punktu przerwania i punkty śledzenia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Debugowanie aplikacji wielowątkowej, która ma interfejs użytkownika, może być szczególnie trudne. Możesz rozważyć uruchomienie aplikacji na drugim komputerze i użycie debugowania zdalnego. Aby uzyskać więcej informacji, zobacz [Zdalne debugowanie](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Artykuły dotyczące debugowania aplikacji wielowątkowych

 [Wprowadzenie do debugowania aplikacji wielowątkowej](../debugger/get-started-debugging-multithreaded-apps.md)

Przewodnik po funkcjach debugowania wątków, który podkreśla funkcje w oknie **stosów równoległych** i oknie **równoległego zegarka.**

 [Narzędzia do debugowania wątków i procesów](../debugger/debug-threads-and-processes.md)

Wyświetla listę funkcji narzędzi do debugowania wątków i procesów.

 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)

Wyjaśnia, jak debugować wiele procesów.

 [Przewodnik: debugowanie przy użyciu okna wątków](../debugger/how-to-use-the-threads-window.md).

Przewodnik, który pokazuje, jak używać okna **wątków** i paska **narzędzi Lokalizacja debugowania.**

 [Przewodnik: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)

Przewodnik, który pokazuje, jak używać okien **Stosy równoległe** **i** Zadania.

 [Instrukcje: przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Kilka sposobów przełączania kontekstu debugowania na inny wątek.

 [Porada: oflagowanie i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md)

Oznacz lub oflaguj wątki, na które chcesz zwrócić szczególną uwagę podczas debugowania.

 [How to: Debug on a high-performance cluster (Jak debugować w klastrze o wysokiej wydajności)](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Techniki debugowania aplikacji uruchamianej w klastrze o wysokiej wydajności.

 [Wskazówki dotyczące debugowania wątków w kodzie natywnym](../debugger/tips-for-debugging-threads-in-native-code.md)

Proste techniki, które mogą być przydatne do debugowania natywnych wątków.

 [Jak ustawić nazwę wątku w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md)

Nadaj wątku nazwę, która jest przeglądana w **oknie Wątki.**

 [How to: Set a thread name in managed code (Jak ustawić nazwę wątku w kodzie zarządzanym)](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Nadaj wątku nazwę, która jest przeglądana w **oknie Wątki.**

## <a name="see-also"></a>Zobacz też

- [Używanie punktów przerwania](../debugger/using-breakpoints.md)
- [Wątkowość](/dotnet/standard/threading/index)
- [Wielowątkowanie w składnikach](/previous-versions/3es4b6yy(v=vs.140))
- [Obsługa wielowątkowych dla starszego kodu](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
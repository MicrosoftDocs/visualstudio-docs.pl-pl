---
title: Debugowanie aplikacji wielowątkowych | Microsoft Docs
description: Debuguj aplikacje wielowątkowe w programie Visual Studio. Przejrzyj narzędzia i inne artykuły dotyczące debugowania aplikacji wielowątkowych.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: e7a133b4b59b11525a7f7ba776b3b4a4a1e6a31e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873213"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debugowanie aplikacji wielowątkowych w programie Visual Studio
Wątek jest sekwencją instrukcji, do których system operacyjny przyznaje czas procesora. Każdy proces, który jest uruchomiony w systemie operacyjnym, składa się z co najmniej jednego wątku. Procesy, które mają więcej niż jeden wątek, są nazywane wielowątkowymi.

Komputery z wieloma procesorami, procesorami wielordzeniowymi lub procesami wielowątkowości mogą uruchamiać kilka równoczesnych wątków. Równoległe przetwarzanie przy użyciu wielu wątków może znacznie poprawić wydajność programu, ale może również utrudnić debugowanie, ponieważ śledzisz wiele wątków.

Wielowątkowość może wprowadzać nowe typy potencjalnych usterek. Na przykład dwa lub więcej wątków może potrzebować dostępu do tego samego zasobu, ale tylko jeden wątek w danym momencie może bezpiecznie uzyskać dostęp do zasobu. Niektóre formy wzajemnego wykluczania są niezbędne do upewnienia się, że tylko jeden wątek uzyskuje dostęp do zasobu w dowolnym momencie. Jeśli wykluczenie wzajemne jest zaimplementowane niepoprawnie, może utworzyć warunek *zakleszczenia* , gdzie żaden wątek nie zostanie wykonany. Zakleszczenia są często twardym problemem do debugowania.

## <a name="tools-for-debugging-multithreaded-apps"></a>Narzędzia do debugowania aplikacji wielowątkowych

Program Visual Studio oferuje różne narzędzia do użycia w debugowaniu aplikacji wielowątkowych.

- W przypadku wątków podstawowe narzędzia do debugowania wątków to okno **wątki** , znaczniki wątków w oknach źródłowych, okno **stosów równoległych** , okno **równoległego czujki** i pasek narzędzi **Lokalizacja debugowania** . Aby dowiedzieć się więcej na temat okna **wątki** i paska narzędzi **lokalizacji debugowania** , zobacz [Przewodnik: debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md). Aby dowiedzieć się, jak używać **stosów równoległych** i **równoległych okien czujek** , zobacz Wprowadzenie [do debugowania aplikacji wielowątkowej](../debugger/get-started-debugging-multithreaded-apps.md). W obu tematach pokazano, jak używać znaczników wątków.

- W przypadku kodu, który korzysta z [biblioteki zadań równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) lub [środowisko uruchomieniowe współbieżności](/cpp/parallel/concrt/concurrency-runtime/), podstawowe narzędzia do debugowania to okno **stosów** równoległych, okno **czujki równoległej** i okno **zadania** , które również obsługuje język JavaScript. Aby rozpocząć, zobacz [Przewodnik: debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md) i [Przewodnik: debugowanie aplikacji C++ amp](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application).

- W przypadku debugowania wątków w procesorze GPU narzędzie podstawowe jest oknem **wątków GPU** . Zobacz [jak: korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md).

- W przypadku procesów podstawowe narzędzia to okno dialogowe **Dołącz do procesu** , okno **procesy** i pasek narzędzi **Lokalizacja debugowania** .

Program Visual Studio udostępnia także zaawansowane punkty przerwania i punkty śledzenia, które mogą być przydatne podczas debugowania aplikacji wielowątkowych. Użyj warunków i filtrów punktów przerwania, aby umieścić punkty przerwania w poszczególnych wątkach. Punkty śledzenia umożliwiają śledzenie wykonywania programu bez przerywania działania, aby badać problemy, takie jak zakleszczenia. Aby uzyskać więcej informacji, zobacz [Akcje punktu przerwania i punkty śledzenia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Debugowanie aplikacji wielowątkowej, która ma interfejs użytkownika, może być szczególnie trudne. Możesz rozważyć uruchomienie aplikacji na drugim komputerze i używanie zdalnego debugowania. Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Artykuły dotyczące debugowania aplikacji wielowątkowych

 [Rozpocznij debugowanie aplikacji wielowątkowej](../debugger/get-started-debugging-multithreaded-apps.md)

Przewodnik po funkcjach debugowania wątków, wyróżnianie funkcji w oknie **stosów równoległych** i okno **czujki równoległej** .

 [Narzędzia do debugowania wątków i procesów](../debugger/debug-threads-and-processes.md)

Zawiera listę funkcji narzędzi do debugowania wątków i procesów.

 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)

Wyjaśnia, jak debugować wiele procesów.

 [Przewodnik: debugowanie przy użyciu okna wątków](../debugger/how-to-use-the-threads-window.md).

Przewodnik, który pokazuje, jak używać okna **wątki** i paska narzędzi **lokalizacji debugowania** .

 [Przewodnik: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)

Przewodnik, który pokazuje, jak używać **stosów równoległych** i okien **zadań** .

 [Instrukcje: przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Kilka sposobów przełączania kontekstu debugowania do innego wątku.

 [Porada: oflagowanie i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md)

Oznacz lub Oflaguj wątki, do których chcesz zwrócić szczególną uwagę podczas debugowania.

 [Instrukcje: debugowanie w klastrze o wysokiej wydajności](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Techniki debugowania aplikacji działającej w klastrze o wysokiej wydajności.

 [Wskazówki dotyczące debugowania wątków w kodzie natywnym](../debugger/tips-for-debugging-threads-in-native-code.md)

Proste techniki, które mogą być przydatne do debugowania natywnych wątków.

 [Instrukcje: Ustawianie nazwy wątku w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md)

Nadaj wątkowi nazwę, która jest wyświetlana w oknie **wątki** .

 [Instrukcje: Ustawianie nazwy wątku w kodzie zarządzanym](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Nadaj wątkowi nazwę, która jest wyświetlana w oknie **wątki** .

## <a name="see-also"></a>Zobacz też

- [Używanie punktów przerwania](../debugger/using-breakpoints.md)
- [Wątkowość](/dotnet/standard/threading/index)
- [Wielowątkowość w składnikach](/previous-versions/3es4b6yy(v=vs.140))
- [Obsługa wielowątkowości dla starszego kodu](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
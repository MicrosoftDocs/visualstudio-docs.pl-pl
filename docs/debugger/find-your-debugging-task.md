---
title: Znajdowanie zadania debugowania
description: Zidentyfikuj funkcję debugera ułatwiającą debugowanie aplikacji
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b833d8b68af418b727861226df41c700d582805e
ms.sourcegitcommit: d55438841123aad56a524a65332a86ad67af386b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73599293"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Znajdowanie zadania debugowania w programie Visual Studio

Jeśli potrzebujesz pomocy w mapowaniu zadania debugowania na poprawną funkcję debugera programu Visual Studio, który jest istotny, Skorzystaj z linków dostępnych w tym artykule. Lista zadań w tym miejscu obejmuje typowe zadania, takie jak Wstrzymywanie kodu do debugowania, sprawdzanie zmiennych i wysyłanie komunikatów do okna **danych wyjściowych** . Jeśli potrzebujesz przeglądu funkcji debugera, zobacz [najpierw Przyjrzyj się debugerowi](debugger-feature-tour.md) .

## <a name="pause-running-code"></a>Wstrzymaj uruchamianie kodu

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Wstrzymaj uruchamianie kodu, aby sprawdzić wiersz kodu, który może zawierać usterkę

Ustaw punkt przerwania. Aby uzyskać więcej informacji, zobacz [Używanie punktów przerwania](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Wstrzymywanie i sprawdzanie aplikacji po osiągnięciu określonego stanu

Wypróbuj warunkowy punkt przerwania, aby kontrolować miejsce i czas, w którym punkt przerwania jest aktywowany przy użyciu logiki warunkowej. Aby uzyskać więcej informacji, zobacz [warunki punktu przerwania](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Wstrzymaj kod tylko wtedy, gdy zmienia się właściwość lub wartość określonego obiektu

Dla C++programu Ustaw [punkt przerwania danych](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
W przypadku aplikacji korzystających z platformy .NET Core 3 można również ustawić [punkt przerwania danych](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

W przeciwnym razie C# dla F# i tylko można [śledzić identyfikator obiektu za pomocą warunkowego punktu przerwania](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Wstrzymywanie kodu wewnątrz pętli w określonej iteracji

Ustaw punkt przerwania z użyciem **liczby trafień** jako warunku. Aby uzyskać więcej informacji, zobacz [liczba trafień](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Wstrzymaj kod na początku funkcji, jeśli znasz nazwę funkcji, ale nie jej lokalizację

Można to zrobić za pomocą punktu przerwania funkcji. Aby uzyskać więcej informacji, zobacz [ustawianie punktów przerwania funkcji](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Wstrzymaj kod na początku wielu funkcji o tej samej nazwie

Jeśli masz wiele funkcji o tej samej nazwie (przeciążone funkcje lub funkcje w różnych projektach), możesz użyć [punktu przerwania funkcji](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Zarządzanie i śledzenie punktów przerwania

Użyj okna **punkty przerwania** . Aby uzyskać więcej informacji, zobacz [Zarządzanie punktami przerwania](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Wstrzymaj kod i Debuguj, gdy zostanie zgłoszony określony obsługiwany lub nieobsługiwany wyjątek

Chociaż pomocnik wyjątku pokazuje, gdzie wystąpił błąd, jeśli chcesz wstrzymać i debugować konkretny błąd, możesz [powiedzieć, że debuger zostanie przerwany w przypadku zgłoszenia wyjątku](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Ustawianie punktu przerwania na podstawie stosu wywołań

Jeśli chcesz wstrzymywać i debugować kod podczas badania przepływu wykonywania lub wyświetlania funkcji w oknach **stosu wywołań** , zobacz [Ustawianie punktu przerwania w oknie stosu wywołań](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Wstrzymywanie kodu w określonej instrukcji zestawu

Można to zrobić przez [ustawienie punktu przerwania w oknie demontażu](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Wykonaj kod

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Poznaj polecenia, aby przejść przez kod podczas debugowania

Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Sprawdzanie danych

### <a name="check-the-value-of-variables-while-running-your-app"></a>Sprawdź wartość zmiennych podczas uruchamiania aplikacji

Umieść wskaźnik myszy nad zmiennymi przy użyciu [etykietek danych](view-data-values-in-data-tips-in-the-code-editor.md) lub [Sprawdź zmienne w oknie Ustawienia autoodtwarzania i lokalne](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Obserwuj zmianę wartości określonej zmiennej

Ustaw czujkę na zmiennej. Aby uzyskać więcej informacji, zobacz [Ustawianie typu czujki dla zmiennych](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Wyświetlanie ciągów, które są zbyt długie dla okna debugera

Otwórz wbudowany [wizualizator ciągu](view-strings-visualizer.md) podczas debugowania.

## <a name="configure-debugging"></a>Konfigurowanie debugowania

### <a name="customize-information-shown-in-the-debugger"></a>Dostosuj informacje wyświetlane w debugerze

Możesz chcieć wyświetlić informacje inne niż typ obiektu jako wartość w różnych oknach debugera. W C#przypadku kodu, F#Visual Basic, C++i/CLI, Użyj atrybutu [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Aby uzyskać bardziej zaawansowane opcje, można również dostosować interfejs użytkownika, tworząc [wizualizację niestandardową](create-custom-visualizers-of-data.md).

W przypadku C++kodu natywnego Użyj [struktury NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Konfigurowanie ustawień debugera

Aby skonfigurować opcje debugera i ustawienia projektu debugera, zobacz [Ustawienia debugera i przygotowania](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Dodatkowe zadania

### <a name="fix-an-exception"></a>Naprawianie wyjątku

Zobacz [Rozwiązywanie wyjątku](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Edytuj kod podczas sesji debugowania

Użyj [Edytuj i Kontynuuj](edit-and-continue.md). W przypadku języka XAML Użyj [gorącego ładowania XAML](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Wysyłaj komunikaty do okna danych wyjściowych bez modyfikowania kodu

Ustaw punkt śledzenia. Aby uzyskać więcej informacji, zobacz [using punkty śledzenia](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Wyświetlanie kolejności, w której są wywoływane funkcje

Zobacz [, jak wyświetlić stos wywołań](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Debugowanie na maszynach zdalnych

Zobacz [debugowanie zdalne](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Debuguj aplikację, która jest już uruchomiona

Zobacz [dołączanie do uruchomionych procesów](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Debugowanie aplikacji wielowątkowych

Zobacz [debugowanie aplikacji wielowątkowych](debug-multithreaded-applications-in-visual-studio.md).
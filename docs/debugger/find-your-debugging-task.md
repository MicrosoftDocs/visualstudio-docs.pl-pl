---
title: Znajdowanie zadania debugowania
description: Identyfikowanie funkcji debugera, która pomoże Ci debugować aplikację
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
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302183"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Znajdowanie zadania debugowania w programie Visual Studio

Jeśli potrzebujesz pomocy, aby zamapować zadanie debugowania do poprawnej funkcji debugera programu Visual Studio, który jest odpowiedni, należy użyć łączy podanych w tym artykule. Lista zadań w tym miejscu zawiera typowe zadania, takie jak wstrzymywanie kodu do debugowania, sprawdzanie zmiennych i wysyłanie wiadomości do okna **Dane wyjściowe.** Jeśli potrzebujesz omówienia funkcji debugera, zobacz [Pierwsze spojrzenie na debuger](debugger-feature-tour.md) zamiast tego.

## <a name="pause-running-code"></a>Wstrzymaj uruchamianie kodu

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Wstrzymaj uruchamianie kodu, aby sprawdzić wiersz kodu, który może zawierać błąd

Ustawianie punktu przerwania. Aby uzyskać więcej informacji, zobacz [Korzystanie z punktów przerwania](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Wstrzymywanie i sprawdzanie aplikacji po osiągnięciu określonego stanu

Spróbuj warunkowego punktu przerwania, aby kontrolować, gdzie i kiedy punkt przerwania zostanie aktywowany przy użyciu logiki warunkowej. Aby uzyskać więcej informacji, zobacz [Warunki punktu przerwania](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Wstrzymaj kod tylko wtedy, gdy zmienia się właściwość lub wartość określonego obiektu

W przypadku języka C++ ustaw [punkt przerwania danych](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
W przypadku aplikacji korzystających z programu .NET Core 3 można również ustawić [punkt przerwania danych](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

W przeciwnym razie tylko dla języka C# i F# można [śledzić identyfikator obiektu z warunkowym punktem przerwania](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Wstrzymaj kod wewnątrz pętli w określonej iteracji

Ustaw punkt przerwania przy użyciu **liczby trafień** jako warunku. Aby uzyskać więcej informacji, zobacz [Liczba trafień](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Wstrzymaj kod na początku funkcji, gdy znasz nazwę funkcji, ale nie jej lokalizację

Można to zrobić za pomocą punktu przerwania funkcji. Aby uzyskać więcej informacji, zobacz [Ustawianie punktów przerwania funkcji](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Wstrzymywanie kodu na początku wielu funkcji o tej samej nazwie

Jeśli masz wiele funkcji o tej samej nazwie (przeciążonych funkcji lub funkcji w różnych projektach), można użyć [punktu przerwania funkcji](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Zarządzanie punktami przerwania i śledzenie ich

Użyj okna **Punkty przerwania.** Aby uzyskać więcej informacji, zobacz [Zarządzanie punktami przerwania](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Wstrzymaj kod i debugowanie, gdy zgłaszany jest określony obsługiwany lub nieobsługiowany wyjątek

Chociaż Pomocnik wyjątku pokazuje, gdzie wystąpił błąd, jeśli chcesz wstrzymać i debugować określony błąd, możesz [powiedzieć debugerowi, aby przerwać, gdy zostanie zgłoszony wyjątek.](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)

### <a name="set-a-breakpoint-from-the-call-stack"></a>Ustawianie punktu przerwania ze stosu wywołań

Jeśli chcesz wstrzymać i debugować kod podczas badania przepływu wykonania lub wyświetlania funkcji w oknach **Stos wywołań,** zobacz [Ustawianie punktu przerwania w oknie Stos wywołań](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Kod wstrzymania w określonej instrukcji montażu

Można to zrobić, [ustawiając punkt przerwania z okna Demontaż](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Wykonanie kodu

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Poznaj polecenia, aby przejść przez kod podczas debugowania

Aby uzyskać więcej informacji, zobacz [Nawigowanie po kodzie za pomocą debugera](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Inspekcja danych

### <a name="check-the-value-of-variables-while-running-your-app"></a>Sprawdzanie wartości zmiennych podczas uruchamiania aplikacji

Umieść wskaźnik myszy na zmiennych za pomocą [wskazówek dotyczących danych](view-data-values-in-data-tips-in-the-code-editor.md) lub sprawdź [zmienne w oknie Autos i Locals](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Obserwować zmieniającą się wartość określonej zmiennej

Ustaw zegarek na zmiennej. Aby uzyskać więcej informacji, zobacz [Ustawianie zegarka na zmiennych](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Wyświetlanie ciągów, które są zbyt długie dla okna debugera

Otwórz wbudowany [wizualizator ciągów](view-strings-visualizer.md) podczas debugowania.

## <a name="configure-debugging"></a>Konfigurowanie debugowania

### <a name="customize-information-shown-in-the-debugger"></a>Dostosowywanie informacji wyświetlanych w debugerze

Można wyświetlić informacje inne niż typ obiektu jako wartość w różnych oknach debugera. W przypadku kodu Języka C#, Visual Basic, F#i C++/CLI należy użyć [atrybutu DebuggerDisplay.](using-the-debuggerdisplay-attribute.md) Aby uzyskać bardziej zaawansowane opcje, można również dostosować interfejs użytkownika, tworząc [niestandardowy wizualizator](create-custom-visualizers-of-data.md).

W przypadku natywnego języka C++ należy użyć [struktury NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Konfigurowanie ustawień debugera

Aby skonfigurować opcje debugera i ustawienia projektu debugera, zobacz [Ustawienia i przygotowanie debugera](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Dodatkowe zadania

### <a name="fix-an-exception"></a>Naprawianie wyjątku

Zobacz [Rozwiązywanie problemu z wyjątkiem](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Edytowanie kodu podczas sesji debugowania

Użyj [funkcji Edytuj i kontynuuj](edit-and-continue.md). W przypadku xaml użyj [funkcji XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Wysyłanie wiadomości do okna Dane wyjściowe bez modyfikowania kodu

Ustaw punkt śledzenia. Aby uzyskać więcej informacji, zobacz [Korzystanie z punktów śledzenia](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Wyświetlanie kolejności wywoływania funkcji

Zobacz [Jak wyświetlić stos połączeń](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Debugowanie na komputerach zdalnych

Zobacz [Zdalne debugowanie](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Debugowanie aplikacji, która jest już uruchomiona

Zobacz [Dołączanie do uruchomionych procesów](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Debugowanie aplikacji wielowątkowych

Zobacz [Debugowanie aplikacji wielowątkowych](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Rozwiązywanie problemów z wydajnością

Zobacz [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
---
title: Często zadawane pytania — znajdowanie funkcji debugowania
description: Często zadawane pytania ułatwiające zidentyfikowanie funkcji debugera, która ułatwi debugowanie aplikacji
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c215b232c64b97c57285618056ee4675587b48e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870717"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Często zadawane pytania — Znajdź wymaganą funkcję debugowania w programie Visual Studio

Jeśli potrzebujesz pomocy w mapowaniu zadania debugowania na poprawną funkcję debugera programu Visual Studio, który jest istotny, Skorzystaj z linków dostępnych w tym artykule. Lista zadań w tym miejscu obejmuje typowe zadania, takie jak Wstrzymywanie kodu do debugowania, sprawdzanie zmiennych i wysyłanie komunikatów do okna **danych wyjściowych** . Jeśli potrzebujesz przeglądu funkcji debugera, zobacz [najpierw Przyjrzyj się debugerowi](debugger-feature-tour.md) .

## <a name="fix-an-exception"></a>Naprawianie wyjątku

- Zobacz [Rozwiązywanie wyjątku](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Wstrzymaj uruchamianie kodu

- **Wstrzymaj uruchamianie kodu, aby sprawdzić wiersz kodu, który może zawierać usterkę**

  Ustaw punkt przerwania. Aby uzyskać więcej informacji, zobacz [Używanie punktów przerwania](using-breakpoints.md).

- **Wstrzymywanie i sprawdzanie aplikacji po osiągnięciu określonego stanu**

  Wypróbuj warunkowy punkt przerwania, aby kontrolować miejsce i czas, w którym punkt przerwania jest aktywowany przy użyciu logiki warunkowej. Aby uzyskać więcej informacji, zobacz [warunki punktu przerwania](using-breakpoints.md#breakpoint-conditions).

- **Wstrzymaj kod tylko wtedy, gdy zmienia się właściwość lub wartość określonego obiektu**

  Dla języka C++ Ustaw [punkt przerwania danych](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
  ::: moniker range=">= vs-2019"
  W przypadku aplikacji korzystających z platformy .NET Core 3 można również ustawić [punkt przerwania danych](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
  ::: moniker-end

  W przeciwnym wypadku dla języków C# i F # można [śledzić identyfikator obiektu za pomocą warunkowego punktu przerwania](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Wstrzymywanie kodu wewnątrz pętli w określonej iteracji**

  Ustaw punkt przerwania z użyciem **liczby trafień** jako warunku. Aby uzyskać więcej informacji, zobacz [liczba trafień](using-breakpoints.md#set-a-hit-count-condition).

- **Wstrzymaj kod na początku funkcji, jeśli znasz nazwę funkcji, ale nie jej lokalizację**

  Można to zrobić za pomocą punktu przerwania funkcji. Aby uzyskać więcej informacji, zobacz [ustawianie punktów przerwania funkcji](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Wstrzymaj kod na początku wielu funkcji o tej samej nazwie**

  Jeśli masz wiele funkcji o tej samej nazwie (przeciążone funkcje lub funkcje w różnych projektach), możesz użyć [punktu przerwania funkcji](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Zarządzanie i śledzenie punktów przerwania**

  Użyj okna **punkty przerwania** . Aby uzyskać więcej informacji, zobacz [Zarządzanie punktami przerwania](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

- **Wstrzymaj kod i Debuguj, gdy zostanie zgłoszony określony obsługiwany lub nieobsługiwany wyjątek**

  Chociaż pomocnik wyjątku pokazuje, gdzie wystąpił błąd, jeśli chcesz wstrzymać i debugować konkretny błąd, możesz [powiedzieć, że debuger zostanie przerwany w przypadku zgłoszenia wyjątku](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

- **Ustawianie punktu przerwania na podstawie stosu wywołań**

  Jeśli chcesz wstrzymywać i debugować kod podczas badania przepływu wykonywania lub wyświetlania funkcji w oknach **stosu wywołań** , zobacz [Ustawianie punktu przerwania w oknie stosu wywołań](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Wstrzymywanie kodu w określonej instrukcji zestawu**

  Można to zrobić przez [ustawienie punktu przerwania w oknie demontażu](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Wykonaj kod

- **Poznaj polecenia, aby przejść przez kod podczas debugowania**

  Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Sprawdzanie danych

- **Sprawdź wartość zmiennych podczas uruchamiania aplikacji**

  Umieść wskaźnik myszy nad zmiennymi przy użyciu [etykietek danych](view-data-values-in-data-tips-in-the-code-editor.md) lub [Sprawdź zmienne w oknie Ustawienia autoodtwarzania i lokalne](autos-and-locals-windows.md).

- **Obserwuj zmianę wartości określonej zmiennej**

  Ustaw czujkę na zmiennej. Aby uzyskać więcej informacji, zobacz [Ustawianie typu czujki dla zmiennych](watch-and-quickwatch-windows.md).

- **Wyświetlanie ciągów, które są zbyt długie dla okna debugera**

  Otwórz wbudowany [wizualizator ciągu](view-strings-visualizer.md) podczas debugowania.

## <a name="debug-an-app-that-is-already-running"></a>Debuguj aplikację, która jest już uruchomiona

- Zobacz [dołączanie do uruchomionych procesów](attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="debug-multithreaded-applications"></a>Debugowanie aplikacji wielowątkowych

- Zobacz [debugowanie aplikacji wielowątkowych](debug-multithreaded-applications-in-visual-studio.md).

## <a name="configure-debugging"></a>Konfigurowanie debugowania

- **Konfigurowanie ustawień debugera**

  Aby skonfigurować opcje debugera i ustawienia projektu debugera, zobacz [Ustawienia debugera i przygotowania](debugger-settings-and-preparation.md).

- **Dostosuj informacje wyświetlane w debugerze**

  Możesz chcieć wyświetlić informacje inne niż typ obiektu jako wartość w różnych oknach debugera. W przypadku języka C#, Visual Basic, F # i kodu C++/CLI należy użyć atrybutu [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Aby uzyskać bardziej zaawansowane opcje, można również dostosować interfejs użytkownika, tworząc [wizualizację niestandardową](create-custom-visualizers-of-data.md).

  W przypadku natywnego języka C++ Użyj [struktury NatVis](create-custom-views-of-native-objects.md).

## <a name="additional-tasks"></a>Dodatkowe zadania

- **Edytuj kod podczas sesji debugowania**

  Użyj [Edytuj i Kontynuuj](edit-and-continue.md). W przypadku języka XAML Użyj [gorącego ładowania XAML](../xaml-tools/xaml-hot-reload.md).

- **Wysyłaj komunikaty do okna danych wyjściowych bez modyfikowania kodu**

  Ustaw punkt śledzenia. Aby uzyskać więcej informacji, zobacz [using punkty śledzenia](using-tracepoints.md).

- **Wyświetlanie kolejności, w której są wywoływane funkcje**

  Zobacz [, jak wyświetlić stos wywołań](how-to-use-the-call-stack-window.md).

- **Debugowanie na maszynach zdalnych**

  Zobacz [debugowanie zdalne](remote-debugging.md).

- **Rozwiązywanie problemów z wydajnością**

  Zobacz [pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)

---
title: Często zadawane pytania — znajdowanie funkcji debugowania
description: Często zadawane pytania, które ułatwiają identyfikację funkcji debugera, która pomoże debugować aplikację
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
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800497"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Często zadawane pytania — znajdowanie funkcji debugowania potrzebnej w Visual Studio

Jeśli potrzebujesz pomocy w zamapowania zadania debugowania na właściwą funkcję odpowiedniego debugera Visual Studio, użyj linków podanych w tym artykule. Lista zadań w tym miejscu zawiera typowe zadania, takie jak wstydowanie kodu do debugowania, sprawdzanie zmiennych i wysyłanie komunikatów do **okna Dane** wyjściowe. Jeśli potrzebujesz przeglądu funkcji debugera, zobacz [Najpierw przyjrzyj się debugerowi.](debugger-feature-tour.md)

## <a name="fix-an-exception"></a>Naprawianie wyjątku

- Zobacz [Naprawianie wyjątku](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Wstrzymywanie uruchomionego kodu

- **Wstrzymywanie uruchamiania kodu w celu sprawdzenia wiersza kodu, który może zawierać usterkę**

  Ustaw punkt przerwania. Aby uzyskać więcej informacji, zobacz [Using breakpoints (Używanie punktów przerwania).](using-breakpoints.md)

- **Wstrzymywanie i sprawdzanie aplikacji po osiągnięciu określonego stanu**

  Wypróbuj warunkowy punkt przerwania, aby kontrolować, gdzie i kiedy punkt przerwania zostanie aktywowany przy użyciu logiki warunkowej. Aby uzyskać więcej informacji, zobacz [Warunki punktu przerwania](using-breakpoints.md#breakpoint-conditions).

- **Wstrzymywanie kodu tylko wtedy, gdy zmienia się właściwość lub wartość określonego obiektu**

  Dla języka C++ ustaw punkt [przerwania danych](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
  ::: moniker range=">= vs-2019"
  W przypadku aplikacji korzystających z programu .NET Core 3 można również ustawić [punkt przerwania danych.](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)
  ::: moniker-end

  W przeciwnym razie tylko w przypadku języka C# i F# można śledzić identyfikator obiektu [z warunkowym punktem przerwania](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Wstrzymywanie kodu wewnątrz pętli w określonej iteracji**

  Ustaw punkt przerwania przy użyciu **liczby trafień** jako warunku. Aby uzyskać więcej informacji, zobacz [Liczba trafień](using-breakpoints.md#set-a-hit-count-condition).

- **Wstrzymywanie kodu na początku funkcji, gdy znasz nazwę funkcji, ale nie jej lokalizację**

  Można to zrobić za pomocą punktu przerwania funkcji. Aby uzyskać więcej informacji, zobacz [Set function breakpoints (Ustawianie punktów przerwania funkcji).](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)

- **Wstrzymywanie kodu na początku wielu funkcji o tej samej nazwie**

  Jeśli masz wiele funkcji o tej samej nazwie (przeciążone funkcje lub funkcje w różnych projektach), możesz użyć [punktu przerwania funkcji](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Śledzenie punktów przerwania i zarządzanie nimi**

  Użyj **okna Punkty przerwania.** Aby uzyskać więcej informacji, zobacz [Zarządzanie punktami przerwania.](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)

- **Wstrzymywanie kodu i debugowanie po wyrzuceniu określonego obsługiwanego lub nieobsługiwanego wyjątku**

  Mimo że Pomocnik wyjątków pokazuje, gdzie wystąpił błąd, jeśli chcesz wstrzymać i debugować określony błąd, możesz poinformować debuger, aby przerywał działania po [wyrzuceniu wyjątku](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

- **Ustawianie punktu przerwania ze stosu wywołań**

  Jeśli chcesz wstrzymać i debugować kod podczas badania  przepływu wykonywania lub przeglądania funkcji w oknach stosu wywołań, zobacz Ustawianie punktu przerwania [w oknie stosu wywołań](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Wstrzymywanie kodu dla określonej instrukcji zestawu**

  Można to zrobić, [ustawiając punkt przerwania w oknie Dezmisja.](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)

## <a name="execute-code"></a>Wykonywanie kodu

- **Poznasz polecenia umożliwiające krokowe przechodzinie przez kod podczas debugowania**

  Aby uzyskać więcej informacji, zobacz [Navigate code with the debugger (Nawigowanie po kodzie za pomocą debugera).](navigating-through-code-with-the-debugger.md)

## <a name="inspect-data"></a>Sprawdzanie danych

- **Sprawdzanie wartości zmiennych podczas uruchamiania aplikacji**

  Umieść kursor na zmiennych przy [użyciu porad dotyczących danych](view-data-values-in-data-tips-in-the-code-editor.md) lub sprawdź zmienne w oknie Wartości automatyczne i zmienne [lokalne.](autos-and-locals-windows.md)

- **Obserwowanie zmieniającej się wartości określonej zmiennej**

  Ustaw zegarek na zmiennej . Aby uzyskać więcej informacji, zobacz [Ustawianie zegarka dla zmiennych](watch-and-quickwatch-windows.md).

- **Wyświetlanie ciągów, które są zbyt długie dla okna debugera**

  Otwórz wbudowany wizualizator [ciągów](view-strings-visualizer.md) podczas debugowania.

## <a name="debug-an-app-that-is-already-running"></a>Debugowanie aplikacji, która jest już uruchomiona

- Zobacz [Dołączanie do uruchomionych procesów.](attach-to-running-processes-with-the-visual-studio-debugger.md)

## <a name="debug-multithreaded-applications"></a>Debugowanie aplikacji wielowątkowych

- Zobacz [Debugowanie aplikacji wielowątkowych.](debug-multithreaded-applications-in-visual-studio.md)

## <a name="configure-debugging"></a>Konfigurowanie debugowania

- **Konfigurowanie ustawień debugera**

  Aby skonfigurować opcje debugera i ustawienia projektu debugera, zobacz [Ustawienia debugera i przygotowanie](debugger-settings-and-preparation.md).

- **Dostosowywanie informacji wyświetlanych w debugerze**

  Informacje inne niż typ obiektu mogą być wyświetlane jako wartość w różnych oknach debugera. W przypadku kodu języka C#, Visual Basic, F# i C++/CLI użyj [atrybutu DebuggerDisplay.](using-the-debuggerdisplay-attribute.md) Aby uzyskać bardziej zaawansowane opcje, możesz również dostosować interfejs użytkownika, tworząc [niestandardowy wizualizator](create-custom-visualizers-of-data.md).

  W przypadku natywnego języka C++, użyj [struktury NatVis](create-custom-views-of-native-objects.md).

## <a name="additional-tasks"></a>Dodatkowe zadania

- **Edytowanie kodu podczas sesji debugowania**

  Użyj [funkcji Edytuj i kontynuuj.](edit-and-continue.md) W przypadku języka XAML [użyj Przeładowywanie kodu XAML na gorąco](../xaml-tools/xaml-hot-reload.md).

- **Wysyłanie komunikatów do okna Danych wyjściowych bez modyfikowania kodu**

  Ustaw punkt śledzenia. Aby uzyskać więcej informacji, zobacz [Using tracepoints (Używanie punktów śledzenia).](using-tracepoints.md)

- **Wyświetlanie kolejności, w której są wywoływane funkcje**

  Zobacz How to view the call stack (Jak [wyświetlić stos wywołań).](how-to-use-the-call-stack-window.md)

- **Debugowanie na maszynach zdalnych**

  Zobacz [Zdalne debugowanie](remote-debugging.md).

- **Rozwiązywanie problemów z wydajnością**

  Zobacz [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)

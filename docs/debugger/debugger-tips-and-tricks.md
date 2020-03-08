---
title: Porady i wskazówki w debugerze
description: Dowiedz się więcej o pewnych funkcjach mniejszym znane obsługiwanych przez debuger programu Visual Studio
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409335"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Dowiedz się więcej i porady dotyczące wydajności w debugerze programu Visual Studio

Przeczytaj ten temat, aby dowiedzieć się kilka produktywność porady i wskazówki dla debugera programu Visual Studio. Aby zapoznać się z podstawowymi funkcjami debugera, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md). Niektóre obszary, które nie są objęte Przewodnik po funkcjach omówione w tym temacie.

## <a name="pin-data-tips"></a>Porady dotyczące danych numeru PIN

Często tak kursor porady dotyczące danych, podczas debugowania, możesz przypiąć poradę danych dla zmiennej, aby zapewnić sobie szybki dostęp. Zmienna pozostaje przypięty nawet po ponownym uruchomieniu komputera. Aby przypiąć Porada danych, kliknij ikonę pinezki umieszczeniu go. Możesz przypiąć wiele zmiennych.

![Przypinanie etykietki danych](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Edytuj kod i Kontynuuj debugowanie (C#, VB, C++)

W większości języków obsługiwanych przez program Visual Studio można edytować swój kod w trakcie sesji debugowania i kontynuować debugowanie. Aby skorzystać z tej funkcji, kliknij swój kod z kursorem podczas wstrzymania w debugerze, dokonaj edycji, a następnie naciśnij klawisz **F5**, **F10**lub **F11** , aby kontynuować debugowanie.

![Edytuj i Kontynuuj debugowanie](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Aby uzyskać więcej informacji na temat korzystania z funkcji i ograniczeń funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Edytuj kod XAML i Kontynuuj debugowanie

Aby zmodyfikować kod XAML podczas sesji debugowania, zobacz [pisanie i debugowanie uruchomionego kodu XAML przy użyciu gorącego ponownego ładowania XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Debugowanie problemów, które są trudne do odtworzenia

Jeśli jest trudne lub czasochłonne ponownie utworzyć określonego stanu w swojej aplikacji, należy rozważyć, czy korzystanie z warunkowego punktu przerwania, może pomóc. Możesz użyć [warunkowych punktów przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) i filtrować punkty przerwania, aby uniknąć podziału kodu aplikacji do momentu, aż aplikacja przejdzie do żądanego stanu (na przykład stan, w którym zmienna przechowuje złe dane). Można ustawić przy użyciu wyrażeń, filtry, liczniki trafień i tak dalej.

#### <a name="to-create-a-conditional-breakpoint"></a>Aby utworzyć warunkowego punktu przerwania

1. Kliknij prawym przyciskiem myszy ikonę punktu przerwania (czerwoną kulkę) i wybierz pozycję **warunki**.

2. W oknie **Ustawienia punktu przerwania** wpisz wyrażenie.

    ![Warunkowy punkt przerwania](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Jeśli interesuje Cię inny typ warunku, w oknie dialogowym **Ustawienia punktu przerwania** wybierz opcję **Filtr** zamiast **wyrażenia warunkowego** , a następnie postępuj zgodnie ze wskazówkami dotyczącymi filtru.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Skonfiguruj dane, które mają być wyświetlane w debugerze

W C#przypadku, Visual Basic i C++ (C++tylko kod/CLI) można poinstruować debuger, jakie informacje mają być wyświetlane za pomocą atrybutu [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) . W C++ przypadku kodu można wykonać te same czynności przy użyciu [wizualizacji Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Zmień przepływ wykonania

Za pomocą debugera wstrzymana na wiersz kodu, za pomocą myszy do pobrania wskaźnika żółta strzałka po lewej stronie. Przesuń wskaźnik żółta strzałka do innego punktu w ścieżce wykonywania kodu. Następnie przy użyciu F5 lub polecenie krok ma kontynuować wykonywanie aplikacji.

![Przenieś wskaźnik wykonywania](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Przenieś wskaźnik wykonywania")

Zmieniając przepływ wykonania, można wykonać czynności, jak przetestować różne ścieżki wykonywania lub uruchom ponownie kodu bez ponownego uruchamiania debugera.

> [!WARNING]
> Często muszą być ostrożnym z tej funkcji, a następnie zostanie wyświetlone ostrzeżenie w etykietce narzędzia. Zbyt mogą pojawić się inne ostrzeżenia. Przeniesienie wskaźnika nie można przywrócić aplikację do wcześniejszego stanu aplikacji.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Śledzenie obiektów poza zakresem (C#, Visual Basic)

Można łatwo wyświetlać zmienne przy użyciu okien debugera, takich jak okno **czujka** . Jednak gdy zmienna wykracza poza zakres w oknie **czujki** , można zauważyć, że jest wyszarzona. W niektórych scenariuszach dla aplikacji wartość zmiennej może ulec zmianie, nawet gdy zmienna jest poza zakresem, i może chcieć ją dokładnie obejrzeć (na przykład zmienna może uzyskać elementy bezużyteczne). Można śledzić zmienną przez utworzenie w oknie **czujki** identyfikatora obiektu.

#### <a name="to-create-an-object-id"></a>Aby utworzyć identyfikator obiektu

1. Ustaw punkt przerwania w pobliżu zmiennej, którą chcesz śledzić.

2. Uruchom Debuger (**F5**) i Zatrzymaj w punkcie przerwania.

3. Znajdź zmienną w oknie **zmiennych lokalnych** (**debuguj > lokalne > systemu Windows**), kliknij prawym przyciskiem myszy zmienną i wybierz pozycję **Utwórz identyfikator obiektu**.

    ![Utwórz identyfikator obiektu](../debugger/media/dbg-tips-watch-create-object-id.png "Nie ObjectID")

4. Powinna zostać wyświetlona **$** Plus cyfra w oknie **zmiennych lokalnych** . Ta zmienna jest identyfikator obiektu.

5. Kliknij prawym przyciskiem myszy zmienną identyfikator obiektu i wybierz polecenie **Dodaj czujkę**.

Aby uzyskać więcej informacji, zobacz [Tworzenie identyfikatora obiektu](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Wyświetl wartości zwracane dla funkcji

Aby wyświetlić wartości zwracane przez funkcje, przyjrzyj się funkcjom, które pojawiają się w oknie **Autostarty** podczas wykonywania kodu. Aby wyświetlić wartość zwracaną dla funkcji, upewnij się, że funkcja, która Cię interesuje, została już wykonana (naciśnij klawisz **F10** , jeśli aktualnie zatrzymano w wywołaniu funkcji). Jeśli okno jest zamknięte, użyj **> debugowania > Windows** , aby otworzyć okno **autostarty** .

![Okno Autokorekty](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Ponadto możesz wprowadzić funkcje w oknie **bezpośrednim** , aby wyświetlić wartości zwracane. (Otwórz go za pomocą polecenia **Debug > Windows > natychmiastowe**).

![Okno bezpośrednie](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Możesz również użyć [pseudozmiennych pokazanych](../debugger/pseudovariables.md) w oknie **czujka** i **natychmiastowe** , na przykład `$ReturnValue`.

## <a name="string_visualizer"></a>Inspekcja ciągów w wizualizatorze

Podczas pracy z ciągami, może być przydatne wyświetlić cały ciąg sformatowany. Aby wyświetlić ciąg w formacie zwykłego tekstu, XML, HTML lub JSON, kliknij ikonę lupy, ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora") , a następnie umieść wskaźnik myszy na zmiennej zawierającej wartość ciągu.

![Otwórz wizualizator ciągu](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Wizualizator ciągu mogą pomóc Ci dowiedzieć się, czy ciąg jest źle sformułowany, w zależności od typu string. Na przykład pole pustej **wartości** wskazuje, że ciąg nie jest rozpoznawany przez typ wizualizatora. Aby uzyskać więcej informacji, zobacz [okno dialogowe wizualizator ciągu](../debugger/string-visualizer-dialog-box.md).

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Dla kilku innych typów, takich jak obiekty DataSet i DataTable, które pojawiają się w oknach debugera, można także otworzyć wbudowany wizualizator.

## <a name="break-into-code-on-handled-exceptions"></a>Wejdź do kodu dotyczące wyjątków obsłużonych

Debuger przerywa kodu na nieobsłużonych wyjątkach. Jednak obsłużone wyjątki (takie jak wyjątki występujące w bloku `try/catch`) mogą być również źródłem błędów i warto zbadać, kiedy wystąpią. Można skonfigurować debuger, aby zerwać kod dla obsłużonych wyjątków, a także Konfigurując opcje w oknie dialogowym **Ustawienia wyjątku** . Otwórz to okno dialogowe, wybierając pozycję **debuguj > ustawienia wyjątków > systemu Windows**.

Okno dialogowe **Ustawienia wyjątku** umożliwia poinformowanie debugera o konieczności podziału kodu na określone wyjątki. Na poniższej ilustracji debuger dzieli się na kod za każdym razem, gdy występuje `System.NullReferenceException`. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami](../debugger/managing-exceptions-with-the-debugger.md).

![Okno dialogowe Ustawienia wyjątku](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Debugowanie zakleszczeń i sytuacje wyścigu

Jeśli musisz debugować rodzaje problemów, które są wspólne dla aplikacji wielowątkowych, często pomaga można wyświetlić lokalizacji wątków podczas debugowania. Można to łatwo zrobić przy użyciu przycisku **Pokaż wątki w źródle** .

#### <a name="to-show-threads-in-your-source-code"></a>Aby wyświetlić wątków w kodzie źródłowym

1. Podczas debugowania kliknij przycisk **Pokaż wątki w źródle** , ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") na pasku narzędzi **debugowania** .

2. Spójrz na oprawę w lewej części okna. W tym wierszu zostanie wyświetlony ![znacznik](../debugger/media/dbg-thread-marker.png "ThreadMarker") wątku ikony *znacznika wątku* , który przypomina dwa wątki. Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji.

    Należy zauważyć, że znacznika wątku może częściowo zasłonięte przez punkt przerwania.

3. Umieść wskaźnik myszy nad znacznika wątku. Pojawi się DataTip. DataTip informuje numer identyfikacyjny nazwy i wątku dla każdego wątku zatrzymania.

    Można również wyświetlić lokalizacje wątków w [oknie stosów równoległych](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Sprawdź ładunków dla usług sieci web i zasobów sieciowych (systemu Windows UWP)

W aplikacjach platformy UWP można analizować operacje sieciowe wykonywane przy użyciu interfejsu API `Windows.Web.Http`. To narzędzie służy do debugowania usług sieci web i zasobami sieciowymi. Aby użyć narzędzia, wybierz pozycję **debuguj > Narzędzie do oceny wydajności**. Wybierz pozycję **Sieć**, a następnie wybierz pozycję **Uruchom**. W aplikacji przejdź przez scenariusz, który używa `Windows.Web.Http`, a następnie wybierz polecenie **Zatrzymaj zbieranie** , aby wygenerować raport.

![Narzędzie profilowania użycia sieci](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Wybierz operację podsumowania bardziej szczegółowo widokami.

![Szczegółowe informacje w narzędziu Użycie sieci](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Aby uzyskać więcej informacji, zobacz temat [użycie sieci](../profiling/network-usage.md).
::: moniker-end

## <a name="modules_window"></a>Uzyskaj więcej informacji na temat sposobu dołączania debugera do aplikacji (C#, C++Visual Basic, F#)

Aby dołączyć do uruchomionej aplikacji, debuger ładuje pliki symboli (.pdb), generowany dla dokładnie tej samej kompilacji aplikacji, którą próbujesz debugować. W niektórych przypadkach nieco znajomości pliki symboli mogą być pomocne. Można ocenić, jak program Visual Studio ładuje pliki symboli przy użyciu okna **moduły** .

Otwórz okno **modułów** podczas debugowania, wybierając pozycję **debuguj > moduły > systemu Windows**. Okno **moduły** pozwala określić, które moduły debuger jest traktowany jako kod użytkownika lub [*mój kod*](../debugger/just-my-code.md), oraz stan ładowania symboli dla modułu. W większości scenariuszy debuger automatycznie odnajduje pliki symboli dla kodu użytkownika, ale jeśli chcesz wkroczyć (lub debugować) kod .NET, kod systemowy lub kod biblioteki innej firmy, konieczne jest wykonanie dodatkowych kroków w celu uzyskania poprawnych plików symboli.

![Wyświetl informacje o symbolach w oknie Moduły](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Informacje o symbolach można załadować bezpośrednio z okna **moduły** , klikając je prawym przyciskiem myszy i wybierając pozycję **Załaduj symbole**.

Czasami deweloperzy aplikacji dostarczaj aplikacje bez pasującego pliki symboli (w celu zmniejszenia rozmiaru), ale zachować kopię pasujących symboli plików kompilacji, dzięki czemu ich później debugowania wydanej wersji.

Aby dowiedzieć się, jak debuger klasyfikuje kod jako kod użytkownika, zobacz [tylko mój kod](../debugger/just-my-code.md). Aby dowiedzieć się więcej na temat plików symboli, zobacz [Określanie symboli (. pdb) i plików źródłowych w debugerze programu Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Dowiedz się więcej

Aby uzyskać dodatkowe porady i wskazówki oraz bardziej szczegółowe informacje Zobacz te Posty na blogu:

- [7 małe znane Hacks do debugowania w programie Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 ukrytych Gems w programie Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Zobacz też

[Skróty klawiaturowe](../ide/productivity-shortcuts.md)

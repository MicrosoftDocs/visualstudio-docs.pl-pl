---
title: Porady i wskazówki w debugerze
description: Dowiedz się więcej o funkcjach, które są obsługiwane przez debuger programu Visual Studio
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
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188621"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Poznaj porady dotyczące produktywności i wskazówki dotyczące debugera w programie Visual Studio

Zapoznaj się z tym tematem, aby poznać kilka porad i wskazówek dotyczących produktywności dla debugera programu Visual Studio. Aby zapoznać się z podstawowymi funkcjami debugera, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md). W tym temacie omówiono niektóre obszary, które nie znajdują się w samouczku dotyczącym funkcji.

## <a name="pin-data-tips"></a>Przypnij porady dotyczące danych

Jeśli podczas debugowania często przemieszczono wskaźnik myszy, możesz przypiąć etykietkę danych dla zmiennej, aby zapewnić sobie szybki dostęp. Zmienna pozostaje przypięta nawet po ponownym uruchomieniu. Aby przypiąć wskazówkę dotyczącą danych, kliknij ikonę pinezki podczas przesuwania nad nią. Możesz przypiąć wiele zmiennych.

![Przypinanie etykietki danych](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Edytuj swój kod i Kontynuuj debugowanie (C#, VB, C++)

W większości języków obsługiwanych przez program Visual Studio można edytować kod w trakcie sesji debugowania i kontynuować debugowanie. Aby skorzystać z tej funkcji, kliknij swój kod z kursorem podczas wstrzymania w debugerze, dokonaj edycji, a następnie naciśnij klawisz **F5**, **F10**lub **F11** , aby kontynuować debugowanie.

![Edytuj i Kontynuuj debugowanie](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Aby uzyskać więcej informacji na temat korzystania z funkcji i ograniczeń funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Edytuj kod XAML i Kontynuuj debugowanie

Aby zmodyfikować kod XAML podczas sesji debugowania, zobacz [pisanie i debugowanie uruchomionego kodu XAML przy użyciu gorącego ponownego ładowania XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problemy z debugowaniem, które są trudne do odtworzenia

Jeśli jest trudne lub czasochłonne ponowne utworzenie określonego stanu w aplikacji, należy wziąć pod uwagę, czy można ułatwić korzystanie z warunkowego punktu przerwania. Możesz użyć [warunkowych punktów przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) i filtrować punkty przerwania, aby uniknąć podziału kodu aplikacji do momentu, aż aplikacja przejdzie do żądanego stanu (na przykład stan, w którym zmienna przechowuje złe dane). Można ustawić warunki przy użyciu wyrażeń, filtrów, liczby trafień i tak dalej.

#### <a name="to-create-a-conditional-breakpoint"></a>Aby utworzyć warunkowy punkt przerwania

1. Kliknij prawym przyciskiem myszy ikonę punktu przerwania (czerwoną kulkę) i wybierz pozycję **warunki**.

2. W oknie **Ustawienia punktu przerwania** wpisz wyrażenie.

    ![Warunkowy punkt przerwania](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Jeśli interesuje Cię inny typ warunku, w oknie dialogowym **Ustawienia punktu przerwania** wybierz opcję **Filtr** zamiast **wyrażenia warunkowego** , a następnie postępuj zgodnie ze wskazówkami dotyczącymi filtru.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Skonfiguruj dane, które mają być wyświetlane w debugerze

W C#przypadku, Visual Basic i C++ (C++tylko kod/CLI) można poinstruować debuger, jakie informacje mają być wyświetlane za pomocą atrybutu [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) . W C++ przypadku kodu można wykonać te same czynności przy użyciu [wizualizacji Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Zmień przepływ wykonywania

Gdy debuger wstrzymał się w wierszu kodu, użyj myszy, aby uzyskać żółty wskaźnik strzałkowy po lewej stronie. Przenieś żółty wskaźnik strzałkowy do innego punktu w ścieżce wykonywania kodu. Następnie użyj klawisza F5 lub kroku, aby kontynuować działanie aplikacji.

![Przenieś wskaźnik wykonywania](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Przenieś wskaźnik wykonywania")

Zmieniając przepływ wykonywania, można wykonywać operacje, takie jak testowanie różnych ścieżek wykonywania kodu lub ponowne uruchamianie kodu bez ponownego uruchamiania debugera.

> [!WARNING]
> Często należy zachować ostrożność dzięki tej funkcji, a w etykietce narzędzia zostanie wyświetlone ostrzeżenie. Mogą również pojawić się inne ostrzeżenia. Przeniesienie wskaźnika nie może przywrócić aplikacji do wcześniejszego stanu aplikacji.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Śledzenie obiektu poza zakresem (C#, Visual Basic)

Można łatwo wyświetlać zmienne przy użyciu okien debugera, takich jak okno **czujka** . Jednak gdy zmienna wykracza poza zakres w oknie **czujki** , można zauważyć, że jest wyszarzona. W niektórych scenariuszach dla aplikacji wartość zmiennej może ulec zmianie, nawet gdy zmienna jest poza zakresem, i może chcieć ją dokładnie obejrzeć (na przykład zmienna może uzyskać elementy bezużyteczne). Można śledzić zmienną przez utworzenie w oknie **czujki** identyfikatora obiektu.

#### <a name="to-create-an-object-id"></a>Aby utworzyć identyfikator obiektu

1. Ustaw punkt przerwania w sąsiedztwie zmiennej, która ma być śledzona.

2. Uruchom Debuger (**F5**) i Zatrzymaj w punkcie przerwania.

3. Znajdź zmienną w oknie **zmiennych lokalnych** (**debuguj > lokalne > systemu Windows**), kliknij prawym przyciskiem myszy zmienną i wybierz pozycję **Utwórz identyfikator obiektu**.

    ![Utwórz identyfikator obiektu](../debugger/media/dbg-tips-watch-create-object-id.png "Nie ObjectID")

4. Powinna zostać wyświetlona **$** Plus cyfra w oknie **zmiennych lokalnych** . Ta zmienna jest IDENTYFIKATORem obiektu.

5. Kliknij prawym przyciskiem myszy zmienną identyfikator obiektu i wybierz polecenie **Dodaj czujkę**.

Aby uzyskać więcej informacji, zobacz [Tworzenie identyfikatora obiektu](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Wyświetlanie wartości zwracanych dla funkcji

Aby wyświetlić wartości zwracane przez funkcje, przyjrzyj się funkcjom, które pojawiają się w oknie **Autostarty** podczas wykonywania kodu. Aby wyświetlić wartość zwracaną dla funkcji, upewnij się, że funkcja, która Cię interesuje, została już wykonana (naciśnij klawisz **F10** , jeśli aktualnie zatrzymano w wywołaniu funkcji). Jeśli okno jest zamknięte, użyj **> debugowania > Windows** , aby otworzyć okno **autostarty** .

![Okno Autokorekty](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Ponadto możesz wprowadzić funkcje w oknie **bezpośrednim** , aby wyświetlić wartości zwracane. (Otwórz go za pomocą polecenia **Debug > Windows > natychmiastowe**).

![Okno bezpośrednie](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Możesz również użyć [pseudozmiennych pokazanych](../debugger/pseudovariables.md) w oknie **czujka** i **natychmiastowe** , na przykład `$ReturnValue`.

## <a name="string_visualizer"></a>Inspekcja ciągów w wizualizatorze

Podczas pracy z ciągami pomocne może być wyświetlenie całego sformatowanego ciągu. Aby wyświetlić ciąg w formacie zwykłego tekstu, XML, HTML lub JSON, kliknij ikonę lupy, ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora") , a następnie umieść wskaźnik myszy na zmiennej zawierającej wartość ciągu.

![Otwórz wizualizator ciągu](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Wizualizator ciągu może pomóc dowiedzieć się, czy ciąg jest źle sformułowany, w zależności od typu ciągu. Na przykład pole pustej **wartości** wskazuje, że ciąg nie jest rozpoznawany przez typ wizualizatora. Aby uzyskać więcej informacji, zobacz [okno dialogowe wizualizator ciągu](../debugger/string-visualizer-dialog-box.md).

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Dla kilku innych typów, takich jak obiekty DataSet i DataTable, które pojawiają się w oknach debugera, można także otworzyć wbudowany wizualizator.

## <a name="break-into-code-on-handled-exceptions"></a>Przerwij do kodu w przypadku obsłużonych wyjątków

Debuger dzieli się na kod w przypadku nieobsłużonych wyjątków. Jednak obsłużone wyjątki (takie jak wyjątki występujące w bloku `try/catch`) mogą być również źródłem błędów i warto zbadać, kiedy wystąpią. Można skonfigurować debuger, aby zerwać kod dla obsłużonych wyjątków, a także Konfigurując opcje w oknie dialogowym **Ustawienia wyjątku** . Otwórz to okno dialogowe, wybierając pozycję **debuguj > ustawienia wyjątków > systemu Windows**.

Okno dialogowe **Ustawienia wyjątku** umożliwia poinformowanie debugera o konieczności podziału kodu na określone wyjątki. Na poniższej ilustracji debuger dzieli się na kod za każdym razem, gdy występuje `System.NullReferenceException`. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami](../debugger/managing-exceptions-with-the-debugger.md).

![Okno dialogowe Ustawienia wyjątku](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Zakleszczenia debugowania i warunki wyścigu

Jeśli konieczne jest debugowanie rodzajów problemów wspólnych dla aplikacji wielowątkowych, często pomocne jest wyświetlenie lokalizacji wątków podczas debugowania. Można to łatwo zrobić przy użyciu przycisku **Pokaż wątki w źródle** .

#### <a name="to-show-threads-in-your-source-code"></a>Aby wyświetlić wątki w kodzie źródłowym

1. Podczas debugowania kliknij przycisk **Pokaż wątki w źródle** , ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") na pasku narzędzi **debugowania** .

2. Spójrz na odstępy po lewej stronie okna. W tym wierszu zostanie wyświetlony ![znacznik](../debugger/media/dbg-thread-marker.png "ThreadMarker") wątku ikony *znacznika wątku* , który przypomina dwa wątki. Znacznik wątku wskazuje, że wątek jest zatrzymany w tej lokalizacji.

    Należy zauważyć, że znacznik wątku może być częściowo ukrywany przez punkt przerwania.

3. Umieść wskaźnik myszy nad znacznikiem wątku. Zostanie wyświetlona etykietki danych. Etykietki danych informuje o nazwie i numerze wątku dla każdego zatrzymanego wątku.

    Można również wyświetlić lokalizacje wątków w [oknie stosów równoległych](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Sprawdzanie ładunków dla usług sieci Web i zasobów sieciowych (platformy UWP)

W aplikacjach platformy UWP można analizować operacje sieciowe wykonywane przy użyciu interfejsu API `Windows.Web.Http`. Tego narzędzia można użyć do debugowania usług sieci Web i zasobów sieciowych. Aby użyć narzędzia, wybierz pozycję **debuguj > Narzędzie do oceny wydajności**. Wybierz pozycję **Sieć**, a następnie wybierz pozycję **Uruchom**. W aplikacji przejdź przez scenariusz, który używa `Windows.Web.Http`, a następnie wybierz polecenie **Zatrzymaj zbieranie** , aby wygenerować raport.

![Narzędzie profilowania użycia sieci](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Wybierz operację w widoku Podsumowanie, aby wyświetlić więcej szczegółów.

![Szczegółowe informacje w narzędziu Użycie sieci](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Aby uzyskać więcej informacji, zobacz temat [użycie sieci](../profiling/network-usage.md).
::: moniker-end

## <a name="modules_window"></a>Uzyskaj więcej informacji na temat sposobu dołączania debugera do aplikacji (C#, C++Visual Basic, F#)

Aby dołączyć do uruchomionej aplikacji, debuger ładuje pliki symboli (. pdb) wygenerowane dla dokładnej kompilacji aplikacji, którą próbujesz debugować. W niektórych scenariuszach pomocne może być niewielka znajomość plików symboli. Można ocenić, jak program Visual Studio ładuje pliki symboli przy użyciu okna **moduły** .

Otwórz okno **modułów** podczas debugowania, wybierając pozycję **debuguj > moduły > systemu Windows**. Okno **moduły** pozwala określić, które moduły debuger jest traktowany jako kod użytkownika lub [*mój kod*](../debugger/just-my-code.md), oraz stan ładowania symboli dla modułu. W większości scenariuszy debuger automatycznie odnajduje pliki symboli dla kodu użytkownika, ale jeśli chcesz wkroczyć (lub debugować) kod .NET, kod systemowy lub kod biblioteki innej firmy, konieczne jest wykonanie dodatkowych kroków w celu uzyskania poprawnych plików symboli.

![Wyświetl informacje o symbolach w oknie Moduły](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Informacje o symbolach można załadować bezpośrednio z okna **moduły** , klikając je prawym przyciskiem myszy i wybierając pozycję **Załaduj symbole**.

Czasami deweloperzy aplikacji dostarczają aplikacje bez plików symboli pasujących (w celu zmniejszenia rozmiaru), ale przechowują kopię pasujących plików symboli dla kompilacji, aby umożliwić im debugowanie wydanej wersji później.

Aby dowiedzieć się, jak debuger klasyfikuje kod jako kod użytkownika, zobacz [tylko mój kod](../debugger/just-my-code.md). Aby dowiedzieć się więcej na temat plików symboli, zobacz [Określanie symboli (. pdb) i plików źródłowych w debugerze programu Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Dowiedz się więcej

Aby uzyskać dodatkowe porady i wskazówki oraz bardziej szczegółowe informacje, zobacz następujące wpisy w blogu:

- [7 małe znane Hacks do debugowania w programie Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 ukrytych Gems w programie Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Zobacz także

[Skróty klawiaturowe](../ide/productivity-shortcuts.md)

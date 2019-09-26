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
ms.openlocfilehash: 61c1efea7340425090adbdd1c9bc865c4a056d42
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "70987760"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Dowiedz się więcej i porady dotyczące wydajności w debugerze programu Visual Studio

Przeczytaj ten temat, aby dowiedzieć się kilka produktywność porady i wskazówki dla debugera programu Visual Studio. Aby zapoznać się z podstawowymi funkcjami debugera, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md). Niektóre obszary, które nie są objęte Przewodnik po funkcjach omówione w tym temacie.

## <a name="pin-data-tips"></a>Porady dotyczące danych numeru PIN

Często tak kursor porady dotyczące danych, podczas debugowania, możesz przypiąć poradę danych dla zmiennej, aby zapewnić sobie szybki dostęp. Zmienna pozostaje przypięty nawet po ponownym uruchomieniu komputera. Aby przypiąć Porada danych, kliknij ikonę pinezki umieszczeniu go. Możesz przypiąć wiele zmiennych.

![Przypinanie etykietki danych](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Edytuj kod i Kontynuuj debugowanie (C#, VB, C++)

W większości języków obsługiwanych przez program Visual Studio można edytować swój kod w trakcie sesji debugowania i kontynuować debugowanie. Aby użyć tej funkcji, kliknij przycisk w kodzie za pomocą kursora podczas wstrzymania w debugerze, zmiany upewnij i naciśnij klawisz **F5**, **F10**, lub **F11** aby kontynuować debugowanie.

![Edytuj i Kontynuuj debugowanie](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Aby uzyskać więcej informacji na temat korzystania z funkcji i ograniczenia dotyczące funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Edytuj kod XAML i Kontynuuj debugowanie

Aby zmodyfikować kod XAML podczas sesji debugowania, zobacz [pisanie i debugowanie uruchomionego kodu XAML przy użyciu gorącego ponownego ładowania XAML](xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Debugowanie problemów, które są trudne do odtworzenia

Jeśli jest trudne lub czasochłonne ponownie utworzyć określonego stanu w swojej aplikacji, należy rozważyć, czy korzystanie z warunkowego punktu przerwania, może pomóc. Możesz użyć [warunkowe punkty przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) i filtrów punktów przerwania, pozwala uniknąć przerwy w kodzie aplikacji, aż aplikacja przejdzie do żądanego stanu (takie jak stan, w którym zmienna jest przechowywanie złe dane). Można ustawić przy użyciu wyrażeń, filtry, liczniki trafień i tak dalej.

#### <a name="to-create-a-conditional-breakpoint"></a>Aby utworzyć warunkowego punktu przerwania

1. Kliknij prawym przyciskiem myszy ikona punktu przerwania (piłka czerwony), a następnie wybierz **warunki**.

2. W **ustawienia punktu przerwania** okna, typ na wyrażenie.

    ![Warunkowego punktu przerwania](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Jeśli interesuje Cię innego typu warunku, wybierz opcję **filtru** zamiast **wyrażenia warunkowego** w **ustawienia punktu przerwania** okno dialogowe, a następnie postępuj zgodnie z Porady dotyczące filtru.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Skonfiguruj dane, które mają być wyświetlane w debugerze

W C#przypadku, Visual Basic i C++ (C++tylko kod/CLI) można poinstruować debuger, jakie informacje mają być wyświetlane za pomocą atrybutu [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) . W C++ przypadku kodu można wykonać te same czynności przy użyciu [wizualizacji Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Zmień przepływ wykonania

Za pomocą debugera wstrzymana na wiersz kodu, za pomocą myszy do pobrania wskaźnika żółta strzałka po lewej stronie. Przesuń wskaźnik żółta strzałka do innego punktu w ścieżce wykonywania kodu. Następnie przy użyciu F5 lub polecenie krok ma kontynuować wykonywanie aplikacji.

![Przenieść wskaźnik wykonania](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Przesuń wskaźnik wykonania")

Zmieniając przepływ wykonania, można wykonać czynności, jak przetestować różne ścieżki wykonywania lub uruchom ponownie kodu bez ponownego uruchamiania debugera.

> [!WARNING]
> Często muszą być ostrożnym z tej funkcji, a następnie zostanie wyświetlone ostrzeżenie w etykietce narzędzia. Zbyt mogą pojawić się inne ostrzeżenia. Przeniesienie wskaźnika nie można przywrócić aplikację do wcześniejszego stanu aplikacji.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Śledzenie obiektów poza zakresem (C#, Visual Basic)

Można łatwo wyświetlić zmiennych przy użyciu okna debugera, takie jak **Obejrzyj** okna. Jednakże, gdy zmienna wykracza poza zakres w **Obejrzyj** okna, możesz zauważyć, że jest wyszarzona. W niektórych scenariuszach aplikacji wartość zmiennej może ulec zmianie, nawet kiedy zmienna jest poza zakresem i należy go ściśle Obejrzyj (na przykład zmienna może uzyskać bezużyteczne). Możesz śledzić zmiennej, tworząc Identyfikatora obiektu dla niego w **Obejrzyj** okna.

#### <a name="to-create-an-object-id"></a>Aby utworzyć identyfikator obiektu

1. Ustaw punkt przerwania w pobliżu zmiennej, którą chcesz śledzić.

2. Uruchom debuger (**F5**) i zaprzestanie w punkcie przerwania.

3. Znajdź zmienną w **zmiennych lokalnych** okna (**debugowania > Windows > lokalne**), kliknij prawym przyciskiem myszy zmienną i wybierz **wprowadzić identyfikator obiektu**.

    ![Tworzenie Identyfikatora obiektu](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Powinien zostać wyświetlony **$** oraz liczbą **lokalne** okna. Ta zmienna jest identyfikator obiektu.

5. Kliknij prawym przyciskiem myszy zmienna Identyfikatora obiektu, a następnie wybierz **Dodaj czujkę**.

Aby uzyskać więcej informacji, zobacz [tworzenia Identyfikatora obiektu](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Wyświetl wartości zwracane dla funkcji

Aby wyświetlić wartości zwracane dla funkcji, Przyjrzyj się funkcji, które pojawiają się w **Autos** okna, gdy są wykonywanie Twojego kodu. Aby zobaczyć wartość zwracaną dla funkcji, upewnij się, funkcja jesteś zainteresowany została już wykonana (naciśnij klawisz **F10** raz, jeśli są aktualnie zatrzymane na wywołanie funkcji). Jeśli okno jest zamknięte, użyj **Debuguj > Windows > automatyczne** otworzyć **automatyczne** okna.

![Okno zmiennych automatycznych](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Ponadto, możesz wprowadzić funkcje w **bezpośrednie** okna, aby wyświetlić wartości zwracane. (Otwórz go za pomocą **Debuguj > Windows > bezpośrednie**.)

![Okno bezpośrednie](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Można również użyć [pseudozmienne](../debugger/pseudovariables.md) w **Obejrzyj** i **bezpośrednie** okna, takie jak `$ReturnValue`.

## <a name="string_visualizer"></a>Sprawdź parametry w wizualizatorze

Podczas pracy z ciągami, może być przydatne wyświetlić cały ciąg sformatowany. Aby wyświetlić zwykłego tekstu, XML, HTML lub JSON ciąg, kliknij na ikonę szkła powiększającego ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikonę Wizualizator") podczas najeżdżania kursorem na zmienną zawierającą wartość ciągu.

![Otwórz Wizualizator ciągu](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Wizualizator ciągu mogą pomóc Ci dowiedzieć się, czy ciąg jest źle sformułowany, w zależności od typu string. Na przykład pusty **wartość** pole wskazuje ciąg nie jest rozpoznawane przez typu wizualizatora. Aby uzyskać więcej informacji, zobacz [okno dialogowe Wizualizator ciągu](../debugger/string-visualizer-dialog-box.md).

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Dla kilku innych typów, takich jak obiekty DataSet i DataTable, które pojawiają się w oknach debugera, można także otworzyć wbudowany wizualizator.

## <a name="break-into-code-on-handled-exceptions"></a>Wejdź do kodu dotyczące wyjątków obsłużonych

Debuger przerywa kodu na nieobsłużonych wyjątkach. Jednak obsługi wyjątków (takich jak wyjątki, które występują w ramach `try/catch` bloku) może być również źródłem błędów i może chcesz zbadać, kiedy występują. Można skonfigurować debuger wszedł do kodu, również wyjątki obsługiwane, konfigurując opcje w **ustawienia wyjątków** okno dialogowe. Otwórz okno dialogowe, wybierając **Debuguj > Windows > Ustawienia wyjątków**.

**Ustawienia wyjątków** okno dialogowe umożliwia polecić debugerowi, aby przerwać działanie kodu w określonych wyjątków. Na poniższej ilustracji, debuger przerywa w kodzie po każdym `System.NullReferenceException` występuje. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami](../debugger/managing-exceptions-with-the-debugger.md).

![Ustawienia wyjątków — okno dialogowe](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Debugowanie zakleszczeń i sytuacje wyścigu

Jeśli musisz debugować rodzaje problemów, które są wspólne dla aplikacji wielowątkowych, często pomaga można wyświetlić lokalizacji wątków podczas debugowania. Można to zrobić za pomocą **Pokaż wątki w źródle** przycisku.

#### <a name="to-show-threads-in-your-source-code"></a>Aby wyświetlić wątków w kodzie źródłowym

1. Podczas debugowania, kliknij przycisk **Pokaż wątki w źródle** przycisk ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") w **debugowania** paska narzędzi.

2. Spójrz na oprawę w lewej części okna. W tym wierszu, zostanie wyświetlony *znacznika wątku* ikonę ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker") o podobny dwoma wątkami ręczników. Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji.

    Należy zauważyć, że znacznika wątku może częściowo zasłonięte przez punkt przerwania.

3. Umieść wskaźnik myszy nad znacznika wątku. Pojawi się DataTip. DataTip informuje numer identyfikacyjny nazwy i wątku dla każdego wątku zatrzymania.

    Można również wyświetlić lokalizację wątków w [okna stosów równoległych](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Sprawdź ładunków dla usług sieci web i zasobów sieciowych (systemu Windows UWP)

W aplikacjach platformy uniwersalnej systemu Windows, można analizować operacje sieciowe, wykonywane przy użyciu `Windows.Web.Http` interfejsu API. To narzędzie służy do debugowania usług sieci web i zasobami sieciowymi. Aby użyć narzędzia, wybierz pozycję **Debuguj > Profiler wydajności**. Wybierz **sieci**, a następnie wybierz **Start**. W swojej aplikacji, przechodzą przez scenariusz, który używa `Windows.Web.Http`, a następnie wybierz **Zatrzymaj Kolekcjonowanie** podczas generowania raportu.

![Użycie narzędzia profilowania sieci](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Wybierz operację podsumowania bardziej szczegółowo widokami.

![Szczegółowe informacje w narzędziu użycie sieci](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Aby uzyskać więcej informacji, zobacz [użycie sieci](../profiling/network-usage.md).

## <a name="modules_window"></a> Zapoznać się z jak dołącza debuger do swojej aplikacji (C#, C++, Visual Basic F#)

Aby dołączyć do uruchomionej aplikacji, debuger ładuje pliki symboli (.pdb), generowany dla dokładnie tej samej kompilacji aplikacji, którą próbujesz debugować. W niektórych przypadkach nieco znajomości pliki symboli mogą być pomocne. Można sprawdzić, jak Visual Studio ładuje pliki symboli za pomocą **modułów** okna.

Otwórz **modułów** okna podczas debugowania, wybierając **Debuguj > Windows > modułów**. **Modułów** okna można stwierdzić, które moduły debuger jest traktowanie jako kod użytkownika lub [ *mój kod*](../debugger/just-my-code.md)oraz symbol podczas ładowania stanu modułu. W większości przypadków debuger automatycznie znajduje pliki symboli dla kodu użytkownika, ale jeśli chcesz przejść do (lub debugowanie) kodzie .NET framework, kod systemu lub innej biblioteki kodu, dodatkowe kroki są wymagane do uzyskania plików symboli poprawne.

![Wyświetlanie informacji o symbolach w oknie moduły](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Możesz załadować informacji o symbolach bezpośrednio z **modułów** okna, kliknij prawym przyciskiem myszy i wybierając pozycję **załadować symbole**.

Czasami deweloperzy aplikacji dostarczaj aplikacje bez pasującego pliki symboli (w celu zmniejszenia rozmiaru), ale zachować kopię pasujących symboli plików kompilacji, dzięki czemu ich później debugowania wydanej wersji.

Aby dowiedzieć się, jak debuger klasyfikuje kod jako kod użytkownika, zobacz [tylko mój kod](../debugger/just-my-code.md). Aby dowiedzieć się więcej na temat plików symboli, zobacz [określanie plików symboli (.pdb) i plików źródłowych w debugerze programu Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Dowiedz się więcej

Aby uzyskać dodatkowe porady i wskazówki oraz bardziej szczegółowe informacje Zobacz te Posty na blogu:

- [7 mniejszym hakerskie znanych do debugowania w programie Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 ukrytych Klejnoty w programie Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Zobacz także

[Skróty klawiaturowe](../ide/productivity-shortcuts.md)

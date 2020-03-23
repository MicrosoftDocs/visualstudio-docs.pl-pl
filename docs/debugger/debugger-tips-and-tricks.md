---
title: Porady i wskazówki w debugerze
description: Dowiedz się więcej o niektórych mniej znanych funkcjach obsługiwanych przez debuger programu Visual Studio
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302218"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Poznaj wskazówki dotyczące produktywności i wskazówki dotyczące debugera w programie Visual Studio

Przeczytaj ten temat, aby dowiedzieć się kilka wskazówek i wskazówek dotyczących produktywności dla debugera programu Visual Studio. Aby zapoznać się z podstawowymi funkcjami debugera, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md). W tym temacie omówimy niektóre obszary, które nie są uwzględnione w przewodniku funkcji.

## <a name="pin-data-tips"></a>Wskazówki dotyczące danych pinów

Jeśli często najedziesz kursorem na wskazówki dotyczące danych podczas debugowania, możesz przypiąć końcówkę danych dla zmiennej, aby zapewnić sobie szybki dostęp. Zmienna pozostaje przypięta nawet po ponownym uruchomieniu. Aby przypiąć końcówkę danych, kliknij ikonę pinezki, najeżdżając na nią kursorem. Można przypiąć wiele zmiennych.

![Przypinanie końcówki danych](../debugger/media/dbg-tips-data-tips-pinned.png "Etykietka z danymi przypinania")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Edytuj kod i kontynuuj debugowanie (C#, VB, C++)

W większości języków obsługiwanych przez program Visual Studio można edytować kod w środku sesji debugowania i kontynuować debugowanie. Aby użyć tej funkcji, kliknij kod z kursorem wstrzymany w debugerze, wykonuj zmiany i naciśnij **klawisze F5**, **F10**lub **F11,** aby kontynuować debugowanie.

![Edytowanie i kontynuowanie debugowania](../debugger/media/dbg-tips-edit-and-continue.gif "Edytuj iwzrozumiej")

Aby uzyskać więcej informacji na temat korzystania z funkcji i ograniczeń funkcji, zobacz [Edytowanie i kontynuowanie](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Edytuj kod XAML i kontynuuj debugowanie

Aby zmodyfikować kod XAML podczas sesji debugowania, zobacz [Pisanie i debugowanie z uruchomionym kodem XAML z załaduj ponownie gorąca xaml](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problemy z debugowaniem, które są trudne do odtworzenia

Jeśli ponowne tworzenie określonego stanu w aplikacji jest trudne lub czasochłonne, należy rozważyć, czy może pomóc użycie warunkowego punktu przerwania. Można użyć [warunkowe punkty przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) i punkty przerwania filtru, aby uniknąć włamania do kodu aplikacji, dopóki aplikacja nie wejdzie w żądany stan (na przykład stan, w którym zmienna przechowuje złe dane). Można ustawić warunki przy użyciu wyrażeń, filtrów, liczby trafień i tak dalej.

#### <a name="to-create-a-conditional-breakpoint"></a>Aby utworzyć warunkowy punkt przerwania

1. Kliknij prawym przyciskiem myszy ikonę punktu przerwania (czerwona kulka) i wybierz pozycję **Warunki**.

2. W oknie **Ustawienia punktu przerwania** wpisz wyrażenie.

    ![Warunkowy punkt przerwania](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "Warunkowypunkt świtu")

3. Jeśli interesuje Cię inny typ warunku, wybierz **opcję Filtruj** zamiast **wyrażenia warunkowego** w oknie dialogowym **Ustawienia punktu przerwania,** a następnie postępuj zgodnie ze wskazówkami dotyczącymi filtru.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Konfigurowanie danych do wyświetlenia w debugerze

W przypadku języka C#, Visual Basic i C++ (tylko kod C++/CLI) można poinformować debuger, jakie informacje mają być wyświetlane przy użyciu [atrybutu DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md) W przypadku kodu C++ można zrobić to samo za pomocą [wizualizacji Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Zmienianie przepływu wykonania

Gdy debuger jest wstrzymany w wierszu kodu, użyj myszy, aby pobrać żółty wskaźnik strzałki po lewej stronie. Przenieś żółty wskaźnik strzałki do innego punktu w ścieżce wykonywania kodu. Następnie użyj F5 lub polecenia kroku, aby kontynuować uruchamianie aplikacji.

![Przenoszenie wskaźnika wykonania](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Przenoszenie wskaźnika wykonania")

Zmieniając przepływ wykonywania, można wykonać takie czynności, jak testowanie różnych ścieżek wykonywania kodu lub ponownego uruchamiania kodu bez ponownego uruchamiania debugera.

> [!WARNING]
> Często należy zachować ostrożność przy tej funkcji, a w etykietce narzędzia jest widoczne ostrzeżenie. Mogą pojawić się również inne ostrzeżenia. Przenoszenie wskaźnika nie można przywrócić aplikacji do wcześniejszego stanu aplikacji.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Śledzenie obiektu poza zakresem (C#, Visual Basic)

Łatwo jest wyświetlać zmienne za pomocą okien debugera, takich jak okno **Czujka.** Jednak gdy zmienna wykracza poza zakres w oknie **Czujki,** można zauważyć, że jest wyszarzony. W niektórych scenariuszach aplikacji wartość zmiennej może ulec zmianie nawet wtedy, gdy zmienna jest poza zakresem i możesz chcieć ją uważnie obserwować (na przykład zmienna może zbierać śmieci). Zmienną można śledzić, tworząc dla niej identyfikator obiektu w oknie **Czujka.**

#### <a name="to-create-an-object-id"></a>Aby utworzyć identyfikator obiektu

1. Ustaw punkt przerwania w pobliżu zmiennej, którą chcesz śledzić.

2. Uruchom debuger (**F5**) i zatrzymaj się w punkcie przerwania.

3. Znajdź zmienną w oknie **Zmienne lokalne** (**Debug > Windows > Locals**), kliknij ją prawym przyciskiem myszy i wybierz polecenie Make Object **ID**.

    ![Tworzenie identyfikatora obiektu](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. W oknie **$** **Locals** powinien zostać wyświetlony numer plus. Ta zmienna jest identyfikatorem obiektu.

5. Kliknij prawym przyciskiem myszy zmienną identyfikatora obiektu i wybierz polecenie **Dodaj czujki**.

Aby uzyskać więcej informacji, zobacz [Tworzenie identyfikatora obiektu](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Wyświetlanie wartości zwracanych dla funkcji

Aby wyświetlić zwracane wartości dla funkcji, spójrz na funkcje, które pojawiają się w oknie **Autos** podczas przechodzenia przez kod. Aby wyświetlić wartość zwracaną dla funkcji, upewnij się, że funkcja, którą jesteś zainteresowany, została już wykonana (naciśnij **klawisz F10** raz, jeśli jest aktualnie zatrzymana w wywołaniu funkcji). Jeśli okno jest zamknięte, otwórz okno **Autos** za pomocą **> Debugowania systemu Windows >.**

![Okno autos](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Ponadto można wprowadzić funkcje w oknie **Bezpośrednim,** aby wyświetlić zwracane wartości. (Otwórz go za pomocą **debugowania > windows > natychmiastowe**.)

![Okno bezpośrednie](../debugger/media/dbg-tips-immediate-window.png "Natychmiastowe okno windowsowe")

Można również użyć [pseudozmienne w](../debugger/pseudovariables.md) oknie **Czujka** i `$ReturnValue` **Natychmiastowe,** takie jak .

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Sprawdzanie ciągów w wizualizatorze

Podczas pracy z ciągami może być pomocne wyświetlanie całego sformatowanego ciągu. Aby wyświetlić zwykły tekst, ciąg XML, HTML lub JSON, kliknij ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora") podczas najeżdżania kursorem na zmienną zawierającą wartość ciągu.

![Otwieranie wizualizatora ciągów](../debugger/media/dbg-tips-string-visualizers.png "OpenStringWizualizator")

Wizualizator ciągu może pomóc dowiedzieć się, czy ciąg jest zniekształcony, w zależności od typu ciągu. Na przykład puste pole **Wartość** wskazuje, że ciąg nie jest rozpoznawany przez typ wizualizatora. Aby uzyskać więcej informacji, zobacz [Okno dialogowe Wizualizator ciągów](../debugger/string-visualizer-dialog-box.md).

![Wizualizator strun JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringWizualizer")

W przypadku kilku innych typów, takich jak DataSet i DataTable obiektów, które pojawiają się w oknach debugera, można również otworzyć wbudowany wizualizator.

## <a name="break-into-code-on-handled-exceptions"></a>Podziel się na kod w obsługiwanych wyjątkach

Debuger dzieli się do kodu na nieobsługiwał wyjątków. Jednak obsługiwane wyjątki (takie jak wyjątki, `try/catch` które występują w bloku) może być również źródłem błędów i można zbadać, kiedy wystąpią. Debugera można skonfigurować tak, aby podzielił się na kod dla obsługiwanych wyjątków, a także konfigurując opcje w oknie dialogowym **Ustawienia wyjątków.** Otwórz to okno dialogowe, wybierając **pozycję Debug > ustawienia wyjątków systemu Windows > .**

Okno dialogowe **Ustawienia wyjątków** umożliwia poinformowanie debugera, aby podzielić się na kod w określonych wyjątkach. Na poniższej ilustracji debuger dzieli się `System.NullReferenceException` do kodu, gdy występuje. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami](../debugger/managing-exceptions-with-the-debugger.md).

![Okno dialogowe Ustawienia wyjątków](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Zakleszczenia debugowania i warunki wyścigu

Jeśli trzeba debugować rodzaje problemów, które są wspólne dla aplikacji wielowątkowych, często pomaga wyświetlić lokalizację wątków podczas debugowania. Można to łatwo zrobić za pomocą przycisku **Pokaż wątki w źródle.**

#### <a name="to-show-threads-in-your-source-code"></a>Aby wyświetlić wątki w kodzie źródłowym

1. Podczas debugowania kliknij przycisk **Pokaż wątki w źródle** Pokaż ![wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "Identyfikator wątku") na pasku narzędzi **Debugowania.**

2. Spójrz na rynnę po lewej stronie okna. W tym wierszu zobaczysz ikonę *znacznika wątku* ![Znacznik wątku,](../debugger/media/dbg-thread-marker.png "Identyfikator wątku") który przypomina dwie nici tkaniny. Znacznik wątku wskazuje, że wątek jest zatrzymany w tej lokalizacji.

    Należy zauważyć, że znacznik wątku może być częściowo ukryte przez punkt przerwania.

3. Umieść wskaźnik myszy na znaczniku wątku. Pojawi się porada data. DataTip informuje nazwę i numer identyfikatora wątku dla każdego zatrzymanego wątku.

    Można również wyświetlić lokalizację wątków w [oknie Stosy równoległe](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Badanie ładunków dla usług sieci web i zasobów sieciowych (UWP)

W aplikacjach platformy uniwersalnej systemu Windows `Windows.Web.Http` można analizować operacje sieciowe wykonywane za pomocą interfejsu API. Za pomocą tego narzędzia można pomóc w debugowaniu usług sieci web i zasobów sieciowych. Aby użyć tego narzędzia, wybierz opcję **Debugowanie > profilera wydajności**. Wybierz **pozycję Sieć**, a następnie wybierz pozycję **Start**. W aplikacji przejdź przez scenariusz, `Windows.Web.Http`który używa , a następnie wybierz **pozycję Zatrzymaj kolekcję,** aby wygenerować raport.

![Narzędzie do profilowania użycia sieci](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Wybierz operację w widoku podsumowania, aby wyświetlić więcej szczegółów.

![Szczegółowe informacje w narzędziu Do korzystania z sieci](../profiling/media/prof-tour-network-usage-details.png "Szczegółowejszewizna sieci")

Aby uzyskać więcej informacji, zobacz [Użycie sieci](../profiling/network-usage.md).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Zapoznaj się z tym, jak debuger dołącza do aplikacji (C#, C++, Visual Basic, F#)

Aby dołączyć do uruchomionej aplikacji, debuger ładuje pliki symbolu (pdb) generowane dla dokładnie tej samej kompilacji aplikacji, którą próbujesz debugować. W niektórych scenariuszach może być przydatna niewielka znajomość plików symboli. Można sprawdzić, jak Visual Studio ładuje pliki symboli przy użyciu okna **Moduły.**

Otwórz okno **Moduły** podczas debugowania, wybierając **debugowanie > modułów > systemu Windows**. Okno **Moduły** może powiedzieć, jakie moduły debuger jest traktowany jako kod użytkownika lub [*Mój kod*](../debugger/just-my-code.md), a stan ładowania symbolu dla modułu. W większości scenariuszy debuger automatycznie znajduje pliki symboli dla kodu użytkownika, ale jeśli chcesz wkroczyć do (lub debugować) kodu .NET, kodu systemu lub kodu biblioteki innej firmy, wymagane są dodatkowe kroki w celu uzyskania poprawnych plików symboli.

![Wyświetlanie informacji o symbolu w oknie Moduły](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation (Wyświetl informacje)")

Informacje o symbolach można załadować bezpośrednio z okna **Moduły,** klikając prawym przyciskiem myszy i wybierając polecenie **Załaduj symbole**.

Czasami deweloperzy aplikacji wysyłają aplikacje bez pasujących plików symboli (aby zmniejszyć footprint), ale przechowują kopię pasujących plików symboli kompilacji, aby mogli debugować wydaną wersję później.

Aby dowiedzieć się, jak debuger klasyfikuje kod jako kod użytkownika, zobacz [Just My Code](../debugger/just-my-code.md). Aby dowiedzieć się więcej o plikach symboli, zobacz [Określanie symboli (pdb) i plików źródłowych w debugerze programu Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Dowiedz się więcej

Aby uzyskać dodatkowe wskazówki i wskazówki oraz bardziej szczegółowe informacje, zobacz następujące wpisy w blogu:

- [7 mniej znanych hacków do debugowania w programie Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 ukrytych klejnotów w programie Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Zobacz też

[Skróty klawiaturowe](../ide/productivity-shortcuts.md)

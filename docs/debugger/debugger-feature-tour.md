---
title: Pierwsze spojrzenie na debugera
description: Rozpocznij debugowanie aplikacji za pomocą debugera programu Visual Studio
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffaeff850c739cd81569a88ae980acf837c413c1
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184214"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Najpierw Spójrz na debuger programu Visual Studio

W tym temacie przedstawiono narzędzia debugera udostępniane przez program Visual Studio. W kontekście programu Visual Studio podczas *debugowania aplikacji*zazwyczaj oznacza to, że aplikacja jest uruchamiana z dołączonym debugerem (to znaczy w trybie debugera). Po wykonaniu tej czynności debuger zapewnia wiele sposobów, aby zobaczyć, co Twój kod działa podczas jego uruchamiania. Możesz przechodzić przez kod i przeglądać wartości przechowywane w zmiennych, można ustawić zegarki dla zmiennych, aby zobaczyć, kiedy zmieniają się wartości, można sprawdzić ścieżkę wykonywania kodu, et al. Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego tematu warto odczytać [debugowanie dla bezwzględnych początkujących](../debugger/debugging-absolute-beginners.md) .

Opisane tutaj funkcje dotyczą języków C#, C++, Visual Basic, JavaScript i innych obsługiwanych przez program Visual Studio (z wyjątkiem sytuacji, w których zaznaczono inaczej).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustawianie punktu przerwania i uruchamianie debugera

Aby debugować, należy uruchomić aplikację za pomocą debugera dołączonego do procesu aplikacji. **F5** (**debugowanie > Rozpocznij debugowanie**) to najbardziej typowy sposób. Jednak teraz możesz nie ustawić żadnych punktów przerwania, aby przeanalizować kod aplikacji, więc należy to zrobić najpierw, a następnie rozpocząć debugowanie. Punkty przerwania są najbardziej podstawową i istotną funkcją niezawodnego debugowania. Punkt przerwania wskazuje, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana.

Jeśli plik jest otwarty w edytorze kodu, można ustawić punkt przerwania, klikając margines na lewo od wiersza kodu.

![Ustawianie punktu przerwania](../debugger/media/dbg-tour-set-a-breakpoint.gif "Ustawianie punktu przerwania")

Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania, a debuger zostanie uruchomiony do pierwszego punktu przerwania, który napotka. Jeśli aplikacja nie jest jeszcze uruchomiona, F5 uruchamia debuger i kończy się przy pierwszym punkcie przerwania.

Punkty przerwania są przydatną funkcją, gdy znasz wiersz kodu lub sekcję kodu, który chcesz szczegółowo sprawdzić.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a>Nawigowanie po kodzie w debugerze przy użyciu poleceń kroków

Udostępniamy skróty klawiaturowe dla większości poleceń, ponieważ umożliwiają one Szybkie nawigowanie po kodzie aplikacji. (Równoważne polecenia, takie jak polecenia menu, są wyświetlane w nawiasach).

Aby uruchomić aplikację z dołączonym debugerem, naciśnij klawisz **F11** (**Debuguj > Step Into**). F11 to **krok do** polecenia i postępuje z jedną instrukcją wykonywania aplikacji w danym momencie. Po uruchomieniu aplikacji za pomocą klawisza F11 debuger przerwie się na pierwszej instrukcji, która jest wykonywana.

![F11 Wkrocz do](../debugger/media/dbg-tour-f11.png "F11 Wkrocz do")

Żółta strzałka reprezentuje instrukcję, na której debuger wstrzymał działanie, co również zawiesza wykonywanie aplikacji w tym samym punkcie (Ta instrukcja nie została jeszcze wykonana).

F11 jest dobrym sposobem na badanie przepływu wykonywania w najbardziej szczegółowy sposób. (W celu szybszego przechodzenia przez kod pokazujemy również inne opcje). Domyślnie debuger pomija kod niebędący użytkownikiem (Aby uzyskać więcej szczegółów, zobacz [tylko mój kod](../debugger/just-my-code.md)).

>[!NOTE]
> W kodzie zarządzanym zostanie wyświetlone okno dialogowe z pytaniem, czy chcesz otrzymywać powiadomienia o automatycznym przekroczeniu właściwości i operatorów (zachowanie domyślne). Jeśli chcesz zmienić to ustawienie później, wyłącz ustawienie **Przekrocz nad właściwościami i operatorami** w menu **Narzędzia > opcje** w obszarze **debugowanie**.

## <a name="step-over-code-to-skip-functions"></a>Przekrocz kod, aby pominąć funkcje

Gdy korzystasz z wiersza kodu, który jest wywołaniem funkcji lub metody, możesz nacisnąć klawisz **F10** (**Debuguj >** przekroczenie) zamiast klawisza F11.

F10 przesuwa debuger bez przechodzenia do funkcji lub metod w kodzie aplikacji (kod nadal jest wykonywany). Naciskając klawisz F10, możesz pominąć kod, który nie jest interesujący. Dzięki temu możesz szybko uzyskać kod, który jest bardziej interesujący.

## <a name="step-into-a-property"></a>Wkrocz do właściwości

Jak wspomniano wcześniej, domyślnie debuger pomija zarządzane właściwości i pola, ale **krok do określonego** polecenia umożliwia przesłonięcie tego zachowania.

Kliknij prawym przyciskiem myszy właściwość lub pole i wybierz opcję **Wkrocz do określonego**, a następnie wybierz jedną z dostępnych opcji.

![Wkrocz do określonego](../debugger/media/dbg-tour-step-into-specific.png "Wkrocz do określonego")

W tym przykładzie **krokowo do określonego** kodu pobiera nam kod dla `Path.set` .

![Wkrocz do określonego](../debugger/media/dbg-tour-step-into-specific-2.png "Wkrocz do określonego")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Szybkie uruchamianie do punktu w kodzie przy użyciu myszy

W debugerze Umieść kursor nad wierszem kodu do momentu **kliknięcia** przycisku (uruchom wykonywanie do tego miejsca) do ![kliknięcia](../debugger/media/dbg-tour-run-to-click.png "RunToClick") po lewej stronie.

![Uruchom do kliknięcia](../debugger/media/dbg-tour-run-to-click-2.png "Uruchom do kliknięcia")

> [!NOTE]
> Przycisk **Uruchom do kliknięcia** (uruchom wykonywanie do tego miejsca) jest dostępny w programie [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Kliknij przycisk **Uruchom do kliknięcia** (uruchom wykonywanie do tego miejsca). Debuger przechodzi do wiersza kodu, w którym został kliknięty.

Użycie tego przycisku jest podobne do ustawiania tymczasowego punktu przerwania. To polecenie jest również przydatne do szybkiego uzyskiwania informacji w widocznym regionie kodu aplikacji. Możesz użyć **polecenia Uruchom, aby kliknąć** dowolny otwarty plik.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Zwiększ debuger z bieżącej funkcji

Czasami może być konieczne kontynuowanie sesji debugowania, ale przechodzenie przez debuger w całości przez bieżącą funkcję.

Naciśnij klawisze **Shift + F11** (lub **Debuguj > krok wychodzący**).

To polecenie wznawia wykonywanie aplikacji (i zwiększa debuger) do momentu, gdy bieżąca funkcja zwróci wartość.

## <a name="run-to-cursor"></a>Uruchom do kursora

Gdy edytujesz kod (zamiast wstrzymywać się w debugerze), kliknij prawym przyciskiem myszy wiersz kodu w aplikacji i wybierz polecenie **Uruchom do kursora**. To polecenie uruchamia debugowanie i ustawia tymczasowy punkt przerwania w bieżącym wierszu kodu.

![Uruchom do kursora](../debugger/media/dbg-tour-run-to-cursor.png "Uruchom do kursora")

Jeśli ustawiono punkty przerwania, debuger zatrzymuje się w pierwszym punkcie przerwania, który trafi.

Naciśnij klawisz **F5** , aż osiągniesz wiersz kodu, w którym wybrano pozycję **Uruchom do kursora**.

To polecenie jest przydatne, gdy edytujesz kod i chcesz szybko ustawić tymczasowy punkt przerwania i uruchomić debuger w tym samym czasie.

> [!NOTE]
> Możesz użyć **do kursora** w oknie **stosu wywołań** podczas debugowania.

## <a name="restart-your-app-quickly"></a>Szybkie ponowne uruchamianie aplikacji

Kliknij przycisk **Uruchom** ponownie ![Uruchom aplikację](../debugger/media/dbg-tour-restart.png "Uruchom ponownie aplikację") na pasku narzędzi debugowania (**Ctrl + Shift + F5**).

Po naciśnięciu przycisku **Uruchom ponownie**program zapisze czas w przeciwieństwie do zatrzymywania aplikacji i ponownego uruchomienia debugera. Debuger zatrzymuje się w pierwszym punkcie przerwania, który jest wywoływany przez wykonanie kodu.

Jeśli chcesz zatrzymać debuger i wrócić do edytora kodu, możesz nacisnąć czerwony przycisk Zatrzymaj ![debugowanie](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") zamiast **ponownego uruchomienia**.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Edytuj swój kod i Kontynuuj debugowanie (C#, VB, C++, XAML)

W większości języków obsługiwanych przez program Visual Studio można edytować kod w trakcie sesji debugowania i kontynuować debugowanie. Aby skorzystać z tej funkcji, kliknij swój kod z kursorem podczas wstrzymania w debugerze, dokonaj edycji, a następnie naciśnij klawisz **F5**, **F10**lub **F11** , aby kontynuować debugowanie.

![Edytuj i Kontynuuj debugowanie](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Aby uzyskać więcej informacji na temat korzystania z funkcji i ograniczeń funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

Aby zmodyfikować kod XAML podczas sesji debugowania, zobacz [pisanie i debugowanie uruchomionego kodu XAML przy użyciu gorącego ponownego ładowania XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych ze wskazówkami dotyczącymi danych

Teraz, gdy wiesz już, jak nieco się znajdziesz, możesz zacząć sprawdzać stan aplikacji (zmienne) za pomocą debugera. Funkcje, które umożliwiają inspekcję zmiennych, to niektóre z najbardziej przydatnych funkcji debugera i istnieją różne sposoby ich wykonania. Często podczas próby debugowania problemu próbujesz dowiedzieć się, czy zmienne przechowują wartości, których oczekujesz, w określonym stanie aplikacji.

Gdy w debugerze zostało zatrzymane, umieść kursor na obiekcie z myszą i zobaczysz jego domyślną wartość właściwości (w tym przykładzie nazwą pliku `market 031.jpg` jest domyślna wartość właściwości).

![Wyświetlanie etykietki danych](../debugger/media/dbg-tour-data-tips.gif "Wyświetlanie etykietki danych")

Rozwiń obiekt, aby wyświetlić wszystkie jego właściwości (na przykład `FullPath` Właściwość w tym przykładzie).

Często podczas debugowania chcesz szybko sprawdzić wartości właściwości obiektów, a porady dotyczące danych to dobry sposób na to.

> [!TIP]
> W większości obsługiwanych języków można edytować kod w trakcie sesji debugowania. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspekcja zmiennych przy użyciu okienek Autostart i locale

Podczas debugowania zapoznaj się z oknem **Autokorekty** u dołu edytora kodu.

![Okno Autokorekty](../debugger/media/dbg-tour-autos-window.png "okno zmiennych automatycznych")

W oknie **Autokorekty** widoczne są zmienne wraz z ich bieżącą wartością i ich typem. W oknie **samochody** są wyświetlane wszystkie zmienne używane w bieżącym wierszu lub w poprzednim wierszu (w języku C++ okno zawiera zmienne w poprzednich trzech wierszach kodu. Zapoznaj się z dokumentacją dotyczącą zachowania specyficznego dla języka).

> [!NOTE]
> W języku JavaScript okno **zmiennych lokalnych** jest obsługiwane, ale nie w oknie **autostarts** .

Następnie zajrzyj do okna **zmiennych lokalnych** . W oknie **Ustawienia lokalne** są wyświetlane zmienne, które znajdują się obecnie w zakresie.

![Okno zmiennych lokalnych](../debugger/media/dbg-tour-locals-window.png "okno zmiennych lokalnych")

W tym przykładzie `this` obiekt i obiekt `f` znajdują się w zakresie. Aby uzyskać więcej informacji, zobacz [Inspekcja zmiennych w oknach Autostart i lokalne](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Ustawianie czujki

Możesz użyć okna **czujki** , aby określić zmienną (lub wyrażenie), dla którego chcesz zachować czujkę.

Podczas debugowania kliknij prawym przyciskiem myszy obiekt i wybierz polecenie **Dodaj czujkę**.

![Okno czujka](../debugger/media/dbg-tour-watch-window.png "okno czujki")

W tym przykładzie masz ustawiony element czujki dla `f` obiektu i można zobaczyć jego zmianę wartości podczas przechodzenia przez debuger. W przeciwieństwie do innych zmiennych okien, okna **czujki** zawsze pokazują zmienne, które są obserwowane (są wyszarzone, gdy poza zakresem).

Aby uzyskać więcej informacji, zobacz [Ustawianie czujki przy użyciu okien czujka i QuickWatch](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Badanie stosu wywołań

Kliknij okno **stos wywołań** podczas debugowania, co jest domyślnie otwarte w prawym dolnym okienku.

![Badanie stosu wywołań](../debugger/media/dbg-tour-call-stack.png "Badanie stosu wywołań")

Okno **stos wywołań** pokazuje kolejność, w której metody i funkcje są wywoływane. Górny wiersz przedstawia bieżącą funkcję ( `Update` Metoda w tym przykładzie). Drugi wiersz pokazuje, że `Update` został wywołany z `Path.set` właściwości i tak dalej. Stos wywołań to dobry sposób, aby sprawdzić i zrozumieć przepływ wykonywania aplikacji.

> [!NOTE]
> Okno **stosu wywołań** przypomina perspektywę debugowania w niektórych środowisk IDE, takich jak przezaćmienie.

Możesz kliknąć dwukrotnie wiersz kodu, aby przejść do tego kodu źródłowego, a także zmienić bieżący zakres, który jest sprawdzany przez debuger. Nie powoduje to przechodzenia do debugera.

Możesz również użyć menu dostępnych po kliknięciu prawym przyciskiem myszy w oknie **stos wywołań** , aby wykonać inne czynności. Na przykład można wstawić punkty przerwania do określonych funkcji, ponownie uruchomić aplikację przy użyciu polecenia **Uruchom do kursora**, a następnie przejrzeć kod źródłowy. Zobacz [jak: badanie stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a><a name="exception"></a>Badanie wyjątku

Gdy aplikacja zgłosi wyjątek, debuger przeprowadzi Cię do wiersza kodu, który wywołał wyjątek.

![Pomocnik wyjątków](../debugger/media/dbg-tour-exception-helper.png "Pomocnik wyjątków")

W tym przykładzie **pomocnik wyjątku** pokazuje `System.Argument` wyjątek i komunikat o błędzie informujący, że ścieżka nie jest formą prawną. Dlatego wiemy, że wystąpił błąd w metodzie lub argumencie funkcji.

W tym przykładzie wywołanie wykazało `DirectoryInfo` błąd w pustym ciągu przechowywanym w `value` zmiennej.

Pomocnik wyjątków to doskonały funkcja, która może pomóc w debugowaniu błędów. Można również wykonywać czynności, takie jak wyświetlanie szczegółów błędów i Dodawanie czujki z pomocnika wyjątków. Lub, w razie potrzeby, można zmienić warunki zgłaszania określonego wyjątku. Aby uzyskać więcej informacji na temat obsługi wyjątków w kodzie, zobacz [techniki debugowania i narzędzia](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> Pomocnik wyjątków zastąpił asystenta wyjątków, rozpoczynając od [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Rozwiń węzeł **Ustawienia wyjątku** , aby zobaczyć więcej opcji obsługi tego typu wyjątku, ale nie musisz niczego zmieniać w przypadku tego samouczka.

## <a name="configure-debugging"></a>Konfigurowanie debugowania

Można skonfigurować projekt do kompilowania jako [Konfiguracja debugowania lub wydania](../debugger/how-to-set-debug-and-release-configurations.md), skonfigurować właściwości projektu na potrzeby debugowania lub skonfigurować [Ustawienia ogólne](../debugger/how-to-specify-debugger-settings.md) dla debugowania. Ponadto można skonfigurować debuger do wyświetlania informacji niestandardowych przy użyciu funkcji, takich jak atrybut [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) lub dla języka C/C++, [struktury NatVis](create-custom-views-of-native-objects.md).

Właściwości debugowania są specyficzne dla każdego typu projektu. Na przykład można określić argument, który ma zostać przekazany do aplikacji po jej uruchomieniu. Aby uzyskać dostęp do właściwości specyficznych dla projektu, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Właściwości**. Właściwości debugowania są zwykle wyświetlane na karcie **kompilacja** lub **debugowanie** , w zależności od określonego typu projektu.

![Właściwości projektu](../debugger/media/dbg-tour-project-properties.png "Właściwości projektu")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Debuguj aplikacje Live ASP.NET w Azure App Service

**Snapshot Debugger** wykonuje migawkę aplikacji w środowisku produkcyjnym, gdy interesujący kod jest wykonywany. Aby polecić debugerowi wykonanie migawki, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie, co poszło źle, bez wpływu na ruch aplikacji produkcyjnej. Snapshot Debugger może pomóc znacząco skrócić czas potrzebny do rozwiązania problemów występujących w środowiskach produkcyjnych.

![Uruchamianie debugera migawek](../debugger/media/snapshot-launch.png "Uruchamianie debugera migawek")

Kolekcja migawek jest dostępna dla aplikacji ASP.NET działających w Azure App Service. Aplikacje ASP.NET muszą działać na .NET Framework 4.6.1 lub nowszych, a aplikacje ASP.NET Core muszą działać na platformie .NET Core 2,0 lub nowszej w systemie Windows.

Aby uzyskać więcej informacji, zobacz [debugowanie live ASP.NET Apps przy użyciu Snapshot Debugger](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Wyświetlanie migawek z IntelliTrace Step-back (Visual Studio Enterprise)

**IntelliTrace Step-back** automatycznie wykonuje migawkę aplikacji przy każdym punkcie przerwania i zdarzeniu debugera. Zapisane migawki umożliwiają powrót do poprzednich punktów przerwania lub kroków oraz wyświetlanie stanu aplikacji w przeszłości. IntelliTrace krokowo umożliwia zaoszczędzenie czasu, gdy chcesz zobaczyć poprzedni stan aplikacji, ale nie chcesz ponownie uruchomić debugowania ani odtworzyć żądanego stanu aplikacji.

Możesz nawigować i przeglądać migawki przy użyciu przycisków **krok wstecz** i **dalej** na pasku narzędzi debugowania. Te przyciski służą do przechodzenia do zdarzeń, które pojawiają się na karcie **zdarzenia** w oknie **Narzędzia diagnostyczne** .

![Przyciski do tyłu i do przodu](../debugger/media/intellitrace-step-back-icons-description.png  "Przyciski do tyłu i do przodu")

Aby uzyskać więcej informacji, zobacz stronę [Sprawdzanie stanu poprzedniej aplikacji przy użyciu IntelliTrace](../debugger/view-historical-application-state.md) .

## <a name="debug-performance-issues"></a>Problemy z wydajnością debugowania

Jeśli aplikacja działa zbyt wolno lub używa zbyt dużej ilości pamięci, może być konieczne przetestowanie aplikacji przy użyciu narzędzi profilowania na początku. Aby uzyskać więcej informacji na temat narzędzi profilowania, takich jak narzędzie użycie procesora CPU i Analizator pamięci, zobacz [najpierw przejrzyj narzędzia profilowania](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

W ramach tego samouczka nastąpiło szybkie przeszukiwanie wielu funkcji debugera. Możesz bardziej szczegółowo zajrzeć do jednej z tych funkcji, takich jak punkty przerwania.

> [!div class="nextstepaction"]
> [Dowiedz się, jak korzystać z punktów przerwania](../debugger/using-breakpoints.md)

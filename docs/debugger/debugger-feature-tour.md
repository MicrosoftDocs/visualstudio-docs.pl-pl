---
title: Pierwsze spojrzenie na debugera
description: Rozpoczynanie debugowania aplikacji za pomocą debugera programu Visual Studio
ms.custom: seoapril2019
ms.date: 04/08/2019
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5c37466ea3f37bca80933cdc069d40f84099790
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679762"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Pierwsze spojrzenie na debugera programu Visual Studio

W tym temacie przedstawiono narzędzi debugera, dostarczanych przez program Visual Studio. W kontekście programu Visual Studio po użytkownik *debugowanie aplikacji*, zwykle oznacza to, że uruchomieniu aplikacji w debugerze (oznacza to, w trybie debugowania). Gdy to zrobisz, debuger zapewnia wiele sposobów, aby zobaczyć, co kod robi podczas jego uruchamiania. Można przejść przez kod i przyjrzyj się wartości przechowywane w zmiennych czujki można ustawić dla zmiennych, aby zobaczyć, po zmianie wartości, można sprawdzić ścieżki wykonywania kodu, et al. Jeśli po raz pierwszy, próbujących przeprowadzić debugowania kodu, warto przeczytać [debugowania dla początkujących](../debugger/debugging-absolute-beginners.md) przed przejściem w tym temacie.

Funkcje opisane w tym miejscu mają zastosowanie do języka C#, C++, Visual Basic, JavaScript i innymi językami obsługiwanymi przez program Visual Studio (z wyjątkiem sytuacji, gdy podane).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustaw punkt przerwania i uruchomić debuger

Do debugowania, należy uruchomić aplikację w debugerze proces aplikacji. **F5** (**Debuguj > Rozpocznij debugowanie**) to najbardziej popularny sposób, aby to zrobić. Jednak po prawej stronie teraz nie może ustawiono żadnych punktów przerwania, aby zbadać aplikacji kodu, dzięki czemu firma Microsoft będzie zrobić w pierwszej kolejności, a następnie rozpocząć debugowanie. Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu.

Jeśli masz plik jest otwarty w edytorze kodu, można ustawić punktu przerwania, klikając na marginesie po lewej stronie wiersza kodu.

![Ustaw punkt przerwania](../debugger/media/dbg-tour-set-a-breakpoint.gif "Ustaw punkt przerwania")

Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub **Rozpocznij debugowanie** przycisk ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie ") w pasku narzędzi debugowania i uruchomienia debugera do pierwszego punktu przerwania, który wykryje. Jeśli aplikacja nie jest jeszcze uruchomiona, F5 uruchomienie debugera i zatrzymuje się na pierwszy punkt przerwania.

Punkty przerwania są to przydatne, gdy wiadomo, wiersz kodu lub sekcji kodu, który chcesz zbadać szczegółowo.

## <a name="navigate"></a> Przechodzenie do kodu w debugerze, przy użyciu poleceń krokowych

Firma Microsoft zapewnia skróty klawiaturowe dla większości poleceń, ponieważ ich nawigacji w kodzie aplikacji szybciej. (Odpowiednik polecenia takie jak polecenia menu są wyświetlane w nawiasach).

Aby uruchomić aplikację w debugerze, naciśnij klawisz **F11** (**Debuguj > Step Into**). Jest F11 **Step Into** poleceń i prowadzi aplikacji wykonanie jednej instrukcji w danym momencie. Po uruchomieniu aplikacji za pomocą F11 debuger przerywa na pierwszej instrukcji, która zostanie wykonana.

![F11 Step Into](../debugger/media/dbg-tour-f11.png "F11 Step Into")

Żółta strzałka reprezentuje instrukcji, w której debuger wstrzymany, również zawiesza wykonywanie aplikacji w tym samym punkcie (Ta instrukcja nie jeszcze wykonane).

F11 jest dobrym sposobem na zbadanie przepływ wykonania w najbardziej szczegółowy. (Aby poruszać się szybciej za pomocą kodu, firma Microsoft dowiesz się także inne opcje także.) Domyślnie debuger pomija nad kodem niezwiązanych z użytkownikiem (Jeśli chcesz, aby uzyskać więcej informacji, zobacz [tylko mój kod](../debugger/just-my-code.md)).

>[!NOTE]
> W kodzie zarządzanym zobaczysz okno dialogowe z pytaniem, jeśli chcesz otrzymywać powiadomienia, gdy można automatycznie wkroczyć nad właściwościami i operatorami (zachowanie domyślne). Jeśli chcesz zmienić ustawienia później wyłączyć **Przekrocz nad właściwościami i operatorami** w **Narzędzia > Opcje** menu w obszarze **debugowanie**.

## <a name="step-over-code-to-skip-functions"></a>Przekrocz nad kod, aby pominąć funkcje

Gdy jesteś w wierszu kodu, który jest wywołaniem funkcji lub metody, możesz nacisnąć przycisk **F10** (**Debuguj > Step Over**) zamiast F11.

F10 przejście do kodu bez przechodzenie krok po kroku do funkcji lub metody w kodzie aplikacji (nadal wykonuje kod). Naciskając klawisz F10, możesz przejść przez kod, który nie interesują Cię. W ten sposób szybki dostęp do kodu, który Cię interesuje więcej.

## <a name="step-into-a-property"></a>Wejdź do właściwości

Jak wspomniano wcześniej, domyślnie debuger pomija za pośrednictwem właściwości zarządzane i pola, ale **Wkrocz do określonego** polecenie pozwala zmienić to zachowanie.

Kliknij prawym przyciskiem myszy na właściwość lub pole, a następnie wybierz **Wkrocz do określonego**, a następnie wybierz jedno z dostępnych opcji.

![Wkrocz do określonego](../debugger/media/dbg-tour-step-into-specific.png "Wkrocz do określonego")

W tym przykładzie **Wkrocz do określonego** pobiera nam na kod, aby `Path.set`.

![Wkrocz do określonego](../debugger/media/dbg-tour-step-into-specific-2.png "Wkrocz do określonego")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Uruchom do punktu w kodzie, szybko za pomocą myszy

Znajduje się w debugerze, umieść kursor nad wiersz kodu do czasu **uruchamianie do kliknięcia** przycisku (Uruchom wykonywanie do tego miejsca) ![uruchamianie do kliknięcia](../debugger/media/dbg-tour-run-to-click.png "RunToClick") pojawia się po lewej stronie.

![Uruchamianie do kliknięcia](../debugger/media/dbg-tour-run-to-click-2.png "uruchamianie do kliknięcia")

> [!NOTE]
> **Uruchamianie do kliknięcia** przycisku (Uruchom wykonywanie do tego miejsca) jest dostępna, począwszy od [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Kliknij przycisk **uruchamianie do kliknięcia** przycisku (Uruchom wykonywanie do tego miejsca). Debuger przechodzi do wiersza kodu, w której zostało kliknięte.

Za pomocą tego przycisku jest podobna do ustawienia tymczasowy punkt przerwania. To polecenie jest również przydatna dla szybko poruszanie się w obrębie regionu widoczne dla kodu aplikacji. Możesz użyć **uruchamianie do kliknięcia** otwartego pliku.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Przejdź do debugera, poza bieżącą funkcję

Czasami możesz chcieć kontynuować sesję debugowania, ale przejdź do debugera przez bieżącą funkcję.

Naciśnij klawisz **Shift + F11** (lub **Debuguj > Wyjdź**).

To polecenie wznawia działanie aplikacji (i umożliwia przejście do) do momentu zwraca bieżącą funkcję.

## <a name="run-to-cursor"></a>Uruchom do kursora

Przerwij debugowanie, naciskając klawisz **Zatrzymaj debugowanie** czerwony przycisk ![Zatrzymaj debugowanie](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") lub **Shift**  +  **F5**.

Kliknij prawym przyciskiem myszy linię kodu w aplikacji, a następnie wybierz **Uruchom do kursora**. To polecenie uruchamiania, debugowania i ustawia tymczasowy punkt przerwania w bieżącym wierszu kodu.

![Uruchom do kursora](../debugger/media/dbg-tour-run-to-cursor.png "Uruchom do kursora")

Jeśli zostały ustawione punkty przerwania, debuger wstrzymane na pierwszy punkt przerwania trafienia.

Naciśnij klawisz **F5** aż do wiersza kodu, gdy wybrana **Uruchom do kursora**.

To polecenie jest przydatne podczas edytowania kodu i chcesz szybko skonfigurować tymczasowy punkt przerwania i uruchomienia debugera w tym samym czasie.

> [!NOTE]
> Możesz użyć **Uruchom do kursora** w **stos wywołań** okna podczas debugowania.

## <a name="restart-your-app-quickly"></a>Szybko Uruchom ponownie swoją aplikację

Kliknij przycisk **ponowne uruchomienie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "ponowne uruchomienie aplikacji") przycisku na pasku narzędzi debugowania (**Ctrl + Shift + F5**).

Po naciśnięciu klawisza **ponowne uruchomienie**, można zaoszczędzić czas i zatrzymywanie aplikacji oraz ponownego uruchamiania debugera. Debuger wstrzymuje na pierwszy punkt przerwania zostanie osiągnięty przez wykonywanie kodu.

Jeśli chcesz zatrzymać debuger i wrócić do edytora kodu, możesz nacisnąć przycisk Zatrzymaj czerwony ![Zatrzymaj debugowanie](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") przycisk zamiast **ponowne uruchomienie**.

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych z poradami do danych

Teraz, gdy wiesz jak poruszać się nieco masz doskonała okazja, aby rozpocząć sprawdzanie stanu swojej aplikacji (zmienne) za pomocą debugera. Funkcje, które pozwalają na sprawdzanie zmiennych są niektóre z najbardziej przydatnych funkcjach debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu próbujesz sprawdzić, czy zmienne są przechowywane wartości, których można oczekiwać w stanie danej aplikacji.

Gdy wstrzymaniu w debugerze, umieść kursor nad obiekt przy użyciu myszy i sprawdź wartość właściwości domyślną (w tym przykładzie nazwa pliku `market 031.jpg` jest wartością domyślną właściwości).

![Wyświetl etykietki danych](../debugger/media/dbg-tour-data-tips.gif "wyświetlanie etykietki danych")

Rozwiń obiekt, aby wyświetlić jego właściwości (takie jak `FullPath` właściwości w tym przykładzie).

Często podczas debugowania, chcesz, aby szybko sprawdzić wartości właściwości obiektów i porady dotyczące danych są dobrym sposobem, aby to zrobić.

> [!TIP]
> W większości obsługiwanych językach można edytować kod w trakcie sesji debugowania. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien zmiennych automatycznych i zmiennych lokalnych

Podczas debugowania, Przyjrzyj się **Autos** okna w dolnej części edytora kodu.

![Okno zmiennych automatycznych](../debugger/media/dbg-tour-autos-window.png "okno zmiennych automatycznych")

W **Autos** okna, widać zmienne wraz z ich bieżącą wartość i ich typu. **Autos** okno pokazuje wszystkie zmienne używane w bieżącym wierszu lub poprzedni wiersz (w języku C++, w oknie wyświetlane zmienne w poprzednim trzech wierszach kodu. Sprawdź dokumentację dla zachowania specyficzne dla języka).

> [!NOTE]
> W języku JavaScript **lokalne** okno jest nie obsługiwane **Autos** okna.

Następnie Przyjrzyj się **lokalne** okna. **Lokalne** okno zawiera zmienne, które obecnie znajdują się w zakresie.

![Okno zmiennych lokalnych](../debugger/media/dbg-tour-locals-window.png "okno zmiennych lokalnych")

W tym przykładzie `this` obiekt oraz obiekt `f` znajdują się w zakresie. Aby uzyskać więcej informacji, zobacz [sprawdzić zmiennych w zmiennych automatycznych i zmiennych lokalnych Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Ustawianie wyrażenia kontrolnego

Możesz użyć **Obejrzyj** okna, aby określić zmienną (lub wyrażenie), który chcesz śledzić na.

Podczas debugowania, kliknij prawym przyciskiem myszy obiekt, a następnie wybierz **Dodaj czujkę**.

![Okno czujki](../debugger/media/dbg-tour-watch-window.png "okno czujki")

W tym przykładzie ma wyrażenia kontrolnego nastavit `f` obiektu, aby sprawdzić jej wartość zmienić podczas przeglądania przez debuger. W przeciwieństwie do innych zmiennych systemu windows **Obejrzyj** systemu windows zawsze pokazuj zmienne czy obserwujesz (są one wygaszone się kiedy poza zakresem).

Aby uzyskać więcej informacji, zobacz [Ustawianie wyrażenia kontrolnego przy użyciu wyrażenie kontrolne i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Sprawdź stos wywołań

Kliknij przycisk **stos wywołań** okna podczas debugowania, która jest domyślnie otwarty w dolnym okienku po prawej stronie.

![Sprawdź stos wywołań](../debugger/media/dbg-tour-call-stack.png "analizować stos wywołań")

**Stos wywołań** okno pokazuje kolejność, w którym są wprowadzenie wywoływane metody i funkcje. Górny wiersz zawiera bieżącą funkcję ( `Update` metody w tym przykładzie). Drugi wiersz wskazuje, że `Update` została wywołana z `Path.set` właściwości i tak dalej. Stos wywołań jest dobrym sposobem na badania i informacje na temat wykonywania przepływu aplikacji.

> [!NOTE]
> **Stos wywołań** jest podobne do perspektywy debugowania w niektórych środowiskach IDE, takich jak Eclipse.

Możesz kliknąć dwukrotnie wiersz kodu, aby przyjrzeć się kodu źródłowego i zmienia także bieżący zakres kontrolowanym przez debuger. To nie jest wcześniejsze debugera.

Można również użyć menu kliknij prawym przyciskiem myszy **stos wywołań** okna, aby wykonywać inne czynności. Na przykład, można wstawić punktów przerwania do określonych funkcji, ponowne uruchomienie aplikacji przy użyciu **Uruchom do kursora**i przejść zbadanie kodu źródłowego. Zobacz [jak: Sprawdź stos wywołań](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Sprawdź wyjątek

Jeśli aplikacja zgłasza wyjątek, debuger umożliwia przejście do wiersza kodu, który wygenerował wyjątek.

![Pomocnik wyjątków](../debugger/media/dbg-tour-exception-helper.png "pomocnika wyjątków")

W tym przykładzie **pomocnika wyjątków** pokazuje `System.Argument` wyjątku i komunikatu o błędzie, informujący o tym, że ścieżka nie jest niedozwolony format. Tak wiemy, że błąd wystąpił w nim argumentu metody lub funkcji.

W tym przykładzie `DirectoryInfo` wywołanie udostępniła błędu na pusty ciąg, które są przechowywane w `value` zmiennej.

Pomocnik wyjątków jest doskonałym funkcja, która pomaga debugować błędy. Można również wykonywać następujące czynności dla widoku szczegółów błędu i Dodaj wyrażenie kontrolne z Pomocnika wyjątków. Lub, jeśli to konieczne, można zmienić warunków zgłaszania określonego wyjątku. Aby uzyskać więcej informacji na temat sposobu obsługi wyjątków w kodzie, zobacz [debugowania, narzędzia i techniki](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> Asystent wyjątków od zastąpione pomocnika wyjątków [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Rozwiń **ustawienia wyjątków** węzeł, aby wyświetlić więcej opcji, w jaki sposób obsługiwać ten typ wyjątku, ale nie trzeba wprowadzić w tym samouczku zmiany!

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Debugowanie na żywo aplikacji ASP.NET w usłudze Azure App Service

**rozszerzenia Snapshot Debugger** tworzy migawkę aplikacji w środowisku produkcyjnym, gdy wykonuje kod, który Cię interesuje. Aby nakazać debugera, aby utworzyć migawkę, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie tego, co poszło, bez wywierania wpływu na ruch z aplikacji produkcyjnej. Rozszerzenie Snapshot Debugger może pomóc w znacznie skrócić czas potrzebny do rozwiązywania problemów występujących w środowiskach produkcyjnych.

![Uruchamianie rozszerzenia snapshot debugger](../debugger/media/snapshot-launch.png "uruchamianie rozszerzenia snapshot debugger")

Zbieranie migawek jest dostępna dla aplikacji ASP.NET uruchomionych w usłudze Azure App Service. Aplikacje ASP.NET musi działać w programie .NET Framework 4.6.1 lub nowszej, a aplikacje platformy ASP.NET Core musi działać w programie .NET Core 2.0 lub nowszych na Windows.

Aby uzyskać więcej informacji, zobacz [debugowania działających aplikacji platformy ASP.NET przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Wyświetl migawki za pomocą funkcji IntelliTrace krok do tyłu (Visual Studio Enterprise)

**IntelliTrace krok do tyłu** umożliwia automatyczne utworzenie migawki aplikacji na każdym punkcie przerwania i debuger krok zdarzenia. Zarejestrowane migawek umożliwiają wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, tak jak w przeszłości. IntelliTrace krok do tyłu pozwalają zaoszczędzić czas podczas mają być wyświetlane poprzedni stan aplikacji, ale nie chcesz ponownie uruchomić debugowanie lub Utwórz ponownie stan żądaną aplikację.

Można poruszać się i Wyświetl migawki za pomocą **krok do tyłu** i **krok do przodu** przycisków na pasku narzędzi debugowania. Te przyciski nawigacji zdarzenia, które pojawiają się w **zdarzenia** karcie **narzędzia diagnostyczne** okna.

![Krok do tyłu i do przodu przyciski](../debugger/media/intellitrace-step-back-icons-description.png  "przyciski krok do tyłu i do przodu")

Aby uzyskać więcej informacji, zobacz [Sprawdź poprzednie Stany aplikacji za pomocą funkcji IntelliTrace](../debugger/view-historical-application-state.md) strony.

## <a name="next-steps"></a>Następne kroki

W tym samouczku przeznaczono krótkie omówienie wielu funkcji debugowania. Możesz bardziej przyjrzeć się dokładnie jeden z tych funkcji, takich jak punkty przerwania.

> [!div class="nextstepaction"]
> [Informacje na temat używania punktów przerwania](../debugger/using-breakpoints.md)

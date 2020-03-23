---
title: Pierwsze spojrzenie na debugera
description: Wprowadzenie do debugowania aplikacji przy użyciu debugera programu Visual Studio
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
ms.openlocfilehash: 93973322c40ca62396414317c2ad8875e9b94854
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77578957"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Pierwsze spojrzenie na debuger programu Visual Studio

W tym temacie przedstawiono narzędzia debugera dostarczone przez program Visual Studio. W kontekście programu Visual Studio podczas *debugowania aplikacji*zwykle oznacza to, że aplikacja jest uruchomiona z dołączonym debugerem (czyli w trybie debugera). Po wykonaniu tej funkcji debuger udostępnia wiele sposobów, aby zobaczyć, co robi kod podczas jego działania. Można przejść przez kod i spojrzeć na wartości przechowywane w zmiennych, można ustawić zegarki na zmienne, aby zobaczyć, kiedy zmiany wartości, można sprawdzić ścieżkę wykonywania kodu, i wsp. Jeśli jest to pierwszy raz, który próbowałeś debugować kod, możesz przeczytać [Debugowanie dla początkujących absolutnych](../debugger/debugging-absolute-beginners.md) przed przejściem przez ten temat.

Funkcje opisane w tym miejscu mają zastosowanie do języka C#, C++, Visual Basic, JavaScript i innych języków obsługiwanych przez program Visual Studio (z wyjątkiem przypadków, w których zaznaczono inaczej).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustawianie punktu przerwania i uruchamianie debugera

Aby debugować, należy uruchomić aplikację z debugerem dołączonym do procesu aplikacji. **F5** **(Debug > Start Debugowanie)** jest najczęstszym sposobem, aby to zrobić. Jednak teraz może nie ustawić żadnych punktów przerwania, aby sprawdzić kod aplikacji, więc zrobimy to najpierw, a następnie rozpocząć debugowanie. Punkty przerwania są najbardziej podstawową i istotną cechą niezawodnego debugowania. Punkt przerwania wskazuje, gdzie visual studio należy zawiesić uruchomiony kod, dzięki czemu można spojrzeć na wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu jest coraz uruchamiany.

Jeśli masz plik otwarty w edytorze kodu, można ustawić punkt przerwania, klikając na marginesie po lewej stronie wiersza kodu.

![Ustawianie punktu przerwania](../debugger/media/dbg-tour-set-a-breakpoint.gif "Ustawianie punktu przerwania")

Naciśnij **klawisz F5** **(Debugowanie > rozpocznij debugowanie)** lub przycisk **Start Debugowania** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi Debugowania, a debuger zostanie uruchomiony do pierwszego punktu przerwania, który napotka. Jeśli aplikacja nie jest jeszcze uruchomiona, F5 uruchamia debugera i zatrzymuje się w pierwszym punkcie przerwania.

Punkty przerwania są przydatne funkcji, gdy znasz wiersz kodu lub sekcji kodu, które chcesz zbadać szczegółowo.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a>Nawigowanie po kodzie w debugerze przy użyciu poleceń kroków

Zapewniamy skróty klawiaturowe dla większości poleceń, ponieważ przyspieszają one nawigację po kodzie aplikacji. (Równoważne polecenia, takie jak polecenia menu, są wyświetlane w nawiasach).

Aby uruchomić aplikację z dołączonym debugerem, naciśnij **klawisz F11** (**Debug > Step Into**). F11 jest **step into** polecenia i zaliczki wykonywania aplikacji jedną instrukcję naraz. Po uruchomieniu aplikacji z F11 debuger przerwy na pierwszej instrukcji, która zostanie wykonana.

![F11 Krok do](../debugger/media/dbg-tour-f11.png "F11 Krok do")

Żółta strzałka reprezentuje instrukcję, na której debuger wstrzymane, który również zawiesza wykonywanie aplikacji w tym samym momencie (ta instrukcja nie została jeszcze wykonana).

F11 jest dobrym sposobem, aby zbadać przepływ wykonania w najbardziej szczegółowo. (Aby szybciej poruszać się po kodzie, pokazujemy również kilka innych opcji). Domyślnie debuger przeskakuje nad kodem niebędącym użytkownikiem (jeśli chcesz uzyskać więcej szczegółów, zobacz [Tylko mój kod](../debugger/just-my-code.md)).

>[!NOTE]
> W kodzie zarządzanym zostanie wyświetlone okno dialogowe z pytaniem, czy chcesz otrzymywać powiadomienia, gdy automatycznie nadchodzą właściwości i operatory (zachowanie domyślne). Jeśli chcesz zmienić to ustawienie później, wyłącz ustawienie **Krok nad właściwościami i operatorami** w menu **Narzędzia > Opcje** w obszarze **Debugowanie**.

## <a name="step-over-code-to-skip-functions"></a>Krok po kroku kodu, aby pominąć funkcje

Gdy jesteś w wierszu kodu, który jest wywołaniem funkcji lub metody, można nacisnąć **klawisz F10** (**Debug > Step Over**) zamiast F11.

F10 zaliczki debugera bez przechodzenia do funkcji lub metod w kodzie aplikacji (kod nadal wykonuje). Naciskając klawisz F10, możesz pominąć kod, który Cię nie interesuje. W ten sposób można szybko uzyskać dostęp do kodu, który jesteś bardziej zainteresowany.

## <a name="step-into-a-property"></a>Wejdź do nieruchomości

Jak wspomniano wcześniej, domyślnie debuger pomija właściwości i pola zarządzane, ale **step into specific** polecenia pozwala zastąpić to zachowanie.

Kliknij prawym przyciskiem myszy właściwość lub pole i wybierz **polecenie Krok do konkretów,** a następnie wybierz jedną z dostępnych opcji.

![Krok do konkretnych](../debugger/media/dbg-tour-step-into-specific.png "Krok do konkretnych")

W tym przykładzie **Step Into Specific** `Path.set`prowadzi nas do kodu dla .

![Krok do konkretnych](../debugger/media/dbg-tour-step-into-specific-2.png "Krok do konkretnych")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Szybkie uruchamianie do punktu w kodzie za pomocą myszy

Podczas gdy w debugerze, najedź kursorem na wiersz kodu, aż **przycisk Uruchom, aby kliknąć** (Uruchom wykonanie tutaj) ![Uruchom do kliknięcia](../debugger/media/dbg-tour-run-to-click.png "RunToClick (RunToClick)") pojawia się po lewej stronie.

![Uruchom do kliknięcia](../debugger/media/dbg-tour-run-to-click-2.png "Uruchom do kliknięcia")

> [!NOTE]
> Przycisk **Uruchom, aby kliknąć** (Uruchom wykonanie [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]w tym miejscu) jest dostępny od .

Kliknij przycisk **Uruchom, aby kliknąć** (Uruchom wykonanie tutaj). Debuger przechodzi do wiersza kodu, w którym kliknięno.

Użycie tego przycisku jest podobne do ustawiania tymczasowego punktu przerwania. To polecenie jest również przydatne do szybkiego poruszania się w widocznym regionie kodu aplikacji. Możesz użyć **uruchom, aby kliknąć** w dowolnym otwartym pliku.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Wyjmij debuger z bieżącej funkcji

Czasami można kontynuować sesję debugowania, ale przejść debugera przez całą drogę przez bieżącą funkcję.

Naciśnij **klawisze Shift + F11** (lub **Debug > Step Out).**

To polecenie wznawia wykonywanie aplikacji (i przesuwa debuger) do momentu powrotu bieżącej funkcji.

## <a name="run-to-cursor"></a>Uruchamianie do kursora

Zatrzymaj debuger, naciskając czerwony przycisk **Zatrzymaj debugowanie** lub **Shift** + **F5**. ![Stop Debugging](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie")

Kliknij prawym przyciskiem myszy wiersz kodu w aplikacji i wybierz polecenie **Uruchom do kursora**. To polecenie uruchamia debugowanie i ustawia tymczasowy punkt przerwania w bieżącym wierszu kodu.

![Uruchom do kursora](../debugger/media/dbg-tour-run-to-cursor.png "Uruchom do kursora")

Jeśli masz ustawione punkty przerwania, debuger wstrzymuje się na pierwszym punkcie przerwania, który zostanie przesunie.

Naciskaj **klawisz F5,** aż dojdziesz do wiersza kodu, w którym wybrano **opcję Uruchom do kursora**.

To polecenie jest przydatne podczas edytowania kodu i chcesz szybko ustawić tymczasowy punkt przerwania i uruchomić debuger w tym samym czasie.

> [!NOTE]
> Można użyć **Uruchom do kursora** w oknie **Stos wywołań** podczas debugowania.

## <a name="restart-your-app-quickly"></a>Szybkie ponowne uruchamianie aplikacji

Kliknij przycisk **Uruchom ponownie** ![aplikację](../debugger/media/dbg-tour-restart.png "Uruchom ponownie aplikację") na pasku narzędzi debugowania (**Ctrl + Shift +F5**).

Po naciśnięciu **przycisku Uruchom ponownie**, oszczędza czas w porównaniu do zatrzymania aplikacji i ponownego uruchomienia debugera. Debuger wstrzymuje w pierwszym punkcie przerwania, który jest trafiony przez wykonanie kodu.

Jeśli chcesz zatrzymać debuger i wrócić do edytora kodu, możesz nacisnąć czerwony przycisk ![zatrzymaj debugowanie](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") zamiast **restartu**.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Edytuj kod i kontynuuj debugowanie (C#, VB, C++, XAML)

W większości języków obsługiwanych przez program Visual Studio można edytować kod w środku sesji debugowania i kontynuować debugowanie. Aby użyć tej funkcji, kliknij kod z kursorem wstrzymany w debugerze, wykonuj zmiany i naciśnij **klawisze F5**, **F10**lub **F11,** aby kontynuować debugowanie.

![Edytowanie i kontynuowanie debugowania](../debugger/media/dbg-tips-edit-and-continue.gif "Edytuj iwzrozumiej")

Aby uzyskać więcej informacji na temat korzystania z funkcji i ograniczeń funkcji, zobacz [Edytowanie i kontynuowanie](../debugger/edit-and-continue.md).

Aby zmodyfikować kod XAML podczas sesji debugowania, zobacz [Pisanie i debugowanie z uruchomionym kodem XAML z załaduj ponownie gorąca xaml](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych za pomocą wskazówek dotyczących danych

Teraz, gdy wiesz, jak się poruszać trochę, masz dobrą okazję, aby rozpocząć sprawdzanie stanu aplikacji (zmienne) z debugerem. Funkcje, które umożliwiają sprawdzanie zmiennych są niektóre z najbardziej przydatnych funkcji debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu, próbujesz dowiedzieć się, czy zmienne są przechowywanie wartości, które oczekują, że mają w określonym stanie aplikacji.

Po wstrzymaniu w debugerze umieść wskaźnik myszy na obiekcie myszy i zobaczysz jego `market 031.jpg` domyślną wartość właściwości (w tym przykładzie nazwa pliku jest domyślną wartością właściwości).

![Wyświetlanie końcówki danych](../debugger/media/dbg-tour-data-tips.gif "Wyświetlanie końcówki danych")

Rozwiń obiekt, aby wyświetlić wszystkie `FullPath` jego właściwości (takie jak właściwość w tym przykładzie).

Często podczas debugowania, chcesz szybki sposób, aby sprawdzić wartości właściwości na obiektach, a wskazówki dotyczące danych są dobrym sposobem, aby to zrobić.

> [!TIP]
> W większości obsługiwanych języków można edytować kod w środku sesji debugowania. Aby uzyskać więcej informacji, zobacz [Edytowanie i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien Autos i Locals

Podczas debugowania, spójrz na **autos** okna w dolnej części edytora kodu.

![Okno autos](../debugger/media/dbg-tour-autos-window.png "okno zmiennych automatycznych")

W oknie **Autos** są widoczne zmienne wraz z ich bieżącą wartością i typem. Okno **Autos** zawiera wszystkie zmienne używane w bieżącym wierszu lub poprzednim wierszu (w języku C++ okno pokazuje zmienne w poprzednich trzech wierszach kodu. Sprawdź dokumentację zachowania specyficznego dla języka).

> [!NOTE]
> W języku JavaScript okno **Zmiennych** jest obsługiwane, ale nie okno **Autos.**

Następnie spójrz na okno **Miejscowi.** W oknie **Locals** są wyświetlane zmienne, które są obecnie w zakresie.

![Okno miejscowi](../debugger/media/dbg-tour-locals-window.png "okno zmiennych lokalnych")

W tym przykładzie `this` obiekt `f` i obiekt znajdują się w zakresie. Aby uzyskać więcej informacji, zobacz [Inspekcja zmiennych w systemie Windows Autos i Locals](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Ustawianie zegarka

Za pomocą okna **Czujka** można określić zmienną (lub wyrażenie), które ma być obserwowane.

Podczas debugowania kliknij prawym przyciskiem myszy obiekt i wybierz polecenie **Dodaj czujki**.

![Okno zegarka](../debugger/media/dbg-tour-watch-window.png "okno czujki")

W tym przykładzie masz zegarek `f` ustawiony na obiekcie i widać jego zmiany wartości podczas poruszania się przez debuger. W przeciwieństwie do innych okien zmiennych okna **czujki** zawsze pokazują zmienne, które oglądasz (są wyszarzone, gdy są poza zakresem).

Aby uzyskać więcej informacji, zobacz [Ustawianie zegarka przy użyciu zegarka i szybkiego zegarka Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Sprawdź stos wywołań

Kliknij okno **Stos wywołań** podczas debugowania, które jest domyślnie otwarte w prawym dolnym okienku.

![Sprawdź stos połączeń](../debugger/media/dbg-tour-call-stack.png "Sprawdź stos wywołań")

Okno **Stos wywołań** pokazuje kolejność, w jakiej metody i funkcje są wywoływane. Górny wiersz pokazuje bieżącą `Update` funkcję (metodę w tym przykładzie). Druga linia pokazuje, że `Update` `Path.set` został wywołany z nieruchomości, i tak dalej. Stos wywołań jest dobrym sposobem, aby zbadać i zrozumieć przepływ wykonywania aplikacji.

> [!NOTE]
> Okno **Stos wywołań** jest podobne do perspektywy debugowania w niektórych środowiskach IDE, takich jak Eclipse.

Można dwukrotnie kliknąć wiersz kodu, aby przejść do tego kodu źródłowego i który również zmienia bieżący zakres jest sprawdzany przez debugera. To nie zaliczki debugera.

Można również użyć menu prawym przyciskiem myszy z okna **Stos wywołań,** aby wykonać inne czynności. Na przykład można wstawić punkty przerwania do określonych funkcji, ponownie uruchomić aplikację przy użyciu **uruchom do kursora**i przejść do badania kodu źródłowego. Zobacz [Jak: Sprawdź stos wywołań](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a><a name="exception"></a>Badanie wyjątku

Gdy aplikacja zgłasza wyjątek, debuger zabierze Cię do wiersza kodu, który zgłosił wyjątek.

![Pomocnik wyjątków](../debugger/media/dbg-tour-exception-helper.png "Pomocnik wyjątków")

W tym **przykładzie Pomocnik wyjątku** pokazuje `System.Argument` wyjątek i komunikat o błędzie, który mówi, że ścieżka nie jest formą prawną. Wiemy więc, że wystąpił błąd w argusie metody lub funkcji.

W tym przykładzie wywołanie `DirectoryInfo` podało błąd na `value` pusty ciąg przechowywany w zmiennej.

Pomocnik wyjątków jest świetną funkcją, która może pomóc w debugowaniu błędów. Można również wykonać takie czynności, jak wyświetlanie szczegółów błędu i dodawanie zegarka z Pomocnika wyjątku. Lub w razie potrzeby można zmienić warunki zgłaszania określonego wyjątku. Aby uzyskać więcej informacji na temat obsługi wyjątków w kodzie, zobacz [Techniki debugowania i narzędzia](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> Pomocnik wyjątków zastąpił Asystenta [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]wyjątków, począwszy od .

Rozwiń węzeł **Ustawienia wyjątków,** aby zobaczyć więcej opcji obsługi tego typu wyjątku, ale nie trzeba niczego zmieniać dla tej wycieczki!

## <a name="configure-debugging"></a>Konfigurowanie debugowania

Można skonfigurować projekt do tworzenia jako [konfiguracji debugowania lub wydania,](../debugger/how-to-set-debug-and-release-configurations.md)skonfigurować właściwości projektu do debugowania lub skonfigurować [ogólne ustawienia](../debugger/how-to-specify-debugger-settings.md) debugowania. Ponadto można skonfigurować debuger do wyświetlania informacji niestandardowych przy użyciu funkcji, takich jak [debuggerDisplay](using-the-debuggerdisplay-attribute.md) atrybut lub, dla C/C ++, [Rama NatVis](create-custom-views-of-native-objects.md).

Właściwości debugowania są specyficzne dla każdego typu projektu. Na przykład można określić argument, aby przekazać do aplikacji po uruchomieniu go. Dostęp do właściwości specyficznych dla projektu można uzyskać, klikając prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierając polecenie **Właściwości**. Właściwości debugowania zazwyczaj pojawiają się na karcie **Kompilacja** lub **Debugowanie,** w zależności od określonego typu projektu.

![Właściwości projektu](../debugger/media/dbg-tour-project-properties.png "Właściwości projektu")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Debugowanie aplikacji ASP.NET na żywo w usłudze Azure App Service

**Debuger migawki** wykonuje migawkę aplikacji w produkcji, gdy kod, który jest zainteresowany wykonuje. Aby poinstruować debugera, aby zrobić migawkę, należy ustawić punkty przyciągania i punkty dziennika w kodzie. Debuger pozwala zobaczyć dokładnie, co poszło nie tak, bez wpływu na ruch aplikacji produkcyjnej. Debuger migawek może pomóc znacznie skrócić czas potrzebny do rozwiązania problemów występujących w środowiskach produkcyjnych.

![Uruchamianie debugera migawki](../debugger/media/snapshot-launch.png "Uruchamianie debugera migawki")

Kolekcja migawek jest dostępna dla aplikacji ASP.NET uruchomionych w usłudze Azure App Service. ASP.NET aplikacje muszą być uruchomione w programie .NET Framework 4.6.1 lub nowszym, a ASP.NET aplikacje Core muszą być uruchomione w systemie .NET Core 2.0 lub nowszym w systemie Windows.

Aby uzyskać więcej informacji, zobacz [Debugowanie aplikacji na żywo ASP.NET przy użyciu debugera migawek](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Wyświetlanie migawek za pomocą funkcji IntelliTrace step-back (Visual Studio Enterprise)

**IntelliTrace krok wstecz** automatycznie wykonuje migawkę aplikacji w każdym punkcie przerwania i debugera zdarzenia kroku. Zarejestrowane migawki umożliwiają powrót do poprzednich punktów przerwania lub kroki i wyświetlić stan aplikacji, jak to było w przeszłości. IntelliTrace krok wstecz można zaoszczędzić czas, gdy chcesz zobaczyć poprzedni stan aplikacji, ale nie chcesz ponownie debugowania lub ponownie utworzyć żądany stan aplikacji.

Migawki można nawigować i wyświetlać za pomocą przycisków **Krok do tyłu** i Krok do **przodu** na pasku narzędzi Debugowania. Te przyciski nawigują po zdarzeniach wyświetlanych na karcie **Zdarzenia** w oknie **Narzędzia diagnostyczne.**

![Przyciski krok do tyłu i do przodu](../debugger/media/intellitrace-step-back-icons-description.png  "Przyciski Krok do tyłu i Do przodu")

Aby uzyskać więcej informacji, zobacz [Inspekcja poprzednich stanów aplikacji przy użyciu intellitrace](../debugger/view-historical-application-state.md) strony.

## <a name="debug-performance-issues"></a>Problemy z wydajnością debugowania

Jeśli aplikacja działa zbyt wolno lub używa zbyt dużej ilości pamięci, może być konieczne przetestowanie aplikacji za pomocą narzędzi profilowania na wczesnym etapie. Aby uzyskać więcej informacji na temat narzędzi profilowania, takich jak narzędzie Użycie procesora i analizator pamięci, zobacz [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku, miałeś szybkie spojrzenie na wiele funkcji debugera. Można bardziej dogłębne spojrzenie na jedną z tych funkcji, takich jak punkty przerwania.

> [!div class="nextstepaction"]
> [Naucz się używać punktów przerwania](../debugger/using-breakpoints.md)

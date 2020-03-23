---
title: Wyświetlanie poprzedniego stanu aplikacji przy użyciu funkcji IntelliTrace
description: Dowiedz się, jak robić migawki i wyświetlać migawki za pomocą funkcji IntelliTrace step-back
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83d444cb5e3345d79ca6e1422982c0ecd37e4287
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67825526"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Sprawdzanie poprzednich stanów aplikacji przy użyciu funkcji IntelliTrace step-back w programie Visual Studio (Visual Studio Enterprise)

IntelliTrace krok wstecz automatycznie wykonuje migawkę aplikacji w każdym punkcie przerwania i debugera zdarzenia kroku. Zarejestrowane migawki umożliwiają powrót do poprzednich punktów przerwania lub kroki i wyświetlić stan aplikacji, jak to było w przeszłości. IntelliTrace krok wstecz można zaoszczędzić czas, gdy chcesz zobaczyć poprzedni stan aplikacji, ale nie chcesz ponownie debugowania lub ponownie utworzyć żądany stan aplikacji.

IntelliTrace krok wstecz jest dostępny począwszy od programu Visual Studio Enterprise 2017 w wersji 15.5 lub nowszej i wymaga aktualizacji rocznicowej systemu Windows 10 lub nowszej. Funkcja jest obecnie obsługiwana do debugowania ASP.NET, WinForms, WPF, zarządzanych aplikacji konsoli i bibliotek klas zarządzanych. Począwszy od programu Visual Studio 2017 Enterprise w wersji 15.7, funkcja jest również obsługiwana dla ASP.NET Core i .NET Core. Począwszy od programu Visual Studio 2017 Enterprise w wersji 15.9 w wersji zapoznawczej 2, funkcja jest również obsługiwana dla aplikacji natywnych przeznaczonych dla systemu Windows. Debugowanie aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu nie jest obecnie obsługiwane.

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
> * Włączanie zdarzeń i migawek funkcji IntelliTrace
> * Nawigowanie po zdarzeniach za pomocą poleceń krok wstecz i krok do przodu
> * Wyświetlanie migawek zdarzeń

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Włącz tryb zdarzeń i migawek IntelliTrace

1. Otwórz projekt w programie Visual Studio Enterprise.

1. Otwórz**opcje** >  **narzędzi** > **IntelliTrace** ustawienia i wybierz opcję **IntelliTrace zdarzenia i migawki**.

    Począwszy od programu Visual Studio 2017 Enterprise w wersji 15.9 Wersja zapoznawcza 2, ta opcja jest **IntelliTrace migawek (zarządzane i natywne)**.

    ![Włącz tryb Zdarzeń i migawek IntelliTrace](../debugger/media/intellitrace-enable-snapshots.png "Włącz tryb Zdarzeń i migawek IntelliTrace")

1. Jeśli chcesz skonfigurować opcje wyświetlania migawek z wyjątkami, wybierz **intellitrace** > **zaawansowane** z okna dialogowego **Opcje.**

    Te opcje są dostępne od programu Visual Studio 2017 Enterprise w wersji 15.7.

    ![Konfigurowanie zachowania dla migawek w przypadku wyjątków](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Po włączeniu zdarzeń i migawek, robienie migawek na wyjątki jest również domyślnie włączona. Migawki można wyłączyć w wyjątkach, odznaczając **zbieranie migawek w zdarzeniach wyjątków.** Gdy ta funkcja jest włączona, migawki są pobierane dla nieobsługiwał wyjątków. W przypadku obsługiwanych wyjątków migawki są podejmowane tylko wtedy, gdy wyjątek jest zgłaszany i jeśli nie jest ponownie zgłosić wcześniej zgłoszony wyjątek. Można ustawić maksymalną liczbę migawek na wyjątki, wybierając wartość z listy rozwijanej. Maksymalna liczba aplikacji ma zastosowanie za każdym razem, gdy aplikacja wchodzi w tryb przerwania (na przykład gdy aplikacja osiągnie punkt przerwania).

    > [!NOTE]
    > Migawki są podejmowane tylko dla zdarzeń wyjątków, które intellitrace rekordy. W przypadku kodu zarządzanego można określić, jakie zdarzenia intellitrace rekordy, wybierając**opcje** >  **narzędzia** > **IntelliTrace Zdarzenia**.

1. W projekcie ustaw jeden lub więcej punktów przerwania i rozpocznij debugowanie (naciśnij **klawisz F5**) lub rozpocznij debugowanie, przechodząc przez krok po kroku (**F10** lub **F11**).

    IntelliTrace wykonuje migawkę procesu aplikacji na każdy krok debugera, zdarzenie punktu przerwania i nieobsługiwał zdarzenia wyjątku. Zdarzenia te są rejestrowane na karcie **Zdarzenia** w oknie **Narzędzia diagnostyczne** wraz z innymi zdarzeniami IntelliTrace. Aby otworzyć to okno, wybierz pozycję **Debugowanie** > **narzędzi diagnostycznych programu****Windows** > Show .

    Obok zdarzeń, dla których są dostępne migawki, pojawi się ikona kamery.

    ![Karta Zdarzenia z migawkami](../debugger/media/intellitrace-events-tab-with-snapshots.png "Karta Zdarzenia z migawkami w punktach przerwania i krokach")

    Ze względu na wydajność migawki nie są podejmowane podczas kroku bardzo szybko. Jeśli obok kroku nie jest wyświetlana żadna ikona aparatu, spróbuj przyspieszyć wolniej.

## <a name="navigate-and-view-snapshots"></a>Nawigowanie i wyświetlanie migawek

1. Nawigowanie między zdarzeniami za pomocą przycisków **Krok do tyłu (Alt + [)** i **Krok do przodu (Alt + ])** na pasku narzędzi Debugowania.

    Te przyciski nawigują po zdarzeniach wyświetlanych na karcie **Zdarzenia** w **oknie Narzędzia diagnostyczne**. Przechodzenie do tyłu lub do przodu do zdarzenia automatycznie aktywuje [debugowanie historyczne](../debugger/historical-debugging.md) na wybrane zdarzenie.

    ![Przyciski Krok do tyłu i Do przodu](../debugger/media/intellitrace-step-back-icons-description.png "Przyciski Krok do tyłu i Krok do przodu")

    Po kroku wstecz lub krok do przodu, Visual Studio wchodzi w tryb debugowania historycznych. W tym trybie kontekst debugera przełącza się do czasu, kiedy zarejestrowano wybrane zdarzenie. Visual Studio przenosi również wskaźnik do odpowiedniego wiersza kodu w oknie źródłowym.

    W tym widoku można sprawdzić wartości w oknach **Stos wywołań,** **Zmienne,** **Autos**i **Obserwuj.** Można również najechać kursorem na zmienne, aby wyświetlić łaty danych i przeprowadzić ocenę wyrażenia w oknie **Natychmiastowe.** Dane, które widzisz, pochodzą z migawki procesu aplikacji wykonanej w tym momencie.

    Tak, na przykład, jeśli już trafić punkt przerwania i podjęte krok **(F10),** **krok wstecz** przycisk stawia Visual Studio w trybie historycznym w wierszu kodu odpowiadającego punkt przerwania.

    ![Aktywowanie trybu historycznego w wydarzeniu z migawką](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Aktywowanie trybu historycznego w wydarzeniu z migawką")

2. Aby powrócić do wykonania na żywo, wybierz przycisk **Kontynuuj (F5)** lub kliknij łącze **Powrót do debugowania na żywo** na pasku informacyjnym.

3. Migawkę można również wyświetlić na karcie **Zdarzenia.** Aby to zrobić, wybierz zdarzenie z migawką i kliknij przycisk **Aktywuj debugowanie historyczne**.

    ![Uaktywnianie debugowania historycznego podczas wydarzenia](../debugger/media/intellitrace-activate-historical-debugging.png "Uaktywnianie debugowania historycznego podczas wydarzenia")

    W przeciwieństwie do polecenia **Ustaw następną instrukcję,** wyświetlanie migawki nie jest ponownie uruchom kod; zapewnia statyczny widok stanu aplikacji w momencie, który wystąpił w przeszłości.

    ![Omówienie kroku IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Omówienie funkcji IntelliTrace Step-Back")

    Aby dowiedzieć się więcej o sprawdzaniu zmiennych w programie Visual Studio, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Czym różni się krok intellitrace od trybu tylko zdarzeń IntelliTrace?

IntelliTrace w trybie tylko zdarzenia pozwala aktywować debugowanie historyczne na debuger kroki i punkty przerwania. Jednak IntelliTrace przechwytuje dane tylko w **oknach Locals** i **Autos,** jeśli okna są otwarte i przechwytuje tylko dane, które są rozwinięte i w widoku. W trybie tylko zdarzenia często nie mają pełnego widoku zmiennych i złożonych obiektów. Ponadto ocena wyrażenia i wyświetlanie danych w oknie **Czujka** nie jest obsługiwane.

W trybie zdarzeń i migawek IntelliTrace przechwytuje całą migawkę procesu aplikacji, w tym złożonych obiektów. W wierszu kodu można zobaczyć te same informacje, jak gdyby zostały zatrzymane w punkcie przerwania (i nie ma znaczenia, czy wcześniej rozwinięto informacje). Ocena wyrażenia jest również obsługiwana podczas wyświetlania migawki.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Jaki jest wpływ tej funkcji na wydajność? 

Wpływ na ogólną wydajność krokowego zależy od aplikacji. Obciążenie związane z zrobieniem migawki wynosi około 30 ms. Po wykonaniu migawki proces aplikacji jest rozwidliony, a kopia rozwidlecowa jest zawieszona. Podczas wyświetlania migawki visual studio jest dołączanie do rozwidał kopię procesu. Dla każdej migawki visual studio kopiuje tylko tabelę stron i ustawia strony do kopiowania na zapis. Jeśli obiekty na stercie zmiany między krokami debugera z skojarzonych migawek, odpowiedniej tabeli strony jest następnie kopiowane, co powoduje minimalny koszt pamięci. Jeśli program Visual Studio wykryje, że nie ma wystarczającej ilości pamięci do zrobienia migawki, nie zajmuje jeden.

## <a name="known-issues"></a>Znane problemy
* Jeśli używasz intellitrace zdarzenia i migawki tryb w wersjach systemu Windows starszych niż Windows 10 Fall Creators Update (RS3), a jeśli docelowa platforma debugowania aplikacji jest ustawiona na x86, IntelliTrace nie wykonuje migawek.

    Obejścia:
  * Jeśli korzystasz z aktualizacji rocznicowej systemu Windows 10 (RS1) i poniżej wersji 10.0.14393.2273, [zainstaluj plik KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * Jeśli korzystasz z aktualizacji Windows 10 Creators Update (RS2) i poniżej wersji 10.0.15063.1112, [zainstaluj kb4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Zainstaluj lub uaktualnij do systemu Windows 10 Fall Creators Update (RS3).
  * Inna możliwość:
    1. Zainstaluj zestaw narzędzi VC++ 2015.3 v140 dla składnika komputera stacjonarnego (x86, x64) przy użyciu Instalatora programu Visual Studio.
    2. Skompiluj aplikację docelową.
    3. W wierszu polecenia użyj narzędzia editbin, aby ustawić flagę `Largeaddressaware` docelowego pliku wykonywalnego. Na przykład można użyć tego polecenia (po zaktualizowaniu ścieżki): "C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
    4. Aby rozpocząć debugowanie, naciśnij klawisz **F5**. Teraz migawki są podejmowane na kroki debugera i punkty przerwania.

       > [!Note]
       > Flaga musi być ustawiona `Largeaddressaware` za każdym razem, gdy plik wykonywalny jest przebudowywany ze zmianami.

* Gdy migawka procesu aplikacji jest podejmowana w aplikacji, która używa pliku mapowanego w pamięci, proces z migawką zawiera blokadę wyłączności na pliku mapowanym w pamięci (nawet po wydaniu blokady przez proces nadrzędny). Inne procesy są nadal w stanie odczytać, ale nie zapisać, do pliku mapowane w pamięci.

  Obejście:
  * Wyczyść wszystkie migawki, kończąc sesję debugowania.

* Podczas debugowania aplikacji, której proces ma dużą liczbę unikatowych regionów pamięci, takich jak aplikacja, która ładuje dużą liczbę bibliotek DLL, wydajność przechodzenia krok po kroku z włączonymi migawkami może mieć wpływ. Ten problem zostanie rozwiązany w przyszłej wersji systemu Windows. Jeśli doświadczasz tego problemu, skontaktuj się stepback@microsoft.comz nami pod adresem .

* Podczas zapisywania pliku za pomocą **funkcji Debug > IntelliTrace > Zapisz sesję IntelliTrace** w trybie zdarzeń i migawek dodatkowe dane przechwycone z migawek nie są dostępne w pliku .itrace. W przypadku zdarzeń punktu przerwania i kroku są wyświetlane te same informacje, które zostały zapisane w trybie tylko zdarzeń IntelliTrace.

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak korzystać z funkcji IntelliTrace step-back. Możesz dowiedzieć się więcej o innych funkcjach IntelliTrace.

> [!div class="nextstepaction"]
> [Funkcje IntelliTrace](../debugger/intellitrace-features.md)

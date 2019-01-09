---
title: Wyświetl poprzedni stan aplikacji za pomocą funkcji IntelliTrace
description: Dowiedz się, jak tworzyć migawki i wyświetlanie migawki za pomocą funkcji IntelliTrace krok do tyłu
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 841812ac5961f30424cdb8ee95cc94fb6b5ce8ad
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154474"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio"></a>Sprawdź poprzednie Stany aplikacji przy użyciu funkcji IntelliTrace krok do tyłu w programie Visual Studio

Krok do tyłu IntelliTrace umożliwia automatyczne utworzenie migawki aplikacji na każdym punkcie przerwania i debuger krok zdarzenia. Zarejestrowane migawek umożliwiają wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, tak jak w przeszłości. IntelliTrace krok do tyłu pozwalają zaoszczędzić czas podczas mają być wyświetlane poprzedni stan aplikacji, ale nie chcesz ponownie uruchomić debugowanie lub Utwórz ponownie stan żądaną aplikację.

Krok do tyłu IntelliTrace jest dostępna, począwszy od programu Visual Studio Enterprise 2017 w wersji 15.5 lub nowszej i wymaga Rocznicowej aktualizacji systemu Windows 10 lub nowszej. Ta funkcja jest obecnie obsługiwane dla debugowania ASP.NET, WinForms, WPF, aplikacji w zarządzanej konsoli i bibliotek klas zarządzanych. Począwszy od programu Visual Studio Enterprise 2017 wersji 15.7, funkcja również jest obsługiwana dla platformy ASP.NET Core i .NET Core. Począwszy od Visual Studio Enterprise 2017 w wersji 15.9 2 (wersja zapoznawcza), ta funkcja jest również obsługiwana dla natywnych aplikacji przeznaczonych dla Windows. Debugowanie aplikacji platformy uniwersalnej systemu Windows nie jest obecnie obsługiwane.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Włącz migawki i zdarzenia funkcji IntelliTrace
> * Przejdź do zdarzenia przy użyciu poleceń krok do tyłu i do przodu kroku
> * Wyświetl zdarzenia migawki
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Włącz tryb zdarzenia i migawki funkcji IntelliTrace 

1. Otwórz swój projekt w programie Visual Studio Enterprise.

1. Otwórz **narzędzia** > **opcje** > **IntelliTrace** ustawienia i wybierz opcję **IntelliTrace zdarzenia i migawki** . 

    Począwszy od Visual Studio Enterprise 2017 w wersji 15.9 2 (wersja zapoznawcza), ta opcja jest **migawki IntelliTrace (zarządzany i natywny)**. 

    ![Włącz tryb migawki i zdarzenia IntelliTrace](../debugger/media/intellitrace-enable-snapshots.png "migawki i zdarzenia IntelliTrace włączyć tryb")

1. Aby skonfigurować opcje przeglądania migawek przy wyjątkach, należy wybrać **IntelliTrace** > **zaawansowane** z **opcje** okno dialogowe.

    Te opcje są dostępne, począwszy od programu Visual Studio Enterprise 2017 wersji 15.7.

    ![Skonfiguruj zachowanie dla migawek przy wyjątkach](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Po włączeniu zdarzenia i migawki, tworzenie migawek przy wyjątkach są również domyślnie włączone. Możesz wyłączyć migawki dla wyjątków, anulując **Zbieraj migawki dotyczące zdarzeń wyjątków**. Gdy ta funkcja jest włączona, tworzeniu migawek woluminów dla nieobsłużonych wyjątków. Obsługiwane wyjątki migawki są pobierane tylko wtedy, gdy wyjątek jest zgłaszany, a jeśli nie jest ponownie wygenerować wcześniej zgłoszony wyjątek. Maksymalna liczba migawek przy wyjątkach można ustawić, wybierając wartość z listy rozwijanej. Wartość maksymalna ma zastosowanie za każdym razem, że Twoja aplikacja przejdzie do trybu przerwania (np. gdy aplikacja trafienia punktu przerwania).

    > [!NOTE]
    > Migawki są pobierane tylko dla zdarzeń dotyczących wyjątków przez IntelliTrace. Dla kodu zarządzanego, jakie zdarzenia funkcja IntelliTrace ma rejestrować można określić, wybierając **narzędzia** > **opcje** > **zdarzenia IntelliTrace**.

1. W projekcie, ustaw co najmniej jednego punktu przerwania i Rozpocznij debugowanie (naciśnij klawisz **F5**), lub Rozpocznij debugowanie poprzez krokowe wykonywanie kodu (**F10** lub **F11**).

    IntelliTrace tworzy migawkę proces aplikacji o każdym kroku debugera, zdarzenie punktu przerwania i zdarzeń nieobsługiwany wyjątek. Te zdarzenia są rejestrowane w **zdarzenia** karcie **narzędzia diagnostyczne** okna oraz inne zdarzenia IntelliTrace. Aby otworzyć to okno, wybierz **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.

    Ikona aparatu fotograficznego pojawia się obok zdarzenia, dla których są dostępne migawki. 

    ![Zdarzenia kartę z migawkami](../debugger/media/intellitrace-events-tab-with-snapshots.png "kartę zdarzenia przy użyciu migawek w punktach przerwania i kroki")

    Ze względu na wydajność migawki nie są wykonywane, kiedy wkraczasz bardzo szybko. Jeśli nie ikonę kamery pojawi się obok kroku, spróbuj wolniej przechodzenie krok po kroku.

## <a name="navigate-and-view-snapshots"></a>Nawigowanie i Wyświetl migawki

1. Przejdź między zdarzeniami przy użyciu **krok do tyłu (Alt + [)** i **krok do przodu (Alt +])** przycisków na pasku narzędzi debugowania.

    Te przyciski nawigacji zdarzenia, które pojawiają się w **zdarzenia** karcie **okno narzędzia diagnostyczne**. Przechodzenie krok po kroku do tyłu lub do przodu do zdarzenia automatycznie aktywuje [debugowania historycznego](../debugger/historical-debugging.md) na wybrane zdarzenie.

    ![Krok do tyłu przyciski i dalej](../debugger/media/intellitrace-step-back-icons-description.png "przyciski krok do tyłu i krok do przodu")

    Gdy cofnijmy lub krok do przodu, Visual Studio przechodzi w tryb debugowania historycznego. W tym trybie kontekst debugera przełącza się do chwili, gdy wybrane zdarzenie została zarejestrowana. Program Visual Studio również przesuwa wskaźnik myszy do odpowiedniego wiersza kodu w oknie źródła. 

    W tym widoku można sprawdzić wartości w **stos wywołań**, **lokalne**, **Autos**, i **Obejrzyj** systemu windows. Możesz również umieścić kursor zmienne, aby wyświetlać etykietek danych i wykonywać obliczenia wyrażenia w **bezpośrednie** okna. Dane, które zostanie wyświetlony jest z migawki proces aplikacji podjęte w danym momencie.

    Tak, na przykład, jeśli został trafiony punkt przerwania i podjęte krok (**F10**), **krok do tyłu** przycisk umieszcza programu Visual Studio w trybie historyczne, w wierszu kodu odpowiadający punkt przerwania. 

    ![Uaktywnianie trybu historycznych na zdarzenia za pomocą migawki](../debugger/media/intellitrace-historical-mode-with-snapshot.png "uaktywnianie trybu historycznych na zdarzenia za pomocą migawki")

2. Aby powrócić do wykonania na żywo, wybierz **Kontynuuj (F5)** lub kliknij przycisk **wrócić do debugowania na żywo** łączy na pasku informacyjnym. 

3. Można również wyświetlić migawka **zdarzenia** kartę. Aby to zrobić, wybierz zdarzenie z migawki, a następnie kliknij przycisk **Uaktywnij debugowanie historyczne**.

    ![Uaktywnij debugowanie historyczne na zdarzenie](../debugger/media/intellitrace-activate-historical-debugging.png "Uaktywnij debugowanie historyczne na zdarzenie")

    W odróżnieniu od **Ustaw następną instrukcję** polecenia, wyświetlając migawki nie ponownie uruchomić kod; daje statyczne widok stanu aplikacji w punkcie w czasie, które miały miejsce w przeszłości.

    ![Omówienie funkcji IntelliTrace krok do tyłu](../debugger/media/intellitrace-step-back-overview.png "Omówienie programu IntelliTrace krok do tyłu")

    Aby dowiedzieć się więcej o tym, jak można sprawdzić zmiennych w programie Visual Studio, zobacz [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Często zadawane pytania

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Czym różni się IntelliTrace krok do tyłu w trybie tylko zdarzenia funkcji IntelliTrace?

Funkcja IntelliTrace w trybie tylko do zdarzeń umożliwiają Uaktywnij debugowanie historyczne na debuger nie wchodzi i punktów przerwania. Jednak IntelliTrace przechwytuje tylko dane w **lokalne** i **Autos** systemu windows, jeśli okna są otwarte i przechwytuje tylko dane, które jest rozwinięty i w widoku. W trybie tylko do zdarzeń często nie masz pełny przegląd zmiennych i złożonych obiektów. Ponadto wyrażenie oceny i wyświetlanie danych w **Obejrzyj** okno nie jest obsługiwane. 

W trybie zdarzenia i migawki funkcji IntelliTrace przechwytuje migawkę całego procesu aplikacji, włącznie z obiektami złożonymi. W wierszu kodu można zobaczyć te same informacje, tak, jakby zostały zatrzymane w punkcie przerwania (i nie ma znaczenia, czy wcześniej powiększone informacje). Obliczanie wyrażeń jest również obsługiwany, wyświetlając migawki.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Co to jest wpływ na wydajność tej funkcji? 

Wpływ na ogólną wydajność wykonywania krokowego zależy od aplikacji. Koszty związane z migawki jest około 30 ms. Migawka zostanie utworzona, proces aplikacji jest forked i rozwidlone kopiowania jest wstrzymana. Po wyświetleniu migawki programu Visual Studio jest dołączenie do rozwidlonego kopię procesu. Dla każdego migawki programu Visual Studio kopiuje tabeli strony i ustawia stron kopii przy zapisie. W przypadku obiektów na stosie zmiany między krokami debugera za pomocą skojarzone migawki, tabeli odpowiednich stron jest następnie kopiowana, wynikowa kosztu minimalnej pamięci. Jeśli program Visual Studio wykryje, że nie ma wystarczającej ilości pamięci, aby utworzyć migawkę, go nie przyjmuje jeden.
 
## <a name="known-issues"></a>Znane problemy  
* Jeśli używasz trybu zdarzenia i migawki funkcji IntelliTrace w wersjach systemu Windows starszych niż Windows 10 Fall Creators Update (RS3) i docelowa platforma debugowania aplikacji jest równa x86, IntelliTrace nie przyjmuje migawki.

    Obejścia:
  * Jeśli jesteś w usłudze Windows 10 Anniversary Update (RS1) i w wersji starszej niż 10.0.14393.2273, [zainstalować KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720). 
  * Jeśli jesteś na Windows 10 Creators Update (RS2) i w wersji starszej niż 10.0.15063.1112, [zainstalować KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Zainstaluj lub Uaktualnij do Windows 10 Fall Creators Update (RS3). 
  * Alternatywnie: 
    1. Zainstaluj zestaw narzędzi VC++ 2015.3 v140 dla składnika komputera stacjonarnego (x86, x64) przy użyciu Instalatora programu Visual Studio.
    2. Skompiluj aplikację docelową.
    3. W wierszu polecenia użyj narzędzia polecenia editbin można ustawić `Largeaddressaware` flagi dla elementu docelowego pliku wykonywalnego. Na przykład można użyć tego polecenia (po zaktualizowaniu ścieżka): "C:\Program pliki (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" / largeaddressaware "C:\Path\To\Application\app.exe".
    4. Aby rozpocząć debugowanie, naciśnij klawisz **F5**. Teraz migawki są wykonywane na debuger nie wchodzi i punktów przerwania.

       > [!Note]
       > `Largeaddressaware` Musi zostać ustawiona flaga za każdym razem, plik wykonywalny zostanie odtworzony ze zmianami.

* Podczas procesu aplikacji migawki w aplikacji korzystającej z utrwalonego pliku mapowane w pamięci, proces z migawką utrzymuje blokady na wyłączność plików zamapowanych w pamięci (nawet po procesie nadrzędnym został wydany blokady). Inne procesy mogą nadal odczytywać, ale nie zapisywać do pliku mapowanych na pamięć.

    Obejście problemu:
    * Wyczyść wszystkie migawki poprzez zakończenie sesji debugowania. 

* Podczas debugowania aplikacji, na których proces składa się z dużą liczbą regionów unikatowy pamięci, takie jak aplikacja, która ładuje dużej liczby bibliotek DLL, może mieć wpływ przechodzenie krok po kroku wydajności przy użyciu migawek włączone. Ten problem zostanie rozwiązany w przyszłej wersji systemu Windows. Jeśli występuje ten problem, skontaktowanie się z nami pod adresem stepback@microsoft.com. 

* Podczas zapisywania pliku z **Debuguj > IntelliTrace > sesji zapisywania funkcji IntelliTrace** w trybie zdarzenia i migawki, dodatkowe dane przechwycone z migawek nie jest dostępna w pliku .itrace. Punkt przerwania i kroku zdarzeń Zobacz te same informacje tak, jakby było zapisany plik w trybie tylko zdarzenia funkcji IntelliTrace. 

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób użycia funkcji IntelliTrace krok do tyłu. Można dowiedzieć się więcej na temat innych funkcji IntelliTrace.

> [!div class="nextstepaction"]
> [Funkcje IntelliTrace](../debugger/intellitrace-features.md)

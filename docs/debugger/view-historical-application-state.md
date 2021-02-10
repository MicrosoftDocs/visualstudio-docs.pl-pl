---
title: Wyświetl poprzedni stan aplikacji za pomocą IntelliTrace
description: Dowiedz się, jak tworzyć migawki i wyświetlać migawki z IntelliTrace krok po kroku
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1ab54ccb3820b3a03724c30d16f08b3e8a45493
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933105"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Sprawdź poprzednie Stany aplikacji za pomocą IntelliTrace Step-back w programie Visual Studio (Visual Studio Enterprise)

IntelliTrace Step-back automatycznie wykonuje migawkę aplikacji przy każdym punkcie przerwania i zdarzeniu debugera. Zapisane migawki umożliwiają powrót do poprzednich punktów przerwania lub kroków oraz wyświetlanie stanu aplikacji w przeszłości. IntelliTrace krokowo umożliwia zaoszczędzenie czasu, gdy chcesz zobaczyć poprzedni stan aplikacji, ale nie chcesz ponownie uruchomić debugowania ani odtworzyć żądanego stanu aplikacji.

IntelliTrace Step-back jest dostępny w Visual Studio Enterprise 2017 w wersji 15,5 lub nowszej. wymaga to również rocznicowej aktualizacji systemu Windows 10. Ta funkcja jest obecnie obsługiwana w przypadku debugowania ASP.NET, WinForms, WPF, zarządzanych aplikacji konsolowych i zarządzanych bibliotek klas. Począwszy od programu Visual Studio 2017 Enterprise w wersji 15,7, funkcja jest również obsługiwana dla ASP.NET Core i .NET Core. Począwszy od programu Visual Studio 2017 Enterprise wersja 15,9 Preview 2, ta funkcja jest również obsługiwana w przypadku aplikacji natywnych przeznaczonych dla systemu Windows. Debugowanie aplikacji platformy UWP nie jest obecnie obsługiwane.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Włączanie zdarzeń IntelliTrace i migawek
> * Nawigowanie po zdarzeniach za pomocą poleceń krok po kroku i do przodu
> * Wyświetlanie migawek zdarzeń

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Włącz tryb IntelliTrace zdarzeń i migawek

1. Otwórz projekt w Visual Studio Enterprise.

1. Otwórz pozycję **Narzędzia**  >  **Opcje**  >  **IntelliTrace** ustawienia i wybierz opcję **IntelliTrace zdarzeń i migawek**.

    Począwszy od programu Visual Studio 2017 Enterprise w 15,9 wersji zapoznawczej 2, ta opcja jest **IntelliTrace migawek (zarządzane i natywne)**.

    ![Włącz tryb IntelliTrace zdarzeń i migawek](../debugger/media/intellitrace-enable-snapshots.png "Włącz tryb IntelliTrace zdarzeń i migawek")

1. Jeśli chcesz skonfigurować opcje wyświetlania migawek na wyjątkach, wybierz pozycję **IntelliTrace**  >  **Advanced (zaawansowane** ) w oknie dialogowym **Opcje** .

    Te opcje są dostępne w programie Visual Studio 2017 Enterprise w wersji 15,7.

    ![Konfigurowanie zachowania migawek w przypadku wyjątków](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Po włączeniu zdarzeń i migawek tworzenie migawek w wyjątkach jest również domyślnie włączone. Migawki można wyłączyć, usuwając zaznaczenie opcji **Zbieraj migawki w zdarzeniach wyjątków**. Gdy ta funkcja jest włączona, migawki są podejmowane w przypadku nieobsłużonych wyjątków. W przypadku obsłużonych wyjątków migawki są wykonywane tylko wtedy, gdy wyjątek jest zgłaszany i jeśli nie jest to ponownie zgłaszane wcześniej zgłoszone wyjątki. Można ustawić maksymalną liczbę migawek na wyjątkach, wybierając wartość z listy rozwijanej. Wartość maksymalna dotyczy każdego momentu, gdy aplikacja przechodzi w tryb przerwania (na przykład gdy aplikacja trafi punkt przerwania).

    > [!NOTE]
    > Migawki są pobierane tylko dla zdarzeń wyjątków, które IntelliTrace rekordy. Dla kodu zarządzanego można określić, jakie zdarzenia IntelliTrace rekordy, wybierając pozycję **Narzędzia**  >  **Opcje**  >  **IntelliTrace zdarzenia**.

1. W projekcie Ustaw jeden lub więcej punktów przerwania i Rozpocznij debugowanie (naciśnij klawisz **F5**) lub Rozpocznij debugowanie, przechodząc przez kod (**F10** lub **F11**).

    IntelliTrace wykonuje migawkę procesu aplikacji w każdym kroku debugera, zdarzeniu punktu przerwania i nieobsługiwanym zdarzeniu wyjątku. Te zdarzenia są rejestrowane na karcie **zdarzenia** w oknie **Narzędzia diagnostyczne** , wraz z innymi zdarzeniami IntelliTrace. Aby otworzyć to okno, wybierz **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**.

    Obok zdarzeń, dla których są dostępne migawki, pojawia się ikona aparatu.

    ![Karta zdarzenia z migawkami](../debugger/media/intellitrace-events-tab-with-snapshots.png "Karta zdarzenia z migawkami dla punktów przerwania i kroków")

    Ze względu na wydajność migawki nie są podejmowane po szybkim przetworzeniu. Jeśli obok kroku nie zostanie wyświetlona ikona aparatu, spróbuj zrobić to wolniej.

## <a name="navigate-and-view-snapshots"></a>Nawigowanie i wyświetlanie migawek

1. Przechodzenie między zdarzeniami przy użyciu przycisków **krok wstecz (Alt + [)** i **krok do przodu (Alt +])** na pasku narzędzi debugowania.

    Te przyciski służą do przechodzenia do zdarzeń, które pojawiają się na karcie **zdarzenia** w **oknie narzędzia diagnostyczne**. Przechodzenie do tyłu lub w przód do zdarzenia automatycznie aktywuje [debugowanie historyczne](../debugger/historical-debugging.md) na wybranym zdarzeniu.

    ![Przyciski do tyłu i do przodu](../debugger/media/intellitrace-step-back-icons-description.png "Przyciski Wstecz i przejdź do przodu")

    Po powrocie lub przejściu do przodu program Visual Studio przechodzi do trybu debugowania historycznego. W tym trybie debuger debugera przechodzi do godziny, w której zarejestrowano wybrane zdarzenie. Program Visual Studio przesuwa również wskaźnik do odpowiedniego wiersza kodu w oknie źródłowym.

    Z tego widoku można sprawdzić wartości w oknach **stos wywołań**, zmienne **lokalne**, **autouzupełniania** i **czujki** . Możesz również umieścić wskaźnik myszy nad zmiennymi, aby wyświetlić etykietki danych i wykonać ocenę wyrażenia w oknie **bezpośrednim** . Dane, które widzisz, pochodzą z migawki procesu aplikacji wykonanego w tym momencie.

    Tak więc, na przykład, jeśli trafisz punkt przerwania i podjęto krok (**F10**), przycisk **Przejdź do tyłu** umieszcza program Visual Studio w trybie historycznym w wierszu kodu odpowiadającym punktowi przerwania.

    ![Aktywowanie trybu historycznego na zdarzeniu z migawką](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Aktywowanie trybu historycznego na zdarzeniu z migawką")

2. Aby powrócić do wykonywania na żywo, wybierz pozycję **Kontynuuj (F5)** lub kliknij link **Wróć do debugowania na żywo** na pasku informacji.

3. Możesz również wyświetlić migawkę na karcie **zdarzenia** . W tym celu wybierz zdarzenie z migawką i kliknij pozycję **Aktywuj debugowanie historyczne**.

    ![Aktywuj debugowanie historyczne na zdarzeniu](../debugger/media/intellitrace-activate-historical-debugging.png "Aktywuj debugowanie historyczne na zdarzeniu")

    W przeciwieństwie do polecenia **Ustaw następną instrukcję** , wyświetlenie migawki nie powoduje ponownego uruchomienia kodu; zapewnia ona statyczny widok stanu aplikacji w danym momencie, który nastąpił w przeszłości.

    ![Przegląd kroku IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Przegląd kroku IntelliTrace")

    Aby dowiedzieć się więcej o tym, jak zbadać zmienne w programie Visual Studio, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Jak IntelliTrace się różnią od trybu IntelliTrace tylko zdarzenia?

IntelliTrace w trybie tylko zdarzenia umożliwia aktywację debugowania historycznego w krokach i punktach przerwania. Jednak IntelliTrace przechwytuje tylko dane w **lokalnych** **i oknach** systemu Windows, jeśli są otwarte i są przechwytywane tylko te dane, które są rozbudowane i w widoku. W trybie tylko zdarzenia, często nie masz pełnego widoku zmiennych i obiektów złożonych. Ponadto obliczanie wyrażeń i wyświetlanie danych w oknie **czujki** nie jest obsługiwane.

W trybie zdarzenia i migawki IntelliTrace przechwytuje całą migawkę procesu aplikacji, w tym obiekty złożone. W wierszu kodu można zobaczyć te same informacje, które zostały zatrzymane w punkcie przerwania (i nie ma znaczenia, czy informacje zostały wcześniej rozwinięte). Obliczanie wyrażeń jest również obsługiwane podczas wyświetlania migawki.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Jaki jest wpływ tej funkcji na wydajność? 

Wpływ na ogólną wydajność, zależy od aplikacji. Obciążenie pracą migawki jest około 30 ms. Gdy wykonywana jest migawka, proces aplikacji jest rozwidlenia, a kopia rozwidlenia jest wstrzymana. Gdy przeglądasz migawkę, program Visual Studio jest dołączany do odtworzonej kopii procesu. Dla każdej migawki program Visual Studio kopiuje tylko tabelę stron i ustawia strony do kopiowania w trakcie zapisu. Jeśli obiekty na stosie zmieniają się między krokami debugera ze skojarzonymi migawkami, odpowiednia tabela stron jest kopiowana, co skutkuje minimalnym kosztem pamięci. Jeśli program Visual Studio wykryje brak wystarczającej ilości pamięci do utworzenia migawki, nie zajmie ona.

## <a name="known-issues"></a>Znane problemy
* W przypadku korzystania z trybu IntelliTrace zdarzeń i migawek w wersjach systemu Windows starszych niż aktualizacja systemu Windows 10 dla twórców (RS3), a jeśli obiekt docelowy platformy debugowania aplikacji jest ustawiony na wartość x86, IntelliTrace nie przyjmuje migawek.

    Obejścia:
  * Jeśli korzystasz z rocznicowej aktualizacji systemu Windows 10 (RS1) i starszej wersji 10.0.14393.2273, [Zainstaluj KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * W przypadku aktualizacji systemu Windows 10 dla twórców (RS2) i poniżej wersji 10.0.15063.1112 [Zainstaluj KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Zainstaluj lub Uaktualnij do systemu Windows 10 — Aktualizacja programu Creators (RS3).
  * Inna możliwość:
    1. Zainstaluj zestaw narzędzi VC++ 2015.3 v140 dla składnika komputera stacjonarnego (x86, x64) przy użyciu Instalatora programu Visual Studio.
    2. Skompiluj aplikację docelową.
    3. W wierszu polecenia Użyj narzędzia polecenia EDITBIN, aby ustawić `Largeaddressaware` flagę dla docelowego pliku wykonywalnego. Można na przykład użyć tego polecenia (po aktualizacji ścieżki): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe"/LARGEADDRESSAWARE "C:\Path\To\Application\app.exe".
    4. Aby rozpocząć debugowanie, naciśnij klawisz **F5**. Teraz migawki są wykonywane na krokach i punktach przerwania debugera.

       > [!Note]
       > `Largeaddressaware`Flaga musi być ustawiana za każdym razem, gdy plik wykonywalny zostanie odbudowany ze zmianami.

* Gdy migawka procesu aplikacji jest wykonywana w aplikacji, która używa utrwalonego pliku mapowanego na pamięć, proces z migawką przechowuje wyłączną blokadę pliku mapowanego na pamięć (nawet po udostępnieniu przez proces nadrzędny blokady). Inne procesy nadal mogą odczytywać, ale nie zapisywać, do pliku mapowanego na pamięć.

  Obejście problemu:
  * Wyczyść wszystkie migawki przez zakończenie sesji debugowania.

* Podczas debugowania aplikacji, której proces ma dużą liczbę unikatowych regionów pamięci, takich jak aplikacja ładująca dużą liczbę bibliotek DLL, może to mieć wpływ na wydajność zwiększania wydajności z włączonymi migawkami. Ten problem zostanie rozwiązany w przyszłej wersji systemu Windows. Jeśli wystąpi ten problem, skontaktuj się z nami pod adresem stepback@microsoft.com .

* Podczas zapisywania pliku z **debugowaniem > IntelliTrace > zapisywania sesji IntelliTrace** w trybie zdarzenia i migawki, dodatkowe dane przechwycone z migawek nie są dostępne w pliku. iTrace. W przypadku zdarzeń punktów przerwania i kroków te informacje są wyświetlane tak samo, jak w przypadku zapisania pliku w trybie tylko zdarzenia IntelliTrace.

## <a name="next-steps"></a>Następne kroki

W ramach tego samouczka nauczysz się korzystać z IntelliTrace kroku. Warto dowiedzieć się więcej o innych funkcjach IntelliTrace.

> [!div class="nextstepaction"]
> [Funkcje IntelliTrace](../debugger/intellitrace-features.md)

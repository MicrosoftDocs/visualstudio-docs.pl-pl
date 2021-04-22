---
title: Edytor kodu XAML
description: Zobacz przewodnik po edytorze kodu XAML w Visual Studio
ms.date: 06/16/2020
ms.topic: overview
f1_keywords:
- VS.XamlEditor
monikerRange: vs-2019
ms.custom: contperf-fy21q4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 672bfa6b28e364351f262cb2a2c6e2258ecd9746
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879398"
---
# <a name="xaml-code-editor"></a>Edytor kodu XAML

Edytor kodu XAML w Visual Studio [IDE](../get-started/visual-studio-ide.md) zawiera wszystkie narzędzia potrzebne do tworzenia aplikacji WPF i UWP dla platformy Windows oraz dla [zestawu narzędzi Xamarin.Forms.](/xamarin/xamarin-forms/user-interface/text/editor/) W tym artykule przedstawiono zarówno rolę, jaką odgrywa edytor kodu podczas tworzenia aplikacji opartych na języku XAML, jak i funkcje, które są unikatowe dla edytora kodu XAML w programie Visual Studio 2019.

Na początek przyjrzyjmy się środowisku IDE (zintegrowanemu środowisku projektowemu) z otwartym projektem WPF. Na poniższej ilustracji przedstawiono kilka kluczowych narzędzi IDE, które będą potrzebne wraz z edytorem kodu XAML.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="Projekt Visual Studio 2019 IDE z otwartym projektem WPF w języku XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

W lewym dolnym rogu obrazu zgodnie z ruchem wskazówek zegara kluczowe narzędzia ide są następujące:

- Okno **[edytora kodu XAML](#xaml-code-editor-ui)** temat tego &mdash; artykułu, w którym można utworzyć i &mdash; edytować kod.
- Okno **[projektant XAML,](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** w którym projektuje się interfejs użytkownika.
- Okno **[z dockowalnym](../ide/reference/toolbox.md)** przybornikem, w którym można dodawać kontrolki do interfejsu użytkownika.
- Przycisk **[](../debugger/debugger-feature-tour.md)** Debuguj, na którym uruchamiasz kod i debuguj go. <br>(Kod można również edytować w czasie rzeczywistym podczas debugowania za pomocą [Przeładowywanie kodu XAML na gorąco).](xaml-hot-reload.md)
- Okno **[Eksplorator rozwiązań,](../ide/solutions-and-projects-in-visual-studio.md)** w którym można zarządzać plikami, projektami i rozwiązaniami.
- Okno **[Właściwości,](../ide/reference/properties-window.md)** w którym można zmienić wygląd interfejsu użytkownika i sposób działania kontrolek interfejsu użytkownika.

Aby kontynuować, dowiedzmy się więcej o edytorze kodu XAML.

## <a name="xaml-code-editor-ui"></a>Interfejs użytkownika edytora kodu XAML

Chociaż okno edytora kodu dla aplikacji XAML udostępnia niektóre elementy interfejsu użytkownika (interfejsu użytkownika), które również pojawiają się w naszym standardowym idee, zawiera również kilka unikatowych funkcji, które ułatwiają tworzenie aplikacji XAML.

Oto przykładowe okno edytora kodu XAML.

![Okno edytora kodu XAML w Visual Studio](media/xaml-code-editor-window.png "Zrzut ekranu przedstawiający okno edytora kodu XAML w programie Visual Studio 2019")

Następnie przyjrzyjmy się funkcji poszczególnych elementów interfejsu użytkownika w edytorze kodu.

### <a name="first-row"></a>Pierwszy wiersz

W pierwszym wierszu w górnej części okna kodu XAML po  lewej  stronie znajduje się karta Projekt, przycisk Zamień okienka, karta **XAML** i przycisk Wyskakujących **okienek XAML.**

![Pierwszy z dwóch pierwszych wierszy okna edytora kodu XAML w Visual Studio z wyróżniona lewą stroną pierwszego wiersza](media/xaml-code-editor-top-row-left.png "Zrzut ekranu przedstawiający pierwszy z dwóch pierwszych wierszy okna edytora kodu XAML w programie Visual Studio 2019, w którym wyróżnione są elementy interfejsu użytkownika po lewej stronie")

Oto jak działają:

- Karta **Projektowanie** zmienia fokus z edytora kodu XAML na projektant XAML.
- Przycisk **Zamień okienka** odwraca lokalizację pliku projektant XAML edytor kodu XAML w idee.
- Karta **XAML** zmienia fokus z powrotem na edytor kodu XAML.
- Przycisk **Wyskakujących okienek XAML** tworzy oddzielne okno edytora kodu XAML spoza środowiska IDE.

Po prawej stronie znajduje się przycisk **Podział** pionowy, **przycisk** Podział poziomy i przycisk **Zwiń okienka.**

![Pierwszy z dwóch pierwszych wierszy okna edytora kodu XAML w Visual Studio z wyróżniona prawą stroną pierwszego wiersza](media/xaml-code-editor-top-row-right.png "Zrzut ekranu przedstawiający pierwszy z dwóch pierwszych wierszy okna edytora kodu XAML w programie Visual Studio 2019, w którym wyróżnione są elementy interfejsu użytkownika po prawej stronie")

Oto jak działają:

- Przycisk **Podział pionowy** zmienia lokalizację pliku projektant XAML edytorze kodu XAML w idee z wyrównania poziomego na wyrównanie w pionie.
- Przycisk **Podział poziomy** zmienia lokalizację pliku projektant XAML edytorze kodu XAML w idee z wyrównania w pionie do wyrównania w poziomie.
- Przycisk **Zwiń okienko** umożliwia zwinięcie tego, co znajduje się w dolnym okienku, niezależnie od tego, czy jest to edytor kodu, czy projektant. (Aby przywrócić dolne okienko, wybierz ponownie ten sam przycisk o nazwie **Przycisk Rozwiń okienko).**

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Drugi wiersz

W drugim wierszu w górnej części okna kodu XAML znajdują się dwie listy rozwijane Okna. Jeśli jednak wyświetlasz etykietkę narzędzia dla tych elementów interfejsu użytkownika, dodatkowo identyfikuje je jako "Element: okno" i "Element członkowski: okno".

![Drugi z dwóch górnych wierszy okna edytora kodu XAML na liście Visual Studio, gdzie są widoczne obie listy rozwijane okna](media/xaml-code-editor-top-row-windows.png "Zrzut ekranu przedstawiający drugi z dwóch górnych wierszy okna edytora kodu XAML w programie Visual Studio 2019, w którym są widoczne obie listy rozwijane okna")

Listy rozwijane Okna mają różne funkcje, takie jak:

- Okno **Element: po lewej** stronie ułatwia wyświetlanie elementów równorzędnych lub elementów nadrzędnych oraz przechodzenie do nich.

  W szczególności przedstawiono widok podobny do konspektu, który ujawnia strukturę tagów kodu. Po wybraniu z listy fokus w edytorze kodu zostanie przyciągnięty do wiersza kodu, który zawiera wybrany element.

    ![Lista rozwijana Element: Okno w Visual Studio](media/xaml-element-window-dropdown.png "Zrzut ekranu przedstawiający listę rozwijaną Element: okno w Visual Studio 2019 r.")

- Okno **Element członkowski: po** prawej stronie ułatwia wyświetlanie i przechodzenie do atrybutów lub elementów podrzędnych.

    W szczególności wyświetla listę właściwości w kodzie. Po wybraniu z listy fokus w edytorze kodu zostanie przyciągnięty do wiersza kodu, który zawiera wybraną właściwość.

    ![Lista rozwijana Member: Window (Członek: okno) w Visual Studio](media/xaml-member-window-dropdown.png "Zrzut ekranu przedstawiający listę rozwijaną Członek: okno w programie Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Środkowe okienko, edytor kodu

Środkowe okienko jest częścią "kodu" edytora kodu XAML. Zawiera większość funkcji, które można znaleźć w edytorze [kodu IDE](../get-started/tutorial-editor.md). Dotkniemy kilku uniwersalnych funkcji środowiska IDE, które mogą ułatwić opracowywanie kodu XAML. Ponadto w idee IDE wyróżnimy funkcje unikatowe w języku XAML.

![Edytor kodu XAML, tylko środkowe okienko, w Visual Studio](media/xaml-code-editor-middle.png "Zrzut ekranu przedstawiający edytor kodu XAML tylko w środkowym okienku w Visual Studio 2019 r.")

#### <a name="quick-actions"></a>Szybkie akcje

Za pomocą [szybkich akcji można](../ide/quick-actions.md) refaktoryzować, generować lub w inny sposób modyfikować kod za pomocą jednej akcji.

Na przykład jednym z przydatnych zadań, które można wykonać za pomocą szybkich akcji, jest usunięcie niepotrzebnych **usings** z kodu C# na karcie **MainWindow.xaml.cs.**

Oto kroki tej procedury:

1. Umieść kursor na instrukcji using, wybierz ikonę żarówki, a następnie wybierz pozycję **Usuń** niepotrzebne deklaracje using z listy rozwijanej.

    ![Opcja "Usuń niepotrzebne usings" w edytorze IDE z menu Szybkie akcje](media/xaml-code-editor-remove-usings.png "Zrzut ekranu przedstawiający opcję Usuń niepotrzebne using w edytorze IDE z menu Szybkie akcje")

1. Wybierz, czy chcesz naprawić wszystkie wystąpienia w **dokumencie,** **projekcie** lub **rozwiązaniu**.
1. Wyświetl okno **dialogowe Podgląd,** a następnie wybierz pozycję **Zastosuj.**

Dostęp do tej funkcji można również uzyskać na pasku menu. W tym celu wybierz pozycję **Edytuj usuwanie** i sortowanie za pomocą  >  **funkcji IntelliSense.**  >  

Aby uzyskać więcej informacji na temat ustawień usings, zobacz [stronę Sortuj usings.](../ide/reference/sort-usings.md) Aby uzyskać więcej informacji na temat funkcji IntelliSense, zobacz stronę [IntelliSense w Visual Studio](../ide/using-intellisense.md) funkcji. Aby uzyskać więcej informacji na temat niektórych typowych sposobów używania szybkich akcji przez deweloperów, zobacz [stronę Typowe szybkie akcje.](../ide/common-quick-actions.md)

#### <a name="change-tracking"></a>Śledzenie zmian

Kolor lewego marginesu umożliwia śledzenie zmian wprowadzonych w pliku. Kolory są powiązane z akcjami, które należy podjąć:

- Zmiany wprowadzone od czasu otwarcia pliku, ale nie zostały  zapisane, są oznaczone żółtym pasku na lewym marginesie (nazywanym marginesem zaznaczenia).

    ![Edytowanie edytora kodu za pomocą żółtego paska](media/code-editor-edit-yellow.png "Zrzut ekranu edytora kodu ze zmianami oznaczonymi żółtym słupkiem na marginesie zaznaczenia.")

- Po zapisaniu zmian (ale przed zamknięciem pliku) pasek zmieni kolor na **zielony**.

    ![Edycja edytora kodu z zielonym słupkiem](media/code-editor-edit-green.png "Zrzut ekranu edytora kodu ze zmianami oznaczonymi zielonym słupkiem na marginesie zaznaczenia.")

Aby wyłączyć i włączyć tę  funkcję, zmień  opcję Śledź zmiany w ustawieniach Edytora tekstu **(Narzędzia**  >  **Opcje Edytor**  >  **tekstu).**

Aby uzyskać więcej informacji na temat śledzenia zmian w celu dołączania falistych wierszy (nazywanych również "zygzykami"), które są wyświetlane pod ciągami kodu, zobacz sekcję Funkcje edytora na stronie Funkcje Visual Studio edytora &mdash; &mdash; kodu. **[](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** [](../ide/writing-code-in-the-code-and-text-editor.md)

#### <a name="right-click-context-menu"></a>Menu kontekstowe dostępne po kliknięciu prawym przyciskiem myszy

Podczas edytowania kodu w edytorze kodu XAML istnieje kilka funkcji, do których można uzyskać dostęp za pomocą menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy. Większość z tych funkcji jest dostępna uniwersalnie w Visual Studio IDE, podczas gdy niektóre są specyficzne dla korzystania z edytora kodu wraz z oknem Projekt.

![Zrzut ekranu przedstawiający menu kontekstowe dostępne po kliknięciu prawym przyciskiem myszy edytora kodu XAML w Visual Studio 2019 r.](media/xaml-code-editor-right-click-menu.png)

Oto, jak działa każda funkcja i jak jest przydatna:

- **Wyświetl kod** — otwiera okno kodu języka programowania, które jest zazwyczaj kartami obok widoku domyślnego, który zawiera okno Projekt i edytor kodu XAML.
- **Projektant widoków** — otwiera widok domyślny, który zawiera okno Projekt i edytor kodu XAML. (Jeśli jesteś już w widoku domyślnym, nic nie robi).
- **Szybkie akcje i refaktoryzatory** — refaktoryzatory, generowanie lub w inny sposób modyfikuje kod za pomocą jednej akcji. Po umieszczeniu wskaźnika myszy na kodzie zobaczysz ikonę żarówki, gdy dostępna jest szybka akcja lub refaktoryzacja. <br>Zobacz też: [Szybkie akcje](../ide/quick-actions.md) i [refaktoryzacja kodu](../ide/refactoring-in-visual-studio.md).
- **Zmień nazwę...** — zmienia nazwy tylko przestrzeni nazw. Jeśli nie masz przestrzeni nazw do zmiany nazwy, zostanie wyświetlony komunikat o błędzie "Można zmienić nazwy tylko prefiksów przestrzeni nazw".
- **Usuń i sortuj przestrzenie nazw** — usuwa nieużywane przestrzenie nazw, a następnie sortuje te przestrzenie nazw, które pozostają.
- **Zobacz definicję** — wyświetla podgląd definicji typu bez opuszczania bieżącej lokalizacji w edytorze. <br>Zobacz też: [Podgląd definicji](../ide/go-to-and-peek-definition.md#peek-definition) oraz [Wyświetlanie i edytowanie kodu za pomocą funkcji Zobacz definicję](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Przejdź do definicji** — przechodzi do źródła typu lub członka i otwiera wynik na nowej karcie. <br>Zobacz też: [Przejdź do definicji](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Otoczyć za pomocą...** — Użyj fragmentów kodu otoki z kodem, które są dodawane wokół wybranego bloku kodu. <br>Zobacz też: [Fragmenty kodu rozszerzenia i otoczyć fragmentami kodu](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Wstaw fragment kodu** — wstawia fragment kodu w lokalizacji kursora.
- **Wycinanie** — bez objaśnienia
- **Kopiuj** — bez objaśnienia
- **Wklej** — bez objaśnienia
- **Zwijanie —** rozwijanie i zwijanie sekcji kodu. <br>Zobacz też: [Opis .](../ide/outlining.md)
- **Kontrola źródła** — wyświetlanie historii wkładu kodu w repozytorium typu open source.

### <a name="middle-pane-scroll-bar"></a>Środkowe okienko, pasek przewijania

Pasek przewijania może nie tylko przewijać kod. Można go również użyć do otwarcia innego okienka edytora kodu. Ponadto możesz użyć paska przewijania, aby ułatwić wydajniejsze kodować, dodając do niego adnotacje lub używając różnych trybów wyświetlania.

#### <a name="split-the-code-window"></a>Dzielenie okna kodu

Na pasku przewijania edytora kodu w  prawym górnym rogu znajduje się przycisk Podziel. Po jego wybraniu możesz otworzyć kolejne okienko edytora kodu. Jest to przydatne, ponieważ działają niezależnie od siebie, dzięki czemu można używać ich do pracy nad kodem w różnych lokalizacjach.

![Zrzut ekranu przedstawiający środkowe okienko edytora kodu XAML w programie Visual Studio 2019 z przyciskiem Podziel wyróżniony w prawym górnym rogu okienka.](media/code-editor-split-window-button.png)

Aby uzyskać więcej informacji na temat sposobu dzielenia okna edytora, zobacz [stronę Zarządzanie oknami edytora.](../ide/how-to-manage-editor-windows.md)

#### <a name="use-annotations-or-map-mode"></a>Używanie adnotacji lub trybu mapy

Możesz również zmienić wygląd paska przewijania i dodatkowe funkcje, które zawiera. Na przykład wiele osób  lubi dołączać adnotacje na pasku przewijania, które zapewniają wizualne wskazówki, takie jak zmiany kodu, punkty przerwania, zakładki, błędy i położenie caret.

Inni doceniają *użycie trybu mapy*, który wyświetla wiersze kodu w miniaturze na pasku przewijania. Deweloperzy, którzy mają dużo kodu w pliku, mogą dowiedzieć się, że tryb mapy śledzi wiersze kodu efektywniej niż domyślny pasek przewijania.

Aby uzyskać więcej informacji na temat zmieniania ustawień domyślnych paska przewijania, zobacz  [stronę Dostosowywanie paska](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) przewijania.

## <a name="xaml-specific-features"></a>Funkcje specyficzne dla języka XAML

Większość z następujących funkcji jest uniwersalnie dostępna w Visual Studio IDE, ale niektóre z nich mają dodane wymiary, które ułatwiają kodowanie deweloperom języka XAML.

### <a name="xaml-code-snippets"></a>Fragmenty kodu XAML

Fragmenty kodu to małe bloki kodu wielokrotnego użytku, które można wstawić do pliku  kodu za pomocą polecenia menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy wstaw fragment kodu lub kombinacji skrótów klawiaturowych **(Ctrl** + **K,** **Ctrl** + **X).** Ulepszyliśmy funkcję [IntelliSense,](../ide/using-intellisense.md) dzięki czemu obsługuje ona wyświetlanie fragmentów kodu XAML, które działają zarówno w przypadku wbudowanych fragmentów kodu, jak i dowolnych niestandardowych fragmentów kodu, które dodajesz ręcznie. Niektóre fragmenty kodu XAML to , `#region` `Column definition` , `Row definition` , `Setter` i `Tag` .

![Edytor kodu XAML z opcjami fragmentu kodu XAML w funkcji IntelliSense](media/xaml-code-snippets.png "Zrzut ekranu przedstawiający edytor kodu XAML z opcjami fragmentu kodu XAML w funkcji IntelliSense")

Aby uzyskać więcej informacji, zobacz [strony Fragmenty kodu](../ide/code-snippets.md) i Fragmenty kodu języka [C#.](../ide/visual-csharp-code-snippets.md)

### <a name="xaml-region-support"></a>Obsługa #region XAML

Począwszy od Visual Studio 2015 roku, w wersji #region deweloperzy XAML w systemach WPF i UWP, a ostatnio także w platformie [Xamarin.Forms.](/xamarin/xamarin-forms/user-interface/text/editor/) W Visual Studio 2019 r. będziemy nadal ulepszać przyrostowe ulepszenia #region technicznej. Na przykład w [wersji 16.4](/visualstudio/releases/2019/release-notes-v16.4/) lub nowszej opcje #region są wyświetlane, gdy zaczniesz wpisywać `<!` .

![Edytor kodu XAML z opcjami #region w funkcji IntelliSense](media/code-editor-xaml-region.png "Zrzut ekranu edytora kodu XAML z #region w funkcji IntelliSense")

Regionów można używać, gdy chcesz grupować sekcje kodu, które chcesz również rozwinąć lub zwinąć.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Aby uzyskać więcej informacji na temat regionów, [zobacz #region (odwołanie w C#).](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) Aby uzyskać więcej informacji na temat rozwijania i zwijania sekcji kodu, zobacz [stronę Zwijanie.](../ide/outlining.md)

### <a name="xaml-comments"></a>Komentarze XAML

Deweloperzy często wolą dokumentować swój kod przy użyciu komentarzy. Komentarze można dodać do kodu XAML, który znajduje się na karcie **MainWindow.xaml,** w następujący sposób:

- Wprowadź `<!--` przed komentarzem, a następnie dodaj `-->` po komentarzu.
- Wprowadź `<!` , a następnie wybierz z listy `!--` opcji.

  ![Okno dialogowe Dodawanie komentarzy w edytorze kodu XAML prawym przyciskiem myszy](media/xaml-code-editor-comments.png "Zrzut ekranu przedstawiający menu kontekstowe dostępne po kliknięciu prawym przyciskiem myszy w celu dodania komentarzy w edytorze kodu XAML")

- Wybierz kod, który chcesz otoczyć komentarzem, a następnie wybierz przycisk **Komentarz** na pasku narzędzi w idee. Aby cofnąć akcję, wybierz przycisk **Uncomment (Cofń).**

  ![Przycisk Komentarz i przycisk Uncomment na pasku narzędzi środowiska IDE](media/comment-undo-comment-buttons.png "Zrzut ekranu przedstawiający przycisk Komentarz i przycisk Cokmentuj na pasku narzędzi środowiska IDE")

- Wybierz kod, który chcesz otoczyć komentarzem, a następnie naciśnij **klawisze Ctrl** + **K,** **Ctrl** + **C**. Aby odkomentować zaznaczony kod, naciśnij **klawisze Ctrl** + **K,** **Ctrl** + **U**.

Aby uzyskać więcej informacji na temat używania komentarzy w kodzie C# na karcie **MainWindow.xaml.cs,** zobacz stronę [Komentarze dokumentacji.](/dotnet/csharp/language-reference/language-specification/documentation-comments/)

### <a name="xaml-lightbulbs"></a>Żarówki XAML

Ikony żarówki, które pojawiają się w [](../ide/quick-actions.md) kodzie XAML, są częścią szybkich akcji, których można użyć do refaktoryzacji, generowania lub modyfikowania kodu w inny sposób.

Poniżej przedstawiono kilka przykładów korzyści, jakie mogą one mieć środowisko kodowania XAML:

- **Usuń niepotrzebne przestrzenie nazw**. W edytorze kodu XAML niepotrzebne przestrzenie nazw są wyświetlane w wygaszonego tekstu. Jeśli najedziesz kursorem na niepotrzebne użycie, pojawi się żarówka. Po wybraniu opcji **Usuń niepotrzebne przestrzenie** nazw z listy rozwijanej zostanie wyświetlony podgląd tej opcji, którą można usunąć.

  ![Opcja Usuń niepotrzebne przestrzenie nazw edytora kodu XAML z żarówki Szybkie akcje](media/xaml-code-editor-dimmed-namespaces-preview.png "Zrzut ekranu przedstawiający opcję Usuń niepotrzebne przestrzenie nazw w edytorze kodu XAML, która jest wyświetlana przy użyciu żarówki Szybkie akcje")

- **Zmień nazwę przestrzeni nazw**. Ta funkcja, dostępna w menu kontekstowym dostępnym po kliknięciu prawym przyciskiem myszy po wyróżnieniu przestrzeni nazw, ułatwia zmianę wielu wystąpień ustawienia w tym samym czasie. Dostęp do tej funkcji można również uzyskać za pomocą paska menu **Edytuj** zmianę nazwy refaktoryzacji lub naciskając klawisze  >    >   **Ctrl** R, a następnie +  **ponownie Ctrl** + **R.**

  ![Opcja Zmień nazwę przestrzeni nazw edytora kodu XAML z menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy](media/code-editor-rename-namespace.png "Zrzut ekranu przedstawiający opcję Zmień nazwę przestrzeni nazw edytora kodu XAML wyświetlaną przy użyciu menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy")

  Aby uzyskać więcej informacji, zobacz stronę [Refaktoryzacja](../ide/reference/rename.md) zmiany nazwy symbolu kodu.

### <a name="conditional-xaml-for-uwp"></a>Warunkowy kod XAML dla platformy UWP

Warunkowy kod XAML umożliwia użycie metody [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) w znacznikach XAML. Pozwala to ustawić właściwości i utworzyć wystąpienia obiektów w znacznikach na podstawie obecności interfejsu API bez konieczności używania kodu za nimi.

Aby uzyskać więcej informacji, zobacz stronę [Warunkowy kod XAML](/windows/uwp/debug-test-perf/conditional-xaml/) i stronę Hostowanie kontrolek XAML platformy UWP w [aplikacjach klasycznych (Wyspy XAML).](/windows/apps/desktop/modernize/xaml-islands/)

### <a name="xaml-structure-visualizer"></a>Wizualizator struktury XAML

Funkcja Wizualizator struktury w edytorze kodu pokazuje linie przewodnika po strukturze, które są pionowymi kreskami wskazującymi pasujące otwarte i zamknięte elementy tagu w kodzie. Te linie pionowe ułatwiają zobaczenie, gdzie zaczynają się i kończą bloki logiczne.

Aby uzyskać więcej informacji, zobacz stronę [z kodem nawigowania.](../ide/navigating-code.md)

### <a name="intellicode-for-xaml"></a>IntelliCode dla XAML

Po dodaniu tagu XAML do kodu zazwyczaj zaczyna się od lewego nawiasu kątowego `<` . Po wpisaniu tego nawiasu kątowego zostanie wyświetlone menu IntelliCode z kilkoma najpopularniejszymi tagami XAML. Wybierz tę, którą chcesz szybko dodać do kodu.

Możesz rozpoznać wybory funkcji IntelliCode, ponieważ są one wyświetlane w górnej części listy i są oznaczone.

![Lista funkcji IntelliCode dla edytora tekstów XAML](media/xaml-intellicode-selection.png "Zrzut ekranu przedstawiający listę funkcji IntelliCode dla edytora tekstów XAML")

Aby uzyskać więcej informacji, zobacz [stronę Omówienie funkcji IntelliCode.](/visualstudio/intellicode/overview/)

### <a name="settings"></a>Ustawienia

Aby uzyskać więcej informacji *na temat wszystkich* ustawień w Visual Studio IDE, zobacz stronę Funkcje [edytora](../ide/writing-code-in-the-code-and-text-editor.md) kodu.

## <a name="xaml-optional-settings"></a>Opcjonalne ustawienia XAML

Okno dialogowe Opcje [umożliwia](../ide/reference/options-dialog-box-visual-studio.md) zmianę ustawień domyślnych edytora kodu XAML. Aby wyświetlić ustawienia, wybierz pozycję **Narzędzia**  >  **Opcje Edytor**  >  **tekstu**  >  **XAML.**

![Lista Opcje dla edytora tekstów XAML](media/xaml-tools-options.png "Zrzut ekranu przedstawiający listę Opcje dla edytora tekstów XAML")

> [!NOTE]
> Możesz również użyć skrótów klawiaturowych, aby uzyskać dostęp do okna dialogowego Opcje. Oto jak: naciśnij **klawisze Ctrl** + **Q,** aby przeszukać ideę, wpisz **opcje**, a następnie naciśnij **klawisz Enter**. Następnie naciśnij klawisze **Ctrl** E, aby przeszukać okno dialogowe Opcje, wpisz Edytor tekstu, naciśnij klawisz +  **Enter,** wpisz **XAML,** a następnie naciśnij **klawisz Enter**. 
>
> Aby uzyskać więcej informacji na temat skrótów klawiaturowych, zobacz porady [dotyczące skrótów Visual Studio](../ide/productivity-shortcuts.md#code-editor) strony.

### <a name="universal-text-editor-options"></a>Opcje uniwersalnego edytora tekstu

W [oknie dialogowym](../ide/reference/options-text-editor-xaml-formatting.md) Opcje języka XAML następujące trzy pierwsze elementy są uniwersalne dla wszystkich języków programowania, które obsługuje Visual Studio IDE. Przejdź do połączonych informacji w poniższej tabeli, aby dowiedzieć się więcej na temat tych opcji i sposobu ich używania.

|Nazwa  |Więcej informacji  |
|---------|---------|
|Ogólne  | [Okno dialogowe Opcje: Edytor tekstu > wszystkie języki](../ide/reference/options-text-editor-all-languages.md) |
|Paski przewijania | [Opcje, Edytor tekstu, Wszystkie języki, Paski przewijania](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Karty  |  [Opcje, Edytor tekstów, Wszystkie języki, Karty](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>Opcje edytora tekstu specyficzne dla języka XAML

W poniższej tabeli wymieniono ustawienia w [oknie dialogowym](../ide/reference/options-text-editor-xaml-formatting.md) Opcje, które mogą ulepszyć środowisko edytowania podczas tworzenia aplikacji opartych na języku XAML. Odwiedź połączone informacje, aby dowiedzieć się więcej na temat tych opcji i sposobu ich używania.

|Nazwa  |Więcej informacji  |
|---------|---------|
|Formatowanie | [Opcje, Edytor tekstów, XAML, Formatowanie](../ide/reference/options-text-editor-xaml-formatting.md) |
|Różne |  [Opcje, Edytor tekstu, XAML, Różne](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> Ustawienie nazwy metody procedury obsługi zdarzeń  z **literami** w sekcji Różne jest szczególnie przydatne dla deweloperów XAML. To ustawienie jest *domyślnie* wyłączone, ponieważ jest nowe, ale sugerujemy, aby ustawić je na *wartość on* w celu obsługi właściwej wielkości obudowy w kodzie.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat edytowania kodu w czasie rzeczywistym podczas uruchamiania aplikacji w trybie debugowania, zobacz stronę [Przeładowywanie kodu XAML na gorąco](xaml-hot-reload.md) debugowania.

## <a name="see-also"></a>Zobacz też

- [Visual Studio funkcji edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Język XAML w aplikacjach platformy UWP](/windows/uwp/xaml-platform/xaml-overview/)
- [Język XAML w aplikacjach platformy Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
- [Tworzenie aplikacji mobilnych platformy Xamarin (Mac)](/visualstudio/mac/xamarin/)
- [Visual Studio 2019 dla komputerów Mac — przewodnik po środowiskach IDE (Mac)](/visualstudio/mac/ide-tour/)

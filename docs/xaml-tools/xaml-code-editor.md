---
title: Edytor kodu XAML
description: Zapoznaj się z edytorem kodu XAML w programie Visual Studio
ms.date: 06/16/2020
ms.topic: overview
monikerRange: vs-2019
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: df2c257caed24e85569ca41f3cc83dd9d47d5b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962317"
---
# <a name="xaml-code-editor"></a>Edytor kodu XAML

Edytor kodu XAML w [środowisku IDE programu Visual Studio](../get-started/visual-studio-ide.md) zawiera wszystkie narzędzia potrzebne do tworzenia aplikacji WPF i platformy UWP dla platformy systemu Windows oraz dla programu [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). W tym artykule opisano rolę, jaką pełni Edytor kodu podczas tworzenia aplikacji opartych na języku XAML, oraz funkcje, które są unikatowe dla edytora kodu XAML w programie Visual Studio 2019.

Aby rozpocząć, przyjrzyjmy się IDE (zintegrowane środowisko programistyczne) za pomocą otwartego projektu WPF. Na poniższej ilustracji przedstawiono kilka kluczowych narzędzi IDE, które będą używane razem z edytorem kodu XAML.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="Środowisko IDE programu Visual Studio 2019 z otwartym projektem WPF w języku XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

W lewym dolnym rogu obrazu można wykonać następujące czynności:

- Okno **[edytora kodu XAML](#xaml-code-editor-ui)** — &mdash; temat w tym artykule, w &mdash; którym tworzysz i edytujesz swój kod.
- Okno **[Projektant XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** , w którym zaprojektowano interfejs użytkownika.
- Okno **[przybornika](../ide/reference/toolbox.md)** było dokować, w którym można dodać kontrolki do interfejsu użytkownika.
- Przycisk **[Debuguj](../debugger/debugger-feature-tour.md)** , w którym uruchomiono kod i go debugujesz. <br>(Możesz również edytować swój kod w czasie rzeczywistym podczas debugowania za pomocą [gorącego ponownego ładowania XAML](xaml-hot-reload.md)).
- Okno **[Eksplorator rozwiązań](../ide/solutions-and-projects-in-visual-studio.md)** , w którym można zarządzać plikami, projektami i rozwiązaniami.
- Okno **[Właściwości](../ide/reference/properties-window.md)** , w którym można zmienić sposób, w jaki wygląda interfejs użytkownika, oraz sposób działania formantów interfejsu użytkownika.

Aby kontynuować, przyjrzyjmy się więcej na temat edytora kodu XAML.

## <a name="xaml-code-editor-ui"></a>Interfejs użytkownika edytora kodu XAML

Podczas gdy okno edytora kodu dla aplikacji XAML udostępnia niektóre elementy interfejsu użytkownika (interfejs użytkowników), które również znajdują się w standardowym IDE, zawiera również kilka unikatowych funkcji, które ułatwiają tworzenie aplikacji XAML.

Poniżej znajduje się podgląd samego okna edytora kodu XAML.

![Okno edytora kodu XAML w programie Visual Studio](media/xaml-code-editor-window.png "Zrzut ekranu okna edytora kodu XAML w programie Visual Studio 2019")

Następnie Przyjrzyjmy się funkcjom każdego elementu interfejsu użytkownika w edytorze kodu.

### <a name="first-row"></a>Pierwszy wiersz

W pierwszym wierszu w górnej części okna kod XAML po lewej stronie znajduje się karta **projektowanie** , przycisk **Zamień okienka** , karta **XAML** i **wyskakujący przycisk XAML** .

![Pierwszy z dwóch górnych wierszy okna edytora kodu XAML w programie Visual Studio z lewej strony pierwszego wiersza wyróżnionego](media/xaml-code-editor-top-row-left.png "Zrzut ekranu pierwszego z dwóch górnych wierszy okna edytora kodu XAML w programie Visual Studio 2019, w którym elementy interfejsu użytkownika po lewej stronie są wyróżnione")

Oto jak to działa:

- Karta **projektowanie** zmienia fokus z edytora kodu XAML na Projektant XAML.
- Przycisk **Zamień okienka** powoduje odwrócenie lokalizacji Projektant XAML i edytora kodu XAML w IDE.
- Karta **XAML** zmienia fokus z powrotem na Edytor kodu XAML.
- Przycisk **wyskakujące XAML** powoduje utworzenie oddzielnego okna edytora kodu XAML, które jest poza IDE.

Kontynuując po prawej stronie znajduje się przycisk **podziału w pionie** , przycisk **podziału poziomego** i przycisk **Zwiń okienka** .

![Pierwszy z dwóch górnych wierszy okna edytora kodu XAML w programie Visual Studio z prawej strony pierwszego wiersza wyróżnionego](media/xaml-code-editor-top-row-right.png "Zrzut ekranu pierwszego z dwóch górnych wierszy okna edytora kodu XAML w programie Visual Studio 2019, w którym elementy interfejsu użytkownika po prawej stronie są wyróżnione")

Oto jak to działa:

- Przycisk **podziału w pionie** zmienia lokalizację Projektant XAML i edytora kodu XAML w środowisku IDE z wyrównania poziomego do pionowego wyrównania.
- Przycisk **Podziel w poziomie** zmienia lokalizację Projektant XAML i edytora kodu XAML w środowisku IDE z wyrównania w pionie do poziomu wyrównania w poziomie.
- Przycisk **Zwiń okienko** umożliwia zwinięcie informacji znajdujących się w dolnym okienku, niezależnie od tego, czy jest to edytor kodu, czy projektant. (Aby przywrócić dolne okienko, ponownie wybierz ten sam przycisk, który jest teraz nazwany przycisk **Rozwiń okienko** ).

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Drugi wiersz

W drugim wierszu w górnej części okna kod XAML istnieją dwa listy rozwijane okna. Jednak po wyświetleniu etykietki narzędzia dla tych elementów interfejsu użytkownika program zidentyfikuje je jako "element: window" i "member: window".

![Drugi z dwóch pierwszych wierszy okna edytora kodu XAML w programie Visual Studio, w którym widoczne są obie listy rozwijane okna.](media/xaml-code-editor-top-row-windows.png "Zrzut ekranu przedstawiający drugi z dwóch górnych wierszy okna edytora kodu XAML w programie Visual Studio 2019, w którym widoczne są obydwa listy rozwijane okna")

Listy rozwijane okna mają różne funkcje w następujący sposób:

- **Element: okno** po lewej stronie ułatwia Wyświetlanie elementów równorzędnych lub nadrzędnych oraz nawigowanie do nich.

  W tym celu pokazuje widok podobny do konspektu, który ujawnia strukturę tagów kodu. Po wybraniu z listy fokus w edytorze kodu zostanie przyciągnięty do wiersza kodu, który zawiera wybrany element.

    ![Element: Lista rozwijana okna w programie Visual Studio](media/xaml-element-window-dropdown.png "Zrzut ekranu przedstawiający element: Lista rozwijana okna w programie Visual Studio 2019")

- **Okno członek:** po prawej stronie ułatwia wyświetlanie atrybutów lub elementów podrzędnych, a także nawigowanie do nich.

    W celu wyświetlenia listy właściwości w kodzie. Po wybraniu z listy fokus w edytorze kodu zostanie przyciągnięty do wiersza kodu, który zawiera wybraną właściwość.

    ![Lista rozwijana "członek: okno" w programie Visual Studio](media/xaml-member-window-dropdown.png "Zrzut ekranu przedstawiający element członkowski: Lista rozwijana okna w programie Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Środkowe okienko, Edytor kodu

Środkowym okienkiem jest część "kod" edytora kodu XAML. Zawiera większość funkcji, które znajdują się w [edytorze kodu IDE](../get-started/tutorial-editor.md). Będziemy korzystać z kilku funkcji uniwersalnego środowiska IDE, które mogą pomóc w opracowaniu kodu XAML. Ponadto wyróżnimy również funkcje unikatowe do XAML w IDE.

![Edytor kodu XAML, tylko środkowe okienko, w programie Visual Studio](media/xaml-code-editor-middle.png "Zrzut ekranu edytora kodu XAML, tylko w środkowym okienku, w programie Visual Studio 2019")

#### <a name="quick-actions"></a>Szybkie akcje

Możesz użyć [szybkich akcji](../ide/quick-actions.md) do refaktoryzacji, wygenerowania lub modyfikacji kodu przy użyciu jednej akcji.

Na przykład jedno przydatne zadanie, które można wykonać za pomocą szybkich akcji, to **usunięcie niepotrzebnych użycia** z kodu C# na karcie **MainWindow.XAML.cs** .

Oto kroki tej procedury:

1. Umieść kursor nad instrukcją using, wybierz ikonę żarówki, a następnie wybierz pozycję **Usuń niepotrzebne użycie** z listy rozwijanej.

    ![Opcja "Usuń niepotrzebne użycie" edytora IDE z menu szybkie akcje](media/xaml-code-editor-remove-usings.png "Zrzut ekranu przedstawiający opcję Usuń niepotrzebne użycie edytora IDE z menu szybkie akcje")

1. Wybierz, czy chcesz naprawić wszystkie wystąpienia w **dokumencie**, **projekcie** lub **rozwiązaniu**.
1. Wyświetl okno dialogowe **Podgląd** , a następnie wybierz pozycję **Zastosuj**.

Możesz również uzyskać dostęp do tej funkcji z paska menu. W tym celu wybierz pozycję **Edytuj**  >  **IntelliSense**  >  **Usuń i Sortuj użycia**.

Aby uzyskać więcej informacji o korzystaniu z ustawień, zobacz stronę [Sortowanie użycia](../ide/reference/sort-usings.md) . Aby uzyskać więcej informacji na temat technologii IntelliSense, zobacz stronę [IntelliSense w programie Visual Studio](../ide/using-intellisense.md) . Aby uzyskać więcej informacji o niektórych typowych sposobach używania szybkich akcji przez deweloperów, zobacz stronę [typowe akcje szybkie](../ide/common-quick-actions.md) .

#### <a name="change-tracking"></a>Śledzenie zmian

Kolor lewego marginesu umożliwia śledzenie zmian wprowadzonych w pliku. Oto, jak kolory odnoszą się do działań, które należy wykonać:

- Zmiany wprowadzone od momentu otwarcia pliku, ale nie zostały zapisane, są oznaczane **żółtym** paskiem na lewym marginesie (znanym jako margines zaznaczenia).

    ![Edycja edytora kodu z żółtym paskiem](media/code-editor-edit-yellow.png "Zrzut ekranu edytora kodu z zmianą oznaczoną żółtym paskiem na marginesie zaznaczenia.")

- Po zapisaniu zmian (ale przed zamknięciem pliku) pasek zmieni **kolor na zielony**.

    ![Edycja edytora kodu z zielonym paskiem](media/code-editor-edit-green.png "Zrzut ekranu edytora kodu z zmianą oznaczoną zielonym paskiem na marginesie zaznaczenia.")

Aby wyłączyć tę funkcję i włączyć ją, Zmień opcję **Śledź zmiany** w obszarze Ustawienia **edytora tekstu** (opcje **Narzędzia**  >    >  **Edytor tekstu**).

Aby uzyskać więcej informacji na temat śledzenia zmian &mdash; w celu uwzględnienia linii falistych (nazywanych także "zygzakami"), które są wyświetlane w obszarze ciągi kodu, &mdash; Zobacz sekcję **[funkcje edytora](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** w temacie [funkcje strony Edytor kodu programu Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md) .

#### <a name="right-click-context-menu"></a>Menu kontekstowe kliknij prawym przyciskiem myszy

Gdy edytujesz kod w edytorze kodu XAML, istnieje kilka funkcji, do których można uzyskać dostęp za pomocą menu kontekstowego po kliknięciu prawym przyciskiem myszy. Większość z tych funkcji jest ogólnie dostępna w środowisku IDE programu Visual Studio, a niektóre z nich są specyficzne dla programu przy użyciu edytora kodu wraz z oknem projektowania.

![Zrzut ekranu przedstawiający menu kontekstowe prawym przyciskiem myszy w edytorze kodu XAML w programie Visual Studio 2019.](media/xaml-code-editor-right-click-menu.png)

Oto, co robią każda funkcja i jak jest to przydatne:

- **Wyświetl kod** — otwiera okno kod języka programowania, który zwykle znajduje się obok widoku domyślnego zawierającego okno projektowania i Edytor kodu XAML.
- **Projektant widoków** — otwiera widok domyślny, który zawiera okno projektowania i Edytor kodu XAML. (Jeśli jesteś już w widoku domyślnym, nie robi nic).
- **Szybkie akcje i refaktoryzacje** — repliky, generowane lub w inny sposób modyfikują kod z pojedynczą akcją. Po umieszczeniu wskaźnika myszy na kodzie zobaczysz ikonę żarówki, gdy zostanie udostępniona szybka akcja lub Refaktoryzacja. <br>Zobacz również: [szybkie akcje](../ide/quick-actions.md) i [kod refaktoryzacji](../ide/refactoring-in-visual-studio.md).
- **Zmień nazwę...** -Zmienia nazwy tylko przestrzeni nazw. Jeśli nie masz przestrzeni nazw do zmiany nazwy, zostanie wyświetlony komunikat o błędzie z informacją o zmianie nazwy prefiksów przestrzeni nazw.
- **Usuń i Sortuj przestrzenie nazw** — usuwa nieużywane przestrzenie nazw, a następnie sortuje te obszary nazw, które pozostaną.
- **Wgląd w definicje** — wyświetla definicję typu bez opuszczania bieżącej lokalizacji w edytorze. <br>Zobacz również: [wgląd do definicji](../ide/go-to-and-peek-definition.md#peek-definition) i [Wyświetlanie i edytowanie kodu za pomocą definicji wglądu](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Przejdź do definicji** — nawiguje do źródła typu lub elementu członkowskiego, a następnie otwiera wynik na nowej karcie. <br>Zobacz również: [Przejdź do definicji](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Otocz za pomocą...** — Użyj fragmentów kodu otaczającego, które są dodawane wokół wybranego bloku kodu. <br>Zobacz również: [fragmenty rozszerzające i fragmenty kodu](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Wstaw fragment** kodu — wstawia wstawkę w lokalizacji kursora.
- **Wycinanie** — wyjaśnienie
- **Kopiowanie** — Wyjaśnij wszystko
- **Wklejanie** — nie Wyjaśnij
- **Tworzenie konspektu** — rozwijanie i zwijanie sekcji kodu. <br>Zobacz również: [Tworzenie konspektu](../ide/outlining.md).
- **Kontrola źródła** — Wyświetlanie historii udziałów kodu w repozytorium typu open source.

### <a name="middle-pane-scroll-bar"></a>Środkowe okienko, pasek przewijania

Pasek przewijania może robić więcej niż przewijanie kodu. Można go również użyć do otwarcia innego okienka edytora kodu. Można również użyć paska przewijania, aby bardziej efektywnie poprawić kod, dodając do niego adnotacje lub używając różnych trybów wyświetlania.

#### <a name="split-the-code-window"></a>Podziel okno kodu

Na pasku przewijania edytora kodu znajduje się przycisk **podziału** w prawym górnym rogu. Po wybraniu tej opcji możesz otworzyć inne okienko edytora kodu. Jest to przydatne, ponieważ działają niezależnie od siebie, więc można używać ich do pracy nad kodem w różnych lokalizacjach.

![Zrzut ekranu przedstawiający środkowe okienko edytora kodu XAML w programie Visual Studio 2019 z wyróżnionym przyciskiem podziału w prawym górnym rogu okienka.](media/code-editor-split-window-button.png)

Więcej informacji o sposobie dzielenia okna edytora znajduje się na stronie [Zarządzanie oknami edytora](../ide/how-to-manage-editor-windows.md) .

#### <a name="use-annotations-or-map-mode"></a>Używanie adnotacji lub trybu mapy

Możesz również zmienić sposób, w jaki wygląda pasek przewijania i jakie dodatkowe funkcje zawiera. Na przykład wiele osób chce dołączyć *Adnotacje* na pasku przewijania, które udostępniają wizualne podpowiedzi, takie jak zmiany kodu, punkty przerwania, zakładki, błędy i położenie karetki.

Inne doceniają użycie *trybu mapy*, który wyświetla linie kodu w miniaturach na pasku przewijania. Deweloperzy, którzy posiadają wiele kodów w pliku, mogą stwierdzić, że tryb mapy jest bardziej wydajny niż domyślny pasek przewijania.

Aby uzyskać więcej informacji na temat zmiany ustawień domyślnych paska przewijania, zobacz stronę  [Dostosowywanie paska przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) .

## <a name="xaml-specific-features"></a>Funkcje specyficzne dla języka XAML

Większość z następujących funkcji jest ogólnie dostępna w środowisku IDE programu Visual Studio, ale dodaliśmy do nich wymiary, które ułatwiają programowanie dla deweloperów języka XAML.

### <a name="xaml-code-snippets"></a>Fragmenty kodu XAML

Fragmenty kodu to małe bloki kodu wielokrotnego użytku, które można wstawić do w pliku kodu za pomocą menu kontekstowego prawym przyciskiem myszy **Wstaw** wstawka lub kombinację skrótów klawiaturowych (**Ctrl** + **K**, **Ctrl** + **X**). Ulepszono funkcję [IntelliSense](../ide/using-intellisense.md) , która obsługuje wyświetlanie fragmentów kodu XAML, które działają dla obu wbudowanych fragmentów kodu oraz wszelkich wstawek niestandardowych, które można dodać ręcznie. Niektóre wbudowane fragmenty kodu XAML obejmują `#region` , `Column definition` , `Row definition` ,, `Setter` i `Tag` .

![Edytor kodu XAML z opcjami fragmentów kodu XAML wyświetlanymi w IntelliSense](media/xaml-code-snippets.png "Zrzut ekranu edytora kodu XAML z opcjami fragmentów kodu XAML wyświetlanymi w IntelliSense")

Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md) i strony [fragmentów kodu w języku C#](../ide/visual-csharp-code-snippets.md) .

### <a name="xaml-region-support"></a>Obsługa #region XAML

Począwszy od programu Visual Studio 2015, firma Microsoft udostępniła #region pomoc techniczną dla deweloperów XAML w WPF i platformy UWP, a także ostatnio w oprogramowaniu [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). W programie Visual Studio 2019 kontynuujemy ulepszanie przyrostowe w celu zapewnienia pomocy technicznej #region. Na przykład, w [wersji 16,4](/visualstudio/releases/2019/release-notes-v16.4/) i nowszych, #region opcje są wyświetlane w momencie rozpoczęcia pisania `<!` .

![Edytor kodu XAML z opcjami #region wyświetlanymi w IntelliSense](media/code-editor-xaml-region.png "Zrzut ekranu edytora kodu XAML z opcjami #region wyświetlanymi w IntelliSense")

Za pomocą regionów można grupować sekcje kodu, które mają być również rozwijane lub zwijane.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Aby uzyskać więcej informacji na temat regionów, zobacz stronę [#region (odwołanie w C#)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) . Aby uzyskać więcej informacji na temat rozszerzania i zwijania sekcji kodu, zobacz stronę [konspektu](../ide/outlining.md) .

### <a name="xaml-comments"></a>Komentarze XAML

Deweloperzy często wolą dokumentować swój kod przy użyciu komentarzy. Komentarze można dodawać do kodu XAML, który znajduje się na karcie **MainWindow. XAML** , w następujący sposób:

- Wprowadź `<!--` przed komentarzem, a następnie Dodaj `-->` po komentarzu.
- Wprowadź `<!` wartość, a następnie wybierz pozycję `!--` z listy opcji.

  ![Edytor kodu XAML kliknij prawym przyciskiem myszy okno dialogowe Dodawanie komentarzy](media/xaml-code-editor-comments.png "Zrzut ekranu przedstawiający menu kontekstowe kliknij prawym przyciskiem myszy, aby dodać komentarze w edytorze kodu XAML")

- Zaznacz kod, który ma być otoczony komentarzem, a następnie wybierz przycisk **komentarz** z paska narzędzi w IDE. Aby wycofać tę akcję, wybierz przycisk Anuluj **komentarz** .

  ![Przycisk komentarz i przycisk Usuń komentarz na pasku narzędzi IDE](media/comment-undo-comment-buttons.png "Zrzut ekranu przedstawiający przycisk komentarz i przycisk Usuń komentarz na pasku narzędzi IDE")

- Zaznacz kod, który ma być otoczony komentarzem, a następnie naciśnij klawisze **Ctrl** + **K**, **Ctrl +** + **C**. Aby usunąć komentarz zaznaczonego kodu, naciśnij **klawisze CTRL** + **K**, **Ctrl** + **U**.

Aby uzyskać więcej informacji o sposobach używania komentarzy w kodzie C#, które znajdują się na karcie **MainWindow.XAML.cs** , zobacz stronę z [komentarzami dotyczącymi dokumentacji](/dotnet/csharp/language-reference/language-specification/documentation-comments/) .

### <a name="xaml-lightbulbs"></a>Lightbulbs XAML

Ikony żarówki, które pojawiają się w kodzie XAML, są częścią [szybkich akcji](../ide/quick-actions.md) , których można użyć do refaktoryzacji, wygenerowania lub modyfikacji kodu.

Poniżej przedstawiono kilka przykładów, w których można skorzystać ze środowiska kodowania języka XAML:

- **Usuń niepotrzebne przestrzenie nazw**. W edytorze kodu XAML niepotrzebne przestrzenie nazw pojawiają się w wygaszonym tekście. Jeśli umieścisz kursor nad niepotrzebnym użyciem, pojawi się żarówki. Po wybraniu opcji **Usuń niepotrzebne przestrzenie nazw** z listy rozwijanej zobaczysz wersję zapoznawczą, którą można usunąć.

  ![Opcja Usuń niepotrzebne przestrzenie nazw edytora kodu XAML z szybkich akcji żarówki](media/xaml-code-editor-dimmed-namespaces-preview.png "Zrzut ekranu przedstawiający opcję Usuń niepotrzebne przestrzenie nazw edytora kodu XAML, która jest wyświetlana przy użyciu szybkich akcji żarówki")

- **Zmień nazwę przestrzeni nazw**. Ta funkcja dostępna w menu kontekstowym po kliknięciu prawym przyciskiem myszy po zaznaczeniu przestrzeni nazw ułatwia zmianę wielu wystąpień ustawienia jednocześnie. Możesz również uzyskać dostęp do tej funkcji przy użyciu paska menu, **edytować**  >  **nazwę refaktoryzacji**  >  lub naciskając **Ctrl** + **r**, a następnie ponownie **Ctrl** + **r** .

  ![Opcja Zmień nazwę przestrzeni nazw edytora kodu XAML z menu kontekstowego po kliknięciu prawym przyciskiem myszy](media/code-editor-rename-namespace.png "Zrzut ekranu opcji Zmień nazwę przestrzeni nazw edytora kodu XAML, która pojawia się za pomocą menu kontekstowego po kliknięciu prawym przyciskiem myszy")

  Aby uzyskać więcej informacji, zobacz stronę [Zmień nazwę wskaźnika refaktoryzacji symboli](../ide/reference/rename.md) .

### <a name="conditional-xaml-for-uwp"></a>Warunkowe XAML dla platformy UWP

Warunkowe XAML umożliwia użycie metody [ApiInformation. IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) w znacznikach XAML. Dzięki temu można ustawić właściwości i utworzyć wystąpienia obiektów w znacznikach na podstawie obecności interfejsu API bez konieczności używania kodu.

Aby uzyskać więcej informacji, zobacz stronę [warunkowej XAML](/windows/uwp/debug-test-perf/conditional-xaml/) i [kontrolki XAML platformy UWP hosta na stronie aplikacje klasyczne (Wyspy XAML)](/windows/apps/desktop/modernize/xaml-islands/) .

### <a name="xaml-structure-visualizer"></a>Wizualizator struktury XAML

Funkcja wizualizator struktury w edytorze kodu pokazuje linie prowadnic struktury, które są liniami kreskowanymi pionowymi, które wskazują pasujące otwarte i zamknięte elementy tag w kodzie. Te pionowe linie sprawiają, że bloki logiczne zaczynają się i kończą.

Aby uzyskać więcej informacji, zobacz stronę [Nawigacja w kodzie](../ide/navigating-code.md) .

### <a name="intellicode-for-xaml"></a>Rozszerzenia intellicode dla języka XAML

Po dodaniu tagu XAML do kodu zwykle zaczyna się od lewego nawiasu kątowego `<` . Po wpisaniu tego nawiasu ostrego zostanie wyświetlone menu rozszerzenia intellicode zawierające kilka popularnych tagów XAML. Wybierz ten, który chcesz szybko dodać do kodu.

Rozszerzenia intellicode zaznaczenia można rozpoznać, ponieważ pojawiają się one u góry listy i są oznaczona gwiazdkami.

![Lista rozszerzenia intellicode dla edytora tekstu XAML](media/xaml-intellicode-selection.png "Zrzut ekranu przedstawiający listę rozszerzenia intellicode dla edytora tekstu XAML")

Aby uzyskać więcej informacji, zobacz [Omówienie strony rozszerzenia intellicode](/visualstudio/intellicode/overview/) .

### <a name="settings"></a>Ustawienia

Aby uzyskać więcej informacji na temat *wszystkich* ustawień w środowisku IDE programu Visual Studio, zobacz [funkcje strony Edytor kodu](../ide/writing-code-in-the-code-and-text-editor.md) .

## <a name="xaml-optional-settings"></a>Ustawienia opcjonalne XAML

Za pomocą okna dialogowego [Opcje](../ide/reference/options-dialog-box-visual-studio.md) można zmienić ustawienia domyślne dla edytora kodu XAML. Aby wyświetlić ustawienia, wybierz opcje **Narzędzia**  >    >  **Edytor tekstu**  >  **XAML**.

![Lista opcji dla edytora tekstu XAML](media/xaml-tools-options.png "Zrzut ekranu przedstawiający listę opcji dla edytora tekstu XAML")

> [!NOTE]
> Możesz również użyć skrótów klawiaturowych, aby uzyskać dostęp do okna dialogowego Opcje. Oto jak to zrobić: naciśnij klawisz **Ctrl** + **Q** , aby przeszukać środowisko IDE, wpisz **Opcje**, a następnie naciśnij klawisz **Enter**. Następnie naciśnij klawisz **Ctrl** + **E** , aby przeszukać okno dialogowe Opcje, wpisz **Edytor tekstu**, naciśnij klawisz **Enter**, wpisz **XAML**, a następnie naciśnij klawisz **Enter**.
>  
> Aby uzyskać więcej informacji na temat skrótów klawiaturowych, zobacz [porady dotyczące skrótów dla programu Visual Studio](../ide/productivity-shortcuts.md#code-editor) .

### <a name="universal-text-editor-options"></a>Opcje uniwersalnego edytora tekstu

W oknie dialogowym [Opcje](../ide/reference/options-text-editor-xaml-formatting.md) dla języka XAML następujące trzy pierwsze elementy są uniwersalne dla wszystkich języków programowania obsługiwanych przez środowisko IDE programu Visual Studio. Zapoznaj się z informacjami w poniższej tabeli, aby dowiedzieć się więcej o tych opcjach i sposobach ich użycia.

|Nazwa  |Więcej informacji  |
|---------|---------|
|Ogólne  | [Opcje — okno dialogowe: Edytor tekstu > wszystkie języki](../ide/reference/options-text-editor-all-languages.md) |
|Paski przewijania | [Opcje, Edytor tekstu, wszystkie języki, paski przewijania](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Karty  |  [Opcje, Edytor tekstów, Wszystkie języki, Karty](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>Opcje edytora tekstu specyficznego dla języka XAML

W poniższej tabeli wymieniono ustawienia w oknie dialogowym [Opcje](../ide/reference/options-text-editor-xaml-formatting.md) , które mogą ulepszyć środowisko edytowania podczas opracowywania aplikacji opartych na języku XAML. Odwiedź połączone informacje, aby dowiedzieć się więcej o tych opcjach i sposobach ich użycia.

|Nazwa  |Więcej informacji  |
|---------|---------|
|Formatowanie | [Opcje, Edytor tekstów, XAML, Formatowanie](../ide/reference/options-text-editor-xaml-formatting.md) |
|Różne |  [Opcje, Edytor tekstu, XAML, różne](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> Ustawienie **Nazwa metody obsługi zdarzeń wielką literą** w sekcji **różne** jest szczególnie przydatne dla deweloperów języka XAML. To ustawienie jest domyślnie *wyłączone* , ponieważ jest nowe, ale sugerujemy, aby ustawić go na wartość *w* celu obsługi odpowiedniej wielkości liter w kodzie.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o tym, jak edytować swój kod w czasie rzeczywistym podczas uruchamiania aplikacji w trybie debugowania, zobacz stronę [Hot reload języka XAML](xaml-hot-reload.md) .

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu programu Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)
- [XAML w aplikacjach platformy UWP](/windows/uwp/xaml-platform/xaml-overview/)
- [XAML w aplikacjach Xamarin. Forms](/xamarin/xamarin-forms/xaml/)
- [Programowanie aplikacji mobilnych platformy Xamarin (Mac)](/visualstudio/mac/xamarin/)
- [Visual Studio 2019 for Mac — samouczek IDE (Mac)](/visualstudio/mac/ide-tour/)

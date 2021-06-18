---
title: Dostosowywanie układów okien
description: Dowiedz się, jak dostosować charakterystyki okien, aby tworzyć układy, które najlepiej działają w przypadku różnych przepływów pracy programistów.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be11db364d0505833e722d3db308b41a18ccbb9d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308132"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Dostosowywanie układów okien w Visual Studio

W Visual Studio można dostosować położenie, rozmiar i zachowanie okien, aby tworzyć układy okien, które najlepiej działają w przypadku różnych przepływów pracy projektowania. Gdy dostosowujesz układ, idee go zapamiętuje. Jeśli na przykład zmienisz lokalizację dokowania usługi **Eksplorator rozwiązań, a** następnie zamkniesz program Visual Studio, przy następnym otwarciu usługi Visual Studio, nawet jeśli pracujesz na innym **komputerze,** Eksplorator rozwiązań zostanie zadokowany w tej samej lokalizacji.

Możesz również nazwać i zapisać układ niestandardowy, a następnie przełączać się między układami za pomocą jednego polecenia. Można na przykład utworzyć układ do edycji i układ debugowania oraz przełączać się między nimi za pomocą polecenia menu Zastosuj  >  **układ okna.**

## <a name="tool-and-document-windows"></a>Okna narzędzi i dokumentów

Ide ma dwa podstawowe typy okien: *okna narzędzi i* okna *dokumentów*. Okna narzędzi **obejmują Eksplorator rozwiązań**, **Eksplorator serwera**, **Okno Dane wyjściowe,** **listę** błędów, projektantów, okna debugera i tak dalej. Okna dokumentów zawierają pliki kodu źródłowego, dowolne pliki tekstowe, pliki konfiguracji itp. Rozmiar okien narzędzi można zmieniać i przeciągać za pomocą paska tytułu. Okna dokumentów można przeciągać przy ich karcie. Kliknij prawym przyciskiem myszy kartę lub pasek tytułu, aby ustawić inne opcje w oknie.

Menu **Okno** zawiera opcje dokowania, zmiennoprzecinkowego i ukrywania okien w idee IDE. Kliknij prawym przyciskiem myszy kartę okna lub pasek tytułu, aby wyświetlić dodatkowe opcje dla tego konkretnego okna. Jednocześnie można wyświetlić więcej niż jedno wystąpienie niektórych okien narzędzi. Można na przykład wyświetlić więcej niż jedno okno przeglądarki internetowej i utworzyć dodatkowe wystąpienia niektórych okien narzędzi, wybierając pozycję **Nowe** okno w menu **Okno.**

### <a name="split-windows"></a>Okna podziału

Jeśli musisz wyświetlić lub edytować dwie lokalizacje jednocześnie w dokumencie, możesz podzielić okna. Aby podzielić dokument na dwie niezależnie przewijane sekcje, kliknij pozycję **Podziel** w menu **Okno.** Kliknij **pozycję Usuń podział** w menu **Okno,** aby przywrócić pojedynczy widok.

### <a name="tabs"></a>Karty

Karty mogą rozmieszczać układ na kilka różnych sposobów. Możesz na przykład wyświetlić podgląd pliku w edytorze bez otwierania pliku, grupować karty i nie tylko.

#### <a name="preview-tab-document-windows"></a>Karta Podgląd (okna dokumentów)

Na karcie **Podgląd** można wyświetlać pliki w edytorze bez ich otwierania. Możesz wyświetlić podgląd plików, wybierając je w Eksplorator rozwiązań **,** podczas debugowania, gdy przechodzisz do plików, za pomocą funkcji **Przejdź** do definicji i przeglądając wyniki wyszukiwania. Pliki podglądu są wyświetlane na karcie po prawej stronie listy kart dokumentów. Plik zostanie otwarty do edycji, jeśli go zmodyfikujesz lub wybierzesz **pozycję Otwórz.**

::: moniker range=">=vs-2019"

#### <a name="vertical-document-tabs"></a>Pionowe karty dokumentów

Nowość w **[wersji 16.4:](/visualstudio/releases/2019/release-notes-v16.4/)** Dodaliśmy jeden z najbędszych żądań [funkcji,](https://developercommunity.visualstudio.com/idea/467369/vertical-group-tab.html)pionowe karty dokumentów , w wersji Visual Studio 2019 w wersji 16.4. Teraz możesz zarządzać kartami dokumentów na pionowej liście po lewej lub prawej stronie edytora.

Pionowe karty dokumentów można stosować w następujący sposób:

- Na **pasku** menu wybierz pozycję Opcje narzędzi Karty  >    >    >  **środowiska** i okna. Następnie w **kontrolce Ustawianie układu** karty wybierz z listy rozwijanej pozycję **Górny,** Lewy **lub** Prawy.

- Kliknij prawym przyciskiem myszy kartę, wybierz polecenie **Ustaw układ karty,** a następnie wybierz pozycję **W lewo lub** w **prawo.** (Aby przywrócić domyślną pozycję kart, wybierz **pozycję Pierwsze).**

    :::image type="content" source="./media/vs-2019/vertical-tabs.gif" alt-text="Animacja, która pokazuje pionowe karty dokumentów w akcji":::

::: moniker-end

#### <a name="tab-groups"></a>Grupy kart

Grupy kart rozszerzają możliwość zarządzania ograniczonym obszarem roboczym podczas pracy z co najmniej dwoma otwartymi dokumentami w idee IDE. Wiele okien dokumentów i okien narzędzi można organizować w pionowe lub poziome grupy kart i mieszać dokumenty z jednej grupy kart do innej.

### <a name="toolbars"></a>Paski narzędzi

Paski narzędzi można rozmieścić, przeciągając je do miejsca, w którym chcesz, lub przy użyciu **okna** dialogowego Dostosowywanie. Aby uzyskać więcej informacji na temat sposobu zmieniania położenia i dostosowywania pasków narzędzi, zobacz [Jak dostosować menu i paski narzędzi.](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)

## <a name="arrange-and-dock-windows"></a>Rozmieszczanie i dokowanie okien

Okno dokumentu lub okno narzędzi można *zadokować,* tak aby zawierało położenie i rozmiar w ramce okna środowiska IDE. Można również umieścić go jako oddzielne okno zmiennoprzecincze, które znajduje się poza ideą IDE.

Okno narzędzi można zadokować w dowolnym miejscu wewnątrz ramki IDE. Niektóre okna narzędzi można również zadokowania jako okna z kartami w ramce edytora. Ponadto można dokować okna dokumentów w ramce edytora i przypiąć je do bieżącej pozycji w kolejności tabuł.

Można również dokować wiele okien, aby zmiennoprzecinkowy w *całości* lub poza ideą. Okna narzędzi mogą być również ukryte lub zminimalizowane.

Okna można rozmieścić w następujący sposób:

- Przypnij okna dokumentów z lewej strony listy kart.

- Okna dokowania kart w ramce edycji.

- Zadokuj okna narzędzi do krawędzi ramki w idee.

- Okna dokumentów lub narzędzi zmiennoprzecinkowy na lub na zewnątrz środowiska IDE.

- Ukryj okna narzędzi wzdłuż krawędzi środowiska IDE.

- Wyświetlanie okien na różnych monitorach.

- Resetowanie położenia okna do domyślnego układu lub zapisanego układu niestandardowego.

Aby rozmieścić okna narzędzi i dokumentów, możesz umieścić kursor na pasku tytułu okna, a następnie przeciągnąć go do miejsca, w którym chcesz. Możesz też kliknąć prawym przyciskiem myszy pasek tytułu okna, aby użyć jego menu kontekstowego, lub użyć poleceń w menu **Okno.**

### <a name="dock-windows"></a>Okna Docka

Po kliknięciu i przeciągnięciu paska tytułu okna narzędzi lub karty okna dokumentu zostanie wyświetlony romb przewodnika. Podczas operacji przeciągania, gdy kursor myszy znajduje się nad jedną ze strzałek w rombu, zostanie wyświetlony zacieniony obszar, w którym będzie wyświetlane miejsce, w którym okno zostanie zadokowane po zwolnieniu przycisku myszy.

Aby przenieść okno dokowalne bez przyciągania go na miejsce, naciśnij klawisz **Ctrl** podczas przeciągania okna.

Aby przywrócić okno narzędzia lub okno dokumentu do najnowszej zadokowane lokalizacji, naciśnij klawisz **Ctrl,** klikając dwukrotnie pasek tytułu lub kartę okna.

Na poniższej ilustracji przedstawiono romb przewodnika dla okien dokumentów, które można zadokować tylko w ramce edycji:

![Romb przewodnika po oknie dokumentu](../ide/media/documentwindowguidediamonds.png)

Okna narzędzi można przypinać do jednej strony ramki w ide lub w ramce edycji. Romb przewodnika jest wyświetlany podczas przeciągania okna narzędzi do innej lokalizacji, aby ułatwić ponowne umieszczenie okna.

![Diamenty przewodnika po oknie narzędzi](../ide/media/vs10guidediamond.png)

Na poniższej **ilustracji Eksplorator rozwiązań** są zadokowane w nowej lokalizacji, która jest oznaczana niebieskim zacienionym obszarem:

![Dokowanie Eksplorator rozwiązań w nowej pozycji](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Zamykanie i automatyczne ukrywanie okien narzędzi

Okno narzędzi można zamknąć, klikając znak **X** w prawym górnym rogu paska tytułu. Aby ponownie otworzyć okno, użyj jego skrótu klawiaturowego lub polecenia menu. Okna narzędzi obsługują funkcję automatycznego *ukrywania,* która powoduje wysuwkę okna podczas korzystania z innego okna. Gdy okno jest automatycznie ukrywane, jego nazwa jest wyświetlana na karcie na krawędzi środowiska IDE. Aby ponownie użyć okna, wskaż kartę, aby okno wsuwało się z powrotem do widoku.

![Autoukrywanie](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Aby określić, czy funkcja automatycznego ukrywania działa na oknach  narzędzi indywidualnie, czy jako grupy zadokowane, zaznacz lub wyczyść przycisk Automatycznie ukryj ma wpływ tylko na aktywne okna narzędzi w **oknie dialogowym** Opcje. Aby uzyskać więcej informacji, zobacz [Ogólne, Środowisko, Opcje okno dialogowe](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna narzędzi, które mają włączoną funkcję automatycznego ukrywania, mogą tymczasowo przesuwać się do widoku, gdy okno ma fokus. Aby ponownie ukryć okno, wybierz element poza bieżącym oknem. Gdy okno utraci fokus, wysuwa się z powrotem z widoku.

### <a name="use-a-second-monitor"></a>Używanie drugiego monitora

Jeśli masz drugi monitor i system operacyjny go obsługuje, możesz wybrać monitor, który wyświetla okno. Można nawet grupować wiele okien w *szprychy na* innych monitorach.

> [!TIP]
> Można utworzyć wiele wystąpień Eksplorator rozwiązań **i** przenieść je do innego monitora. Kliknij prawym przyciskiem myszy okno i wybierz pozycję **Nowy Eksplorator rozwiązań widok.** Możesz przywrócić wszystkie okna do oryginalnego monitora, klikając dwukrotnie podczas wybierania **klawisza Ctrl.**

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetowanie, nazywanie i przełączanie między układami okien

Możesz przywrócić ideę do oryginalnego układu okna dla kolekcji ustawień za pomocą polecenia **Resetuj układ** okna. Po uruchomieniu tego polecenia są uruchamiane następujące akcje:

- Wszystkie okna są przenoszone do ich domyślnych pozycji.

- Okna zamknięte w domyślnym układzie okien są zamykane.

- Otwarte okna w domyślnym układzie okien są otwierane.

### <a name="create-and-save-custom-layouts"></a>Tworzenie i zapisywanie układów niestandardowych

Visual Studio umożliwia zapisanie maksymalnie 10 niestandardowych układów okien i szybkie przełączanie się między nimi. Poniższe kroki pokazują, jak tworzyć, zapisywać, wywoływać i zarządzać układami niestandardowymi, które mogą korzystać z wielu monitorów z zadokowanych i przestawnych okien narzędzi.

Najpierw utwórz rozwiązanie testowe, które ma dwa projekty, z których każdy ma inny optymalny układ.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Tworzenie projektu interfejsu użytkownika i dostosowywanie układu

::: moniker range="vs-2017"

1. Utwórz nowy projekt aplikacji **WPF w języku** C#. Wyobraź sobie, że w tym projekcie będziesz oowywają interfejs użytkownika. Chcesz zmaksymalizować miejsce w oknie projektanta i przenieść inne okna narzędzi poza drogę.

::: moniker-end

::: moniker range=">=vs-2019"

1. Utwórz nowy projekt aplikacji **WPF w języku** C#. Wyobraź sobie, że w tym projekcie będziesz oowywają interfejs użytkownika. Chcesz zmaksymalizować miejsce w oknie projektanta i przenieść inne okna narzędzi poza drogę.

::: moniker-end

2. Jeśli masz wiele monitorów, **ściągnij okno Eksplorator rozwiązań** i okno **Właściwości** do drugiego monitora. W jednym systemie monitorowania spróbuj zamknąć wszystkie okna z wyjątkiem projektanta.

3. Naciśnij **klawisze Ctrl** + **Alt** + **X,** aby wyświetlić **okno przybornika.** Jeśli okno jest zadokowane, przeciągnij je tak, aby unosiło się w miejscu, w którym chcesz je umieścić.

4. Naciśnij **klawisz F5,** aby Visual Studio tryb debugowania. Dostosuj położenie okien debugowania **Autos,** **Call Stack** i **Output** w sposób, w jaki chcesz. Układ, który utworzysz, będzie miał zastosowanie zarówno do trybu edycji, jak i debugowania.

5. Jeśli układy w trybie debugowania i edycji są takie, jak chcesz, wybierz pozycję **Układ**  >  **okna Zapisz okno.** Wywołaj ten układ "Projektant".

     Zwróć uwagę, że nowy układ ma przypisany następny skrót klawiaturowy z zastrzeżonej listy **Ctrl** + **Alt** + **1...0.**

#### <a name="create-a-database-project-and-layout"></a>Tworzenie projektu i układu bazy danych

1. Dodaj nowy **projekt SQL Server Database** do rozwiązania.

2. Kliknij prawym przyciskiem myszy nowy projekt w **programie Eksplorator rozwiązań** a następnie wybierz **pozycję Wyświetl w Eksplorator obiektów**. Zostanie wyświetlone **okno Eksplorator obiektów SQL Server,** które umożliwia dostęp do tabel, widoków i innych obiektów w bazie danych. Możesz ustawić to okno jako zmiennoprzecinkowy lub pozostawić je zadokowane. Dostosuj okna innych narzędzi tak, jak chcesz. Aby uzyskać dodatkowy realizm, możesz dodać rzeczywistą bazę danych, ale nie jest to konieczne w tym przewodniku.

3. Gdy układ jest odpowiedni, z menu głównego wybierz pozycję **Układ** okna  >  **Zapisz okno.** Wywołaj ten układ "PROJEKT BAZY DANYCH". (Nie będziemy zawłaszczać układem trybu debugowania dla tego projektu).

#### <a name="switch-between-the-layouts"></a>Przełączanie między układami

Aby przełączać się między układami, użyj skrótów klawiaturowych lub z menu głównego wybierz pozycję **Zastosuj**  >  **układ okna okna.**

![Menu układu okna Zastosuj](../ide/media/vs2015_applywindowlayout.png)

Po zastosowaniu układu interfejsu użytkownika zwróć uwagę, jak układ jest zachowywany zarówno w trybie edycji, jak i w trybie debugowania.

Jeśli w pracy masz konfigurację wielu monitorów i laptop z jednym monitorem, możesz tworzyć układy zoptymalizowane pod kątem poszczególnych maszyn.

> [!NOTE]
> Jeśli zastosujemy układ z wieloma monitorami w systemie z jednym monitorem, przestawne okna umieszczone na drugim monitorze będą teraz ukryte za Visual Studio monitorem. Te okna można przyblizyć do przodu, naciskając klawisze **Alt + Tab**. Jeśli później otworzysz Visual Studio z wieloma monitorami, możesz przywrócić okna do ich określonych pozycji, stosując ponownie układ.

#### <a name="manage-and-roam-your-layouts"></a>Zarządzanie układami i zarządzanie nimi

Możesz usunąć, zmienić nazwę lub zmienić kolejność układu niestandardowego, wybierając pozycję **Okna**  >  **Zarządzaj układami okien.** Jeśli przeniesiesz układ, powiązanie klucza zostanie automatycznie dostosowane w celu odzwierciedlenia nowej pozycji na liście. Powiązań nie można modyfikować w inny sposób, dlatego można przechowywać maksymalnie 10 układów jednocześnie.

![Zarządzanie układami okien](../ide/media/managewindowlayouts.png)

Aby przypomnieć sobie, do którego układu jest przypisany skrót klawiaturowy, wybierz pozycję **Zastosuj**  >  **układ okna** okna.

Te układy automatycznie są używane Visual Studio różnych wersjach, a także między wystąpieniami programu Blend na oddzielnych maszynach i z dowolnej wersji Express do dowolnej innej organizacji express. Jednak układy nie są połączone między Visual Studio, Blend i Express.

## <a name="see-also"></a>Zobacz też

- [Jak poruszać się w idee](../ide/how-to-move-around-in-the-visual-studio-ide.md)

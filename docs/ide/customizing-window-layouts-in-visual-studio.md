---
title: Dostosowywanie układów okien
description: Dowiedz się, jak dostosować cechy, które są widziane w systemie Windows w celu utworzenia układów, które działają najlepiej dla różnych przepływów pracy deweloperskiej
ms.custom: SEO-VS-2020
ms.date: 07/31/2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c433a6faf3eab9dd959cc25f26033c74852c0899
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006669"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Dostosowywanie układów okien w programie Visual Studio

W programie Visual Studio można dostosować położenie, rozmiar i zachowanie systemu Windows w celu utworzenia układów okna, które działają najlepiej dla różnych przepływów pracy deweloperskiej. Po dostosowaniu układu środowisko IDE zapamiętuje go. Na przykład jeśli zmienisz lokalizację dokowania **Eksplorator rozwiązań** a następnie zamkniesz program Visual Studio, następnym razem, gdy otworzysz program Visual Studio, nawet jeśli pracujesz na innym komputerze, **Eksplorator rozwiązań** zostanie zadokowany w tej samej lokalizacji.

Możesz również nazwać i zapisać niestandardowy układ, a następnie przełączać się między układami za pomocą jednego polecenia. Na przykład można utworzyć układ do edycji i układu do debugowania oraz przełączać **się między** nimi przy użyciu  >  polecenia menu **Układ okna stosowanie** .

## <a name="tool-and-document-windows"></a>Okna narzędzi i dokumentów

Środowisko IDE ma dwa podstawowe typy okien, okna *narzędzi* i *okna dokumentów*. Okna narzędzi obejmują **Eksplorator rozwiązań**, **Eksplorator serwera**, **okno dane wyjściowe**, **Lista błędów**, projektantów, okien debugera i tak dalej. Okna dokumentów zawierają pliki kodu źródłowego, dowolne pliki tekstowe, pliki konfiguracji i tak dalej. Rozmiar okien narzędzi można zmienić i przeciągnąć je na pasku tytułu. Okna dokumentów można przeciągnąć przez ich kartę. Kliknij prawym przyciskiem myszy kartę lub pasek tytułu, aby ustawić inne opcje okna.

Menu **okno** zawiera opcje dokowania, zmiennoprzecinkowe i ukrywające okna w środowisku IDE. Kliknij prawym przyciskiem myszy kartę okna lub pasek tytułu, aby wyświetlić dodatkowe opcje dla danego okna. Można wyświetlić więcej niż jedno wystąpienie niektórych okien narzędzi naraz. Można na przykład wyświetlić więcej niż jedno okno przeglądarki sieci Web i utworzyć dodatkowe wystąpienia niektórych okien narzędzi, wybierając pozycję **nowe okno** w menu **okno** .

### <a name="split-windows"></a>Podziel okna

W przypadku konieczności wyświetlania lub edytowania dwóch lokalizacji jednocześnie w dokumencie można podzielić okna. Aby podzielić dokument na dwa osobne sekcje, kliknij przycisk **Podziel** w menu **okno** . Kliknij pozycję **Usuń podział** w menu **okno** , aby przywrócić pojedynczy widok.

### <a name="tabs"></a>Karty

Karty umożliwiają rozmieszczenie układu na kilka różnych sposobów. Na przykład możesz wyświetlić podgląd pliku w edytorze bez otwierania pliku, możesz grupować karty i nie tylko.

#### <a name="preview-tab-document-windows"></a>Karta Podgląd (okna dokumentów)

Na karcie **Podgląd** można wyświetlić pliki w edytorze bez ich otwierania. Możesz wyświetlić podgląd plików, wybierając je w **Eksplorator rozwiązań** podczas debugowania, gdy przejdziesz do plików, z **Przejdź do definicji**, a następnie przeglądając wyniki wyszukiwania. Pliki w wersji zapoznawczej są wyświetlane na karcie po prawej stronie karty dokumentu. Plik zostanie otwarty do edycji w przypadku jego modyfikacji lub wybrania opcji  **Otwórz**.

::: moniker range="vs-2019"

#### <a name="vertical-document-tabs"></a>Pionowe karty dokumentu

**[Nowość w wersji 16,4](/visualstudio/releases/2019/release-notes-v16.4/)**: dodaliśmy jedną z pierwszych żądań funkcji, [kart dokumentu pionowego](https://developercommunity.visualstudio.com/idea/467369/vertical-group-tab.html)w wersji programu Visual Studio 2019 wersja 16,4. Teraz możesz zarządzać kartami dokumentów na liście pionowej po lewej lub prawej stronie edytora.

Możesz zastosować pionowe karty dokumentu w następujący sposób:

- Wybierz **Tools**  >  **Opcje** narzędzia  >  karty **środowisko**  >  **i okna** z paska menu. Następnie w kontrolce **Ustawianie układu karty** wybierz z listy rozwijanej opcję z **góry**, z **lewej** lub z **prawej strony** .

- Kliknij prawym przyciskiem myszy kartę, wybierz polecenie **Ustaw układ karty**, a następnie wybierz opcję w **lewo** lub w **prawo**. (Aby przywrócić domyślne położenie kart, wybierz pozycję **Top**).

    :::image type="content" source="./media/vs-2019/vertical-tabs.gif" alt-text="Animacja pokazująca pionowe karty dokumentu w akcji":::

::: moniker-end

#### <a name="tab-groups"></a>Grupy kart

Grupy kart rozszerzają możliwość zarządzania obszarem roboczym ograniczonym podczas pracy z co najmniej dwoma otwartymi dokumentami w środowisku IDE. Można organizować okna z wieloma dokumentami i oknami narzędzi do pionowych lub poziomych grup kart i losowo przeciągać dokumenty z jednej grupy kart do innej.

### <a name="toolbars"></a>Paski narzędzi

Paski narzędzi można rozmieścić, przeciągając je do dowolnego miejsca lub korzystając z okna dialogowego **Dostosowywanie** . Aby uzyskać więcej informacji na temat sposobu pozycjonowania i dostosowywania pasków narzędzi, zobacz [How to: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Rozmieszczanie i Dokowanie okien

Okno dokumentu lub okno narzędzi może być *zadokowane*, tak aby miało położenie i rozmiar w obrębie ramki okna środowiska IDE. Możesz również ustawić ją jako oddzielne okno przestawne, które jest poza IDE.

Można zadokować okno narzędzia w dowolnym miejscu wewnątrz ramki IDE. Możesz również zadokować niektóre okna narzędzi jako okna z kartami w ramce edytora. I można zadokować okna dokumentów w ramce edytora i można przypiąć je do ich bieżącej pozycji w kolejności tabulacji.

Możesz również zadokować wiele okien do pływania w miejscu do *lub na zewnątrz* IDE. Okna narzędzi można także ukryć lub zminimalizować.

System Windows można rozmieścić w następujący sposób:

- Przypnij okna dokumentów z lewej strony karty.

- Karta — dokowanie systemu Windows do ramki edycji.

- Dokowanie okien narzędzi do krawędzi ramki w IDE.

- Przestaw okna dokumentu lub narzędzia na zewnątrz lub poza IDE.

- Ukryj okna narzędzi wzdłuż krawędzi IDE.

- Wyświetlanie okien na różnych monitorach.

- Resetowanie położenia okna do układu domyślnego lub do zapisanego układu niestandardowego.

Aby rozmieścić okna narzędzi i dokumentów, możesz umieścić kursor na pasku tytułu okna, a następnie przeciągnąć je do żądanego miejsca. Alternatywnie możesz kliknąć prawym przyciskiem myszy pasek tytułu okna, aby użyć jego menu kontekstowego lub użyć poleceń z menu **okno** .

### <a name="dock-windows"></a>Okna dokowania

Gdy klikniesz i przeciągniesz pasek tytułu okna narzędzi lub kartę okna dokumentu, pojawi się romb przewodnika. Podczas operacji przeciągania, gdy wskaźnik myszy znajduje się nad jedną strzałką w karo, zostanie wyświetlony zacieniowany obszar pokazujący, gdzie okno zostanie zadokowane po zwolnieniu przycisku myszy.

Aby przenieść okno było dokować bez przyciągania do miejsca, naciśnij klawisz **Ctrl** podczas przeciągania okna.

Aby zwrócić okno narzędzi lub okno dokumentu do jego najnowszej lokalizacji zadokowanej, naciśnij klawisz **Ctrl** , a następnie kliknij dwukrotnie pasek tytułu lub kartę okna.

Na poniższej ilustracji przedstawiono romb przewodnika dla okien dokumentów, który można zadokować tylko w obrębie ramki edycji:

![Romb przewodnika okna dokumentu](../ide/media/documentwindowguidediamonds.png)

Okna narzędzi można dołączać do jednej strony ramki w IDE lub wewnątrz ramki edycji. Romb przewodnik pojawia się po przeciągnięciu okna narzędzia do innej lokalizacji, aby ułatwić zadokowanie okna.

![Przewodnik po oknach narzędzi](../ide/media/vs10guidediamond.png)

Na poniższej ilustracji przedstawiono **Eksplorator rozwiązań** zadokowane w nowej lokalizacji, która została odtworzona przez niebieską powierzchnię:

![Dokowanie Eksplorator rozwiązań w nowej pozycji](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Zamknij i Autoukrywanie okien narzędzi

Możesz zamknąć okno narzędzi, klikając **symbol X** w prawym górnym rogu paska tytułu. Aby ponownie otworzyć okno, użyj skrótu klawiaturowego lub polecenia menu. Okna narzędzi obsługują funkcję o nazwie *Autohide*, która powoduje, że okno jest w sposób nieobecny, gdy używasz innego okna. Gdy okno jest Autoukrywanie, jego nazwa jest wyświetlana na karcie na krawędzi IDE. Aby ponownie użyć tego okna, wskaż kartę, aby wyświetlić ponownie slajdy okna.

![Ukryj Autoukrywanie](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Aby ustawić, czy Autoukrywanie działa w oknach narzędzi indywidualnie, czy jako zadokowanych, zaznacz lub wyczyść pole wyboru **Autoukrywanie, które ma wpływ na aktywne okna narzędzi tylko** w oknie dialogowym **Opcje** . Aby uzyskać więcej informacji, zobacz [Ogólne, środowisko, Opcje — okno dialogowe](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna narzędzi, które mają włączoną funkcję Autoukrywanie, mogą tymczasowo przesuwać się do widoku, gdy okno ma fokus. Aby ponownie ukryć okno, wybierz element poza bieżącym oknem. Gdy okno utraci fokus, slajdy są wychodzące z widoku.

### <a name="use-a-second-monitor"></a>Użyj drugiego monitora

Jeśli masz drugi monitor i obsługuje go system operacyjny, możesz wybrać monitor wyświetla okno. Można nawet grupować jednocześnie wiele okien w *tratwach* na innych monitorach.

> [!TIP]
> Można utworzyć wiele wystąpień **Eksplorator rozwiązań** i przenieść je do innego monitora. Kliknij okno prawym przyciskiem myszy i wybierz polecenie **Nowy widok Eksplorator rozwiązań**. Możesz przywrócić wszystkie okna z powrotem do oryginalnego monitora, dwukrotnie klikając podczas wybierania klawisza **Ctrl** .

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetowanie, nazwa i przełączanie między układami okien

Można przywrócić IDE do oryginalnego układu okna dla kolekcji ustawień przy użyciu polecenia **Zresetuj układ okna** . Po uruchomieniu tego polecenia są wykonywane następujące akcje:

- Wszystkie okna są przenoszone do ich domyślnych pozycji.

- Okna, które są zamknięte w domyślnym układzie okna, są zamknięte.

- Okna, które są otwarte w domyślnym układzie okna, są otwarte.

### <a name="create-and-save-custom-layouts"></a>Tworzenie i zapisywanie układów niestandardowych

Program Visual Studio umożliwia zapisywanie do 10 niestandardowych układów okien i szybkie przełączanie się między nimi. W poniższych krokach pokazano, jak tworzyć, zapisywać i wywoływać układy niestandardowe oraz zarządzać nimi, korzystając z wielu monitorów z oknami narzędzi zadokowanych i przestawnych.

Najpierw utwórz rozwiązanie testowe, które ma dwa projekty, każdy z innym optymalnym układem.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Tworzenie projektu interfejsu użytkownika i dostosowywanie układu

1. Utwórz nowy projekt **aplikacji WPF** w języku C#. Załóżmy, że w tym projekcie utworzysz interfejs użytkownika. Chcesz zmaksymalizować miejsce dla okna projektanta i przenieść inne okna narzędzi w sposób nieobecny.

2. Jeśli masz wiele monitorów, wyciągnij okno **Eksplorator rozwiązań** i okno **Właściwości** do drugiego monitora. W jednym systemie monitorowania Spróbuj zamknąć wszystkie okna z wyjątkiem projektanta.

3. Naciśnij **klawisze CTRL** + **Alt** + **X** , aby wyświetlić okno **Przybornik** . Jeśli okno jest zadokowane, przeciągnij je tak, aby było przepływać w miejscu, gdzie chcesz go umieścić.

4. Naciśnij klawisz **F5** , aby umieścić program Visual Studio w trybie debugowania. Dostosuj **pozycję okien,** **stosu wywołań** i debugowania **danych wyjściowych** w żądany sposób. Układ, który zamierzasz utworzyć, będzie stosowany do trybu edycji i trybu debugowania.

5. Gdy układy w trybie debugowania i trybie edycji są odpowiednie, wybierz kolejno opcje okno, **Window**  >  **Układ okna**. Wywołaj ten układ "Projektant".

     Zwróć uwagę, że nowy układ jest przypisany do następnego skrótu klawiaturowego z listy zarezerwowanych **Ctrl** + **Alt** + **1... 0**.

#### <a name="create-a-database-project-and-layout"></a>Tworzenie projektu i układu bazy danych

1. Dodaj nowy projekt **bazy danych SQL Server** do rozwiązania.

2. Kliknij prawym przyciskiem myszy nowy projekt w **Eksplorator rozwiązań** a następnie wybierz polecenie **Widok w Eksplorator obiektów**. Spowoduje to wyświetlenie okna **Eksplorator obiektów SQL Server** , które umożliwia dostęp do tabel, widoków i innych obiektów w bazie danych. Można to zrobić w tym oknie lub pozostawić zadokowane. Dostosuj inne okna narzędzi w odpowiedni sposób. W przypadku dodanej wartości rzeczywistej można dodać rzeczywistą bazę danych, ale nie jest to konieczne w tym instruktażu.

3. Gdy układ jest odpowiedni, z menu głównego wybierz kolejno opcje **okno**  >  **Zapisz układ okna**. Wywołaj ten układ "DB Project". (Nie bother z układem trybu debugowania dla tego projektu).

#### <a name="switch-between-the-layouts"></a>Przełączenie między układami

Aby przełączać się między układami, użyj skrótów klawiaturowych lub z menu głównego wybierz pozycję **okno**  >  **Zastosuj Układ okna**.

![Menu Zastosuj Układ okna](../ide/media/vs2015_applywindowlayout.png)

Po zastosowaniu układu interfejsu użytkownika należy zwrócić uwagę, jak układ jest zachowywany zarówno w trybie edycji, jak i w trybie debugowania.

Jeśli masz konfigurację z wieloma monitorami w pracy i pojedynczy laptop w domu, możesz utworzyć układy zoptymalizowane pod kątem poszczególnych maszyn.

> [!NOTE]
> W przypadku zastosowania układu wielomonitorowego w systemie z jednym monitorem przestawne okna, które zostały umieszczone na drugim monitorze, zostaną teraz ukryte za oknem programu Visual Studio. Możesz przenieść te okna na wierzch, naciskając **klawisze Alt + Tab**. Jeśli później otworzysz program Visual Studio z wieloma monitorami, możesz przywrócić te okna do określonych pozycji przez ponowne zastosowanie układu.

#### <a name="manage-and-roam-your-layouts"></a>Zarządzanie układami i poruszanie się po nich

Układ niestandardowy można usunąć, zmienić jego nazwę, wybierając kolejno **okna**  >  **Zarządzanie układami okien**. Przeniesienie układu powoduje automatyczne dostosowanie powiązania klucza w celu odzwierciedlenia nowej pozycji na liście. Powiązania nie mogą być modyfikowane w inny sposób, więc można przechowywać maksymalnie 10 układów jednocześnie.

![Zarządzanie układami okien](../ide/media/managewindowlayouts.png)

Aby przypomnić, który skrót klawiaturowy jest przypisany do układu, wybierz pozycję **okno**  >  **Zastosuj Układ okna**.

Te układy są automatycznie przenoszone między wersjami programu Visual Studio, a także między wystąpieniami Blend na oddzielnych maszynach i w dowolnej innej organizacji Express Edition. Jednak układy nie poruszają się w programie Visual Studio, Blend i Express.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: poruszanie się w środowisku IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)

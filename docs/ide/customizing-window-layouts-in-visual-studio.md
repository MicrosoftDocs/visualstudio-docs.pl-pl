---
title: Dostosowywanie układów okien
ms.date: 01/23/2017
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
ms.openlocfilehash: c1963c76b67eaedea4cdf013739c112275ecffb2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596713"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Dostosowywanie układów okien w programie Visual Studio

W programie Visual Studio można dostosować położenie, rozmiar i zachowanie okien, aby utworzyć układy okien, które najlepiej działają dla różnych przepływów pracy programowania. Podczas dostosowywania układu IDE zapamiętuje go. Na przykład jeśli zmienisz lokalizację **dokującą Eksploratora rozwiązań,** a następnie zamkniesz program Visual Studio przy następnym otwarciu programu Visual Studio, nawet jeśli pracujesz na innym komputerze, **Eksplorator rozwiązań** zostanie zadokowany w tej samej lokalizacji.

Można również nadać nazwę i zapisać układ niestandardowy, a następnie przełączać się między układami za pomocą jednego polecenia. Można na przykład utworzyć układ do edycji i układ do debugowania i przełączać się między nimi za pomocą polecenia menu**Menu Rozmieszczenia** **okna.** > 

## <a name="kinds-of-windows"></a>Rodzaje okien

### <a name="tool-and-document-windows"></a>Okna narzędzi i dokumentów

IDE ma dwa podstawowe typy okien, *okna narzędzi* i *okna dokumentów.* Okna narzędzi obejmują **Eksplorator rozwiązań,** **Eksplorator** **serwerów, okno** **wyjściowe, listę błędów,** projektantów, okna debugera itd. Okna dokumentów zawierają pliki kodu źródłowego, dowolne pliki tekstowe, pliki konfiguracyjne itd. Okna narzędzi można zmieścić i przeciągnąć przez pasek tytułu. Okna dokumentów można przeciągać po karcie. Kliknij prawym przyciskiem myszy kartę lub pasek tytułu, aby ustawić inne opcje w oknie.

Menu **Okno** zawiera opcje dokowania, przestawne i ukrywanie okien w IDE. Kliknij prawym przyciskiem myszy kartę okna lub pasek tytułu, aby wyświetlić dodatkowe opcje dla tego określonego okna. Jednocześnie można wyświetlać więcej niż jedno wystąpienie niektórych okien narzędzi. Na przykład można wyświetlić więcej niż jedno okno przeglądarki sieci Web i można utworzyć dodatkowe wystąpienia niektórych okien narzędzi, wybierając **nowe okno** w menu **Okno.**

### <a name="preview-tab-document-windows"></a>Karta Podgląd (okna dokumentów)

Na karcie **Podgląd** można wyświetlać pliki w edytorze bez ich otwierania. Można wyświetlić podgląd plików, wybierając je w **Eksploratorze rozwiązań**podczas debugowania podczas przechodzenia do plików, za pomocą **funkcji Przejdź do definicji**i podczas przeglądania wyników wyszukiwania. Pliki podglądu są wyświetlane na karcie po prawej stronie karty dokumentu. Plik zostanie otwarty do edycji, jeśli go zmodyfikujesz lub wybierzesz **polecenie Otwórz**.

### <a name="tab-groups"></a>Grupy kart

Grupy kart rozszerzają możliwość zarządzania ograniczonym obszarem roboczym podczas pracy z co najmniej dwoma otwartymi dokumentami w ide. Można organizować wiele okien dokumentów i okien narzędzi w pionowe lub poziome grupy kart i losować dokumenty z jednej grupy kart do drugiej.

### <a name="split-windows"></a>Okna dzielone

Gdy w dokumencie trzeba wyświetlić lub edytować dwie lokalizacje naraz, można podzielić okna. Aby podzielić dokument na dwie sekcje niezależnie przewijane, kliknij polecenie **Podziel** w menu **Okno.** Kliknij **polecenie Usuń podział** w menu **Okno,** aby przywrócić pojedynczy widok.

### <a name="toolbars"></a>Paski narzędzi

Paski narzędzi można rozmieszczać przez przeciąganie lub korzystanie z okna dialogowego **Dostosowywanie.** Aby uzyskać więcej informacji na temat pozycjonowania i dostosowywania pasków narzędzi, zobacz [Jak: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Rozmieszczanie i dokowanie okien

Okno dokumentu lub okno narzędzia może być *zadokowane,* tak aby miało położenie i rozmiar w ramce okna IDE lub pływające jako oddzielne okno niezależne od IDE. Okna narzędzi mogą być zadokowane w dowolnym miejscu wewnątrz ramki IDE; niektóre okna narzędzi mogą być zadokowane jako okna z kartami w ramce edytora. Okna dokumentów mogą być zadokowane w ramce edytora i można je przypiąć do ich bieżącej pozycji w kolejności tabulacji. Można zadokować wiele okien, aby unosić się razem w *tratwie* nad lub poza IDE. Okna narzędzi mogą być również ukryte lub zminimalizowane.

Okna można rozmieścić w następujący sposób:

- Dobrze przypinaj okna dokumentów po lewej stronie karty.

- Okna dokowania kart do ramki edycji.

- Dokowanie okien narzędzi do krawędzi ramki w IDE.

- Float okna dokumentu lub narzędzia nad lub poza IDE.

- Ukryj okna narzędzi wzdłuż krawędzi IDE.

- Wyświetlanie okien na różnych monitorach.

- Resetowanie umiejscowienia okna do układu domyślnego lub do zapisanego układu niestandardowego.

Rozmieść okna narzędzi i dokumentów, przeciągając, używając poleceń w menu **Okno** lub klikając prawym przyciskiem myszy pasek tytułu okna, które ma być rozmieszczone.

### <a name="dock-windows"></a>Okna dokowania

Po kliknięciu i przeciągnięciu paska tytułu okna narzędzia lub karty okna dokumentu pojawi się romb prowadnicy. Podczas operacji przeciągania, gdy kursor myszy znajduje się nad jedną ze strzałek w rombie, pojawi się zacieniony obszar, który pokaże, gdzie okno zostanie zadokowane, jeśli zwolnisz teraz przycisk myszy.

Aby przenieść okno dokowane bez przyciągania go na miejsce, naciśnij klawisz **Ctrl** podczas przeciągania okna.

Aby przywrócić okno narzędzia lub okno dokumentu do ostatnio zadokowanego miejsca, naciśnij klawisz **Ctrl** podczas dwukrotnego kliknięcia paska tytułu lub karty okna.

Na poniższej ilustracji przedstawiono romb prowadnicy dla okien dokumentów, które można zadokować tylko w ramce edycji:

![Diament prowadnicy okien dokumentu](../ide/media/documentwindowguidediamonds.png)

Okna narzędzi mogą być mocowane z jednej strony ramki w ŚRODOWISKU IDE lub w ramce edycyjnej. Po przeciągnięciu okna narzędzia w inne miejsce pojawia się prowadnik, który ułatwia ponowne zatrzaśnięcie okna.

![Diamenty prowadnicy okien narzędzi](../ide/media/vs10guidediamond.png)

Na poniższej ilustracji pokazano, że **Eksplorator rozwiązań** jest zadokowany w nowej lokalizacji, która jest wyznaczana przez niebieski obszar cieniowany:

![Eksplorator rozwiązań dokowania w nowej pozycji](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Zamykanie i automatyczne ukrywanie okien narzędzi

Okno narzędzia można zamknąć, klikając **x** w prawym górnym rogu paska tytułu. Aby ponownie otworzyć okno, użyj skrótu klawiaturowego lub polecenia menu. Okna narzędzi obsługują funkcję o nazwie *automatyczne ukrywanie*, co powoduje, że okno wysuwa się z drogi podczas korzystania z innego okna. Gdy okno jest autohidden, jego nazwa pojawia się na karcie na krawędzi IDE. Aby ponownie użyć okna, wskaż kartę, aby okno przesunął się z powrotem do widoku.

![Autoukrywanie](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Aby ustawić, czy automatyczne ukrywanie działa w oknach narzędzi indywidualnie czy jako zadokowane grupy, zaznacz lub **wyczyść przycisk Automatyczne ukrywanie wpływa na aktywne okna narzędzi tylko** w oknie dialogowym **Opcje.** Aby uzyskać więcej informacji, zobacz [Ogólne, Środowisko, Opcje okna dialogowego](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna narzędzi, w których włączono automatyczne ukrywanie, mogą tymczasowo przesunąć się do widoku, gdy okno ma fokus. Aby ponownie ukryć okno, zaznacz element poza bieżącym oknem. Gdy okno traci fokus, wysuwa się z widoku.

### <a name="specifying-a-second-monitor"></a>Określanie drugiego monitora

Jeśli masz drugi monitor, a system operacyjny go obsługuje, możesz wybrać, który monitor wyświetla okno. Możesz nawet zgrupować wiele okien w *tratwach* na innych monitorach.

> [!TIP]
> Można utworzyć wiele wystąpień **Eksploratora rozwiązań** i przenieść je na inny monitor. Kliknij prawym przyciskiem myszy okno i wybierz polecenie **Widok Eksploratora nowych rozwiązań**. Wszystkie okna można przywrócić do oryginalnego monitora, klikając dwukrotnie, wybierając klawisz **Ctrl.**

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetowanie, nazywanie i przełączanie między układami okien

IDE można przywrócić do oryginalnego układu okna dla kolekcji ustawień za pomocą polecenia **Resetuj układ okna.** Po uruchomieniu tego polecenia występują następujące akcje:

- Wszystkie okna są przenoszone do ich domyślnych pozycji.

- Okna zamknięte w domyślnym układzie okna są zamknięte.

- Okna otwarte w domyślnym układzie okna są otwierane.

### <a name="create-and-save-custom-layouts"></a>Tworzenie i zapisywanie układów niestandardowych

Visual Studio umożliwia zapisanie do 10 niestandardowych układów okien i szybkie przełączanie się między nimi. Poniższe kroki pokazują, jak tworzyć, zapisywać, wywoływać i zarządzać niestandardowymi układami, które wykorzystują wiele monitorów z zadokowanymi i przestawnymi oknami narzędzi.

Najpierw utwórz rozwiązanie testowe, które ma dwa projekty, każdy z innym optymalnym układem.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Tworzenie projektu interfejsu użytkownika i dostosowywanie układu

1. Utwórz nowy projekt **aplikacji WPF** w języku C#. Wyobraź sobie, że w tym projekcie będziesz rozwijać interfejs użytkownika. Chcesz zmaksymalizować miejsce dla okna projektanta i przenieść inne okna narzędzi z drogi.

2. Jeśli masz wiele monitorów, przeciągnij okno **Eksploratora rozwiązań** i okno **Właściwości** do drugiego monitora. W systemie jednego monitora spróbuj zamknąć wszystkie okna z wyjątkiem projektanta.

3. Naciśnij **klawisz Ctrl**+**Alt**+**X,** aby wyświetlić okno **Przybornika.** Jeśli okno jest zadokowane, przeciągnij je tak, aby unosiło się w miejscu, w którym chcesz je umieścić.

4. Naciśnij **klawisz F5,** aby umieścić program Visual Studio w trybie debugowania. Dostosuj położenie okien **autos,** **call stack**i **output** debugowania w odpowiedni sposób. Układ, który zamierzasz utworzyć, będzie miał zastosowanie zarówno do trybu edycji, jak i trybu debugowania.

5. Gdy układy zarówno w trybie debugowania, jak i w trybie edycji są zgodne z ich potrzeby, wybierz opcję**Układ okna zapisywania** **okien** > . Nazwij ten układ "Projektant".

     Należy pamiętać, że nowy układ jest przypisany do następnego skrótu klawiaturowego z listy zastrzeżonej **Ctrl**+**Alt**+**1...0**.

#### <a name="create-a-database-project-and-layout"></a>Tworzenie projektu i układu bazy danych

1. Dodaj nowy projekt **bazy danych programu SQL Server** do rozwiązania.

2. Kliknij prawym przyciskiem myszy nowy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Wyświetl w Eksploratorze obiektów**. Spowoduje to wyświetlenie okna **Eksploratora obiektów programu SQL Server,** które umożliwia dostęp do tabel, widoków i innych obiektów w bazie danych. Możesz float to okno lub pozostawić zadokowany. Dostosuj inne okna narzędzi tak, jak chcesz. Aby uzyskać realizmu, można dodać rzeczywistą bazę danych, ale nie jest to konieczne dla tego instruktażu.

3. Gdy układ jest taki, jak chcesz, z menu głównego wybierz polecenie**Układ okna zapisywania** **okien** > . Nazwij ten układ "Projekt bazy danych". (Nie będziemy się przejmować układem trybu debugowania dla tego projektu).

#### <a name="switch-between-the-layouts"></a>Przełączanie między układami

Aby przełączać się między układami, użyj skrótów klawiaturowych lub z menu głównego wybierz **polecenie Okno** > **Zastosuj układ okna**.

![Zastosuj menu układu okna](../ide/media/vs2015_applywindowlayout.png)

Po zastosowaniu układu interfejsu użytkownika należy zwrócić uwagę na sposób zachowania układu zarówno w trybie edycji, jak i w trybie debugowania.

Jeśli masz konfigurację wielu monitorów w pracy i jeden monitor laptopa w domu, można utworzyć układy, które są zoptymalizowane dla każdego komputera.

> [!NOTE]
> Jeśli zastosujesz układ wielu monitorów w systemie z jednym monitorem, okna przestawne umieszczone na drugim monitorze będą teraz ukryte za oknem programu Visual Studio. Możesz przenieść te okna do przodu, naciskając **klawisze Alt + Tab**. Jeśli później otworzysz program Visual Studio z wieloma monitorami, można przywrócić okna do ich określonych pozycji, ponownie stosując układ.

#### <a name="manage-and-roam-your-layouts"></a>Zarządzanie układami i poruszanie nimi

Można usunąć, zmienić nazwę lub zmienić kolejność układu niestandardowego, wybierając **pozycję Zarządzanie układami** > **okien**. Jeśli przeniesiesz układ, powiązanie klawisza zostanie automatycznie dostosowane w celu odzwierciedlenia nowej pozycji na liście. Powiązania nie mogą być modyfikowane w inny sposób, a więc można przechowywać maksymalnie 10 układów naraz.

![Zarządzanie układami okien](../ide/media/managewindowlayouts.png)

Aby przypomnieć sobie, który skrót klawiaturowy jest przypisany do którego układu, wybierz polecenie **Zastosowanie okna** > **Układ okna**.

Te układy automatycznie przemieszczają się między wersjami programu Visual Studio, a także między wystąpieniami blend na oddzielnych komputerach i z dowolnej wersji expressowej do dowolnej innej organizacji Express. Jednak układy nie są przemierzane w programie Visual Studio, Blend i Express.

## <a name="see-also"></a>Zobacz też

- [Jak: Poruszanie się w ide](../ide/how-to-move-around-in-the-visual-studio-ide.md)

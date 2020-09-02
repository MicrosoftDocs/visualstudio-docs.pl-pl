---
title: Dostosowywanie układów okien
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 509ec978815ae57e548188941a8de24c5f36d77e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665838"
---
# <a name="customizing-window-layouts-in-visual-studio"></a>Dostosowywanie układów okien w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można dostosować położenie, rozmiar i zachowanie systemu Windows w celu utworzenia układów okna, które działają najlepiej dla różnych przepływów pracy deweloperskiej. Po dostosowaniu układu środowisko IDE zapamiętuje go. Na przykład jeśli zmienisz lokalizację dokowania **Eksplorator rozwiązań** a następnie zamkniesz program Visual Studio, przy następnym uruchomieniu, nawet jeśli pracujesz na innym komputerze, **Eksplorator rozwiązań** zostanie zadokowany w tej samej lokalizacji. Możesz również nadać niestandardowemu układowi nazwę i zapisać go, a następnie przełączać się między układami za pomocą jednego polecenia. Na przykład można utworzyć układ do edycji, drugi dla debugowania i przełączać się między nimi przy użyciu **okna &#124; Zastosuj Układ okna** polecenie menu.

## <a name="kinds-of-windows"></a>Rodzaje okien

### <a name="tool-and-document-windows"></a>Okna narzędzi i dokumentów
 Środowisko IDE ma dwa podstawowe typy okien, okna *narzędzi* i *okna dokumentów*. Okna narzędzi obejmują Eksplorator rozwiązań, Eksplorator serwera, Okno Dane wyjściowe, Lista błędów, projektantów, okien debugera i tak dalej. Okna dokumentów zawierają pliki kodu źródłowego, dowolne pliki tekstowe, pliki konfiguracji i tak dalej. Rozmiar okien narzędzi można zmienić i przeciągnąć je na pasku tytułu. Okna dokumentów można przeciągnąć przez ich kartę. Kliknij prawym przyciskiem myszy kartę lub pasek tytułu, aby ustawić inne opcje okna.

 Menu **okno** zawiera opcje dokowania, zmiennoprzecinkowe i ukrywające okna w IDE. Kliknij prawym przyciskiem myszy kartę okna lub pasek tytułu, aby wyświetlić dodatkowe opcje dla danego okna. Można wyświetlić więcej niż jedno wystąpienie niektórych okien narzędzi naraz. Można na przykład wyświetlić więcej niż jedno okno przeglądarki sieci Web i utworzyć dodatkowe wystąpienia niektórych okien narzędzi, wybierając pozycję **nowe okno** w menu **okno** .

### <a name="preview-tab-document-windows"></a>Karta Podgląd (okna dokumentów)
 Na karcie Podgląd można wyświetlić pliki w edytorze bez ich otwierania. Możesz wyświetlić podgląd plików, wybierając je w **Eksplorator rozwiązań**podczas debugowania, gdy przejdziesz do plików, z przejdź do definicji, a następnie przeglądając wyniki wyszukiwania. Pliki w wersji zapoznawczej są wyświetlane na karcie po prawej stronie karty dokumentu. Plik zostanie otwarty do edycji w przypadku jego modyfikacji lub wybrania **otwarte**.

### <a name="tab-groups"></a>Grupy kart
 Grupy kart umożliwiają zarządzanie obszarem roboczym ograniczonym podczas pracy z dwoma lub więcej otwartymi dokumentami w środowisku IDE. Można organizować okna z wieloma dokumentami i oknami narzędzi do pionowych lub poziomych grup kart i losowo przeciągać dokumenty z jednej grupy kart do innej.

### <a name="split-windows"></a>Podziel okna
 W przypadku konieczności wyświetlania lub edytowania dwóch lokalizacji jednocześnie w dokumencie można podzielić okna. Aby podzielić dokument na dwa osobne sekcje, kliknij przycisk **Podziel** w menu **okno** . Kliknij pozycję **Usuń podział** w menu **okno** , aby przywrócić pojedynczy widok.

### <a name="toolbars"></a>Paski narzędzi
 Paski narzędzi można rozmieścić przez przeciąganie lub użycie okna dialogowego **Dostosowywanie** . Aby uzyskać więcej informacji na temat sposobu pozycjonowania i dostosowywania pasków narzędzi, zobacz [How to: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arranging-and-docking-windows"></a>Rozmieszczanie i Dokowanie okien
 Okna dokumentów i okna narzędzi mogą być *zadokowane*, tak aby miało położenie i rozmiar w obrębie ramki okna środowiska IDE lub przestawne jako oddzielne okno niezależne od środowiska IDE. Okna narzędzi można zadokować w dowolnym miejscu wewnątrz ramki IDE; Niektóre okna narzędzi można zadokować jako okna z kartami w ramce edytora. Okna dokumentów mogą być zadokowane w obrębie ramki edytora i mogą być przypięte do ich bieżącej pozycji w kolejności tabulacji. Można zadokować wiele okien, aby umieścić je w "tratwie" lub poza IDE. Okna narzędzi można także ukryć lub zminimalizować.

 System Windows można rozmieścić w następujący sposób:

- Przypnij okna dokumentów z lewej strony karty.

- Karta — dokowanie systemu Windows do ramki edycji.

- Dokowanie okien narzędzi do krawędzi ramki w IDE.

- Przestaw okna dokumentu lub narzędzia na zewnątrz lub poza IDE.

- Ukryj okna narzędzi wzdłuż krawędzi IDE.

- Wyświetlanie okien na różnych monitorach.

- Resetowanie położenia okna do układu domyślnego lub do zapisanego układu niestandardowego.

  Okna narzędzi i dokumentów można rozmieścić, przeciągając je za pomocą poleceń w menu **okno** i klikając prawym przyciskiem myszy pasek tytułu okna, które ma zostać ułożone.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="docking-windows"></a>Dokowanie okien
 Gdy klikniesz i przeciągniesz pasek tytułu okna narzędzi lub kartę okna dokumentu, pojawi się romb przewodnika. Podczas operacji przeciągania, gdy wskaźnik myszy znajduje się nad jedną strzałką w karo, zostanie wyświetlony zacieniowany obszar pokazujący, gdzie okno zostanie zadokowane po zwolnieniu przycisku myszy.

 Aby przenieść okno było dokować bez przyciągania do miejsca, wybierz klawisz CTRL podczas przeciągania okna.

 Aby zwrócić okno narzędzi lub okno dokumentu do jego najnowszej lokalizacji zadokowanej, naciśnij klawisz **Ctrl** , a następnie kliknij dwukrotnie pasek tytułu lub kartę okna.

 Na poniższej ilustracji przedstawiono romb przewodnika dla okien dokumentów, który można zadokować tylko w obrębie ramki edycji:

 ![Romb przewodnika okna dokumentu](../ide/media/documentwindowguidediamonds.png "Documentwindowguidediamonds")

 Okna narzędzi można dołączać do jednej strony ramki w IDE lub wewnątrz ramki edycji. Romb przewodnik pojawia się po przeciągnięciu okna narzędzia do innej lokalizacji, aby ułatwić ponowne zadokowanie okna.

 Romb przewodnika dla okien narzędzi

 ![Przewodnik po oknach narzędzi](../ide/media/vs10guidediamond.png "VS10GuideDiamond")

 Na poniższej ilustracji przedstawiono Eksplorator rozwiązań zadokowane w nowej lokalizacji, która jest pokazywana przez niebieską powierzchnię:

 ![Dokowanie Eksplorator rozwiązań w nowej pozycji](../ide/media/vs2015-dock-diamond.png "VS2015_Dock_diamond")

### <a name="closing-and-auto-hiding-tool-windows"></a>Zamykanie i Autoukrywanie okien narzędzi
 Możesz zamknąć okno narzędzi, klikając symbol X w prawym górnym rogu paska tytułu. Aby ponownie otworzyć okno, użyj skrótu klawiaturowego lub polecenia menu. Okna narzędzi obsługują funkcję o nazwie Autohide, która powoduje, że okno jest w sposób nieobecny, gdy używasz innego okna. Gdy okno jest Autoukrywanie, jego nazwa jest wyświetlana na karcie na krawędzi IDE. Aby ponownie użyć tego okna, wskaż kartę, aby wyświetlić ponownie slajdy okna.

 ![Ukryj Autoukrywanie](../ide/media/vs2015-auto-hide.png "vs2015_auto_hide")

> [!NOTE]
> Aby ustawić, czy Autoukrywanie działa w oknach narzędzi indywidualnie, czy jako zadokowanych, zaznacz lub wyczyść pole wyboru **Autoukrywanie, które ma wpływ na aktywne okna narzędzi tylko** w oknie dialogowym **Opcje** . Aby uzyskać więcej informacji, zobacz [Ogólne, środowisko, Opcje — okno dialogowe](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna narzędzi, które mają włączoną funkcję Autoukrywanie, mogą tymczasowo przesuwać się do widoku, gdy okno ma fokus. Aby ponownie ukryć okno, wybierz element poza bieżącym oknem. Gdy okno utraci fokus, slajdy są wychodzące z widoku.

### <a name="specifying-a-monitor"></a>Określanie monitora
 Jeśli masz drugi monitor i obsługuje go system operacyjny, możesz wybrać monitor wyświetla okno. Można nawet grupować wiele okien razem w "tratws" na innych monitorach.

> [!TIP]
> Można utworzyć wiele wystąpień **Eksplorator rozwiązań** i przenieść je do innego monitora. Kliknij okno prawym przyciskiem myszy i wybierz polecenie **Nowy widok Eksplorator rozwiązań**. Możesz przywrócić wszystkie okna z powrotem do oryginalnego monitora, dwukrotnie klikając podczas wybierania klawisza CTRL.

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetowanie, nazwa i przełączanie między układami okien
 Można przywrócić IDE do oryginalnego układu okna dla kolekcji ustawień przy użyciu polecenia **Zresetuj układ okna** . Po uruchomieniu tego polecenia są wykonywane następujące akcje:

- Wszystkie okna są przenoszone do ich domyślnych pozycji.

- Okna, które są zamknięte w domyślnym układzie okna, są zamknięte.

- Okna, które są otwarte w domyślnym układzie okna, są otwarte.

### <a name="create-and-save-custom-layouts"></a>Tworzenie i zapisywanie układów niestandardowych
 Program Visual Studio 2015 umożliwia zapisywanie do 10 niestandardowych układów okien i szybkie przełączanie się między nimi. W poniższych krokach pokazano, jak tworzyć, zapisywać i wywoływać układy niestandardowe oraz zarządzać nimi, korzystając z wielu monitorów z oknami narzędzi zadokowanych i przestawnych.

 Najpierw utwórz rozwiązanie testowe, które ma dwa projekty, każdy z innym optymalnym układem.

##### <a name="create-a-ui-project-and-customize-the-layout"></a>Tworzenie projektu interfejsu użytkownika i dostosowywanie układu

1. W oknie dialogowym **Nowy projekt** Utwórz aplikację klasyczną Visual C# WPF i Wywołaj ją w dowolny sposób. Poudawać, że jest to projekt, w którym pracujemy nad interfejsem użytkownika, więc chcemy zmaksymalizować miejsce dla okna projektanta i przenieść inne okna narzędzi w sposób niezależny.

2. Jeśli masz wiele monitorów, Pobierz okno **Eksplorator rozwiązań** i okno **Właściwości** do drugiego monitora. W jednym systemie monitorowania Spróbuj zamknąć wszystkie okna z wyjątkiem projektanta.

3. Naciśnij **kombinację klawiszy CTRL + ALT + X** , aby wyświetlić przybornik. Jeśli okno jest zadokowane, przeciągnij je tak, aby było przepływać w miejscu, w którym chcesz go umieścić, na dowolnym monitorze.

4. Naciśnij klawisz F5, aby umieścić program Visual Studio w trybie debugowania. Dostosuj położenie okien, stosu wywołań i debugowania danych wyjściowych w żądany sposób. Układ, który chcesz utworzyć, będzie stosowany do trybu edycji i trybu debugowania.

5. Gdy układy w trybie debugowania i trybie edycji są odpowiednie, z menu głównego wybierz **okno > Zapisz układ okna**. Wywołaj ten układ "Projektant".

     Należy pamiętać, że nowy układ jest przypisany do następnego skrótu klawiaturowego z listy zarezerwowanych kombinacji klawiszy Ctrl + Alt + 1... 0.

##### <a name="create-a-database-project-and-layout"></a>Tworzenie projektu i układu bazy danych

1. Dodaj nowy projekt **bazy danych SQL Server** do rozwiązania.

2. Kliknij prawym przyciskiem myszy nowy projekt w Eksplorator rozwiązań a następnie wybierz polecenie **Widok w Eksplorator obiektów**. Spowoduje to wyświetlenie okna **Eksplorator obiektów SQL Server** , które umożliwia dostęp do tabel, widoków i innych obiektów w bazie danych. Można to zrobić w tym oknie lub pozostawić zadokowane. Dostosuj inne okna narzędzi w odpowiedni sposób. W przypadku dodanej wartości rzeczywistej można dodać rzeczywistą bazę danych, ale nie jest to konieczne w tym instruktażu.

3. Gdy układ jest odpowiedni, z menu głównego wybierz **okno > Zapisz układ okna**. Wywołaj ten układ "DB Project". (Nie bother z układem trybu debugowania dla tego projektu).

##### <a name="switch-between-the-layouts"></a>Przełączenie między układami

1. Aby przełączać się między układami, użyj skrótów klawiaturowych lub z menu głównego wybierz **okno > Zastosuj Układ okna**.

     ![Menu Zastosuj Układ okna](../ide/media/vs2015-applywindowlayout.png "VS2015_ApplyWindowLayout")

     Po zastosowaniu układu interfejsu użytkownika należy zwrócić uwagę, jak układ jest zachowywany zarówno w trybie edycji, jak i w trybie debugowania.

     Jeśli masz konfigurację z wieloma monitorami w pracy i pojedynczy laptop w domu, możesz utworzyć układy zoptymalizowane pod kątem poszczególnych maszyn.

     Uwaga: w przypadku zastosowania układu wielomonitorowego w systemie z jednym monitorem przestawne okna, które zostały umieszczone na drugim monitorze, zostaną teraz ukryte za oknem programu Visual Studio. Możesz przenieść te okna na wierzch, naciskając klawisze Alt + Tab. Jeśli później otworzysz program Visual Studio z wieloma monitorami, możesz przywrócić te okna do określonych pozycji przez ponowne zastosowanie układu.

##### <a name="manage-and-roam-your-layouts"></a>Zarządzanie układami i poruszanie się po nich

1. Układ niestandardowy można usunąć, zmienić jego kolejność, wybierając **okno > zarządzanie układami okien**. Przeniesienie układu powoduje automatyczne dostosowanie powiązania klucza w celu odzwierciedlenia nowej pozycji na liście. Powiązania nie mogą być modyfikowane w inny sposób, więc można przechowywać maksymalnie 10 układów jednocześnie.

     ![Zarządzanie układami okien](../ide/media/managewindowlayouts.png "ManageWindowLayouts")

     Aby przypomnić, który skrót klawiaturowy jest przypisany do układu, wybierz **okno > Zastosuj Układ okna**.

     Te układy są automatycznie przenoszone między wersjami programu Visual Studio, a także między wystąpieniami Blend na oddzielnych maszynach i w dowolnej innej organizacji Express Edition. Jednak układy nie poruszają się w programie Visual Studio, Blend i Express.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Rodzaje okien](../misc/kinds-of-windows.md)|W tym artykule omówiono różnice między oknami narzędzi i oknami dokumentu w IDE.|
|[Porady: aranżowanie i dokowanie okien](../misc/how-to-arrange-and-dock-windows.md)|W tym artykule opisano, jak dokować, automatycznie ukrywać i rozkładać sąsiadująco okna, a także jak zresetować układ okien.|
|[Instrukcje: poruszanie się w środowisku IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)|W tym artykule opisano, jak przechodzić kolejno przez otwarte okna w IDE, w kolejności ich użycia. Opisano również, jak można przejść do określonych dokumentów.|
|[Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)|Zawiera informacje dotyczące kombinacji ustawień i wpływu ustawień na układy okien, skróty klawiaturowe i inne elementy w IDE.|

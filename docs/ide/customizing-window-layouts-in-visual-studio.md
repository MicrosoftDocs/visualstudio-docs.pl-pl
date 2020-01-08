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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596713"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Dostosowywanie układów okien w programie Visual Studio

W programie Visual Studio można dostosować położenie, rozmiar i zachowanie systemu Windows w celu utworzenia układów okna, które działają najlepiej dla różnych przepływów pracy deweloperskiej. Podczas dostosowywania układu IDE pamięta. Na przykład jeśli zmienisz lokalizację dokowania **Eksplorator rozwiązań** a następnie zamkniesz program Visual Studio, następnym razem, gdy otworzysz program Visual Studio, nawet jeśli pracujesz na innym komputerze, **Eksplorator rozwiązań** zostanie zadokowany w tej samej lokalizacji.

Możesz również nazwać i zapisać niestandardowy układ, a następnie przełączać się między układami za pomocą jednego polecenia. Na przykład można utworzyć układ do edycji i układu debugowania oraz przełączać się między nimi przy użyciu **okna** > **Zastosuj Układ okna** polecenie menu.

## <a name="kinds-of-windows"></a>Rodzaje okien

### <a name="tool-and-document-windows"></a>Okna narzędzi i dokumentów

IDE ma dwa typy podstawowe okna, *okna narzędzi* i *dokumentu windows*. Okna narzędzi obejmują **Eksplorator rozwiązań**, **Eksplorator serwera**, **okno dane wyjściowe**, **Lista błędów**, projektantów, okien debugera i tak dalej. Okna dokumentów zawierają pliki kodu źródłowego, pliki dowolnego tekstu, pliki konfiguracji i tak dalej. Okna narzędzi można ze zmienionym rozmiarem i przeciągnąć przez ich paska tytułu. Okna dokumentów można przeciągać według ich kart. Kliknij prawym przyciskiem myszy kartę lub pasek tytułu, aby ustawić inne opcje okna.

**Okna** menu wyświetlane są opcje dla dokowania, liczb zmiennoprzecinkowych i ukrywanie okna w IDE. Kliknij prawym przyciskiem myszy pasek okna karty lub tytuł, aby wyświetlić dodatkowe opcje dla tego określonego okna. Możesz wyświetlić więcej niż jedno wystąpienie niektórych okien narzędzi w danym momencie. Na przykład, można wyświetlić więcej niż jedno okno przeglądarki sieci web i utworzyć dodatkowe wystąpienia niektórych oknach narzędzi, wybierając **nowe okno** na **okna** menu.

### <a name="preview-tab-document-windows"></a>Karta (wersja zapoznawcza) (system windows dokumentu)

Na karcie **Podgląd** można wyświetlić pliki w edytorze bez ich otwierania. Możesz wyświetlić podgląd plików, wybierając je w **Eksplorator rozwiązań**podczas debugowania, gdy przejdziesz do plików, z **Przejdź do definicji**, a następnie przeglądając wyniki wyszukiwania. Pliki (wersja zapoznawcza) są wyświetlane na karcie po prawej stronie obszaru karty dokumentu. Plik zostanie otwarty do edycji w przypadku jego modyfikacji lub wybrania opcji **Otwórz**.

### <a name="tab-groups"></a>Grupy kart

Grupy kart umożliwiają zarządzanie obszarem roboczym ograniczonym podczas pracy z dwoma lub więcej otwartymi dokumentami w środowisku IDE. Można organizować okna z wieloma dokumentami i oknami narzędzi do pionowych lub poziomych grup kart i losowo przeciągać dokumenty z jednej grupy kart do innej.

### <a name="split-windows"></a>Podziel okna

Jeżeli masz wyświetlić lub edytować dwóch lokalizacjach jednocześnie w dokumencie, można podzielić systemu windows. Aby dokumentu należy podzielić na dwie sekcje niezależnie przewijania, kliknij przycisk **podziału** na **okna** menu. Kliknij przycisk **Usuń podział** na **okna** menu, aby przywrócić jednego widoku.

### <a name="toolbars"></a>Paski narzędzi

Paski narzędzi mogą być ułożone przez przeciąganie lub za pomocą **Dostosuj** okno dialogowe. Aby uzyskać więcej informacji na temat sposobu pozycjonowania i dostosowywania pasków narzędzi, zobacz [How to: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Rozmieszczanie i Dokowanie okien

Okno dokumentu lub okno narzędzi może być *zadokowane*, tak aby miało położenie i rozmiar w obrębie ramki okna IDE lub przestawne jako oddzielne okno niezależne od środowiska IDE. Narzędzia systemu windows może być zadokowane w dowolne miejsce wewnątrz ramki IDE; Niektóre narzędzia systemu windows może być zadokowane jako okien z zakładkami w ramce edytora. Okna dokumentów, może być zadokowane w ramce edytora i można przypiąć do bieżącego położenia w kolejności tabulacji. Można zadokować wiele okien, aby umieścić je razem w miejscu *lub na zewnątrz* IDE. Można również ukryte okna narzędzi lub zminimalizowana.

Rozmieść z systemu windows, w następujący sposób:

- Przypnij dobrze okna dokumentu do lewej strony karty.

- Karta dokowanie okien do ramki edycji.

- Dokowanie okien narzędzi do krawędzi ramki w IDE.

- Przestawianie okien dokumentu lub narzędzia na lub poza IDE.

- Ukrywanie okien narzędzi wzdłuż krawędzi środowiska IDE.

- Wyświetlaj okna na różnych monitorach.

- Resetowanie położenia okna, domyślny układ lub zapisanego układu niestandardowego.

Rozmieszczaj okna narzędzi i dokumentów, przeciągając je za pomocą poleceń w menu **okno** lub klikając prawym przyciskiem myszy pasek tytułu okna.

### <a name="dock-windows"></a>Okna dokowania

W przypadku kliknij i przeciągnij pasek tytułu okna narzędzi lub na karcie okna dokumentu romb przewodnik pojawia się. Podczas operacji przeciągania gdy wskaźnik myszy znajduje się nad jedną strzałki rombu, zacieniony obszar pojawi się informujący o tym, gdzie okna zostanie zadokowany po zwolnieniu przycisku myszy teraz.

Aby przenieść okno było dokować bez przyciągania do miejsca, naciśnij klawisz **Ctrl** podczas przeciągania okna.

Aby zwrócić okno narzędzi lub okno dokumentu do jego najnowszej lokalizacji zadokowanej, naciśnij klawisz **Ctrl** , a następnie kliknij dwukrotnie pasek tytułu lub kartę okna.

Poniższa ilustracja przedstawia dokowania dla okien dokumentu, które może być zadokowane tylko wewnątrz ramki edycji:

![Romb przewodnika okna dokumentu](../ide/media/documentwindowguidediamonds.png)

Okna narzędzi mogą być mocowane po jednej stronie ramki w IDE lub wewnątrz ramki edycji. Romb przewodnik pojawia się po przeciągnięciu okna narzędzia do innej lokalizacji, aby ułatwić zadokowanie okna.

![Przewodnik po oknach narzędzi](../ide/media/vs10guidediamond.png)

Na poniższej ilustracji przedstawiono **Eksplorator rozwiązań** zadokowane w nowej lokalizacji, która została odtworzona przez niebieską powierzchnię:

![Dokowanie Eksplorator rozwiązań w nowej pozycji](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Zamknij i Autoukrywanie okien narzędzi

Możesz zamknąć okno narzędzi, klikając **symbol X** w prawym górnym rogu paska tytułu. Aby ponownie otworzyć okno, użyj skrótu klawiaturowego lub polecenia menu. Okna narzędzi obsługują funkcję o nazwie *Autohide*, która powoduje, że okno jest w sposób nieobecny, gdy używasz innego okna. Gdy okno jest Autoukrywanie, jego nazwa jest wyświetlana na karcie na krawędzi IDE. Aby ponownie użyć okna, wskaż kartę tak, że okno zostanie wsunięte z powrotem do widoku.

![Ukryj Autoukrywanie](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Aby ustawić, czy Autoukrywanie działa w oknach narzędzi indywidualnie, czy jako zadokowanych, zaznacz lub wyczyść pole wyboru **Autoukrywanie, które ma wpływ na aktywne okna narzędzi tylko** w oknie dialogowym **Opcje** . Aby uzyskać więcej informacji, zobacz [Ogólne, środowisko, Opcje — okno dialogowe](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna narzędzi, które mają włączoną funkcję Autoukrywanie, mogą tymczasowo przesuwać się do widoku, gdy okno ma fokus. Aby ukryć okno ponownie, zaznacz element spoza bieżącego okna. Gdy okno traci fokus, jest wycofywane z widoku.

### <a name="specifying-a-second-monitor"></a>Określanie drugiego monitora

Jeśli masz drugi monitor, a system operacyjny obsługuje go, można wybrać, który monitor wyświetla okno. Można nawet grupować jednocześnie wiele okien w *tratwach* na innych monitorach.

> [!TIP]
> Możesz utworzyć wiele wystąpień **Eksploratora rozwiązań** i przenieść je do innego monitora. Kliknij prawym przyciskiem myszy okno, a następnie wybierz **nowy widok Eksploratora rozwiązania**. Możesz przywrócić wszystkie okna z powrotem do oryginalnego monitora, dwukrotnie klikając podczas wybierania klawisza **Ctrl** .

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetowanie, nazwę i przełączać się między układy okien

Możesz powrócić IDE do oryginalnego layoutu okna zestawu ustawień za pomocą **Zresetuj układ okna** polecenia. Po uruchomieniu tego polecenia, są wykonywane następujące akcje:

- Wszystkie okna są przenoszone do ich domyślnych pozycji.

- Windows, które zostały zamknięte w domyślnym układzie okien są zamknięte.

- Windows, które są otwarte w domyślnym układzie okien są otwarte.

### <a name="create-and-save-custom-layouts"></a>Utworzyć i zapisać niestandardowe układy

Program Visual Studio umożliwia zapisywanie do 10 niestandardowych układów okien i szybkie przełączanie się między nimi. Poniższe kroki pokazują sposób tworzenia, zapisywania, wywołania i zarządzać układy niestandardowe, które wykorzystują wielu monitorów z oba okna zadokowane i przestawne narzędzie.

Najpierw utwórz test rozwiązanie, które ma dwa projekty: każdy inny, optymalny układ.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Utwórz projekt interfejsu użytkownika i dostosować układ

1. Utwórz nowy C# projekt **aplikacji WPF** . Załóżmy, że w tym projekcie utworzysz interfejs użytkownika. Chcesz zmaksymalizować miejsce dla okna projektanta i przenieść inne okna narzędzi w sposób nieobecny.

2. Jeśli masz wiele monitorów, ściąganie **Eksploratora rozwiązań** okna i **właściwości** okna za pośrednictwem drugiego monitora. W systemie pojedynczy monitor Zamknij wszystkie okna z wyjątkiem projektanta.

3. Naciśnij klawisz **Ctrl**+**Alt**+**X** , aby wyświetlić okno **Przybornik** . Jeśli okno jest zadokowane, przeciągnij je tak, aby było przepływać w miejscu, gdzie chcesz go umieścić.

4. Naciśnij klawisz **F5** , aby umieścić program Visual Studio w trybie debugowania. Dostosuj **pozycję okien,** **stosu wywołań**i debugowania **danych wyjściowych** w żądany sposób. Układ, który zamierzasz utworzyć, będzie stosowany do trybu edycji i trybu debugowania.

5. Gdy układy w trybie debugowania i trybie edycji są odpowiednie, wybierz **okno** > **Zapisz układ okna**. Wywołaj ten układ "Projektant".

     Należy pamiętać, że nowy układ jest przypisany do kolejnego skrótu klawiaturowego z listy zarezerwowanych **Ctrl**+**Alt**+**1... 0**.

#### <a name="create-a-database-project-and-layout"></a>Tworzenie bazy danych projektu i układu

1. Dodaj nową **bazy danych SQL Server** projektu do rozwiązania.

2. Kliknij prawym przyciskiem myszy nowy projekt w **Eksplorator rozwiązań** a następnie wybierz polecenie **Widok w Eksplorator obiektów**. Spowoduje to wyświetlenie **Eksplorator obiektów SQL Server** okno, które umożliwia dostęp do tabel, widoków i innych obiektów w bazie danych. Można przestawić to okno lub zostawić zadokowany. Dostosuj innymi oknami narzędzi w żądany sposób. W przypadku dodanej wartości rzeczywistej można dodać rzeczywistą bazę danych, ale nie jest to konieczne w tym instruktażu.

3. Gdy układ jest odpowiedni, z menu głównego wybierz **okno** > **Zapisz układ okna**. Wywołaj ten układ "DB Project". (Nie bother z układem trybu debugowania dla tego projektu).

#### <a name="switch-between-the-layouts"></a>Przełączanie między układów

Aby przełączać się między układami, użyj skrótów klawiaturowych lub z menu głównego wybierz **okno** > **Zastosuj Układ okna**.

![Menu Zastosuj Układ okna](../ide/media/vs2015_applywindowlayout.png)

Po zastosowaniu układ interfejsu użytkownika, należy pamiętać, jak zachować układ zarówno w trybie edycji, jak i w trybie debugowania.

Jeśli masz wielu konfiguracji monitora, w miejscu pracy oraz pojedynczy monitor komputera przenośnego w domu, można utworzyć układów, które są zoptymalizowane dla każdego komputera.

> [!NOTE]
> W przypadku zastosowania układu wielomonitorowego w systemie z jednym monitorem przestawne okna, które zostały umieszczone na drugim monitorze, zostaną teraz ukryte za oknem programu Visual Studio. Możesz przenieść te okna na wierzch, naciskając **klawisze Alt + Tab**. Jeśli później otworzysz program Visual Studio z wieloma monitorami, możesz przywrócić te okna do określonych pozycji przez ponowne zastosowanie układu.

#### <a name="manage-and-roam-your-layouts"></a>Zarządzanie i są przekazywane układów

Układ niestandardowy można usunąć, zmienić jego kolejność, wybierając **okno** > **Zarządzanie układami okien**. Jeśli przenosisz układu, klucz powiązania jest automatycznie dostosowywany do nowej pozycji na liście. Powiązania nie może być inny sposób modyfikować, a więc może przechowywać maksymalnie 10 układów w danym momencie.

![Zarządzanie układami okien](../ide/media/managewindowlayouts.png)

Aby przypomnić, który skrót klawiaturowy jest przypisany do układu, wybierz **okno** > **Zastosuj Układ okna**.

Te układy automatycznie przenoszone między wersjami programu Visual Studio, a także między wystąpieniami programu Blend na oddzielnych komputerach i z dowolnej wersji Express do innej organizacji Express. Jednak układy nie są przekazywane między Visual Studio, program Blend i Express.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: poruszanie się w środowisku IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)

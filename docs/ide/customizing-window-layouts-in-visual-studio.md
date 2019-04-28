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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4904f7bb57430fc71ab6875d39a18c5bfb0c2fe0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975398"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Dostosowywanie układów okien w programie Visual Studio

W programie Visual Studio można dostosować położenie, rozmiar i zachowanie systemu windows, aby utworzyć układy okna, które najlepiej działać dla różnych przepływów pracy programowania. Podczas dostosowywania układu IDE pamięta. Na przykład, jeśli zmienisz lokalizację dokowania **Eksploratora rozwiązań** , a następnie zamknij program Visual Studio przy następnym, Otwórz program Visual Studio, nawet jeśli pracujesz na innym komputerze, **Eksploratora rozwiązań**będzie zadokowany w tym samym miejscu.

Możesz też nazwać i zapisać niestandardowe układy i następnie przełączać się między układy za pomocą jednego polecenia. Na przykład można utworzyć układ do edycji i układu do debugowania i przełączać się między nimi przy użyciu **okna** > **Zastosuj układ okna** polecenia menu.

## <a name="kinds-of-windows"></a>Rodzaje okien

### <a name="tool-and-document-windows"></a>Narzędzia i okna dokumentu

IDE ma dwa typy podstawowe okna, *okna narzędzi* i *dokumentu windows*. Okna narzędzi obejmują **Eksploratora rozwiązań**, **Eksploratora serwera**, **okno danych wyjściowych**, **lista błędów**, projektantów, oknach debugera , i tak dalej. Okna dokumentów zawierają pliki kodu źródłowego, pliki dowolnego tekstu, pliki konfiguracji i tak dalej. Okna narzędzi można ze zmienionym rozmiarem i przeciągnąć przez ich paska tytułu. Okna dokumentów można przeciągać za jego kartę. Kliknij prawym przyciskiem myszy, na karcie lub pasek tytułu można ustawić inne opcje w oknie.

**Okna** menu wyświetlane są opcje dla dokowania, liczb zmiennoprzecinkowych i ukrywanie okna w IDE. Kliknij prawym przyciskiem myszy pasek okna karty lub tytuł, aby wyświetlić dodatkowe opcje dla tego określonego okna. Możesz wyświetlić więcej niż jedno wystąpienie niektórych okien narzędzi w danym momencie. Na przykład, można wyświetlić więcej niż jedno okno przeglądarki sieci web i utworzyć dodatkowe wystąpienia niektórych oknach narzędzi, wybierając **nowe okno** na **okna** menu.

### <a name="preview-tab-document-windows"></a>Karta (wersja zapoznawcza) (system windows dokumentu)

W **Podgląd** karty, możesz wyświetlać pliki w edytorze bez ich otwierania. Możesz wyświetlić podgląd plików, wybierając je w **Eksploratora rozwiązań**, podczas debugowania, gdy wkroczenia do plików, za pomocą **przejdź do definicji**, a podczas przeglądania wyników wyszukiwania. Pliki (wersja zapoznawcza) są wyświetlane na karcie po prawej stronie obszaru karty dokumentu. Plik zostanie otwarty do edycji, jeśli możesz go zmodyfikować, lub wybrać **Otwórz**.

### <a name="tab-groups"></a>Zakładek

Zakładek rozszerzyć możliwości zarządzania ograniczone obszaru roboczego podczas pracy z co najmniej dwóch otwartych dokumentów w IDE. Można organizować wiele okien dokumentu i okna narzędzi w obu grupach kartę pionową lub poziomą i manipulowanie dokumentami z jednej karty, grupy, do innego.

### <a name="split-windows"></a>Podzielone okna

Jeżeli masz wyświetlić lub edytować dwóch lokalizacjach jednocześnie w dokumencie, można podzielić systemu windows. Aby dokumentu należy podzielić na dwie sekcje niezależnie przewijania, kliknij przycisk **podziału** na **okna** menu. Kliknij przycisk **Usuń podział** na **okna** menu, aby przywrócić jednego widoku.

### <a name="toolbars"></a>Paski narzędzi

Paski narzędzi mogą być ułożone przez przeciąganie lub za pomocą **Dostosuj** okno dialogowe. Aby uzyskać więcej informacji o tym, jak to pozycjonowania i dostosowywanie pasków narzędzi, zobacz [jak: Dostosowywanie menu i pasków zadań](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Aranżowanie i dokowanie okien

Okno dokumentu lub okna narzędzi mogą być *zadokowany*, dzięki czemu ma położenie i rozmiar w obrębie ramki okna środowiska IDE lub zmiennoprzecinkowego jako oddzielne okno niezależnie od środowiska IDE. Narzędzia systemu windows może być zadokowane w dowolne miejsce wewnątrz ramki IDE; Niektóre narzędzia systemu windows może być zadokowane jako okien z zakładkami w ramce edytora. Okna dokumentów, może być zadokowane w ramce edytora i można przypiąć do bieżącego położenia w kolejności tabulacji. Można zadokować wiele okien float razem w *tratwie* nad lub poza IDE. Można również ukryte okna narzędzi lub zminimalizowana.

Rozmieść z systemu windows, w następujący sposób:

- Przypnij dobrze okna dokumentu do lewej strony karty.

- Karta dokowanie okien do ramki edycji.

- Dokowanie okien narzędzi do krawędzi ramki w IDE.

- Przestawianie okien dokumentu lub narzędzia na lub poza IDE.

- Ukrywanie okien narzędzi wzdłuż krawędzi środowiska IDE.

- Wyświetlaj okna na różnych monitorach.

- Resetowanie położenia okna, domyślny układ lub zapisanego układu niestandardowego.

Rozmieść okna dokumentów i narzędzi, przeciągając, przy użyciu poleceń w **okna** menu, klikając prawym przyciskiem myszy pasek tytułu okna.

### <a name="dock-windows"></a>Dokowanie okien

W przypadku kliknij i przeciągnij pasek tytułu okna narzędzi lub na karcie okna dokumentu romb przewodnik pojawia się. Podczas operacji przeciągania gdy wskaźnik myszy znajduje się nad jedną strzałki rombu, zacieniony obszar pojawi się informujący o tym, gdzie okna zostanie zadokowany po zwolnieniu przycisku myszy teraz.

Aby przenieść okno zadokowane bez przyciągania go w miejscu, naciśnij klawisz **Ctrl** klucza podczas przeciągania okna.

Aby przywrócić jego najnowsze położenie zadokowanego okna narzędzi lub okno dokumentu, naciśnij klawisz **Ctrl** gdy klikniesz dwukrotnie pasek tytułu lub karcie okna.

Poniższa ilustracja przedstawia dokowania dla okien dokumentu, które może być zadokowane tylko wewnątrz ramki edycji:

![Romb przewodnik okna dokumentu](../ide/media/documentwindowguidediamonds.png)

Okna narzędzi mogą być mocowane po jednej stronie ramki w IDE lub wewnątrz ramki edycji. Romb przewodnik pojawia się po przeciągnięciu okna narzędzia do innej lokalizacji, aby pomóc łatwo ponownie zadokować okno.

![Diamenty przewodnik okna narzędzi](../ide/media/vs10guidediamond.png)

Poniższa ilustracja przedstawia **Eksploratora rozwiązań** jest zadokowany w nowej lokalizacji, która jest zaznaczonymi przez niebieski zacieniony obszar:

![Dokowanie Eksploratora rozwiązań w nowym położeniu](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Zamknij i automatyczne ukrywanie okien narzędzi

Możesz zamknąć okna narzędzi, klikając **X** w prawym górnym rogu paska tytułu. Aby ponownie otworzyć okno, polecenie jego klawiatury skrótów lub menu. Okna narzędzi obsługują funkcję o nazwie *Autoukrywanie*, co powoduje, że okno chowa sposób w przypadku, gdy używasz innego okna się. Gdy okno jest autohidden, jego nazwa jest wyświetlana na karcie na krawędzi IDE. Aby ponownie użyć okna, wskaż kartę tak, że okno zostanie wsunięte z powrotem do widoku.

![Autoukrywanie](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Aby ustalić, czy automatyczne ukrywanie działa narzędzie windows indywidualnie czy jako zadokowane grupy, zaznacz lub wyczyść **przycisku automatycznego ukrywania wpływa na aktywne okna narzędzi tylko** w **opcje** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ogólne, środowisko, opcje, okno dialogowe](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna narzędzi, które mają Autoukrywanie włączone może tymczasowo Przesuń do widoku, gdy okno jest ustawiony fokus. Aby ukryć okno ponownie, zaznacz element spoza bieżącego okna. Gdy okno traci fokus, jest wycofywane z widoku.

### <a name="specifying-a-second-monitor"></a>Określanie drugim monitorze

Jeśli masz drugi monitor, a system operacyjny obsługuje go, można wybrać, który monitor wyświetla okno. Użytkownik może nawet grupować liczne okna razem w *tratwach* na innych monitorach.

> [!TIP]
> Możesz utworzyć wiele wystąpień **Eksploratora rozwiązań** i przenieść je do innego monitora. Kliknij prawym przyciskiem myszy okno, a następnie wybierz **nowy widok Eksploratora rozwiązania**. Wszystkie systemy windows można wrócić do oryginalnego monitora, klikając dwukrotnie podczas wybierania **Ctrl** klucza.

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetowanie, nazwę i przełączać się między układy okien

Możesz powrócić IDE do oryginalnego layoutu okna zestawu ustawień za pomocą **Zresetuj układ okna** polecenia. Po uruchomieniu tego polecenia, są wykonywane następujące akcje:

- Wszystkie okna są przenoszone do ich domyślnych pozycji.

- Windows, które zostały zamknięte w domyślnym układzie okien są zamknięte.

- Windows, które są otwarte w domyślnym układzie okien są otwarte.

### <a name="create-and-save-custom-layouts"></a>Utworzyć i zapisać niestandardowe układy

Program Visual Studio można zapisać maksymalnie 10 niestandardowe układy okien i szybko przełączaj się między nimi. Poniższe kroki pokazują sposób tworzenia, zapisywania, wywołania i zarządzać układy niestandardowe, które wykorzystują wielu monitorów z oba okna zadokowane i przestawne narzędzie.

Najpierw utwórz test rozwiązanie, które ma dwa projekty: każdy inny, optymalny układ.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Utwórz projekt interfejsu użytkownika i dostosować układ

1. Utwórz nową C# **aplikacja WPF** projektu. Załóżmy, że w tym projekcie, będzie tworzenia interfejsu użytkownika. Chcesz zmaksymalizować miejsce w oknie projektanta, a następnie przejść z innymi oknami narzędzi.

2. Jeśli masz wiele monitorów, ściąganie **Eksploratora rozwiązań** okna i **właściwości** okna za pośrednictwem drugiego monitora. W systemie pojedynczy monitor Zamknij wszystkie okna z wyjątkiem projektanta.

3. Naciśnij klawisz **Ctrl**+**Alt**+**X** do wyświetlenia **przybornika** okna. Jeśli okno jest zadokowany, przeciągnij go tak, że jest ona wyświetlana innym miejscu, gdzie chcesz umieścić go.

4. Naciśnij klawisz **F5** aby umieścić programu Visual Studio w trybie debugowania. Dopasować położenie **Autos**, **stos wywołań**, i **dane wyjściowe** debugowania systemu windows w żądany sposób. Układ, który masz zamiar utworzyć dotyczą zarówno trybem edycji i w trybie debugowania.

5. Kiedy układów w trybie debugowania i tryb edycji są, jak chcesz, wybierz polecenie **okna** > **Zapisz układ okna**. Wywołaj ten układ "Designer".

     Należy pamiętać, nowy układ jest przypisany dalej skrótu klawiaturowego z listy zarezerwowanych **Ctrl**+**Alt**+**1... 0**.

#### <a name="create-a-database-project-and-layout"></a>Tworzenie bazy danych projektu i układu

1. Dodaj nową **bazy danych SQL Server** projektu do rozwiązania.

2. Kliknij prawym przyciskiem myszy nad nowym projektem w **Eksploratora rozwiązań** i wybierz polecenie **widoku w Eksploratorze obiektów**. Spowoduje to wyświetlenie **Eksplorator obiektów SQL Server** okno, które umożliwia dostęp do tabel, widoków i innych obiektów w bazie danych. Można przestawić to okno lub zostawić zadokowany. Dostosuj innymi oknami narzędzi w żądany sposób. Dla dodano realizmu można dodać istniejącej bazy danych, ale nie jest konieczne w ramach tego przewodnika.

3. Gdy układ jest, jak chcesz, w menu głównym wybierz **okna** > **Zapisz układ okna**. Wywołaj ten układ "Projekt bazy danych". (Firma Microsoft nie będą odblokowane z układem trybu debugowania dla tego projektu.)

#### <a name="switch-between-the-layouts"></a>Przełączanie między układów

Aby przełączyć się między układów, skróty klawiaturowe lub w menu głównym wybierz **okna** > **Zastosuj układ okna**.

![Zastosuj menu układu okna](../ide/media/vs2015_applywindowlayout.png)

Po zastosowaniu układ interfejsu użytkownika, należy pamiętać, jak zachować układ zarówno w trybie edycji, jak i w trybie debugowania.

Jeśli masz wielu konfiguracji monitora, w miejscu pracy oraz pojedynczy monitor komputera przenośnego w domu, można utworzyć układów, które są zoptymalizowane dla każdego komputera.

> [!NOTE]
> Jeśli zastosujesz układ wielu monitorów w systemie jednego monitora zmiennoprzecinkowy systemu windows, które umieszczone na drugim monitorze teraz będzie ukryty pod okna programu Visual Studio. Możesz wyświetlić te okna na pierwszym planie, naciskając klawisz **Alt + Tab**. Po otwarciu programu Visual Studio z wieloma monitorami, stosując ponownie układ można przywrócić systemu windows do ich określonych pozycji.

#### <a name="manage-and-roam-your-layouts"></a>Zarządzanie i są przekazywane układów

Można usunąć, zmienić lub zmiana kolejności układu niestandardowego, wybierając **okna** > **Zarządzanie układami okien**. Jeśli przenosisz układu, klucz powiązania jest automatycznie dostosowywany do nowej pozycji na liście. Powiązania nie może być inny sposób modyfikować, a więc może przechowywać maksymalnie 10 układów w danym momencie.

![Zarządzanie układami okien](../ide/media/managewindowlayouts.png)

Przypominał klawiatury, którego skrót jest przypisany do którego układu, wybierz polecenie **okna** > **Zastosuj układ okna**.

Te układy automatycznie przenoszone między wersjami programu Visual Studio, a także między wystąpieniami programu Blend na oddzielnych komputerach i z dowolnej wersji Express do innej organizacji Express. Jednak układy nie są przekazywane między Visual Studio, program Blend i Express.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Poruszanie się w środowisku IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)
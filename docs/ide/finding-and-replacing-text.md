---
title: Znajdowanie i zamienianie tekstu oraz wybór wielu łóżek
ms.date: 08/14/2018
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc31a0d0e2b6878b5dd5173a35ce4f538e135be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590348"
---
# <a name="find-and-replace-text"></a>Znajdowanie i zastępowanie tekstu

Tekst można znaleźć i zastąpić w edytorze Programu Visual Studio za pomocą funkcji [Znajdź i zamień](#find-and-replace-control) **(Ctrl**+**F** lub **Ctrl**+**H)** lub [Znajdź/Zamień w plikach](#find-in-files-and-replace-in-files) **(Ctrl**+**Shift**+**F** lub **Ctrl**+**Shift**+**H**). Można również znaleźć i zastąpić tylko *niektóre* wystąpienia wzorca za pomocą *[wyboru wielobarwnego](#multi-caret-selection)*.

> [!TIP]
> Jeśli zmieniasz nazwę symboli kodu, takich jak zmienne i metody, lepiej je *[refaktoryzuje](../ide/reference/rename.md)* niż używać find-and-replace. Refaktoryzowanie jest inteligentne i rozumie zakres, podczas gdy find-and-replace ślepo zastępuje wszystkie wystąpienia.

Funkcja znajdowania i zamieniania jest dostępna w edytorze, w niektórych innych oknach tekstowych, takich jak okna **Znajdź wyniki,** w oknach projektanta, takich jak projektant XAML i projektant windows forms, oraz w oknach narzędzi.

Można wyszukiwać zakres do bieżącego dokumentu, bieżącego rozwiązania lub niestandardowego zestawu folderów. Można również określić zestaw rozszerzeń nazw plików do wyszukiwania wielu plików. Dostosuj składnię wyszukiwania przy użyciu [wyrażeń regularnych](../ide/using-regular-expressions-in-visual-studio.md)platformy .NET .

> [!TIP]
> Pole [Znajdź/Polecenie](../ide/find-command-box.md) jest dostępne jako kontrolka paska narzędzi, ale nie jest domyślnie widoczne. Aby wyświetlić pole **Znajdź/Polecenie,** wybierz pozycję **Dodaj lub usuń przyciski** na pasku narzędzi **Standardowy,** a następnie wybierz pozycję **Znajdź**.

## <a name="find-and-replace-control"></a>Znajdź i zamień formant

- Naciśnij **klawisz Ctrl**+**F** jako skrót, aby *znaleźć* ciąg w bieżącym pliku.
- Naciśnij **klawisz Ctrl**+**H** jako skrót, aby znaleźć *i zastąpić* ciąg w bieżącym pliku.

Kontrolka **Znajdź i Zamień** pojawi się w prawym górnym rogu okna edytora kodu. Natychmiast wyróżnia każde wystąpienie danego ciągu wyszukiwania w bieżącym dokumencie. Możesz poruszać się z jednego wystąpienia do drugiego, wybierając przycisk **Znajdź następny** lub Przycisk **Znajdź poprzedni** w formancie wyszukiwania.

![Znajdowanie i zamienianie w programie Visual Studio](media/find-and-replace-box.png)

Dostęp do opcji zastępowania można uzyskać, wybierając przycisk obok pola tekstowego **Znajdź.** Aby zastąpić jedną wymianę naraz, wybierz przycisk **Zamień następny** obok pola tekstowego **Zamień.** Aby zastąpić wszystkie dopasowania, wybierz przycisk **Zamień wszystko.**

Aby zmienić kolor podświetlenia dla dopasowań, wybierz menu **Narzędzia,** wybierz polecenie **Opcje**, a następnie wybierz pozycję **Środowisko**i wybierz pozycję **Czcionki i kolory**. Na liście **Pokaż ustawienia dla** pozycji Edytor **tekstu**, a następnie na liście **Elementy wyświetlane** wybierz pozycję Znajdź **wyróżnienie (rozszerzenie).**

### <a name="search-tool-windows"></a>Okna narzędzia wyszukiwania

Kontrolki **Znajdź** w oknach kodu lub tekstu, takich jak **Okna wyjściowe** i **Znajdź wyniki,** można użyć, zaznaczając pozycję **Edytuj** > **znajdź i zamień** lub naciskając **klawisze Ctrl+F**.

Wersja **znajdź** kontrolki jest również dostępna w niektórych oknach narzędzi. Na przykład można filtrować listę kontrolek w oknie **Przybornika,** wprowadzając tekst w polu wyszukiwania. Inne okna narzędzi, które umożliwiają wyszukiwanie ich zawartości, obejmują **Eksplorator rozwiązań,** okno **Właściwości** i **Eksplorator zespołu**.

## <a name="find-in-files-and-replace-in-files"></a>Znajdź w plikach i zamień w plikach

- Naciśnij **klawisze Ctrl**+**Shift**+**F** jako skrót, aby *znaleźć* ciąg w wielu plikach.
- Naciśnij **klawisz Ctrl**+**Shift**+**H** jako skrót, aby znaleźć i *zastąpić* ciąg w wielu plikach.

**Znajdź/Zamień w plikach** działa jak **znajdź i zamień** kontrolki, z tą różnicą, że można zdefiniować zakres wyszukiwania. Można przeszukiwać bieżący otwarty plik w edytorze, ale także wszystkie otwarte dokumenty, całe rozwiązanie, bieżący projekt i wybrane zestawy folderów. Można również wyszukiwać według rozszerzenia nazwy pliku. Aby uzyskać dostęp do okna dialogowego **Znajdowanie/zamienianie w plikach,** wybierz polecenie **Znajdź i zamień** w menu **Edycja** (lub naciśnij **klawisze Ctrl**+**Shift**+**F**).

![Znajdowanie w plikach w programie Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Znajdź wyniki

Po **wybraniu**opcji Znajdź wszystko zostanie otwarte okno **Znajdź wyniki** i wyświetlenie dopasowania do wyszukiwania. Wybranie wyniku na liście powoduje wyświetlenie skojarzonego pliku i wyróżnienie dopasowania. Jeśli plik nie jest jeszcze otwarty do edycji, jest dobrze otwierany na karcie podglądu po prawej stronie karty. Za pomocą kontrolki **Znajdź** można przeszukiwać listę **Znajdź wyniki.**

### <a name="create-custom-search-folder-sets"></a>Tworzenie niestandardowych zestawów folderów wyszukiwania

Zakres wyszukiwania można zdefiniować, wybierając przycisk **Wybierz foldery wyszukiwania** (wygląda jak **...**) obok pola **Szukaj w.** W oknie dialogowym **Wybieranie folderów wyszukiwania** można określić zestaw folderów do wyszukania i zapisać specyfikację, aby można było jej użyć ponownie później.

> [!TIP]
> Jeśli dysk komputera zdalnego został zamapowany na komputer lokalny, można określić foldery do wyszukiwania na komputerze zdalnym.

### <a name="create-custom-component-sets"></a>Tworzenie niestandardowych zestawów składników

Zestawy składników można zdefiniować jako zakres wyszukiwania, wybierając przycisk **Edytuj niestandardowy zestaw składników** obok pola **Szukaj w.** Można określić zainstalowane składniki .NET lub COM, projekty programu Visual Studio, które są zawarte w rozwiązaniu, lub dowolną bibliotekę zestawu lub typów (*.dll*, *.tlb*, *.olb*, *.exe*lub *.ocx*). Aby wyszukać odwołania, zaznacz pole **Szukaj w odwołaniach.**

## <a name="multi-caret-selection"></a>Wybór wielu łóżek

> [!NOTE]
> Ta sekcja dotyczy programu Visual Studio w systemie Windows. W programie Visual Studio dla komputerów Mac zobacz [Blokowanie zaznaczania](/visualstudio/mac/block-selection).

**Wprowadzony w programie Visual Studio 2017 w wersji 15.8**

Użyj *zaznaczenia wielodyskowego,* aby dokonać tej samej edycji w dwóch lub więcej miejscach w tym samym czasie. Na przykład można wstawić ten sam tekst lub zmodyfikować istniejący tekst w wielu lokalizacjach w tym samym czasie.

Na poniższym `-0000` zrzucie ekranu jest zaznaczona w trzech lokalizacjach; jeśli użytkownik naciśnie **klawisz Delete**, wszystkie trzy selekcje zostaną usunięte:

![Wybór wielu pielęgnacyjnych w pliku XML w programie Visual Studio](media/multi-caret-selection.png)

Aby zaznaczyć wiele daszków, kliknij lub dokonaj pierwszego zaznaczenia tekstu w zwykły sposób, a następnie naciśnij klawisz **Alt** podczas klikania lub zaznaczania tekstu w każdej dodatkowej lokalizacji. Można również automatycznie dodać pasujący tekst jako dodatkowe zaznaczenia lub zaznaczyć pole tekstu, aby edytować je identycznie w każdym wierszu.

> [!TIP]
> Jeśli jako klawisz **modyfikatora** wybrano klawisz Alt jako klawisz modyfikatora myszy, kliknij pozycję Przejdź do opcji definicji w**opcjach** **narzędzi,** > wybór wielu daszek jest wyłączony.

### <a name="commands"></a>Polecenia

Użyj następujących klawiszy i akcji dla zachowań wyboru wielu pielęgnacyjnych:

|Skrót|Akcja|
|-|-|
|**Ctrl**+**Alt** + kliknij|Dodawanie pomocniczej daszku|
|**Ctrl**+**Alt** + kliknij dwukrotnie|Dodawanie dodatkowego zaznaczenia wyrazu|
|**Ctrl**+**Alt** + kliknij + przeciągnij|Dodawanie zaznaczenia pomocniczego|
|**Shift**+**Alt**+**.**|Dodawanie następnego pasującego tekstu jako zaznaczenia|
|**Ctrl**+**Shift**+**Alt**+**,**|Dodawanie całego pasującego tekstu jako zaznaczenia|
|**Shift**+**Alt**+**,**|Usuwanie ostatnio zaznaczonego wystąpienia|
|**Ctrl**+**Shift**+**Alt**+**.**|Pomiń następne pasujące wystąpienie|
|**Alt** + kliknięcie|Dodawanie zaznaczenia pola|
|**Esc** lub kliknij przycisk|Wyczyść wszystkie zaznaczenia|

Niektóre polecenia są również dostępne w menu **Edycja** w obszarze **Wiele troski:**

![Menu wysuwu wielu daszek w programie Visual Studio](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>Zobacz też

- [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Kod refaktoryzatora w programie Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Wybór bloku (Visual Studio dla komputerów Mac)](/visualstudio/mac/block-selection)

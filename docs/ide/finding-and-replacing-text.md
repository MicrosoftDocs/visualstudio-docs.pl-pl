---
title: Znajdź i Zamień tekst i wybieranie wielu karetki
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80a6b369826c9f03d8f40d2dc924845acbf6a3f4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039414"
---
# <a name="find-and-replace-text"></a>Znajdowanie i zastępowanie tekstu

Możesz znaleźć i zamienić tekst w edytorze programu Visual Studio przy użyciu [Znajdź i Zamień](#find-and-replace-control) lub [Znajdź/Zamień w plikach](#find-in-files-and-replace-in-files). Nowość w programie Visual Studio 2017 w wersji 15.8 można znaleźć i zamienić *niektóre* wystąpień wzorca za pomocą  *[zaznaczenie wielu karetki](#multi-caret-selection)*.

> [!TIP]
> Jeśli zmieniasz kodu symbole, takie jak zmienne i metody, lepiej jest *[zrefaktoryzuj](../ide/reference/rename.md)* ich niż korzystać Znajdź i Zamień. Refaktoryzacja jest inteligentne i określa zakres, Znajdź i Zamień bezrefleksyjne zastępuje wszystkie wystąpienia.

Funkcja Znajdź i zamień jest dostępna w edytorze, a w niektórych oparte na tekście windows takich jak **Find Results** systemu windows, w oknach projektantów, takich jak projektant XAML i Projektant formularzy Windows i w oknach narzędzi.

Możesz ograniczyć wyszukiwanie do bieżącego dokumentu, bieżącego rozwiązania lub niestandardowego zestawu folderów. Można również określić zestaw rozszerzeń nazw plików dla wyszukiwania wieloplikowego. Dostosować składnię wyszukiwania przy użyciu platformy .NET [wyrażeń regularnych](../ide/using-regular-expressions-in-visual-studio.md).

> [!TIP]
> [Find/Command](../ide/find-command-box.md) pole jest dostępne jako formant paska narzędzi, ale nie jest wyświetlany domyślnie. Do wyświetlenia **Find/Command** wybierz opcję **apletu Dodaj lub usuń przyciski** na **standardowa** narzędzi, a następnie wybierz pozycję **znaleźć**.

## <a name="find-and-replace-control"></a>Formant Znajdź i Zamień

**Znajdź i Zamień** formant jest widoczny w prawym górnym rogu okna edytora kodu. **Znajdź i Zamień** kontroli natychmiast wyróżnia każde wystąpienie wyszukiwanego ciągu w bieżącym dokumencie. Możesz przejść z jednego wystąpienia do innego, wybierając **Znajdź następny** przycisk lub **Find Previous** przycisku na kontrolce wyszukiwania.

![Znajdź i Zamień w programie Visual Studio](media/find-and-replace-box.png)

Dostęp do opcji zastępowania, wybierając przycisk obok **znaleźć** pola tekstowego. Aby wykonywać jedną zamianę naraz, wybierz opcję **Zamień następny** znajdujący się obok **Zastąp** pola tekstowego. Aby zamienić wszystkie dopasowania, wybierz opcję **Zamień wszystkie** przycisku.

Aby zmienić kolor podświetlenia dopasowań, wybierz **narzędzia** menu, wybierz opcję **opcje**, a następnie wybierz **środowiska**i wybierz **czcionki i kolory** . W **Pokaż ustawienia dla** listy wybierz **edytora tekstów**, a następnie w polu **wyświetlania elementów** listy wybierz **Znajdź zaznaczone (rozszerzenie)**.

### <a name="search-tool-windows"></a>Wyszukiwanie okien

Możesz użyć **znaleźć** kontrolować w oknach kodu lub tekstu, takie jak **dane wyjściowe** systemu windows i **Find Results** systemu windows, wybierając **Edytuj**  >  **Znajdź i Zamień** lub naciskając **Ctrl + F**.

Wersja **znaleźć** kontroli jest również dostępna w niektórych oknach narzędzi. Na przykład można filtrować listę formantów w **przybornika** okna, wprowadzając tekst w polu wyszukiwania. Innymi oknami narzędzi, które umożliwiają wyszukiwanie ich zawartość zawierają **Eksploratora rozwiązań**, **właściwości** oknie i **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Znajdź w plikach i Zamień w plikach

**Znajdź/Zamień w plikach** działa jak **Znajdź i Zamień** kontrolować, z tą różnicą, że można zdefiniować zakres wyszukiwania. Nie tylko można przeszukiwać bieżący plik otwarty w edytorze, ale również wszystkie otwierać dokumenty, całe rozwiązanie, bieżący projekt i wybrane foldery zestawów. Możesz również wyszukiwać według rozszerzenia nazwy pliku. Aby uzyskać dostęp do **Znajdź/Zamień w plikach** okno dialogowe, wybierz opcję **Znajdź i Zamień** na **Edytuj** menu lub naciśnij klawisz **Ctrl + Shift + F**.

![Znajdź w plikach w programie Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Znajdź wyniki

Po wybraniu **Znajdź wszystkie**, **Find Results** okna otwiera i wyświetla listę wyników wyszukiwania. Wybranie wyniku na liście Wyświetla skojarzony plik i wyróżnienie dopasowania. Jeśli plik nie jest już otwarty do edycji, jest otwierany w karcie podglądu po prawej stronie na karcie dobrze. Możesz użyć **znaleźć** formantu, aby przeszukiwać **Find Results** listy.

### <a name="create-custom-search-folder-sets"></a>Tworzenie zestawów folderu wyszukiwania niestandardowego

Można zdefiniować zakres wyszukiwania, wybierając **Choose Search Folders** przycisku (wygląda jak **...** ) obok pozycji **przeszukania** pole. W **Choose Search Folders** okno dialogowe, można określić zbiór folderów wyszukiwania i zapisać specyfikację dzięki czemu użytkownik może użyć go ponownie później.

> [!TIP]
> Jeśli komputer zdalny dysk zamapowany na komputer lokalny, możesz określić folderów do wyszukiwania na komputerze zdalnym.

### <a name="create-custom-component-sets"></a>Tworzenie zestawów składników niestandardowych

Można zdefiniować zestawy składników jako zakres wyszukiwania, wybierając **Edit Custom Component Set** znajdujący się obok **przeszukania** pole. Można określić zainstalowane składniki .NET lub COM, projekty programu Visual Studio, które znajdują się w rozwiązaniu lub wszystkie zestawy lub typy biblioteki (*.dll*, *.tlb*, *.olb*, *.exe*, lub *.ocx*). Aby przeszukać odwołania, zaznacz **Szukaj w odwołaniach** pole.

## <a name="multi-caret-selection"></a>Wybieranie wielu karetki

> [!NOTE]
> Ta sekcja dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [naczenie blokowe](/visualstudio/mac/block-selection).

**Nowość w programie Visual Studio 2017 w wersji 15.8**

Użyj *zaznaczenie wielu karetki* się tego samego edycji w dwóch lub więcej miejsc, w tym samym czasie. Na przykład można wstawić ten sam tekst lub zmodyfikować istniejący tekst w wielu lokalizacjach, w tym samym czasie.

Poniższy zrzut ekranu `-0000` wybrane w trzech miejscach; gdy użytkownik naciśnie **Usuń**, zostaną usunięte wszystkie trzy opcje:

![Zaznaczenie wielu daszek w pliku XML w programie Visual Studio](media/multi-caret-selection.png)

Aby wybrać wiele daszka, kliknij przycisk lub utworzyć pierwszy wybór tekstu w zwykły sposób, a następnie naciśnij **Alt** podczas kliknij lub wybierz tekst w każdej lokalizacji dodatkowej. Można również automatycznie dodać pasujący tekst jako dodatkowe opcje lub zaznacz pole tekstowe do edycji identycznie w każdym wierszu.

> [!TIP]
> Jeśli wybrano **Alt** jako klucz modyfikujący kliknięcie myszą, przejdź do definicji w **narzędzia** > **opcje**, wybierz wielu daszka jest wyłączona.

### <a name="commands"></a>Polecenia

Dla zachowania wyboru wielu karetki, należy użyć następujących kluczy i akcji:

|Skrót|Akcja|
|-|-|
|**CTRL**+**Alt** + kliknięcie|Dodawanie dodatkowej karetki|
|**CTRL**+**Alt** i kliknij dwukrotnie ikonę|Dodaj wybrane elementy dodatkowej programu word|
|**CTRL**+**Alt** kliknij i przeciągnij|Dodaj pomocniczy zaznaczenie|
|**SHIFT**+**Alt**+**.**|Dodaj następny szukanego tekstu jako zaznaczenia|
|**CTRL**+**Shift**+**Alt**+**,**|Dodaj wszystkie dopasowania tekstu jako zaznaczenia|
|**SHIFT**+**Alt**+**,**|Usuń ostatni zaznaczone wystąpienie|
|**CTRL**+**Shift**+**Alt**+**.**|Pomiń kolejne wystąpienie dopasowania|
|**ALT** + kliknięcie|Dodaj pole wyboru|
|**ESC** lub kliknij przycisk|Wyczyść wszystkie zaznaczenia|

Niektóre polecenia są również dostępne na **Edytuj** menu, w obszarze **wielu daszka**:

![Wiele menu wysuwanego daszka w programie Visual Studio](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>Zobacz także

- [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refaktoryzacja kodu w programie Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Zablokuj zaznaczenie (Visual Studio dla komputerów Mac)](/visualstudio/mac/block-selection)
---
title: Znajdowanie i zastępowanie tekstu oraz Zaznaczanie z obsługą wiele karetki
ms.date: 10/17/2020
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
ms.openlocfilehash: b878ccbf6714987599d1585ca9c0dc3ceb759144
ms.sourcegitcommit: 4450abc99453ccaf8936449bbff437c5b9efa022
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2020
ms.locfileid: "92334197"
---
# <a name="find-and-replace-text"></a>Znajdowanie i zastępowanie tekstu

Możesz znaleźć i zamienić tekst w edytorze programu Visual Studio za pomocą [Znajdź i Zamień](#find-and-replace-control) (**Ctrl** + **F** lub **Ctrl** + **h**) lub [Znajdź/Zamień w plikach](#find-in-files-and-replace-in-files) (**Ctrl** + **SHIFT** + **F** lub **Ctrl** + **SHIFT** + **H**). Można również znajdować i zamieniać tylko *niektóre* wystąpienia wzorca przy użyciu *[wyboru o wiele karetki](#multi-caret-selection)*.

> [!TIP]
> W przypadku zmiany nazwy symboli kodu, takich jak zmienne i metody, lepsze jest ich *[Refaktoryzacja](../ide/reference/rename.md)* niż użycie Znajdź i Zamień. Refaktoryzacja jest inteligentna i rozumie zakres, podczas gdy Znajdowanie i zamienianie powoduje ukrycie wszystkich wystąpień.

Funkcje znajdowania i zamieniania są dostępne w edytorze, w niektórych innych oknach tekstowych, takich jak okna **szukania wyników** , w oknach projektanta, takich jak Projektant XAML i Projektant Windows Forms, oraz w oknach narzędzi.

Można zakres wyszukiwania do bieżącego dokumentu, bieżącego rozwiązania lub niestandardowego zestawu folderów. Możesz również określić zestaw rozszerzeń nazw plików dla wyszukiwania wieloplikowego. Dostosuj składnię wyszukiwania za pomocą [wyrażeń regularnych](../ide/using-regular-expressions-in-visual-studio.md)programu .NET.

> [!TIP]
> Pole [Znajdź/polecenie](../ide/find-command-box.md) jest dostępne jako formant paska narzędzi, ale nie jest domyślnie widoczny. Aby wyświetlić okno **Znajdź/polecenie** , wybierz pozycję **Dodaj lub usuń przyciski** na pasku narzędzi **Standardowy** , a następnie wybierz pozycję **Znajdź**.

## <a name="find-and-replace-control"></a>Znajdź i Zamień formant

- Naciśnij klawisz **Ctrl** + **F** jako skrót, aby *znaleźć* ciąg w bieżącym pliku.
- Naciśnij klawisz **Ctrl** + **H** jako skrót, aby *znaleźć i zamienić* ciąg w bieżącym pliku.

Kontrolka **Znajdź i Zamień** pojawia się w prawym górnym rogu okna edytora kodu. Natychmiast podświetla każde wystąpienie danego ciągu wyszukiwania w bieżącym dokumencie. Możesz nawigować z jednego wystąpienia do innego, wybierając przycisk **Znajdź dalej** lub przycisk **Znajdź poprzedni** w kontrolce wyszukiwanie.

![Znajdź i Zamień w programie Visual Studio](media/find-and-replace-box.png)

Możesz uzyskać dostęp do opcji zamiany, wybierając przycisk obok pola tekstowego **Znajdź** . Aby dokonać jednej zamiany, wybierz przycisk **Zamień następny** obok pola tekstowego **Zastąp** . Aby zastąpić wszystkie dopasowania, wybierz przycisk **Zamień wszystko** .

Aby zmienić kolor podświetlenia dla dopasowania, wybierz menu **Narzędzia** , wybierz pozycję **Opcje**, a następnie wybierz pozycję **środowisko**i wybierz pozycję **czcionki i kolory**. Na liście **Pokaż ustawienia dla** wybierz pozycję **Edytor tekstu**, a następnie na liście **Wyświetl elementy** wybierz pozycję **Znajdź Wyróżnij (rozszerzenie)**.

### <a name="search-tool-windows"></a>Okna narzędzi wyszukiwania

Możesz użyć kontrolki **Znajdź** w oknach kodu lub tekstu, takich jak okna **danych wyjściowych** i **Znajdź wyniki** w systemie Windows, wybierając opcję **Edytuj**  >  **Znajdź i Zamień** lub naciskając **klawisze CTRL + F**.

Wersja kontrolki **Znajdź** jest również dostępna w niektórych oknach narzędzi. Na przykład można filtrować listę kontrolek w oknie **przybornika** , wprowadzając tekst w polu wyszukiwania. Inne okna narzędzi, które umożliwiają przeszukiwanie zawartości, obejmują **Eksplorator rozwiązań**, okno **Właściwości** i **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Znajdź w plikach i Zastąp w plikach

- Naciśnij **klawisze CTRL** + **SHIFT** + **F** jako skrót, aby *znaleźć* ciąg w wielu plikach.
- Naciśnij **klawisze CTRL** + **SHIFT** + **H** jako skrót, aby *znaleźć i zamienić* ciąg w wielu plikach.

**Znajdź/Zamień w plikach** działa jak formant **Znajdź i Zamień** , z tą różnicą, że można zdefiniować zakres wyszukiwania. Można nie tylko przeszukiwać bieżący otwarty plik w edytorze, ale również wszystkie otwarte dokumenty, całe rozwiązanie, bieżący projekt i wybrane foldery. Możesz również wyszukiwać według rozszerzenia nazwy pliku. Aby uzyskać dostęp do okna dialogowego **Znajdź/Zastąp w plikach** , wybierz pozycję **Znajdź i Zamień** w menu **Edycja** (lub naciśnij **klawisze CTRL** + **SHIFT** + **F**).

![Znajdź w plikach w programie Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Znajdź wyniki

Po wybraniu przycisku **Znajdź wszystkie**zostanie otwarte okno **Znajdź wyniki** i zostanie wyświetlona lista dopasowań dla wyszukiwania. Wybranie wyniku z listy powoduje wyświetlenie skojarzonego pliku i wyróżnienie dopasowania. Jeśli plik nie jest jeszcze otwarty do edycji, zostanie otwarty na karcie podglądu po prawej stronie w obszarze karty. Możesz użyć kontrolki **Znajdź** , aby przeszukać listę **Znajdź wyniki** .

### <a name="create-custom-search-folder-sets"></a>Tworzenie niestandardowych zestawów folderów wyszukiwania

Zakres wyszukiwania można zdefiniować, wybierając przycisk **Wybierz foldery wyszukiwania** (wygląda jak **...**) obok pola **Szukaj w** . W oknie dialogowym **Wybieranie folderów wyszukiwania** można określić zestaw folderów do przeszukania, a także zapisać specyfikację, aby można było ponownie użyć jej później.

> [!TIP]
> Jeśli dysk maszyny zdalnej został zmapowany na komputer lokalny, można określić foldery do wyszukania na komputerze zdalnym.

### <a name="create-custom-component-sets"></a>Tworzenie niestandardowych zestawów składników

Zestawy składników można definiować jako zakres wyszukiwania, wybierając przycisk **Edytuj niestandardowy zestaw składników** obok pola **Szukaj w** . Można określić zainstalowane składniki .NET lub COM, projekty programu Visual Studio, które znajdują się w rozwiązaniu lub dowolnego zestawu lub biblioteki typów (*. dll*, *. tlb*, *. olb*, *. exe*lub *. ocx*). Aby wyszukać odwołania, zaznacz pole **odszukaj w odwołaniach** .

## <a name="multi-caret-selection"></a>Wybór o wiele karetki

> [!NOTE]
> Ta sekcja ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [blok zaznaczania](/visualstudio/mac/block-selection).

**Wprowadzone w programie Visual Studio 2017 w wersji 15,8**

Użyj *zaznaczenia z wieloma* znakami, aby wprowadzić tę samą edycję w dwóch lub więcej miejscach jednocześnie. Na przykład można wstawić ten sam tekst lub zmodyfikować istniejący tekst w wielu lokalizacjach w tym samym czasie.

Na poniższym zrzucie ekranu `-0000` wybrano w trzech lokalizacjach. Jeśli użytkownik naciśnie klawisz **delete**, wszystkie trzy zaznaczenia zostaną usunięte:

![Wybór z wybieraniem karetki w pliku XML w programie Visual Studio](media/multi-caret-selection.png)

Aby zaznaczyć wiele karetki, kliknij lub Zwolnij pierwszy wybór tekstu w zwykły sposób, a następnie naciśnij klawisz **Alt** podczas klikania lub zaznaczania tekstu w każdej dodatkowej lokalizacji. Możesz również automatycznie dodać pasujący tekst jako dodatkowe wybory lub zaznaczyć pole tekstu do edycji identycznie w każdym wierszu.

> [!TIP]
> Jeśli wybrano opcję **Alt** jako klawisz modyfikujący dla kliknięcia przycisku myszy, przejdź do definicji **Tools**w  >  **opcji**narzędzia, wybór wieloznaczny jest wyłączony.

### <a name="commands"></a>Polecenia

Użyj następujących kluczy i akcji dla zachowań zaznaczania z zastosowaniem kilku karetki:

|Skrót|Akcja|
|-|-|
|**Ctrl** + **Alt** + kliknięcie|Dodawanie dodatkowego karetki|
|**Ctrl** + **Alt** + dwukrotnie kliknij|Dodaj dodatkowy wybór wyrazów|
|**Ctrl** + **Alt** + kliknięcie + przeciągnij|Dodaj wybór pomocniczy|
|**SHIFT** + **Alt** + **.**|Dodaj następny pasujący tekst jako zaznaczenie|
|**SHIFT** + **Alt** + **;**|Dodaj cały pasujący tekst jako zaznaczenie|
|**SHIFT** + **Alt** + **,**|Usuń ostatnie wybrane wystąpienie|
|**SHIFT** + **Alt**+**/**|Pomiń następne dopasowane wystąpienie|
|**Alt** + kliknięcie|Dodaj zaznaczenie pola|
|**ESC** lub kliknij|Wyczyść wszystkie zaznaczenia|

Niektóre polecenia są również dostępne w menu **Edycja** w obszarze **wielu karetki**:

:::image type="content" source="media/edit-menu-multiple-carets-find-replace.png" alt-text="Zrzut ekranu przedstawiający menu z wieloma karetkami w programie Visual Studio":::

## <a name="see-also"></a>Zobacz też

- [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Kod refaktoryzacji w programie Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Blokuj zaznaczenie (Visual Studio dla komputerów Mac)](/visualstudio/mac/block-selection)

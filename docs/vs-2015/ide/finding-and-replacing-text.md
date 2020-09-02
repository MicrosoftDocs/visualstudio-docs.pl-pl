---
title: Znajdowanie i zastępowanie tekstu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 025ba2eb95514efc740d1f8f7b3bf674d6bf237a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645637"
---
# <a name="finding-and-replacing-text"></a>Znajdowanie i zastępowanie tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz znaleźć i zamienić tekst w edytorze kodu programu Visual Studio oraz niektóre okna danych wyjściowych oparte na tekście, takie jak okna **szukania wyników** , przy użyciu kontrolki **Znajdź i Zamień** lub **Znajdź/Zamień w plikach**. Możesz również wyszukiwać i zamieniać w niektórych oknach projektanta, takich jak Projektant XAML i Projektant Windows Forms, oraz okna narzędzi

 Można zakres wyszukiwania do bieżącego dokumentu, bieżącego rozwiązania lub niestandardowego zestawu folderów. Możesz również określić zestaw rozszerzeń nazw plików dla wyszukiwania wieloplikowego. Składnię wyszukiwania można dostosować za pomocą wyrażeń regularnych programu .NET.

 Aby znaleźć i zamienić wyrażenia regularne, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!TIP]
> Pole **Znajdź/polecenie** jest nadal dostępne jako kontrolka paska narzędzi, ale nie jest już widoczne domyślnie. Możesz wyświetlić okno **Znajdź/polecenie** , wybierając pozycję **Dodaj lub usuń przyciski** na pasku narzędzi **Standardowy** , a następnie wybierając pozycję **Znajdź**. Aby uzyskać więcej informacji, zobacz [Find/Command Box](../ide/find-command-box.md).

## <a name="find-and-replace-control"></a>Znajdź i Zamień formant
 Kontrolka **Znajdź i Zamień** pojawia się w prawym górnym rogu okna edytora kodu. Kontrolka **Znajdź i Zamień** natychmiast podświetla każde wystąpienie danego ciągu wyszukiwania w bieżącym dokumencie. Możesz nawigować z jednego wystąpienia do innego, wybierając przycisk **Znajdź dalej** lub przycisk **Znajdź poprzedni** w kontrolce wyszukiwanie.

 Możesz uzyskać dostęp do opcji zamiany, wybierając przycisk obok pola tekstowego **Znajdź** . Aby dokonać jednej zamiany, wybierz przycisk **Zamień następny** obok pola tekstowego **Zastąp** . Aby zastąpić wszystkie dopasowania, wybierz przycisk **Zamień wszystko** .

 Aby zmienić kolor podświetlenia dla dopasowania, wybierz menu **Narzędzia** , wybierz pozycję **Opcje**, a następnie wybierz pozycję **środowisko**i wybierz pozycję **czcionki i kolory**. Na liście **Pokaż ustawienia dla** wybierz pozycję **Edytor tekstu**, a następnie na liście **Wyświetl elementy** wybierz pozycję **Znajdź Wyróżnij (rozszerzenie)**.

### <a name="searching-tool-windows"></a>Wyszukiwanie okien narzędzi
 Możesz użyć kontrolki **Znajdź** w oknach kodu lub tekstu, takich jak okna **danych wyjściowych** , i **znajdować wyniki** w systemie Windows, wybierając **Znajdź i Zamień** w menu **Edycja** lub (Ctrl + F).

 Wersja kontrolki Znajdź jest również dostępna w niektórych oknach narzędzi. Na przykład możesz teraz filtrować listę kontrolek w oknie **przybornika** , wprowadzając tekst w polu wyszukiwania. Inne okna narzędzi, które teraz umożliwiają wyszukiwanie ich zawartości, obejmują **Eksplorator rozwiązań**, okna **Właściwości** i **Team Explorer**, między innymi.

## <a name="findreplace-in-files"></a>Znajdź/Zamień w plikach
 **Znajdź/Zamień w plikach** działa jak formant **Znajdź i Zamień** , z tą różnicą, że można zdefiniować zakres wyszukiwania. Można nie tylko przeszukiwać bieżący otwarty plik w edytorze, ale można również przeszukiwać wszystkie otwarte dokumenty, całe rozwiązanie, bieżący projekt i wybrane foldery. Możesz również wyszukiwać według rozszerzenia nazwy pliku. Aby uzyskać dostęp do okna dialogowego **Znajdź/Zastąp w plikach** , wybierz pozycję **Znajdź i Zamień** w menu **Edycja** (lub naciśnij klawisze Ctrl + Shift + F).

 Po wybraniu przycisku **Znajdź wszystkie**zostanie otwarte okno **Znajdź wyniki** i zostanie wyświetlona lista dopasowań dla wyszukiwania. Wybranie wyniku z listy powoduje wyświetlenie skojarzonego pliku i wyróżnienie dopasowania. Jeśli plik nie jest jeszcze otwarty do edycji, zostanie otwarty na karcie podglądu po prawej stronie w obszarze karty. Możesz użyć kontrolki **Znajdź** , aby przeszukać listę **Znajdź wyniki** .

### <a name="creating-custom-search-folder-sets"></a>Tworzenie niestandardowych zestawów folderów wyszukiwania
 Zakres wyszukiwania można zdefiniować, wybierając przycisk **Wybierz foldery wyszukiwania** (wygląda jak **...**) obok pola **Szukaj w** . W oknie dialogowym **Wybieranie folderów wyszukiwania** możesz określić zestaw folderów do wyszukania, a także zapisać specyfikację, aby później można było użyć jej ponownie. Foldery na komputerze zdalnym można określić tylko wtedy, gdy dysk został zmapowany na komputer lokalny.

### <a name="creating-custom-component-sets"></a>Tworzenie niestandardowych zestawów składników
 Zestawy składników można definiować jako zakres wyszukiwania, wybierając przycisk **Edytuj niestandardowy zestaw składników** obok pola **Szukaj w** . Można określić zainstalowane składniki .NET lub COM, projekty programu Visual Studio, które znajdują się w rozwiązaniu lub dowolnego zestawu lub biblioteki typów (. dll,. tlb,. olb,. exe lub. ocx). Aby wyszukać odwołania, zaznacz pole **odszukaj w odwołaniach** .

## <a name="see-also"></a>Zobacz też
 [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)

---
title: Znajdowanie i zastępowanie tekstu | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a0edc40a8a6523c76a6b6f8074a108219152c06
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756881"
---
# <a name="finding-and-replacing-text"></a>Znajdowanie i zastępowanie tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz znaleźć i zamienić tekst w Edytor kodu programu Visual Studio, a niektóre oparte na tekście oknie danych wyjściowych, takich jak **Find Results** systemu windows, za pomocą **Znajdź i Zamień** kontroli lub **Znajdź / Zastąp w plikach**. Możesz również wyszukiwać i zamieniać w niektórych oknach projektantów, takich jak projektant XAML i Projektant Windows Forms i okna narzędzi  
  
 Możesz ograniczyć wyszukiwanie do bieżącego dokumentu, bieżącego rozwiązania lub niestandardowego zestawu folderów. Można również określić zestaw rozszerzeń nazw plików dla wyszukiwania wieloplikowego. Można dostosować składnię wyszukiwania za pomocą wyrażeń regularnych programu .NET.  
  
 Aby znaleźć i zamienić wyrażenia regularne, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  **Find/Command** pole jest nadal dostępne jako formant paska narzędzi, ale nie jest już domyślnie widoczne. Możesz wyświetlić **Find/Command** pola, wybierając **apletu Dodaj lub usuń przyciski** na **standardowa** narzędzi, a następnie wybierając **znaleźć**. Aby uzyskać więcej informacji, zobacz [polu Znajdź/polecenie](../ide/find-command-box.md).  
  
## <a name="find-and-replace-control"></a>Formant Znajdź i Zamień  
 **Znajdź i Zamień** formant jest widoczny w prawym górnym rogu okna edytora kodu. **Znajdź i Zamień** kontroli natychmiast wyróżnia każde wystąpienie wyszukiwanego ciągu w bieżącym dokumencie. Możesz przejść z jednego wystąpienia do innego, wybierając **Znajdź następny** przycisk lub **Find Previous** przycisku na kontrolce wyszukiwania.  
  
 Dostęp do opcji zastępowania, wybierając przycisk obok **znaleźć** pola tekstowego. Aby wykonywać jedną zamianę naraz, wybierz opcję **Zamień następny** znajdujący się obok **Zastąp** pola tekstowego. Aby zamienić wszystkie dopasowania, wybierz opcję **Zamień wszystkie** przycisku.  
  
 Aby zmienić kolor podświetlenia dopasowań, wybierz **narzędzia** menu, wybierz opcję **opcje**, a następnie wybierz **środowiska**i wybierz **czcionki i kolory** . W **Pokaż ustawienia dla** listy wybierz **edytora tekstów**, a następnie w polu **wyświetlania elementów** listy wybierz **Znajdź zaznaczone (rozszerzenie)**.  
  
### <a name="searching-tool-windows"></a>Wyszukiwanie narzędzia Windows  
 Możesz użyć **znaleźć** kontrolować w oknach kodu lub tekstu, takie jak **dane wyjściowe** systemu windows, i **Find Results** systemu windows, wybierając **Znajdź i Zamień**na **Edytuj** menu lub (CTRL + F).  
  
 W niektórych oknach narzędzi jest także dostępna wersja Znajdź formant. Na przykład, można teraz filtrować listę formantów w **przybornika** okna, wprowadzając tekst w polu wyszukiwania. Innymi oknami narzędzi, które obecnie umożliwiają wyszukiwanie ich zawartość zawierają **Eksploratora rozwiązań**, **właściwości** oknie i **Team Explorer**, między innymi.  
  
## <a name="findreplace-in-files"></a>Znajdź/Zamień w plikach  
 **Znajdź/Zamień w plikach** działa jak **Znajdź i Zamień** kontrolować, z tą różnicą, że można zdefiniować zakres wyszukiwania. Nie tylko można przeszukiwać bieżący plik otwarty w edytorze, ale można także przeszukać wszystkie otwarte dokumenty, całe rozwiązanie, bieżące projekty i wybrane foldery zestawów. Możesz również wyszukiwać według rozszerzenia nazwy pliku. Aby uzyskać dostęp do **Znajdź/Zamień w plikach** okna dialogowego wybierz **Znajdź i Zamień** na **Edytuj** menu (lub CTRL + SHIFT + F).  
  
 Po wybraniu **Znajdź wszystkie**, **Find Results** okna otwiera i wyświetla listę wyników wyszukiwania. Wybranie wyniku na liście Wyświetla skojarzony plik i wyróżnienie dopasowania. Jeśli plik nie jest już otwarty do edycji, jest otwierany w karcie podglądu po prawej stronie na karcie dobrze. Możesz użyć **znaleźć** formantu, aby przeszukiwać **Find Results** listy.  
  
### <a name="creating-custom-search-folder-sets"></a>Tworzenie zestawów folderu wyszukiwania niestandardowego  
 Można zdefiniować zakres wyszukiwania, wybierając **Choose Search Folders** przycisku (wygląda jak **...** ) obok pozycji **przeszukania** pole. W **Choose Search Folders** okno dialogowe, można określić zbiór folderów wyszukiwania i zapisać specyfikację dzięki czemu użytkownik może użyć go ponownie później. Foldery na komputerze zdalnym można określić tylko wtedy, gdy zmapowano jego dysk do maszyny lokalnej.  
  
### <a name="creating-custom-component-sets"></a>Tworzenie zestawów składników niestandardowych  
 Można zdefiniować zestawy składników jako zakres wyszukiwania, wybierając **Edit Custom Component Set** znajdujący się obok **przeszukania** pole. Można określić zainstalowane składniki .NET lub COM, projekty programu Visual Studio, które znajdują się w rozwiązaniu lub wszystkie zestawy lub typy biblioteki (.dll, .tlb, .olb, .exe lub .ocx). Aby przeszukać odwołania, zaznacz **Szukaj w odwołaniach** pole.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)

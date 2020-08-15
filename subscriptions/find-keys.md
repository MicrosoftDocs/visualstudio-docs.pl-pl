---
title: Znajdowanie i pojmowanie kluczy produktów w subskrypcjach programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: cabuschl
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 07/30/2020
ms.topic: conceptual
description: Dowiedz się, jak znaleźć, zatwierdzić i wyeksportować klucze produktów w subskrypcjach programu Visual Studio
ms.openlocfilehash: e9be61db1f72684dcff12d015ec5180607b41977
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250734"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Znajdowanie i pojmowanie kluczy produktów w subskrypcjach programu Visual Studio
W tym artykule opisano sposób lokalizowania, zgłaszania i eksportowania kluczy produktów z programu https://my.visualstudio.com/productkeys .  Aby uzyskać więcej informacji na temat aktywowania produktu przy użyciu klucza, wersji programu Key i licencji zbiorczych oraz dziennych limitów roszczeń dotyczących klucza produktu, przejdź do [omówienia kluczy produktów](product-keys.md).

## <a name="locating-and-claiming-product-keys"></a>Lokalizowanie i pojmowanie kluczy produktów
Musisz się zalogować do subskrypcji programu Visual Studio, aby wyświetlić klucze produktów. Poszczególne klucze produktu można znaleźć, wybierając niebieskie łącze **Uzyskaj klucz** dla określonego produktu na stronie [pliki do pobrania](https://my.visualstudio.com/downloads) , jak pokazano poniżej.  Wszystkie klucze są również dostępne w agregacji na stronie [klucze produktów](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) . Jeśli istnieje wiele kluczy dla pojedynczego produktu, w kolumnie uwagi zostanie wyświetlona informacja, która ułatwia zidentyfikowanie, który klucz ma być używany.
> [!div class="mx-imgBorder"]
> ![Pobierz klucz ze strony plików do pobrania](_img/product-keys/download-get-key.png "Wybierz pozycję Pobierz klucz na stronie informacje, aby pobrać klucz dla tego produktu.")

Niektóre produkty łączą wiele wersji produktu w jeden plik do pobrania. W takich przypadkach wprowadzony klucz produktu określa, która wersja produktu jest zainstalowana.
Niektóre klucze są udostępniane automatycznie, takie jak klucze "static", których można użyć dowolną liczbę razy, ponieważ aktywacja nie jest wymagana. Inne klucze muszą zostać przejęte przez wybranie linku **Pobierz klucz** dla produktu.

W zależności od produktu dostępne są różne typy kluczy.

### <a name="product-key-types"></a>Typy kluczy produktu

|    Typ klucza           |    Opis                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Nie dotyczy                    |    Do zainstalowania tego produktu nie jest wymagany żaden klucz.                                                       |
|    Retail                     |    Klucze detaliczne umożliwiają używanie wielu aktywacji i są używane na potrzeby kompilacji detalicznej produktu. W wielu przypadkach dozwolone są 10 aktywacji na klucz, chociaż często są dozwolone na tym samym komputerze.                                                       |
|    Aktywacja wielokrotna        |    Klucz aktywacji wielokrotnej (MAK) umożliwia aktywację wielu instalacji produktu z tym samym kluczem. Wartości MAKs są zwykle używane z wersjami produktów licencjonowania zbiorowego. Zazwyczaj dla każdej subskrypcji jest dostarczany tylko jeden klucz MAK.    |
|    Statyczny klucz aktywacji    |    Klucze aktywacji statycznej są udostępniane dla produktów, które nie wymagają aktywacji. Mogą one być używane dla dowolnej liczby instalacji.                                                                                                                  |
|    Klucz niestandardowy                 |    Klucze niestandardowe udostępniają specjalne akcje lub informacje umożliwiające aktywację lub instalację produktu.                                                                                                                                                                |
|    VA 1,0                     |    Są to wiele kluczy aktywacji, podobne do klucza MAK.                                                                                                                                                                                                 |
|    Klucz OEM                    |    Są to oryginalne klucze producenta sprzętu, które umożliwiają wiele aktywacji.                                                                                                                                                                       |
|    DreamSpark — klucz sprzedaży    |    Te klucze sprzedaży detalicznej są przeznaczone dla DreamSpark i umożliwiają jedną aktywację. Klucze detaliczne DreamSpark są wydawane w partiach i są przeznaczone głównie do użycia przez uczniów.                                                                                     |
|    Klucz laboratorium DreamSpark         |    Te klucze użycia są przeznaczone dla programów DreamSpark i umożliwiają wiele aktywacji. Klucze Lab DreamSpark są przeznaczone do użytku w scenariuszach laboratorium komputerowego na Uniwersytecie.                                                                                       |
|    Klucz MAK DreamSpark         |    Są to Klucze MAK dla klientów programu DreamSpark.                                                                                                                                                                                                  |
|

Klucz można przejąć ze strony pobierania produktu lub można wyszukać wymagany klucz na stronie [klucze produktu](https://my.visualstudio.com/productkeys) .

### <a name="claiming-product-keys"></a>Pojmowanie kluczy produktów
Tylko subskrybenci z aktywnymi subskrypcjami mogą pobierać produkty i zgłaszać klucze produktów.  Można wyeksportować zatwierdzono klucze ze strony [klucze produktu](https://my.visualstudio.com/productkeys) , gdy subskrypcja jest aktywna.

Aby zgłosić klucz produktu:
1. Zaloguj się do swojej subskrypcji programu Visual Studio.  Musisz się zalogować, aby pobrać produkty lub zatwierdzić klucze produktów.
2. Wybierz kartę [klucze produktów](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) .
3. Klucze produktów są wyświetlane alfabetycznie według nazwy produktu.  Możesz albo przewinąć w dół do nazwy żądanego produktu, albo poszukać go za pomocą paska wyszukiwania w górnej części strony.
> [!div class="mx-imgBorder"]
> ![Wyszukaj klucz produktu](_img/product-keys/search-keys.png "Przewiń do żądanego produktu lub użyj pola wyszukiwania, aby szybko zlokalizować każdy produkt.")
   
W tym przykładzie używamy paska wyszukiwania do lokalizowania klucza produktu dla Visual Studio Enterprise 2019.
Jak widać, na liście są wyświetlane różne wersje.  Jeden z najważniejszych kluczy został już przejęty dla Visual Studio Enterprise 2019 wersji 16,0 i 16,1.  Dodatkowe klucze różnych typów są nadal dostępne dla obu wersji. Należy zauważyć, że w kolumnie **uwagi** można zarejestrować krótką notatkę dotyczącą przejętych kluczy.  Można go użyć w połączeniu z datą w kolumnie **przejęte** , aby śledzić klucze, które zostały przejęte.  Możesz na przykład wprowadzić uwagi podczas aktywowania instalacji produktu przy użyciu klucza.

### <a name="exporting-your-claimed-keys"></a>Eksportowanie przejętych kluczy
Można wyeksportować listę wszystkich przejętych kluczy, a także duży wybór statycznych i innych kluczy, które są automatycznie oznaczane jako "żądane".

> [!IMPORTANT]
> Jeśli subskrypcja wygaśnie, nie będzie już można żądać nowych kluczy ani eksportować pożądanych kluczy.

Aby wyeksportować klucze, po prostu wybierz link **Eksportuj wszystkie klucze** z prawej strony na stronie klucze produktów.  Zostanie utworzony plik XML zatytułowany KeysExport.xml i będzie można otworzyć lub zapisać plik.  Otwarcie tego pliku jest możliwe przy użyciu aplikacji obsługującej pliki XML.  Na przykład możesz otworzyć ten plik jako skoroszyt tylko do odczytu w programie Excel.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Gdy wszystko jest gotowe do pobrania oprogramowania i używania klawiszy, odwiedź stronę https://my.visualstudio.com/downloads .  Aby uzyskać więcej informacji o pobieraniu oprogramowania, zobacz [Omówienie pobierania](download-software.md).
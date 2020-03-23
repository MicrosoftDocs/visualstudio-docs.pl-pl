---
title: Znajdowanie kluczy produktów i odchyliwanie ich w subskrypcjach programu Visual Studio | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/09/2020
ms.topic: conceptual
description: Dowiedz się, jak znajdować, zgłaszać roszczenia i eksportować klucze produktów w ramach subskrypcji programu Visual Studio
ms.openlocfilehash: 984a89f5085867ea7b23735d05d0e22ef51dcfdb
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "78937505"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Znajdowanie kluczy produktów i odchyliwanie ich w subskrypcjach programu Visual Studio
W tym artykule wyjaśniono, jak zlokalizować, zgłosić roszczenie i wyeksportować klucze produktu z pliku https://my.visualstudio.com/productkeys.  Aby uzyskać więcej informacji na temat aktywacji produktu za pomocą klucza, wersji kluczy licencji detalicznej i zbiorczej oraz dziennych limitów oświadczeń dotyczących kluczy produktu, odwiedź [przegląd kluczy produktu](product-keys.md).

## <a name="locating-and-claiming-product-keys"></a>Lokalizowanie i odbierzenie kluczy produktu
Aby wyświetlić klucze produktu, musisz zalogować się do subskrypcji programu Visual Studio. Poszczególne klucze produktu można znaleźć, wybierając niebieski link **Pobierz klucz** dla określonego produktu na stronie [Pliki do pobrania,](https://my.visualstudio.com/downloads) jak pokazano poniżej.  Wszystkie klucze są również dostępne w zagregowane na stronie [Klucze produktu.](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) Jeśli dla pojedynczego produktu istnieje wiele kluczy, notatki będą wyświetlane w kolumnie Notatki do pobrania, aby ułatwić identyfikację klucza, który powinien być używany.
> [!div class="mx-imgBorder"]
> ![Pobierz klucz ze strony pobierania](_img/product-keys/download-get-key.png)

Niektóre produkty łączą wiele wersji produktu w jednym pliku do pobrania. W takich przypadkach wprowadzony klucz produktu określa, która wersja produktu jest zainstalowana.
Niektóre klucze są dostarczane automatycznie, takie jak "statyczne" klucze, których można używać tyle razy, ile potrzeba, ponieważ aktywacja nie jest wymagana. Inne klucze należy zgłoś się, wybierając łącze **Pobierz klucz** dla produktu.

Dostępne są różne typy kluczy, w zależności od produktu.

### <a name="product-key-types"></a>Typy kluczy produktu

|    Typ klucza           |    Opis                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Nie dotyczy                    |    Do zainstalowania tego produktu nie jest potrzebny żaden klucz.                                                       |
|    Sprzedaż detaliczna                     |    Klucze sieci sprzedaży umożliwiają wiele aktywacji i są używane do kompilacji detalicznych produktu. W wielu przypadkach 10 aktywacji jest dozwolonych na klucz, ale często więcej jest dozwolonych na tym samym komputerze.                                                       |
|    Aktywacja wielokrotna        |    Klucz aktywacji wielokrotnej (MAK) umożliwia aktywację wielu instalacji produktu za pomocą tego samego klucza. Maks są zwykle używane z wersjami licencjonowania zbiorowego produktów. Zazwyczaj tylko jeden klucz KLUCZA MAK jest dostarczany na subskrypcję.    |
|    Statyczny klucz aktywacyjny    |    Statyczne klucze aktywacyjne są dostarczane dla produktów, które nie wymagają aktywacji. Mogą być używane do dowolnej liczby instalacji.                                                                                                                  |
|    Klucz niestandardowy                 |    Klucze niestandardowe zapewniają specjalne akcje lub informacje, aby aktywować lub zainstalować produkt.                                                                                                                                                                |
|    VA 1.0                     |    Są to wiele kluczy aktywacji, podobne do klucza MAK.                                                                                                                                                                                                 |
|    Klucz OEM                    |    Są to klucze producenta oryginalnego sprzętu, które umożliwiają wielokrotne aktywacje.                                                                                                                                                                       |
|    DreamSpark Klucz detaliczny    |    Te klucze sprzedaży detalicznej są dla DreamSpark i umożliwiają jedną aktywację. Klucze dreamspark retail są wydawane w partiach i są przeznaczone głównie do konsumpcji studentów.                                                                                     |
|    Klucz laboratorium DreamSpark         |    Te klucze do użytku laboratoryjego są przeznaczone dla programów DreamSpark i umożliwiają wielokrotne aktywacje. DreamSpark Lab Keys są przeznaczone do użytku w scenariuszach laboratorium komputerowego uniwersytetu.                                                                                       |
|    Klucz MAK DreamSpark         |    Są to klucze KLUCZYKÓW MAK dla klientów programu DreamSpark.                                                                                                                                                                                                  |
|

Możesz ubiegać się o klucz ze strony pobierania produktu lub wyszukać klucz, którego potrzebujesz na stronie [Klucze produktu.](https://my.visualstudio.com/productkeys)

### <a name="claiming-product-keys"></a>Odebranie kluczy produktu
Tylko subskrybenci z aktywnymi subskrypcjami mogą pobierać produkty i żądać kluczy produktów.  Odebrane klucze można wyeksportować ze strony [Klucze produktu,](https://my.visualstudio.com/productkeys) gdy subskrypcja jest aktywna.

Aby odebrać klucz produktu:
1. Zaloguj się do subskrypcji programu Visual Studio.  Aby pobrać produkty lub odebrać klucze produktów, musisz się zalogować.
2. Kliknij kartę [Klucze produktu.](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs)
3. Klucze produktu są wyświetlane alfabetycznie według nazwy produktu.  Możesz przewinąć w dół do nazwy żądanego produktu lub wyszukać go za pomocą paska wyszukiwania u góry strony.
> [!div class="mx-imgBorder"]
> ![Wyszukaj klucz produktu](_img/product-keys/search-keys.png)
   
W tym przykładzie użyliśmy paska wyszukiwania, aby zlokalizować klucz produktu dla programu Visual Studio Enterprise 2019.
Jak widać, istnieje kilka wersji wymienionych.  Jeden klucz każdy został już zgłoszony dla programu Visual Studio Enterprise 2019 w wersjach 16.0 i 16.1.  Dodatkowe klucze różnych typów są nadal dostępne dla obu wersji. Należy zauważyć, że można zarejestrować krótką notatkę o odebranych kluczach w kolumnie **Notatki.**  Można użyć tego w połączeniu z datą w **kolumnie Zgłoszone,** aby śledzić klucze, które zostały zgłoszone.  Notatki można na przykład zrobić podczas aktywowania instalacji produktu za pomocą klucza.

### <a name="exporting-your-claimed-keys"></a>Eksportowanie odebranych kluczy
Możesz wyeksportować listę wszystkich zgłoszonych kluczy wraz z dużym wyborem kluczy statycznych i innych, które są automatycznie oznaczane jako "zgłoszone" dla Ciebie.

> [!IMPORTANT]
> Jeśli subskrypcja wygaśnie, nie będzie już można ubiegać się o nowe klucze ani eksportować żądanych kluczy.

Aby wyeksportować klucze, wystarczy kliknąć **łącze Eksportuj wszystkie klucze** po prawej stronie kluczy produktu.  Zostanie utworzony plik xml zatytułowany KeysExport.xml i będziesz mieć możliwość otwarcia lub zapisania pliku.  Należy otworzyć plik za pomocą aplikacji zdolnej do obsługi plików xml.  Na przykład można otworzyć plik jako skoroszyt tylko do odczytu w programie Excel.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Gdy będziesz gotowy do pobierania oprogramowania https://my.visualstudio.com/downloadsi używania klawiszy, odwiedź stronę .  Aby uzyskać więcej informacji na temat pobierania oprogramowania, zobacz [przegląd pobierania](download-software.md).
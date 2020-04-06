---
title: Przeglądarka biblioteki obrazów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707748"
---
# <a name="image-library-viewer"></a>Przeglądarka biblioteki obrazów
Narzędzie Visual Studio Image Library Viewer można załadować i wyszukać manifesty obrazów, dzięki czemu użytkownik może manipulować nimi w taki sam sposób, jak program Visual Studio. Użytkownik może zmieniać tło, rozmiary, DPI, wysoki kontrast i inne ustawienia. Narzędzie wyświetla również informacje o wczytywania dla każdego manifestu obrazu i wyświetla informacje o źródle dla każdego obrazu w manifeście obrazu. To narzędzie jest przydatne dla:

1. Diagnozowanie błędów

2. Upewnianie się, że atrybuty są poprawnie ustawione w niestandardowych manifestach obrazu

3. Wyszukiwanie obrazów w wykazie obrazów programu Visual Studio, tak aby rozszerzenie programu Visual Studio można było używać obrazów pasujących do stylu programu Visual Studio

   ![Bohater przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-hero.png "Bohater przeglądarki biblioteki obrazów")

   **Moniker obrazu**

   Moniker obrazu (lub w skrócie moniker) to para GUID:ID, która jednoznacznie identyfikuje zasób obrazu lub zasób listy obrazów w Bibliotece obrazów.

   **Pliki manifestu obrazu**

   Pliki manifestu obrazu (.imagemanifest) to pliki XML definiujące zestaw zasobów obrazu, pseudonimy reprezentujące te zasoby oraz rzeczywisty obraz lub obrazy reprezentujące każdy zasób. Manifesty obrazów można zdefiniować autonomiczne obrazy lub listy obrazów dla obsługi starszego interfejsu użytkownika. Ponadto istnieją atrybuty, które można ustawić na zasobie lub na poszczególnych obrazów za każdego zasobu, aby zmienić, kiedy i jak te zasoby są wyświetlane.

   **Schemat manifestu obrazu**

   Pełny manifest obrazu wygląda następująco:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symbole**

 Jako pomoc w zakresie czytelności i konserwacji manifest obrazu może używać symboli dla wartości atrybutów. Symbole są zdefiniowane w ten sposób:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Podelement**|**Definicja**|
|Import|Importuje symbole danego pliku manifestu do użycia w bieżącym manifeście.|
|Guid (identyfikator GUID)|Symbol reprezentuje identyfikator GUID i musi być zgodny z formatowaniem identyfikatorów GUID.|
|ID|Symbol reprezentuje identyfikator i musi być nieujemną całkowitej liczby.|
|Ciąg|Symbol reprezentuje dowolną wartość ciągu.|

 W symbolach rozróżniana jest wielkość liter i odwołuje się do niego przy użyciu składni $(nazwa symbolu):Symbols are case-sensitive, and referenced using $(symbol-name) składna:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Niektóre symbole są wstępnie zdefiniowane dla wszystkich manifestów. Mogą one służyć w uri atrybut \<Source> lub \<Import> element do ścieżek odwołania na komputerze lokalnym.

|||
|-|-|
|**Symbol**|**Opis**|
|Pliki commonprogramowe|Wartość zmiennej środowiskowej %CommonProgramFiles%|
|Localappdata|Wartość zmiennej środowiskowej %LocalAppData%|
|ManifestFolder|Folder zawierający plik manifestu|
|Mydocuments|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika|
|ProgramFiles|Wartość zmiennej środowiskowej %ProgramFiles%|
|System|Folder Windows\System32|
|Windir|Wartość zmiennej środowiskowej %WinDir%|

 **Image (Obraz)**

 Element \<Image> definiuje obraz, do którego można się odwoływać za pomocą monikera. Identyfikator GUID i identyfikator razem tworzą moniker obrazu. Moniker obrazu musi być unikatowy w całej bibliotece obrazów. Jeśli więcej niż jeden obraz ma dany pseudonim, pierwszy napotkany podczas tworzenia biblioteki jest tym, który jest zachowywany.

 Musi zawierać co najmniej jedno źródło. Chociaż źródła neutralne pod względem rozmiaru dadzą najlepsze wyniki w szerokim zakresie rozmiarów, nie są one wymagane. Jeśli usługa jest proszona o obraz o \<rozmiarze nie zdefiniowanym w Image> element i nie ma źródła neutralnego pod względem rozmiaru, usługa wybierze najlepsze źródło specyficzne dla rozmiaru i skaluje go do żądanego rozmiaru.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Guid (identyfikator GUID)|[Wymagane] Część guid moniker obrazu|
|ID|[Wymagane] Część identyfikatora moniker obrazu|
|AllowColorInversion (Zezwalaj kolorowainwersja)|[Opcjonalnie, domyślna wartość true] Wskazuje, czy obraz może mieć swoje kolory programowo odwrócone, gdy jest używany na ciemnym tle.|

 **Źródła**

 Element \<Source> definiuje pojedynczy zasób źródłowy obrazu (XAML i PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Identyfikator uri|[Wymagane] Identyfikator URI, który definiuje, gdzie obraz może być ładowany z. Może to być jedna z następujących czynności:<br /><br /> - Identyfikator [URI pakietu](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) przy użyciu application:/// urzędu<br /><br /> - Odwołanie do zasobu komponentu bezwzględnego<br /><br /> - Ścieżka do pliku zawierającego zasób macierzysty|
|Tło|[Opcjonalnie] Wskazuje, co na rodzaju tła źródło jest przeznaczone do użycia.<br /><br /> Może to być jedna z następujących czynności:<br /><br /> - *Światło:* Źródło może być używane na jasnym tle.<br /><br /> - *Ciemny*: Źródło może być używane na ciemnym tle.<br /><br /> - *HighContrast:* Źródło może być używane na dowolnym tle w trybie wysokiego kontrastu.<br /><br /> - *HighContrastLight*: Źródło może być używane na jasnym tle w trybie wysokiego kontrastu.<br /><br /> -*HighContrastDark*: Źródło może być używane na ciemnym tle w trybie wysokiego kontrastu.<br /><br /> Jeśli **atrybut Background** zostanie pominięty, źródło może być używane na dowolnym tle.<br /><br /> Jeśli **tło** jest *Jasne,* *Ciemne,* *HighContrastLight*lub *HighContrastDark*, kolory źródła nigdy nie są odwrócone. Jeśli **tło** zostanie pominięte lub ustawione na *HighContrast*, inwersja kolorów źródła jest kontrolowana przez atrybut **AllowColorInversion** obrazu.|

 Element \<source> może mieć dokładnie jedną z następujących opcjonalnych podelementów:

||||
|-|-|-|
|**Element**|**Atrybuty (wszystkie wymagane)**|**Definicja**|
|\<Rozmiar>|Wartość|Źródło będzie używane do obrazów o danym rozmiarze (w jednostkach urządzenia). Obraz będzie kwadratowy.|
|\<> SizeRange|MinSize, MaxSize|Źródło będzie używane dla obrazów z MinSize do MaxSize (w jednostkach urządzenia) włącznie. Obraz będzie kwadratowy.|
|\<Wymiary>|Szerokość, Wysokość|Źródło będzie używane do obrazów o danej szerokości i wysokości (w jednostkach urządzenia).|
|\<> DimensionRange|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Źródło będzie używane dla obrazów od minimalnej szerokości/wysokości do maksymalnej szerokości/wysokości (w jednostkach urządzenia) włącznie.|

 A \<Source> element może również \<mieć opcjonalne NativeResource> podelement, który definiuje \<Source>, który jest ładowany z zestawu macierzystego, a nie zestawu zarządzanego.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Typ|[Wymagane] Typ zasobu macierzystego, XAML lub PNG|
|ID|[Wymagane] Część identyfikatora liczby całkowitej zasobu macierzystego|

 **Imagelist**

 ImageList \<> element definiuje kolekcję obrazów, które mogą być zwracane w jednym pasku. Taśma jest zbudowana na żądanie, w razie potrzeby.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Guid (identyfikator GUID)|[Wymagane] Część guid moniker obrazu|
|ID|[Wymagane] Część identyfikatora moniker obrazu|
|Zewnętrzna|[Opcjonalnie, domyślnie false] Wskazuje, czy moniker obrazu odwołuje się do obrazu w bieżącym manifeście.|

 Moniker dla zawartego obrazu nie musi odwoływać się do obrazu zdefiniowanego w bieżącym manifeście. Jeśli nie można znaleźć zawartego obrazu w bibliotece obrazów, w jego miejscu zostanie użyty pusty obraz zastępczy.

## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia
 **Sprawdzanie poprawności niestandardowego manifestu obrazu**

 Aby utworzyć manifest niestandardowy, zaleca się użycie narzędzia ManifestFromResources do autogenerowania manifestu. Aby sprawdzić poprawność manifestu niestandardowego, uruchom Przeglądarkę biblioteki obrazów i wybierz pozycję Plik > Ustaw ścieżki... , aby otworzyć okno dialogowe Wyszukaj katalogi. Narzędzie użyje katalogów wyszukiwania do ładowania manifestów obrazu, ale będzie również używać ich do znajdowania plików .dll, które zawierają obrazy w manifeście, więc upewnij się, że zawiera zarówno katalogi manifestu, jak i biblioteki DLL w tym oknie dialogowym.

 ![Wyszukiwanie w przeglądarce biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-search.png "Wyszukiwanie w przeglądarce biblioteki obrazów")

 Kliknij **przycisk Dodaj...** aby wybrać nowe katalogi wyszukiwania w celu wyszukania manifestów i odpowiadających im bibliotek DLL. Narzędzie zapamięta te katalogi wyszukiwania i można je włączyć lub wyłączyć, zaznaczając lub odznaczając katalog.

 Domyślnie narzędzie spróbuje znaleźć katalog instalacyjny programu Visual Studio i dodać te katalogi do listy katalogów wyszukiwania. Możesz ręcznie dodać katalogi, których narzędzie nie znajdzie.

 Po załadowaniu wszystkich manifestów narzędzie może służyć do przełączania kolorów **tła,** **DPI**, **wysokiego kontrastu**lub **skalowania szarości** dla obrazów, aby użytkownik mógł wizualnie sprawdzić zasoby obrazu, aby sprawdzić, czy są one poprawnie renderowane dla różnych ustawień.

 ![Tło przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-background.png "Tło przeglądarki biblioteki obrazów")

 Kolor tła można ustawić na Jasny, Ciemny lub wartość niestandardową. Wybranie opcji "Kolor niestandardowy" spowoduje otwarcie okna dialogowego wyboru kolorów i dodanie tego niestandardowego koloru do dołu pola kombi w tle, aby ułatwić późniejsze przywołanie.

 ![Niestandardowy kolor przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-custom-color.png "Niestandardowy kolor przeglądarki biblioteki obrazów")

 Wybranie monikera obrazu powoduje wyświetlenie informacji o każdym rzeczywistym obrazie za tym monikerem w okienku Szczegóły obrazu po prawej stronie. Okienko umożliwia również użytkownikom kopiowanie moniker według nazwy lub według nieprzetworzonej wartości GUID:ID.

 ![Szczegóły obrazu przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-image-details.png "Szczegóły obrazu przeglądarki biblioteki obrazów")

 Informacje wyświetlane dla każdego źródła obrazu obejmują rodzaj tła, na które ma być wyświetlane, czy może być tematyce lub obsługuje wysoki kontrast, jakie rozmiary jest prawidłowy dla lub czy jest neutralny pod względem rozmiaru i czy obraz pochodzi z natywnego zestawu.

 ![Przeglądarka obrazów może motywować](../../extensibility/internals/media/image-library-viewer-can-theme.png "Przeglądarka obrazów może motywować")

 Podczas sprawdzania poprawności manifestu obrazu zaleca się wdrożenie biblioteki DLL manifestu i obrazu w ich rzeczywistych lokalizacjach. Spowoduje to sprawdzenie, czy wszystkie ścieżki względne działają poprawnie i czy biblioteka obrazów może znaleźć i załadować bibliotekę DLL manifestu i obrazu.

 **Wyszukiwanie katalogu obrazów ZnaneMonikery**

 Aby lepiej dopasować styl programu Visual Studio, rozszerzenie programu Visual Studio może używać obrazów w wykazie obrazów programu Visual Studio, a nie tworzyć i używać własnych. Ma to tę zaletę, że nie ma konieczności utrzymywania tych obrazów i gwarantuje, że obraz będzie miał obraz kopiiowy o wysokiej rozdzielczości, więc powinien wyglądać poprawnie we wszystkich ustawieniach DPI, które obsługuje program Visual Studio.

 Przeglądarka biblioteki obrazów umożliwia wyszukiwanie manifestu, dzięki czemu użytkownik może znaleźć moniker reprezentujący zasób obrazu i użyć tego pseudonimu w kodzie. Aby wyszukać obrazy, wprowadź żądany termin wyszukiwania w polu wyszukiwania i naciśnij klawisz Enter. Pasek stanu na dole wyświetli liczbę dopasowań znalezionych z całkowitej liczby obrazów we wszystkich manifestach.

 ![Filtr Przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter.png "Filtr Przeglądarki biblioteki obrazów")

 Podczas wyszukiwania monikerów obrazów w istniejących manifestach zaleca się wyszukiwanie i używanie tylko monikerów wykazu obrazów programu Visual Studio, innych celowo publicznie dostępnych monikerów lub własnych monikerów niestandardowych. Jeśli używasz niepublicznych monikerów, niestandardowy interfejs użytkownika może zostać uszkodzony lub jego obrazy zostały zmienione w nieoczekiwany sposób, jeśli lub gdy te niepubliczne monikery i obrazy zostaną zmienione lub zaktualizowane.

 Ponadto możliwe jest wyszukiwanie według identyfikatora GUID. Ten typ wyszukiwania jest przydatny do filtrowania listy do pojedynczego manifestu lub pojedynczej podsekcji manifestu, jeśli ten manifest zawiera wiele identyfikatorów GUID.

 ![Identyfikator GUID filtra biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Identyfikator GUID filtra biblioteki obrazów")

 Wreszcie, wyszukiwanie według identyfikatora jest również możliwe.

 ![Identyfikator filtru podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter-id.png "Identyfikator filtru podglądu biblioteki obrazów")

## <a name="notes"></a>Uwagi

- Domyślnie narzędzie będzie pobierać w kilku manifestów obrazu znajdujących się w katalogu instalacji programu Visual Studio. Jedynym, który ma publicznie materiałów eksploatacyjnych monikerers jest **Microsoft.VisualStudio.ImageCatalog** manifestu. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 **(nie** zastępuj tego identyfikatora GUID w manifeście niestandardowym) Typ: KnownMonikers

- Narzędzie próbuje uruchomić, aby załadować wszystkie manifesty obrazu znajdzie, więc może upłynąć kilka sekund dla aplikacji faktycznie pojawiają. Może być również powolny lub nie odpowiada podczas ładowania manifestów.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 To narzędzie nie generuje żadnych danych wyjściowych.

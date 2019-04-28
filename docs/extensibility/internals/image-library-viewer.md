---
title: Przeglądarka biblioteki obrazów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 749441e960363fe208e3ad67288180c1935db35f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860605"
---
# <a name="image-library-viewer"></a>Przeglądarka biblioteki obrazów
Narzędzie przeglądarka biblioteki obrazów programu Visual Studio można załadować i wyszukaj obraz o nazwie manifesty umożliwienie użytkownikowi nimi manipulować w taki sam sposób, który będzie programu Visual Studio. Użytkownik może zmienić tła, rozmiary, DPI, duży kontrast i inne ustawienia. Narzędzie również Wyświetla informacje ładowania dla każdego z manifestu obrazu i wyświetla informacje dotyczące źródła dla każdego obrazu w manifeście obrazu. To narzędzie jest przydatne w przypadku:

1. Diagnozowanie błędów

2. Zapewnianie atrybuty są prawidłowo ustawione w manifestach obrazu niestandardowego

3. Wyszukiwanie obrazów w Visual Studio katalogu obrazu tak, aby rozszerzenia programu Visual Studio mogą używać obrazów, które mieszczą się stylu programu Visual Studio

   ![Obraz Hero podglądu biblioteki](../../extensibility/internals/media/image-library-viewer-hero.png "Hero przeglądarka biblioteki obrazów")

   **Moniker obrazu**

   Moniker obrazu (lub krótkiej nazwy w skrócie) jest parą GUID:ID, która jednoznacznie identyfikuje zasób obrazu lub obraz listy zasobów w bibliotece obrazów.

   **Pliki manifestu obrazu**

   Pliki manifestu (.imagemanifest) obrazów są pliki XML, które definiują zestaw zasoby obrazów, monikerów, które reprezentują te zasoby i rzeczywistego obrazu lub obrazów, które reprezentują każdego zasobu. Manifesty obrazu można zdefiniować obrazy autonomiczne lub listy obrazów do obsługi starszych wersji interfejsu użytkownika. Ponadto są atrybuty, które mogą być ustawione na zasób lub na poszczególnych obrazów za każdy zasób do zmiany, kiedy i jak te zasoby są wyświetlane.

   **Obraz schematu manifestu**

   Manifest pełny obraz wygląda następująco:

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

 **Symbols**

 Jak zwiększyć czytelność i konserwacja pomocy, manifestu obrazu można użyć symboli dla wartości atrybutów. Symbole są zdefiniowane następująco:

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
|**Element podrzędny**|**Definicja**|
|Import|Importuje symbole dany plik manifestu do użycia w bieżącym manifeście.|
|Guid|Symbol reprezentuje identyfikator GUID i muszą być zgodne, formatowania identyfikatora GUID.|
|Identyfikator|Symbol reprezentuje identyfikator i musi być nieujemną liczbą całkowitą.|
|String|Symbol reprezentuje wartość dowolny ciąg.|

 Symbole jest rozróżniana wielkość liter i odwołania, przy użyciu składni $(symbol-name):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Niektóre symbole są wstępnie zdefiniowane dla wszystkich manifestów. Mogą one być używane w atrybucie Uri \<źródło > lub \<Import > element ścieżki odwołania na komputerze lokalnym.

|||
|-|-|
|**Symbol**|**Opis**|
|CommonProgramFiles|Wartość zmiennej środowiskowej % CommonProgramFiles %|
|LocalAppData|Wartość zmiennej środowiskowej % LocalAppData %|
|ManifestFolder|Folder zawierający plik manifestu|
|Moje dokumenty|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika|
|ProgramFiles|Wartość zmiennej środowiskowej % ProgramFiles %|
|System|Do folderu Windows\System32|
|WinDir|Wartość zmiennej środowiskowej % WinDir %|

 **Obraz**

 \<Obrazu > element Określa obraz, który można się odwoływać za krótka. Identyfikator GUID i identyfikator razem tworzą monikera obrazu. Moniker obrazu musi być unikatowa w biblioteki całego obrazu. Jeśli więcej niż jeden obraz ma monikera danego, pierwszy z nich podczas kompilowania biblioteki jest ten, który jest zachowywana.

 Musi zawierać co najmniej jedno źródło. Mimo że niezależny od rozmiaru źródeł zapewni najlepsze wyniki do szerokiego zakresu rozmiarów, nie są one wymagane. Jeśli usługa zostanie poproszony o obrazu o rozmiarze nie jest zdefiniowany w \<obraz > elementu i nie istnieje źródło niezależny od rozmiaru, usługa Wybierz najlepsze źródło określonego rozmiaru i przeprowadzi jej skalowanie do żądanego rozmiaru.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Guid|[Wymagane] Identyfikator GUID część monikera obrazu|
|Identyfikator|[Wymagane] Część Identyfikatora monikera obrazu|
|AllowColorInversion|[Opcjonalna, domyślne true] Wskazuje, czy obraz, który może mieć jego kolorów programowo odwrócona, gdy jest używana na ciemnym tle.|

 **Element źródłowy**

 \<Źródło > element definiuje pojedynczy źródła zasób obrazu (XAML i PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Identyfikator URI|[Wymagane] Identyfikator URI, który określa, gdzie można załadować obrazu z. Może to być jedna z następujących czynności:<br /><br /> -A [identyfikatora URI pakietu](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) za pomocą aplikacji: / / / urzędu<br /><br /> — Odwołanie do zasobu składnik bezwzględne<br /><br /> — Ścieżka do pliku zawierającego zasobu natywnego|
|Tło|[Opcjonalnie] Wskazuje, jakie na rodzaju tła, których źródłem jest przeznaczony do użycia.<br /><br /> Może to być jedna z następujących czynności:<br /><br /> - *Jasny*: Źródło może być używane na tle światła.<br /><br /> - *Ciemny*: Źródło może być używane na ciemnym tle.<br /><br /> - *HighContrast*: Źródło może służyć w dowolnym tła w trybie dużego kontrastu.<br /><br /> - *HighContrastLight*: Źródło może być używane na tle światła w trybie dużego kontrastu.<br /><br /> -*HighContrastDark*: Źródło może być używane na ciemnym tle w trybie dużego kontrastu.<br /><br /> Jeśli **tła** atrybut zostanie pominięty, źródła można używać na dowolnym tła.<br /><br /> Jeśli **tła** jest *światła*, *ciemny*, *HighContrastLight*, lub *HighContrastDark*, nigdy nie są odwrócone kolory źródła. Jeśli **tła** jest pominięty lub ustawiony jako *HighContrast*, odwracanie kolorów źródło jest kontrolowane przez obraz **AllowColorInversion** atrybutu.|

 A \<źródło > element może mieć dokładnie jeden następujące opcjonalne elementy podrzędne:

||||
|-|-|-|
|**Element**|**Atrybuty (wszystkie wymagane)**|**Definicja**|
|\<Rozmiar >|Wartość|Źródła będą używane dla obrazów o danym rozmiarze (w jednostkach urządzenia). Obraz, który będzie mieć kształtu kwadratu.|
|\<SizeRange>|MinSize, MaxSize|Źródła będą używane dla obrazów z MinSize MaxSize (w jednostkach urządzenia) (włącznie). Obraz, który będzie mieć kształtu kwadratu.|
|\<Wymiary >|Szerokość, wysokość|Źródła będą używane dla obrazów o danym szerokość i wysokość (w jednostkach urządzenia).|
|\<DimensionRange >|Wartości elementu MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Źródła będą używane dla obrazów z minimalną szerokość/wysokość, szerokość/wysokość maksymalna (w jednostkach urządzenia) (włącznie).|

 A \<źródło > element może mieć również opcjonalny \<NativeResource > podelement, który definiuje \<źródło > który jest ładowany z natywnego zestawu, a nie zestaw zarządzany.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Typ|[Wymagane] Typ zasobu natywnego, XAML lub PNG|
|Identyfikator|[Wymagane] Całkowitą część Identyfikatora zasobu natywnego|

 **ImageList**

 \<ImageList > element definiuje kolekcję obrazów, które mogą być zwracane w pojedynczej taśmy. Pasek bazuje na żądanie, zgodnie z potrzebami.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Guid|[Wymagane] Identyfikator GUID część monikera obrazu|
|Identyfikator|[Wymagane] Część Identyfikatora monikera obrazu|
|Zewnętrzna|[Opcjonalnie, wartość domyślna to false] Wskazuje, czy monikera obrazu odwołuje się do obrazu w bieżącym manifeście.|

 Moniker obrazu zawarte nie musi odwoływać się do obrazu, który został zdefiniowany w bieżącym manifeście. Jeśli nie można odnaleźć obrazu zawarte w bibliotece obrazów, obraz pusty symbol zastępczy zostanie użyty w tym miejscu.

## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia
 **Sprawdzanie poprawności manifestu obrazu niestandardowego**

 Aby utworzyć niestandardowy manifest, zaleca się, że używasz narzędzia ManifestFromResources automatyczne generowanie manifestu. Wykonać walidację manifestu niestandardowych, uruchom przeglądarka biblioteki obrazów, a następnie wybierz pozycję Plik > Ustaw ścieżki... Aby otworzyć okno dialogowe katalogów wyszukiwania. Narzędzie użyje katalogów wyszukiwania można załadować obrazu manifestów, ale również użyje on je, aby znaleźć pliki .dll, które zawierają obrazy w manifeście, dlatego upewnij się, że zawierają manifestu i katalogi biblioteki DLL w tym oknie dialogowym.

 ![Wyszukiwanie przeglądarka biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-search.png "wyszukiwania przeglądarka biblioteki obrazów")

 Kliknij przycisk **Dodaj...**  wybrać nowe katalogi wyszukiwania należy szukać manifesty i ich odpowiednie biblioteki dll. Narzędzie zapamiętają te katalogi wyszukiwania, a ich można włączyć lub wyłączyć przez zaznaczenie lub usunięcie zaznaczenia katalogu.

 Domyślnie narzędzie spróbuje znaleźć katalogu instalacyjnego programu Visual Studio i dodać tych katalogów do listy katalogów wyszukiwania. Można ręcznie dodać katalogi, których nie może znaleźć to narzędzie.

 Po załadowaniu wszystkich manifestów, narzędzie może służyć do przełączenia **tła** kolory, **DPI**, **o wysokim kontraście**, lub **odcieni szarości** dla obrazy, dzięki czemu użytkownik może wizualnie badać zasoby obrazów, aby zweryfikować, że są one są renderowane prawidłowo dla różnych ustawień.

 ![Obraz tła podglądu biblioteki](../../extensibility/internals/media/image-library-viewer-background.png "tła przeglądarka biblioteki obrazów")

 Światła, ciemne lub niestandardową wartość można ustawić kolor tła. Wybieranie "Koloru niestandardowego" Otwórz okno dialogowe wyboru kolorów i dodawanie tego niestandardowego koloru do dolnej części pola kombi tła, aby ułatwić odwoływanie później.

 ![Kolor niestandardowy przeglądarka biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-custom-color.png "koloru niestandardowego przeglądarka biblioteki obrazów")

 Wybieranie monikera obrazu Wyświetla informacje dotyczące każdego rzeczywistego obrazu za tej krótkiej nazwy w okienku szczegółów obraz po prawej stronie. Okienka umożliwia także użytkownikom kopiowania krótka według nazwy lub wartości pierwotnych GUID:ID.

 ![Obraz szczegółów obrazu podglądu biblioteki](../../extensibility/internals/media/image-library-viewer-image-details.png "szczegóły obrazu podglądu biblioteki obrazów")

 Informacje wyświetlane dla każdego źródła obrazu obejmuje jakiego rodzaju tła, aby go wyświetlić, czy można zastosować motyw lub obsługuje duży kontrast i jakie rozmiary, jest on prawidłowy dla lub czy jest niezależny od rozmiaru i tego, czy obraz jest dostarczany z natywnego zestawu.

 ![Przeglądarka biblioteki obrazów można motyw](../../extensibility/internals/media/image-library-viewer-can-theme.png "przeglądarka biblioteki obrazów można motywu")

 Podczas sprawdzania poprawności manifestu obrazu, zaleca się wdrożenie manifestu i obraz biblioteki DLL w lokalizacjach rzeczywistych. Pozwoli to zweryfikować, czy wszystkie ścieżki względne są poprawne i czy biblioteka obrazów można znaleźć i załadować manifestu i obraz biblioteki DLL.

 **Wyszukiwanie obrazów katalogu KnownMonikers**

 Aby lepiej dopasować je do programu Visual Studio stylów, rozszerzenia programu Visual Studio mogą używać obrazów, w katalogu obrazu w usłudze Visual Studio, zamiast tworzenia i używania swój własny. Ma tę zaletę, nie muszą obsługiwać te obrazy i gwarantuje, czy obraz ma obrazu zapasowego wysokiej rozdzielczości DPI tak powinien wyglądać w wszystkich ustawień DPI, które obsługuje program Visual Studio.

 Przeglądarka biblioteki obrazów umożliwia manifestu do przeszukania, tak aby użytkownik może odnaleźć monikera elementu, reprezentujący zasób obrazu i użycie tej krótkiej nazwy w kodzie. Aby wyszukać obrazów, wprowadź żądane wyszukiwany termin w polu wyszukiwania, a następnie naciśnij klawisz Enter. Pasek stanu u dołu będą wyświetlane, ile wyników poza całkowita liczba obrazów we wszystkich manifestów.

 ![Filtr przeglądarka biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter.png "filtr przeglądarka biblioteki obrazów")

 Podczas wyszukiwania dla monikerów obrazu w manifestach istniejących, firma Microsoft zaleca wyszukiwania, a następnie użyj tylko Visual Studio obraz wykazu monikerów, inne monikerów celowo publicznie lub własne monikerów. Użycie monikerów niepublicznych, niestandardowego interfejsu użytkownika może być uszkodzony lub jego obrazów lub zostały zmienione w nieoczekiwany sposób Jeśli podczas tych niepublicznych monikerów i obrazy są zmieniane lub aktualizowane.

 Ponadto wyszukiwanie według identyfikatora GUID jest możliwe. Ten typ wyszukiwania jest przydatne w przypadku filtrowania na liście, aby jeden manifest lub pojedynczego podsekcję manifestu, jeśli to manifest zawiera wiele identyfikatorów GUID.

 ![Obraz biblioteki podglądu Filtr identyfikatora GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "obrazu biblioteki podglądu Filtr identyfikatora GUID")

 Na koniec wyszukiwanie według Identyfikatora jest możliwe również.

 ![Identyfikator filtru przeglądarka biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter-id.png "identyfikator filtru przeglądarka biblioteki obrazów")

## <a name="notes"></a>Uwagi

- Domyślnie narzędzie będzie ściągać kilka obrazów manifesty obecny w katalogu instalacyjnym programu Visual Studio. Jest jedyną, która ma publicznie w użyciu monikerów **Microsoft.VisualStudio.ImageCatalog** manifestu. Identyfikator GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (czy **nie** Zastąp ten identyfikator GUID w niestandardowym manifeście) typu: KnownMonikers

- Narzędzie prób podczas uruchamiania można załadować wszystkich manifestów obrazu, które znajdzie, dzięki czemu może potrwać kilka sekund dla aplikacji, aby faktycznie są wyświetlane. Być może wolno lub nieodpowiadający podczas ładowania manifestów.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 To narzędzie nie generuje żadnych danych wyjściowych.
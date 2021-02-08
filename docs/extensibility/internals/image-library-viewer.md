---
title: Podgląd biblioteki obrazów | Microsoft Docs
description: Dowiedz się więcej na temat narzędzia do przeglądania bibliotek obrazów programu Visual Studio, które ładuje i przeszukuje manifesty obrazu, co pozwala na wyświetlanie atrybutów obrazu i manipulowanie nimi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc0acd64a61acac2cb30b9251bcb4e528c08f227
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840122"
---
# <a name="image-library-viewer"></a>Przeglądarka biblioteki obrazów
Narzędzie przeglądarka obrazów programu Visual Studio może ładować i przeszukiwać manifesty obrazów, umożliwiając użytkownikowi manipulowanie nimi w taki sam sposób, jak w programie Visual Studio. Użytkownik może zmienić ustawienia tła, rozmiarów, DPI, dużego kontrastu i innych ustawień. Narzędzie wyświetla również informacje o ładowaniu dla każdego manifestu obrazu i wyświetla informacje o źródle dla każdego obrazu w manifeście obrazu. To narzędzie jest przydatne w przypadku:

1. Diagnozowanie błędów

2. Sprawdzanie, czy atrybuty są poprawnie ustawione w manifestach obrazu niestandardowego

3. Wyszukiwanie obrazów w katalogu obrazów programu Visual Studio, dzięki czemu rozszerzenie programu Visual Studio może korzystać z obrazów pasujących do stylu programu Visual Studio

   ![Podgląd biblioteki obrazów Hero](../../extensibility/internals/media/image-library-viewer-hero.png "Podgląd biblioteki obrazów Hero")

   **Moniker obrazu**

   Moniker obrazu (lub moniker krótki) to identyfikator GUID: identyfikator, który jednoznacznie identyfikuje zasób obrazu lub element zawartości listy obrazów w bibliotece obrazów.

   **Pliki manifestu obrazu**

   Pliki manifestu obrazu (. imagemanifest) to pliki XML, które definiują zestaw zasobów obrazu, monikery reprezentujące te elementy zawartości oraz rzeczywisty obraz lub obrazy reprezentujące każdy element zawartości. Manifesty obrazu mogą definiować autonomiczne obrazy lub listy obrazów do obsługi starszego interfejsu użytkownika. Ponadto istnieją atrybuty, które można ustawić w elemencie zawartości lub w poszczególnych obrazach za każdy element zawartości, aby zmienić czas i sposób wyświetlania tych zasobów.

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

 Jako pomoc w zakresie czytelności i konserwacji, manifest obrazu może używać symboli dla wartości atrybutów. Symbole są zdefiniowane w następujący sposób:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Podelementu**|**Definicja**|
|-|-|
|Import|Importuje symbole danego pliku manifestu do użycia w bieżącym manifeście.|
|Guid (identyfikator GUID)|Symbol reprezentuje identyfikator GUID i musi pasować do formatowania identyfikatora GUID.|
|ID (Identyfikator)|Symbol reprezentuje identyfikator i musi być nieujemną liczbą całkowitą.|
|Ciąg|Symbol reprezentuje dowolną wartość ciągu.|

 W symbolach jest rozróżniana wielkość liter i istnieje odwołanie do niej przy użyciu składni $ (symbol-nazwa):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Niektóre symbole są wstępnie zdefiniowane dla wszystkich manifestów. Mogą one być używane w atrybucie URI \<Source> \<Import> elementu lub do odwoływania się do ścieżek na komputerze lokalnym.

|**Symbol**|**Opis**|
|-|-|
|CommonProgramFiles|Wartość zmiennej środowiskowej% CommonProgramFiles%|
|LocalAppData|Wartość zmiennej środowiskowej% LocalAppData%|
|ManifestFolder|Folder zawierający plik manifestu|
|Czy|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika|
|ProgramFiles|Wartość zmiennej środowiskowej% ProgramFiles%|
|System|Folder Windows\System32|
|WinDir|Wartość zmiennej środowiskowej% WinDir%|

 **Obraz**

 \<Image>Element definiuje obraz, do którego może odwoływać się moniker. Identyfikatory GUID i ID razem tworzą moniker obrazu. Moniker obrazu musi być unikatowy w całej bibliotece obrazów. Jeśli więcej niż jeden obraz ma daną moniker, pierwszy napotkany podczas kompilowania biblioteki jest zachowywany.

 Musi zawierać co najmniej jedno źródło. Mimo że źródła o rozmiarze neutralnym będą dawać najlepsze wyniki dla szerokiego zakresu rozmiarów, nie są one wymagane. Jeśli zostanie wyświetlona prośba o obraz rozmiaru, który nie jest zdefiniowany w \<Image> elemencie i nie ma źródła o rozmiarze neutralnym, usługa wybierze Źródło najlepszego rozmiaru i przeskaluje je do żądanego rozmiaru.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Atrybut**|**Definicja**|
|-|-|
|Guid (identyfikator GUID)|Potrzeb Część identyfikatora GUID obrazu monikera|
|ID (Identyfikator)|Potrzeb Część identyfikatora monikera obrazu|
|AllowColorInversion|[Opcjonalne, wartość domyślna true] Wskazuje, czy obraz może być programowo odwrócony, gdy jest używany na ciemnym tle.|

 **Element źródłowy**

 \<Source>Element definiuje pojedynczy zasób źródłowy obrazu (XAML i PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Atrybut**|**Definicja**|
|-|-|
|Adresu|Potrzeb Identyfikator URI, który definiuje miejsce, z którego można załadować obraz. Może to być jedna z następujących opcji:<br /><br /> - [Identyfikator URI pakietu](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) przy użyciu urzędu Application:///<br /><br /> -Bezwzględne odwołanie do zasobu składnika<br /><br /> -Ścieżka do pliku zawierającego zasób natywny|
|Tło|Obowiązkowe Wskazuje, jaki rodzaj tła ma być używany.<br /><br /> Może to być jedna z następujących opcji:<br /><br /> - *Jasne*: Źródło może być używane na jasnym tle.<br /><br /> - *Ciemny*: Źródło może być używane w ciemnym tle.<br /><br /> - *HighContrast*: Źródło może być używane na dowolnym tle w trybie duży kontrast.<br /><br /> - *HighContrastLight*: Źródło może być używane na jasnym tle w trybie duży kontrast.<br /><br /> -*HighContrastDark*: Źródło może być używane na ciemnym tle w trybie duży kontrast.<br /><br /> Jeśli atrybut **Background** zostanie pominięty, źródło może być używane w dowolnym tle.<br /><br /> Jeśli **tło** jest *jasne*, *ciemne*, *HighContrastLight* lub *HighContrastDark*, kolory źródła nigdy nie są odwracane. Jeśli **tło** zostanie pominięte lub ustawiona na *HighContrast*, inwersja kolorów źródła jest kontrolowana przez atrybut **AllowColorInversion** obrazu.|

 \<Source>Element może mieć dokładnie jeden z następujących opcjonalnych podelementów:

|**Element**|**Atrybuty (wszystkie wymagane)**|**Definicja**|
|-|-|-|
|\<Size>|Wartość|Źródło będzie używane dla obrazów o danym rozmiarze (w jednostkach urządzeń). Obraz będzie kwadratowy.|
|\<SizeRange>|MinSize, brak|Źródło będzie używane dla obrazów z MinSize do rozmiaru całkowitego (w jednostkach urządzeń) włącznie. Obraz będzie kwadratowy.|
|\<Dimensions>|Szerokość, Wysokość|Źródło będzie używane dla obrazów o danej szerokości i wysokości (w jednostkach urządzeń).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Źródło będzie używane w przypadku obrazów o minimalnej szerokości/wysokości do maksymalnej szerokości/wysokości (w jednostkach urządzeń) włącznie.|

 \<Source>Element może również mieć opcjonalny \<NativeResource> podelement, który definiuje, \<Source> który jest ładowany z zestawu natywnego, a nie z zestawu zarządzanego.

```xml
<NativeResource Type="type" ID="int" />
```

|**Atrybut**|**Definicja**|
|-|-|
|Typ|Potrzeb Typ zasobu natywnego, XAML lub PNG|
|ID (Identyfikator)|Potrzeb Część identyfikatora całkowitego zasobu natywnego|

 **Obrazów**

 \<ImageList>Element definiuje kolekcję obrazów, które mogą być zwracane w jednym pasku. Pasek jest zbudowany na żądanie, zgodnie z potrzebami.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Atrybut**|**Definicja**|
|-|-|
|Guid (identyfikator GUID)|Potrzeb Część identyfikatora GUID obrazu monikera|
|ID (Identyfikator)|Potrzeb Część identyfikatora monikera obrazu|
|Zewnętrzna|[Opcjonalne, wartość domyślna to false] Wskazuje, czy moniker obrazu odwołuje się do obrazu w bieżącym manifeście.|

 Moniker zawartego obrazu nie musi odwoływać się do obrazu zdefiniowanego w bieżącym manifeście. Jeśli w bibliotece obrazów nie można znaleźć zawartego obrazu, w jego miejscu zostanie użyty pusty obraz zastępczy.

## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia
 **Sprawdzanie poprawności manifestu obrazu niestandardowego**

 W celu utworzenia manifestu niestandardowego zaleca się automatyczne generowanie manifestu przy użyciu narzędzia ManifestFromResources. Aby sprawdzić poprawność manifestu niestandardowego, uruchom przeglądarkę biblioteki obrazów i wybierz pozycję plik > Ustaw ścieżki... Aby otworzyć okno dialogowe katalogi wyszukiwania. Narzędzie użyje katalogów wyszukiwania do załadowania manifestów obrazów, ale będzie również używać ich do znajdowania plików DLL, które zawierają obrazy w manifeście, dlatego pamiętaj, aby w tym oknie dialogowym uwzględnić zarówno katalog manifestu, jak i biblioteki DLL.

 ![Wyszukiwanie podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-search.png "Wyszukiwanie podglądu biblioteki obrazów")

 Kliknij przycisk **Dodaj...** , aby wybrać nowe katalogi wyszukiwania do wyszukiwania manifestów i ich odpowiednich bibliotek DLL. Narzędzie zapamiętaje te katalogi wyszukiwania i będzie można je włączyć lub wyłączyć, sprawdzając lub usuwając zaznaczenie katalogu.

 Domyślnie narzędzie spróbuje znaleźć katalog instalacyjny programu Visual Studio i dodać te katalogi do listy katalogów wyszukiwania. Można ręcznie dodawać katalogi, które nie znajdują się w narzędziu.

 Po załadowaniu wszystkich manifestów narzędzie może służyć do przełączania kolorów **tła** , **dpi**, **dużego kontrastu** lub **grayscaling** obrazów, dzięki czemu użytkownik może wizualnie zbadać zasoby obrazu, aby upewnić się, że są one prawidłowo renderowane dla różnych ustawień.

 ![Tło podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-background.png "Tło podglądu biblioteki obrazów")

 Kolor tła można ustawić na wartość jasny, ciemny lub niestandardową. Wybranie opcji "kolor niestandardowy" spowoduje otwarcie okna dialogowego wyboru koloru i dodanie tego niestandardowego koloru do dolnej części pola kombi tła w celu łatwego odwoływania się później.

 ![Kolor niestandardowy podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-custom-color.png "Kolor niestandardowy podglądu biblioteki obrazów")

 Wybranie monikera obrazu powoduje wyświetlenie informacji dla każdego rzeczywistego obrazu znajdującego się za tym monikerem w okienku szczegółów obrazu po prawej stronie. Okienko umożliwia również użytkownikom kopiowanie monikera według nazwy lub przez pierwotny identyfikator GUID: wartość identyfikatora.

 ![Szczegóły obrazu podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-image-details.png "Szczegóły obrazu podglądu biblioteki obrazów")

 Informacje wyświetlane dla każdego źródła obrazu obejmują rodzaj tła, na którym ma być wyświetlana zawartość, czy mogą być przeznaczone do użytku lub duży kontrast, jakie rozmiary są poprawne dla lub czy nie są neutralne od rozmiaru i czy obraz pochodzi z zestawu natywnego.

 ![Podgląd biblioteki obrazów może być motywem](../../extensibility/internals/media/image-library-viewer-can-theme.png "Podgląd biblioteki obrazów może być motywem")

 Podczas sprawdzania poprawności manifestu obrazu zalecamy wdrożenie pliku DLL manifestu i obrazu w ich lokalizacjach w świecie rzeczywistym. Spowoduje to sprawdzenie, czy wszystkie ścieżki względne działają prawidłowo i czy biblioteka obrazów może znaleźć i załadować plik DLL manifestu i obrazu.

 **Wyszukiwanie KnownMonikers wykazu obrazów**

 Aby lepiej dopasować style programu Visual Studio, rozszerzenie programu Visual Studio może używać obrazów w katalogu obrazów programu Visual Studio, a nie do tworzenia własnych i używania własnych. Dzięki temu nie trzeba obsługiwać tych obrazów i gwarantujemy, że obraz będzie miał obraz o wysokiej rozdzielczości DPI, dlatego powinien wyglądać poprawnie we wszystkich ustawieniach DPI obsługiwanych przez program Visual Studio.

 Przeglądarka biblioteki obrazów umożliwia przeszukiwanie manifestu, aby użytkownik mógł znaleźć moniker reprezentujący zasób obrazu i używać tego monikera w kodzie. Aby wyszukać obrazy, wprowadź żądany termin wyszukiwania w polu wyszukiwania i naciśnij klawisz ENTER. Na pasku stanu u dołu będzie wyświetlana liczba dopasowań znalezionych z łącznej liczby obrazów we wszystkich manifestach.

 ![Filtr podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter.png "Filtr podglądu biblioteki obrazów")

 Podczas wyszukiwania monikerów obrazów w istniejących manifestach zalecamy wyszukiwanie i używanie tylko monikerów wykazu obrazów programu Visual Studio, innych zamierzonych publicznie dostępnych monikerów lub własnych niestandardowych monikerów. W przypadku używania niepublicznych monikerów niestandardowy interfejs użytkownika może być uszkodzony lub jego obrazy uległy zmianie w nieoczekiwany sposób, jeśli te niepubliczne monikery i obrazy zostaną zmienione lub zaktualizowane.

 Ponadto możliwe jest wyszukiwanie według identyfikatora GUID. Ten typ wyszukiwania jest przydatny do filtrowania listy do jednego manifestu lub pojedynczej podsekcji manifestu, jeśli ten manifest zawiera wiele identyfikatorów GUID.

 ![Identyfikator GUID filtru podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Identyfikator GUID filtru podglądu biblioteki obrazów")

 Na koniec wyszukiwanie według identyfikatora jest również możliwe.

 ![Identyfikator filtru podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter-id.png "Identyfikator filtru podglądu biblioteki obrazów")

## <a name="notes"></a>Uwagi

- Domyślnie narzędzie pobierze kilka manifestów obrazów znajdujących się w katalogu instalacyjnym programu Visual Studio. Jedyną z nich, która ma publicznie wykorzystane monikery, jest manifest **Microsoft. VisualStudio. ImageCatalog** . GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 ( **nie** Przesłoń tego identyfikatora GUID w manifeście niestandardowym) Typ: KnownMonikers

- Narzędzie próbuje uruchomić polecenie, aby załadować wszystkie znalezione manifesty obrazu, co może potrwać kilka sekund. Może to być również powolne lub nieodpowiadające podczas ładowania manifestów.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 To narzędzie nie generuje żadnych danych wyjściowych.

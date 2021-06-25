---
title: Przeglądarka bibliotek obrazów | Microsoft Docs
description: Dowiedz się więcej o Visual Studio podglądu bibliotek obrazów, które ładuje i wyszukuje manifesty obrazów, umożliwiając wyświetlanie atrybutów obrazu i manipulowanie nimi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02e7c5d5ed45b7a6c19c248e949e667ec0a1bdc0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898713"
---
# <a name="image-library-viewer"></a>Przeglądarka biblioteki obrazów
Narzędzie Visual Studio Image Library Viewer może ładować i wyszukiwać manifesty obrazów, umożliwiając użytkownikowi manipulowanie nimi w taki sam sposób, Visual Studio sposób. Użytkownik może zmieniać tło, rozmiary, dpi, wysoki kontrast i inne ustawienia. Narzędzie wyświetla również informacje ładowania dla każdego manifestu obrazu i wyświetla informacje o źródle dla każdego obrazu w manifeście obrazu. To narzędzie jest przydatne w przypadku:

1. Diagnozowanie błędów

2. Upewnianie się, że atrybuty są poprawnie ustawione w manifestach obrazu niestandardowego

3. Wyszukiwanie obrazów w katalogu obrazów Visual Studio, dzięki czemu rozszerzenie Visual Studio może używać obrazów, które pasują do stylu Visual Studio

   ![Biblioteka obrazów Viewer Hero](../../extensibility/internals/media/image-library-viewer-hero.png "Biblioteka obrazów Viewer Hero")

   **Moniker obrazów**

   Moniker obrazu (lub krótka monikerka) to para identyfikatorów GUID:ID, która jednoznacznie identyfikuje zasób obrazu lub zasób listy obrazów w bibliotece obrazów.

   **Pliki manifestu obrazu**

   Pliki manifestu obrazu (imagemanifest) to pliki XML definiujące zestaw zasobów obrazów, monikery reprezentujące te zasoby oraz rzeczywisty obraz lub obrazy reprezentujące każdy zasób. Manifesty obrazów mogą definiować obrazy autonomiczne lub listy obrazów w celu obsługi starszego interfejsu użytkownika. Ponadto istnieją atrybuty, które można ustawić dla zasobu lub na poszczególnych obrazach poszczególnych zasobów, aby zmienić czas i sposób wyświetlania tych zasobów.

   **Schemat manifestu obrazu**

   Kompletny manifest obrazu wygląda następująco:

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

|**Podelement**|**Definicja**|
|-|-|
|Importuj|Importuje symbole danego pliku manifestu do użycia w bieżącym manifeście.|
|Guid (identyfikator GUID)|Symbol reprezentuje identyfikator GUID i musi być zgodne z formatowaniem identyfikatora GUID.|
|ID (Identyfikator)|Symbol reprezentuje identyfikator i musi być liczbą całkowitą niegeneratywną.|
|Ciąg|Symbol reprezentuje dowolną wartość ciągu.|

 W symbolach jest rozróżniana wielkość liter, do których odwołuje się składnia $(nazwa-symbolu):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Niektóre symbole są wstępnie zdefiniowane dla wszystkich manifestów. Mogą one być używane w atrybutu Uri elementu lub , aby odwoływać się \<Source> do ścieżek na komputerze \<Import> lokalnym.

|**Symbol**|**Opis**|
|-|-|
|CommonProgramFiles|Wartość zmiennej środowiskowej %CommonProgramFiles%|
|Localappdata|Wartość zmiennej środowiskowej %LocalAppData%|
|ManifestFolder|Folder zawierający plik manifestu|
|Mydocuments|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika|
|ProgramFiles|Wartość zmiennej środowiskowej %ProgramFiles%|
|System|Folder Windows\System32|
|Windir|Wartość zmiennej środowiskowej %WinDir%|

 **Obraz**

 Element \<Image> definiuje obraz, do których może odwoływać się moniker. Identyfikator GUID i identyfikator razem tworzą moniker obrazu. Moniker obrazu musi być unikatowy w całej bibliotece obrazów. Jeśli więcej niż jeden obraz ma podaną monikerkę, pierwszym obrazem napotkanym podczas tworzenia biblioteki jest ten, który jest zachowywany.

 Musi zawierać co najmniej jedno źródło. Mimo że źródła neutralne pod względem rozmiaru zapewniają najlepsze wyniki w szerokim zakresie rozmiarów, nie są one wymagane. Jeśli usługa zostanie poproszony o obraz o rozmiarze nie zdefiniowanym w elemencie i nie ma źródła neutralnego dla rozmiaru, usługa wybierze najlepsze źródło specyficzne dla rozmiaru i przeskaluje je do żądanego \<Image> rozmiaru.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Atrybut**|**Definicja**|
|-|-|
|Guid (identyfikator GUID)|[Wymagane] Część identyfikatora GUID moniker obrazu|
|ID (Identyfikator)|[Wymagane] Część identyfikatora monikera obrazu|
|AllowColorInversion|[Opcjonalnie, wartość domyślna true] Wskazuje, czy kolory obrazu mogą być programowo odwrócone, gdy są używane na ciemnym tle.|

 **Element źródłowy**

 Element definiuje pojedynczy zasób źródłowy \<Source> obrazu (XAML i PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Atrybut**|**Definicja**|
|-|-|
|Identyfikator uri|[Wymagane] URI definiujący miejsce, z którego można załadować obraz. Może to być jedna z następujących opcji:<br /><br /> - A [Pack URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) using the application:/// authority (URI pakietu przy użyciu application:/// urzędu)<br /><br /> - Bezwzględna odwołanie do zasobów składnika<br /><br /> - Ścieżka do pliku zawierającego zasób natywny|
|Tło|[Opcjonalnie] Wskazuje, jakie dane źródło ma być używane w tle.<br /><br /> Może to być jedna z następujących opcji:<br /><br /> - *Jasny:* źródła można używać na jasnym tle.<br /><br /> - *Ciemny:* źródła można używać na ciemnym tle.<br /><br /> - *HighContrast:* źródła można używać na dowolnym tle w duży kontrast trybie.<br /><br /> - *HighContrastLight:* źródła można używać na jasnym tle w duży kontrast trybu.<br /><br /> -*HighContrastDark:* źródła można używać na ciemnym tle w duży kontrast trybu.<br /><br /> Jeśli **atrybut Background** zostanie pominięty, źródło może być używane w dowolnym tle.<br /><br /> Jeśli **tło** ma kolor *Jasny,* *Ciemny,* *HighContrastLight* lub *HighContrastDark,* kolory źródła nigdy nie są odwrócone. Jeśli **ustawienie Background** zostanie pominięte lub ustawione na wartość *HighContrast,* odwrócenie kolorów źródła jest kontrolowane przez atrybut **AllowColorInversion** obrazu.|

 Element \<Source> może mieć dokładnie jeden z następujących opcjonalnych podelementów:

|**Element**|**Atrybuty (wszystkie wymagane)**|**Definicja**|
|-|-|-|
|\<Size>|Wartość|Źródło będzie używane dla obrazów o danym rozmiarze (w jednostkach urządzenia). Obraz będzie kwadratowy.|
|\<SizeRange>|MinSize, MaxSize|Źródło będzie używane w przypadku obrazów od MinSize do MaxSize (w jednostkach urządzenia) włącznie. Obraz będzie kwadratowy.|
|\<Dimensions>|Szerokość, Wysokość|Źródło będzie używane dla obrazów o danej szerokości i wysokości (w jednostkach urządzenia).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Źródło będzie używane dla obrazów z opcji od minimalnej szerokości/wysokości do maksymalnej szerokości/wysokości (w jednostkach urządzenia) włącznie.|

 Element może również mieć opcjonalny podelement, który definiuje element , który jest ładowany z zestawu natywnego, \<Source> \<NativeResource> a nie \<Source> zestawu zarządzanego.

```xml
<NativeResource Type="type" ID="int" />
```

|**Atrybut**|**Definicja**|
|-|-|
|Typ|[Wymagane] Typ zasobu natywnego ( XAML lub PNG)|
|ID (Identyfikator)|[Wymagane] Część identyfikatora liczby całkowitej zasobu natywnego|

 **Imagelist**

 Element \<ImageList> definiuje kolekcję obrazów, które mogą być zwracane w jednym pasku. Pasek jest zbudowany na żądanie, zgodnie z potrzebami.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Atrybut**|**Definicja**|
|-|-|
|Guid (identyfikator GUID)|[Wymagane] Część identyfikatora GUID moniker obrazu|
|ID (Identyfikator)|[Wymagane] Część identyfikatora monikera obrazu|
|Zewnętrzna|[Opcjonalna, domyślna wartość false] Wskazuje, czy monikera obrazu odwołuje się do obrazu w bieżącym manifeście.|

 Moniker zawartego obrazu nie musi odwoływać się do obrazu zdefiniowanego w bieżącym manifeście. Jeśli zawartego obrazu nie można znaleźć w bibliotece obrazów, w jego miejscu zostanie użyty pusty obraz zastępczy.

## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia
 **Sprawdzania poprawności niestandardowego manifestu obrazu**

 Aby utworzyć manifest niestandardowy, zalecamy użycie narzędzia ManifestFromResources do automatycznego wygenerowania manifestu. Aby zweryfikować manifest niestandardowy, uruchom podgląd biblioteki obrazów i wybierz pozycję > ustaw ścieżki... , aby otworzyć okno dialogowe Wyszukiwanie katalogów. Narzędzie użyje katalogów wyszukiwania do załadowania manifestów obrazów, ale użyje ich również do znalezienia plików .dll zawierających obrazy w manifeście, dlatego upewnij się, że w tym oknie dialogowym znajdują się zarówno katalogi manifestu, jak i dll.

 ![Wyszukiwanie podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-search.png "Wyszukiwanie podglądu biblioteki obrazów")

 Kliknij **pozycję Dodaj...,** aby wybrać nowe katalogi wyszukiwania w celu wyszukania manifestów i odpowiadających im bibliotek DLL. Narzędzie zapamięta te katalogi wyszukiwania i można je włączać lub wyłączać przez zaznaczenie lub usunięcie zaznaczenia katalogu.

 Domyślnie narzędzie spróbuje znaleźć katalog Visual Studio i dodać te katalogi do listy katalogów wyszukiwania. Katalogi można dodać ręcznie, których narzędzie nie znajdzie.

 Po załadowaniu wszystkich manifestów narzędzie może służyć  do przełączania kolorów tła,  **DPI,** wysokiego kontrastu lub skalowania na szaro dla obrazów, dzięki czemu użytkownik może wizualnie sprawdzać zasoby obrazów w celu sprawdzenia, czy są one poprawnie renderowane pod względem różnych ustawień.

 ![Tło podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-background.png "Tło podglądu biblioteki obrazów")

 Kolor tła można ustawić na Jasny, Ciemny lub wartość niestandardową. Wybranie opcji "Kolor niestandardowy" spowoduje otwarcie okna dialogowego wyboru koloru i dodanie tego koloru niestandardowego w dolnej części pola kombi tła w celu późniejszego łatwego odwoływania.

 ![Kolor niestandardowy przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-custom-color.png "Kolor niestandardowy przeglądarki biblioteki obrazów")

 Wybranie monikera obrazu powoduje wyświetlenie informacji o każdym rzeczywistym obrazie, za którym ta monikera jest wyświetlana w okienku Szczegóły obrazu po prawej stronie. Okienko umożliwia również użytkownikom kopiowanie monikera według nazwy lub pierwotnej wartości identyfikatora GUID:ID.

 ![Szczegóły obrazu przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-image-details.png "Szczegóły obrazu przeglądarki biblioteki obrazów")

 Informacje wyświetlane dla każdego źródła obrazu obejmują rodzaj tła, w jakim ma być wyświetlane, czy można je o treściach lub obsługuje program duży kontrast, jakie rozmiary są prawidłowe, czy neutralne pod względem rozmiaru oraz czy obraz pochodzi z zestawu macierzystego.

 ![Podgląd biblioteki obrazów może być motywem](../../extensibility/internals/media/image-library-viewer-can-theme.png "Podgląd biblioteki obrazów może być motywem")

 Podczas sprawdzania poprawności manifestu obrazu zalecamy wdrożenie manifestu i biblioteki DLL obrazów w ich rzeczywistych lokalizacjach. Pozwoli to sprawdzić, czy wszystkie ścieżki względne działają prawidłowo oraz czy biblioteka obrazów może znaleźć i załadować manifest i bibliotekę DLL obrazów.

 **Wyszukiwanie katalogu obrazów KnownMonikers**

 Aby lepiej dopasować Visual Studio, rozszerzenie Visual Studio może używać obrazów w katalogu obrazów Visual Studio zamiast tworzyć i używać własnych. Dzięki temu nie trzeba utrzymywać tych obrazów i gwarantuje, że obraz będzie miał obraz zapasowy o wysokiej rozdzielczości DPI, więc powinien wyglądać poprawnie we wszystkich ustawieniach DPI, które Visual Studio obsługuje.

 Przeglądarka biblioteki obrazów umożliwia przeszukiwanie manifestu, dzięki czemu użytkownik może znaleźć monikera reprezentującą zasób obrazu i użyć tej monikera w kodzie. Aby wyszukać obrazy, wprowadź odpowiedni termin wyszukiwania w polu wyszukiwania i naciśnij klawisz Enter. Na pasku stanu u dołu będzie wyświetlana liczba dopasowania znalezionych spośród wszystkich obrazów we wszystkich manifestach.

 ![Filtr przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter.png "Filtr przeglądarki biblioteki obrazów")

 Podczas wyszukiwania monikerów obrazów w istniejących manifestach zalecamy wyszukiwanie i używanie tylko monikerów usługi Visual Studio Image Catalog, innych celowo dostępnych monikerów lub własnych niestandardowych monikerów. Jeśli używasz niepubliczne monikerów, niestandardowy interfejs użytkownika może zostać uszkodzony lub jego obrazy mogą zostać zmienione w nieoczekiwany sposób, jeśli lub gdy te niepubliczne monikery i obrazy zostaną zmienione lub zaktualizowane.

 Ponadto możliwe jest wyszukiwanie według identyfikatora GUID. Ten typ wyszukiwania jest przydatny do filtrowania listy do pojedynczego manifestu lub pojedynczej podsekcji manifestu, jeśli ten manifest zawiera wiele identyfikatorów GUID.

 ![Identyfikator GUID filtru przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Identyfikator GUID filtru przeglądarki biblioteki obrazów")

 Możliwe jest również wyszukiwanie według identyfikatora.

 ![Identyfikator filtru przeglądarki biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter-id.png "Identyfikator filtru przeglądarki biblioteki obrazów")

## <a name="notes"></a>Uwagi

- Domyślnie narzędzie ściąga kilka manifestów obrazów obecnych w katalogu Visual Studio instalacji. Jedynym publicznie dostępnym monikerem jest manifest **Microsoft.VisualStudio.ImageCatalog.** Identyfikator GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (nie zastępuj tego identyfikatora GUID w manifeście niestandardowym) Typ: KnownMonikers 

- Narzędzie próbuje przy uruchomieniu załadować wszystkie znalezione manifesty obrazów, więc może mieć kilka sekund, aż aplikacja faktycznie pojawi się. Ładowanie manifestów może być również powolne lub nie odpowiadać.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 To narzędzie nie generuje żadnych danych wyjściowych.

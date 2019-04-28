---
title: Dokumentacja języka DGML (Directed Graph Markup Language)
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b473dc706cd7183835c5d84091fb53e45337c013
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834220"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Dokumentacja języka DGML (Directed Graph Markup Language)

Przekierowanie Graph Markup Language (DGML) opisano informacje używane do wizualizacji i przeprowadzać analizę złożoności i jest używany format można utrwalić map kodu w programie Visual Studio. Używa prostego formatu XML do opisania zarówno cyklicznie i acyklicznie kierowanych wykresów. Wykres kierowany jest zestawem węzłów połączonych przez łącza lub krawędzie. Węzły i łącza mogą być używane do reprezentacji struktur sieciowych, takich jak elementy projektu oprogramowania.

Należy pamiętać, że niektóre wersje programu Visual Studio obsługuje tylko podzestaw możliwości DGML, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Podczas edycji pliku .dgml technologia IntelliSense pomaga identyfikować atrybuty, które są dostępne dla każdego elementu i ich wartości. Aby określić kolor w atrybucie, użyj nazw dla pospolitych kolorów, takich jak „Niebieski” lub wartości szesnastkowych ARGB, takich jak „#ffa0b1c3”. DGML używa małego podzbioru formatów definicji koloru Windows Presentation Foundation (WPF). Aby uzyskać więcej informacji, zobacz [klasa kolory](http://go.microsoft.com/fwlink/?LinkId=182345).

## <a name="DGML"></a> Składnia DGML

W poniższej tabeli opisano rodzaje elementów, które są używane w DGML:

- `<DirectedGraph></DirectedGraph>`

   Ten element jest głównym elementem dokumentu (.dgml) mapy kodu. Wszystkie inne elementy DGML pojawiają się w zakresie tego elementu.

   Na poniższej liście opisano opcjonalne atrybuty, które mogą obejmować:

   `Background` — Kolor tła mapy

   `BackgroundImage` — Lokalizacja pliku obrazu do użycia jako tło w formie mapy.

   `GraphDirection` -Jeśli mapa została ustawiona na układ drzewa (`Sugiyama`), Rozmieść węzły, tak aby większość łączy przepływu w określonym kierunku: `TopToBottom`, `BottomToTop`, `LeftToRight`, lub `RightToLeft`. Zobacz [zmienić układ mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout` -Ustawienia mapy następujących układów: `None`, `Sugiyama` (układ drzewa) `ForceDirected` (szybkie klastry) lub `DependencyMatrix`. Zobacz [zmienić układ mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance` -Nastavena mapy na układ drzewa lub układ szybkich klastrów, pokazują tylko węzły, które są przez określoną liczbę (1-7) łączy od wybranych węzłów. Zobacz [zmienić układ mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   Przykład:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   Ten opcjonalny element zawiera listę `<Node/>` elementów, które definiują węzły na mapie. Aby uzyskać więcej informacji, zobacz `<Node/>` elementu.

  > [!NOTE]
  > Podczas odwoływania się do niezdefiniowanego węzła w `<Link/>` element, tworzy mapę `<Node/>` elementu automatycznie.

   Przykład:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   Element ten określa pojedynczy węzeł. Wygląda na to, w ramach `<Nodes><Nodes/>` elementu listy.

   Element ten musi zawierać następujące atrybuty:

   `Id` -Unikatową nazwę węzła i wartość domyślną `Label` atrybutu, jeśli nie osobnej `Label` atrybut jest określony. Ta nazwa musi być zgodna `Source` lub `Target` atrybut łącza, który odwołuje się do niej.

   Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

   `Label` — Nazwa wyświetlana węzła.

   Atrybuty stylu. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` — Nazwa kategorii identyfikującej elementy, które współdzielą ten atrybut. Aby uzyskać więcej informacji, zobacz `<Category/>` elementu.

   `Property` — Nazwa właściwości identyfikująca elementy, które mają tę samą wartość właściwości. Aby uzyskać więcej informacji, zobacz `<Property/>` elementu.

   `Group` — Jeśli węzeł zawiera inne węzły, ustaw ten atrybut na `Expanded` lub `Collapsed` pokazać lub ukryć jego zawartość. Musi istnieć `<Link/>` element, który zawiera `Category="Contains"` atrybutu i określa węzeł nadrzędny jako źródłowy oraz węzeł podrzędny jako docelowy. Zobacz [grupować elementy kodu](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility` — Ustaw ten atrybut na `Visible`, `Hidden`, lub `Collapsed`. Używa `System.Windows.Visibility`. Zobacz [ukrywanie lub pokazywanie węzłów i łączy](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` — Ustaw ten atrybut, aby utworzyć łącze do dokumentu lub adresu URL. Zobacz [połączyć dokumenty lub adresy URL elementów kodu i linków](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

   Przykład:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   Element ten zawiera listę `<Link>` elementy, które definiują łącza między węzłami. Aby uzyskać więcej informacji, zobacz `<Link/>` elementu.

   Przykład:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   Element ten określa pojedyncze łącze, które łączy węzeł źródłowy z węzłem docelowym. Wygląda na to, w ramach `<Links></Links>` elementu listy.

  > [!NOTE]
  > Jeśli ten element odwołuje się do niezdefiniowanego węzła, dokument mapy automatycznie tworzy węzeł, który ma określone atrybuty, jeśli istnieje.

   Element ten musi zawierać następujące atrybuty:

   `Source` -Węzeł źródłowy łącza

   `Target` -Węzeł docelowy łącza

   Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

   `Label` — Nazwa wyświetlana łącza

   Atrybuty stylu. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` — Nazwa kategorii identyfikującej elementy, które współdzielą ten atrybut. Aby uzyskać więcej informacji, zobacz `<Category/>` elementu.

   `Property` — Nazwa właściwości identyfikująca elementy, które mają tę samą wartość właściwości. Aby uzyskać więcej informacji, zobacz `<Property/>` elementu.

   Przykład:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   Element ten zawiera listę `<Category/>` elementów. Aby uzyskać więcej informacji, zobacz `<Category/>` elementu.

   Przykład:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   Ten element definiuje `Category` atrybut, który jest używany do identyfikowania elementów współdzielących ten atrybut. A `Category` atrybut może służyć do organizowania elementów mapy, dostarczania współdzielonych atrybutów poprzez dziedziczenie lub definiowania dodatkowych metadanych.

   Element ten musi zawierać następujące atrybuty:

   `Id` — Unikatowa nazwa kategorii i wartość domyślną `Label` atrybutu, jeśli nie osobnej `Label` atrybut jest określony.

   Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

   `Label` — Przyjazna dla czytelnika nazwa dla kategorii.

   `BasedOn` — Kategoria nadrzędna, z którym `<Category/>` bieżącego elementu dziedziczy.

   W przykładzie dla tego elementu `FailedTest` kategorii dziedziczy jej `Stroke` atrybut z `PassedTest` kategorii. Zobacz sekcję "Tworzenie kategorii hierarchicznych" w [mapy Dostosuj kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Kategorie dostarczają również niektórych podstawowych zachowań szablonu, kontrolują wygląd węzłów i łączy, gdy są one wyświetlane na mapie. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Przykład:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   Element ten zawiera listę `<Property/>` elementów. Aby uzyskać więcej informacji, zobacz `<Property/>` elementu.

   Przykład:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   Ten element definiuje `Property` atrybut, który służy do przypisywania wartości do dowolnego atrybutu, włączając kategorie i inne właściwości lub elementów DGML.

   Element ten musi zawierać następujące atrybuty:

  - `Id` -Unikatową nazwę właściwości i wartość domyślną `Label` atrybutu, jeśli nie osobnej `Label` atrybut jest określony.

  - `DataType` — Typ danych przechowywanych przez właściwość

    Jeśli chcesz, aby właściwość pojawiła się w **właściwości** oknie, użyj `Label` właściwości w celu określenia nazwy wyświetlania właściwości.

    Zobacz [przypisywać kategorie elementów kodu i linków](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

    Przykład:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="AddAlias"></a> Aliasy dla najczęściej używanych ścieżek

Zamienianie najczęściej używanych ścieżek na aliasy pomaga zredukować rozmiar pliku .dgml i czas wymagany do załadowania lub zapisania pliku. Aby utworzyć alias, należy dodać `<Paths></Paths>` sekcji na końcu pliku .dgml. W tej sekcji Dodaj `<Path/>` element, aby zdefiniować alias dla ścieżki:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

Aby odwoływać się do aliasu z elementu w pliku .dgml, należy ująć `Id` z \<Path / > znak dolara ($) i nawiasy (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
---
title: Dokumentacja języka DGML (Directed Graph Markup Language)
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b038acd9527cae197223e288349e431e81ea6dd6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748406"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Dokumentacja języka DGML (Directed Graph Markup Language)

Program Direct Graph Markup Language (DGML) opisuje informacje używane do wizualizacji oraz do analizy złożoności i jest formatem używanym do utrwalania map kodu w programie Visual Studio. Używa prostego kodu XML do opisywania zarówno cyklicznie, jak i acykliczne wykresy ukierunkowane. Wykres kierowany jest zestawem węzłów połączonych przez łącza lub krawędzie. Węzły i łącza mogą być używane do reprezentacji struktur sieciowych, takich jak elementy projektu oprogramowania.

Należy pamiętać, że niektóre wersje programu Visual Studio obsługują tylko podzbiór funkcji DGML, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Podczas edycji pliku .dgml technologia IntelliSense pomaga identyfikować atrybuty, które są dostępne dla każdego elementu i ich wartości. Aby określić kolor w atrybucie, użyj nazw dla pospolitych kolorów, takich jak „Niebieski” lub wartości szesnastkowych ARGB, takich jak „#ffa0b1c3”. DGML używa małego podzbioru formatów definicji koloru Windows Presentation Foundation (WPF). Aby uzyskać więcej informacji, zobacz [klasy Colors](http://go.microsoft.com/fwlink/?LinkId=182345).

## <a name="DGML"></a>Składnia DGML

W poniższej tabeli opisano rodzaje elementów, które są używane w DGML:

- `<DirectedGraph></DirectedGraph>`

   Ten element jest elementem głównym dokumentu mapy kodu (. dgml). Wszystkie inne elementy DGML pojawiają się w zakresie tego elementu.

   Na poniższej liście opisano opcjonalne atrybuty, które mogą obejmować:

   `Background` — kolor tła mapy

   `BackgroundImage` — lokalizacja pliku obrazu do użycia jako tło w formie mapy.

   `GraphDirection` — gdy mapa jest ustawiona na układ drzewa (`Sugiyama`), Rozmieść węzły tak, aby większość przepływów linków w określonym kierunku: `TopToBottom`, `BottomToTop`, `LeftToRight` lub `RightToLeft`. Zobacz [Zmiana układu mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout` — Ustaw mapę dla następujących układów: `None`, `Sugiyama` (układ drzewa), `ForceDirected` (szybkie klastry) lub `DependencyMatrix`. Zobacz [Zmiana układu mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance` — gdy mapa jest ustawiona na układ drzewa lub szybkie klastry, Pokaż tylko te węzły, które mają określoną liczbę (1-7) linków od wybranych węzłów. Zobacz [Zmiana układu mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

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

   Ten opcjonalny element zawiera listę elementów `<Node/>`, które definiują węzły na mapie. Aby uzyskać więcej informacji, zobacz `<Node/>` elementu.

  > [!NOTE]
  > Gdy odwołujesz się do niezdefiniowanego węzła w elemencie `<Link/>`, Mapa tworzy `<Node/>` element automatycznie.

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

   Element ten określa pojedynczy węzeł. Pojawia się na liście elementów `<Nodes><Nodes/>`.

   Element ten musi zawierać następujące atrybuty:

   `Id` — unikatowa nazwa węzła i wartość domyślna atrybutu `Label`, jeśli nie zostanie określony oddzielny atrybut `Label`. Ta nazwa musi być zgodna z atrybutem `Source` lub `Target` linku, który odwołuje się do niego.

   Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

   `Label` — nazwa wyświetlana węzła.

   Atrybuty stylu. Aby dowiedzieć [się, jak dostosować mapy kodu, edytuj pliki DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` — nazwa kategorii, która identyfikuje elementy, które współużytkują ten atrybut. Aby uzyskać więcej informacji, zobacz `<Category/>` elementu.

   `Property` — nazwa właściwości, która identyfikuje elementy, które mają tę samą wartość właściwości. Aby uzyskać więcej informacji, zobacz `<Property/>` elementu.

   `Group` — Jeśli węzeł zawiera inne węzły, ustaw ten atrybut na `Expanded` lub `Collapsed`, aby pokazać lub ukryć jego zawartość. Musi istnieć element `<Link/>`, który zawiera atrybut `Category="Contains"` i określa węzeł nadrzędny jako węzeł źródłowy i węzeł podrzędny jako węzeł docelowy. Zobacz [elementy kodu grupy](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility` — Ustaw ten atrybut na `Visible`, `Hidden` lub `Collapsed`. Używa `System.Windows.Visibility`. Zobacz [ukrywanie lub pokazywanie węzłów i linków](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` — Ustaw ten atrybut na link do dokumentu lub adresu URL. Zobacz [łączenie dokumentów lub adresów URL z elementami kodu i łączami](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

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

   Ten element zawiera listę elementów `<Link>`, które definiują linki między węzłami. Aby uzyskać więcej informacji, zobacz `<Link/>` elementu.

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

   Element ten określa pojedyncze łącze, które łączy węzeł źródłowy z węzłem docelowym. Pojawia się na liście elementów `<Links></Links>`.

  > [!NOTE]
  > Jeśli ten element odwołuje się do niezdefiniowanego węzła, dokument mapy automatycznie utworzy węzeł o określonych atrybutach (jeśli istnieją).

   Element ten musi zawierać następujące atrybuty:

   `Source` — węzeł źródłowy łącza

   `Target` — węzeł docelowy łącza

   Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

   `Label` — wyświetlana nazwa linku

   Atrybuty stylu. Aby dowiedzieć [się, jak dostosować mapy kodu, edytuj pliki DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` — nazwa kategorii, która identyfikuje elementy, które współużytkują ten atrybut. Aby uzyskać więcej informacji, zobacz `<Category/>` elementu.

   `Property` — nazwa właściwości, która identyfikuje elementy, które mają tę samą wartość właściwości. Aby uzyskać więcej informacji, zobacz `<Property/>` elementu.

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

   Ten element zawiera listę elementów `<Category/>`. Aby uzyskać więcej informacji, zobacz `<Category/>` elementu.

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

   Ten element definiuje atrybut `Category`, który służy do identyfikowania elementów, które współużytkują ten atrybut. Atrybut `Category` może służyć do organizowania elementów mapy, zapewniania atrybutów udostępnionych przez dziedziczenie lub definiowania dodatkowych metadanych.

   Element ten musi zawierać następujące atrybuty:

   `Id` — unikatowa nazwa kategorii i wartość domyślna atrybutu `Label`, jeśli nie zostanie określony oddzielny atrybut `Label`.

   Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

   `Label` — przyjazna dla czytnika nazwa dla kategorii.

   `BasedOn` — Kategoria nadrzędna, z której dziedziczy `<Category/>` bieżącego elementu.

   W przykładzie dla tego elementu Kategoria `FailedTest` dziedziczy atrybut `Stroke` z kategorii `PassedTest`. Zobacz "aby utworzyć kategorie hierarchiczne" w temacie [Dostosowywanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Kategorie zapewniają również podstawowe zachowanie szablonów, które kontroluje wygląd węzłów i łączy, gdy są wyświetlane na mapie. Aby dowiedzieć [się, jak dostosować mapy kodu, edytuj pliki DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

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

   Ten element zawiera listę elementów `<Property/>`. Aby uzyskać więcej informacji, zobacz `<Property/>` elementu.

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

   Ten element definiuje `Property` atrybutu, który służy do przypisywania wartości do dowolnego elementu lub atrybutu DGML, w tym kategorii i innych właściwości.

   Element ten musi zawierać następujące atrybuty:

  - `Id` — unikatowa nazwa właściwości i wartość domyślna atrybutu `Label`, jeśli nie zostanie określony oddzielny atrybut `Label`.

  - `DataType` — typ danych przechowywanych przez właściwość

    Jeśli chcesz, aby właściwość była widoczna w oknie **Właściwości** , użyj właściwości `Label`, aby określić nazwę wyświetlaną właściwości.

    Zobacz [Przypisywanie kategorii do elementów kodu i linków](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

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

### <a name="AddAlias"></a>Aliasy dla najczęściej używanych ścieżek

Zamienianie najczęściej używanych ścieżek na aliasy pomaga zredukować rozmiar pliku .dgml i czas wymagany do załadowania lub zapisania pliku. Aby utworzyć alias, należy dodać sekcję `<Paths></Paths>` na końcu pliku. dgml. W tej sekcji Dodaj element `<Path/>`, aby zdefiniować alias dla ścieżki:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

Aby odwołać się do aliasu z elementu w pliku. dgml, należy ująć `Id` elementu \<Path/> za pomocą znaku dolara ($) i nawiasów (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Zobacz także

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
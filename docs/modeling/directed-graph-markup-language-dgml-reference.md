---
title: Dokumentacja języka DGML (Directed Graph Markup Language)
description: Dowiedz się, w jaki sposób język DGML (Directed Graph Markup Language) opisuje informacje używane do wizualizacji i przeprowadzania analizy złożoności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: adaa09ca7c58652c85cf6c3510e9e47bc4af00f3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389114"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Dokumentacja języka DGML (Directed Graph Markup Language)

Directed Graph Markup Language (DGML) opisuje informacje używane do wizualizacji i przeprowadzania analizy złożoności oraz jest formatem używanym do utrwalania map kodu w Visual Studio. Używa on prostego kodu XML do opisywania zarówno cyklicznych, jak i acyklicznych grafów skierowanych. Wykres kierowany jest zestawem węzłów połączonych przez łącza lub krawędzie. Węzły i łącza mogą być używane do reprezentacji struktur sieciowych, takich jak elementy projektu oprogramowania.

Pamiętaj, że niektóre wersje Visual Studio obsługują tylko podzbiór możliwości DGML. Zobacz Obsługa wersji dla architektury i [narzędzi do modelowania](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

> [!NOTE]
> Podczas edycji pliku .dgml technologia IntelliSense pomaga identyfikować atrybuty, które są dostępne dla każdego elementu i ich wartości. Aby określić kolor w atrybucie, użyj nazw dla pospolitych kolorów, takich jak „Niebieski” lub wartości szesnastkowych ARGB, takich jak „#ffa0b1c3”. DGML używa małego podzbioru formatów definicji koloru Windows Presentation Foundation (WPF). Aby uzyskać więcej informacji, zobacz [Colors Class (Klasa kolorów).](/dotnet/api/system.windows.media.colors?view=netframework-4.8&preserve-view=true)

## <a name="dgml-syntax"></a><a name="DGML"></a> Składnia DGML

W poniższej tabeli opisano rodzaje elementów używanych w DGML:

- `<DirectedGraph></DirectedGraph>`

   Ten element jest głównym elementem dokumentu mapy kodu (dgml). Wszystkie inne elementy DGML pojawiają się w zakresie tego elementu.

   Na poniższej liście opisano opcjonalne atrybuty, które mogą obejmować:

   `Background` — kolor tła mapy

   `BackgroundImage` — lokalizacja pliku obrazu do użycia jako tło mapy.

   `GraphDirection` - Gdy mapa jest ustawiona na układ drzewa ( ), rozmieść węzły tak, aby większość łączy przepływała w `Sugiyama` określonym kierunku: `TopToBottom` , , `BottomToTop` lub `LeftToRight` `RightToLeft` . Zobacz [Zmienianie układu mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout` — Ustaw mapę na następujące układy: `None` , `Sugiyama` (układ drzewa), `ForceDirected` (szybkie klastry) lub `DependencyMatrix` . Zobacz [Zmienianie układu mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance` — Gdy mapa jest ustawiona na układ drzewa lub szybki układ klastrów, pokaż tylko te węzły, które są określoną liczbą (1–7) linków od wybranych węzłów. Zobacz [Zmienianie układu mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

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

   Ten opcjonalny element zawiera listę `<Node/>` elementów, które definiują węzły na mapie. Aby uzyskać więcej informacji, zobacz `<Node/>` element .

  > [!NOTE]
  > Gdy odwołujesz się do niezdefiniowanych węzłów w `<Link/>` elemencie, mapa automatycznie `<Node/>` tworzy element.

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

   Element ten określa pojedynczy węzeł. Pojawia się na `<Nodes><Nodes/>` liście elementów.

   Element ten musi zawierać następujące atrybuty:

   `Id` - Unikatowa nazwa węzła i wartość domyślna atrybutu, jeśli `Label` nie określono `Label` oddzielnego atrybutu. Ta nazwa musi odpowiadać `Source` atrybutowi lub `Target` linku, który się do niego odwołuje.

   Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

   `Label` — nazwa wyświetlana węzła.

   Atrybuty stylu. Zobacz [Dostosowywanie map kodu przez edycję plików DGML.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

   `Category` - Nazwa kategorii, która identyfikuje elementy, które współużytkuje ten atrybut. Aby uzyskać więcej informacji, zobacz `<Category/>` element .

   `Property` - Nazwa właściwości, która identyfikuje elementy, które mają tę samą wartość właściwości. Aby uzyskać więcej informacji, zobacz `<Property/>` element .

   `Group` - Jeśli węzeł zawiera inne węzły, ustaw ten atrybut na wartość lub , `Expanded` aby pokazać lub ukryć jego `Collapsed` zawartość. Musi być element, który zawiera atrybut i określa węzeł nadrzędny jako węzeł źródłowy, a węzeł podrzędny `<Link/>` `Category="Contains"` jako węzeł docelowy. Zobacz [Grupowanie elementów kodu](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility` - Ustaw ten atrybut na `Visible` , `Hidden` lub `Collapsed` . Używa `System.Windows.Visibility` . Zobacz [Ukrywanie lub pokazywanie węzłów i linków](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` — ustaw ten atrybut tak, aby łączył się z dokumentem lub adresem URL. Zobacz [Łączenie dokumentów lub adresów URL z elementami kodu i linkami](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

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

   Ten element zawiera listę `<Link>` elementów, które definiują połączenia między węzłami. Aby uzyskać więcej informacji, zobacz `<Link/>` element .

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

   Element ten określa pojedyncze łącze, które łączy węzeł źródłowy z węzłem docelowym. Pojawia się na `<Links></Links>` liście elementów.

  > [!NOTE]
  > Jeśli ten element odwołuje się do niezdefiniowanych węzłów, dokument mapy automatycznie tworzy węzeł, który ma określone atrybuty, jeśli takie są.

   Element ten musi zawierać następujące atrybuty:

   `Source` - Węzeł źródłowy linku

   `Target` - Węzeł docelowy linku

   Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

   `Label` - Nazwa wyświetlana linku

   Atrybuty stylu. Zobacz [Dostosowywanie map kodu przez edycję plików DGML.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

   `Category` - Nazwa kategorii, która identyfikuje elementy, które współużytkuje ten atrybut. Aby uzyskać więcej informacji, zobacz `<Category/>` element .

   `Property` - Nazwa właściwości, która identyfikuje elementy, które mają tę samą wartość właściwości. Aby uzyskać więcej informacji, zobacz `<Property/>` element .

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

   Ten element zawiera listę `<Category/>` elementów. Aby uzyskać więcej informacji, zobacz `<Category/>` element .

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

   Ten element definiuje `Category` atrybut, który służy do identyfikowania elementów, które współużytkuje ten atrybut. Atrybut może służyć do organizowania elementów mapy, zapewnienia udostępnionych atrybutów za pośrednictwem dziedziczenia `Category` lub zdefiniowania dodatkowych metadanych.

   Element ten musi zawierać następujące atrybuty:

   `Id` - Unikatowa nazwa kategorii i wartość domyślna `Label` atrybutu, jeśli nie określono `Label` oddzielnego atrybutu.

   Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

   `Label` — przyjazna dla czytelnika nazwa kategorii.

   `BasedOn` - Kategoria nadrzędna, z której dziedziczy element `<Category/>` bieżącego elementu.

   W przykładzie dla tego elementu kategoria `FailedTest` dziedziczy swój `Stroke` atrybut z `PassedTest` kategorii. Zobacz "Aby utworzyć kategorie hierarchiczne" w tece [Dostosowywanie map kodu przez edycję plików DGML.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

   Kategorie zapewniają również pewne podstawowe zachowanie szablonu, które steruje wyglądem węzłów i linków wyświetlanych na mapie. Zobacz [Dostosowywanie map kodu przez edycję plików DGML.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

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

   Ten element zawiera listę `<Property/>` elementów. Aby uzyskać więcej informacji, zobacz `<Property/>` element .

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

   Ten element definiuje atrybut, który służy do przypisywania wartości do dowolnego elementu LUB atrybutu DGML, w tym `Property` kategorii i innych właściwości.

   Element ten musi zawierać następujące atrybuty:

  - `Id` - Unikatowa nazwa właściwości i wartość domyślna atrybutu, jeśli `Label` nie określono `Label` oddzielnego atrybutu.

  - `DataType` - Typ danych przechowywanych przez właściwość

    Jeśli chcesz, aby właściwość pojawiła się w **oknie** Właściwości, użyj właściwości , aby określić `Label` nazwę wyświetlaną właściwości.

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

### <a name="aliases-for-commonly-used-paths"></a><a name="AddAlias"></a> Aliasy dla często używanych ścieżek

Zamienianie najczęściej używanych ścieżek na aliasy pomaga zredukować rozmiar pliku .dgml i czas wymagany do załadowania lub zapisania pliku. Aby utworzyć alias, dodaj sekcję na `<Paths></Paths>` końcu pliku .dgml. W tej sekcji dodaj `<Path/>` element w celu zdefiniowania aliasu ścieżki:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

Aby odwołać się do aliasu z elementu w pliku .dgml, należy ująć element w znak dolara `Id` \<Path/> ($) i nawiasy (()):

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

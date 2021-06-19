---
title: Dostosowanie map kodu przez edycję plików DGML
description: Dowiedz się, jak dostosować mapę kodu, edytując jej plik Directed Graph Markup Language (dgml).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b7c94834aeb6aa82efdb53dead97e26daa667c0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389491"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Dostosowanie map kodu przez edycję plików DGML

Aby dostosować mapę kodu, możesz edytować jej plik Directed Graph Markup Language (dgml). Na przykład można edytować elementy, aby określić style niestandardowe, przypisać właściwości i kategorie do elementów kodu i linków lub połączyć dokumenty lub adresy URL z elementami kodu lub linkami. Aby uzyskać więcej informacji na temat elementów DGML, zobacz [Directed Graph Markup Language (DGML) reference (Directed Graph Markup Language, DGML) reference (Directed Graph Markup Language, DGML) reference (Directed Graph Markup Language, DGML) reference (Directed Graph Markup Language](../modeling/directed-graph-markup-language-dgml-reference.md)

Edytuj plik .dgml mapy kodu w edytorze tekstów lub XML. Jeśli mapa jest częścią rozwiązania Visual Studio, wybierz ją w programie **Eksplorator rozwiązań,** otwórz menu skrótów, a następnie wybierz pozycję **Otwórz** za pomocą edytora **XML (tekstowego).**

> [!NOTE]
> Aby tworzyć mapy kodu, musisz mieć Visual Studio Enterprise wersji. Podczas edytowania mapy kodu Visual Studio usuwa wszystkie nieużywane elementy i atrybuty DGML, usuwając je podczas zapisywania pliku .dgml. Tworzy również elementy kodu automatycznie podczas ręcznego dodawania nowych linków. Podczas zapisywania pliku .dgml wszelkie atrybuty, które są dodawane do elementu, mogą się ponownie rozmieszczać w kolejności alfabetycznej.

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a> Grupowanie elementów kodu
 Możesz dodać nowe grupy lub przekonwertować istniejące węzły na grupę.

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. Aby przekonwertować element kodu na grupę, znajdź `<Node/>` element dla tego elementu kodu.

    \- lub —

    Aby dodać nową grupę, znajdź `<Nodes>` sekcję . Dodaj nowy `<Node/>` element.

3. W `<Node/>` elemencie dodaj atrybut , aby `Group` określić, czy grupa ma być rozwinięta, czy zwinięta. Na przykład:

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. W sekcji upewnij się, że element, który ma następujące atrybuty, istnieje dla każdej relacji między elementem kodu grupy `<Links>` `<Link/>` i jego podrzędnymi elementami kodu:

   - Atrybut `Source` określający element kodu grupy

   - Atrybut `Target` określający podrzędny element kodu

   - Atrybut `Category` określający relację między elementem kodu grupy i jego `Contains` podrzędnym elementem kodu

     Na przykład:

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    Aby uzyskać więcej informacji na temat `Category` atrybutu, zobacz [Przypisywanie kategorii do elementów kodu i linków](#AssignCategories).

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a> Zmienianie stylu mapy
 Kolor tła i kolor obramowania mapy można zmienić, edytując plik .dgml mapy. Aby zmienić styl elementów kodu i linków, zobacz [Zmienianie stylu elementów kodu i linków](#Highlight).

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. W `<DirectedGraph>` elemencie dodaj dowolny z następujących atrybutów, aby zmienić jego styl:

     Kolor tła

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Kolor obramowania

    ```xml
    Stroke="StrokeValue"
    ```

     Na przykład:

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a> Zmienianie stylu elementów kodu i linków

### <a name="CreateCustomStyles"></a>
 Style niestandardowe można stosować do następujących elementów kodu:

- Pojedyncze elementy kodu i linki

- Grupy elementów kodu i linków

- Grupy elementów kodu i linki na podstawie określonych warunków

> [!TIP]
> Jeśli style powtarza się w wielu elementach kodu lub linkach, warto rozważyć zastosowanie kategorii do tych elementów kodu lub linków, a następnie zastosowanie stylu do tej kategorii. Aby uzyskać więcej informacji, zobacz [Assign Categories to Code elements and Links (Przypisywanie](#AssignCategories) kategorii do elementów kodu i linków) oraz Assign Properties to Code elements and Links (Przypisywanie właściwości do elementów kodu i [linków).](#AssignProperties)

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Aby zastosować styl niestandardowy do pojedynczego elementu kodu

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. Znajdź element elementu `<Node/>` kodu. Dodaj dowolny z tych atrybutów, aby dostosować jego styl:

     Kolor tła

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Kontur

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Grubość konturu

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Kolor tekstu

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     Ikona

    ```xml
    Icon="IconFilePathLocation"
    ```

     Rozmiar tekstu

    ```xml
    FontSize="FontSizeValue"
    ```

     Typ Tekst

    ```xml
    FontFamily="FontFamilyName"
    ```

     Waga tekstu

    ```xml
    FontWeight="FontWeightValue"
    ```

     Styl tekstu

    ```xml
    FontStyle="FontStyleName"
    ```

     Można na przykład określić `Italic` styl tekstu.

     Tekstura

    ```xml
    Style="Glass"
    ```

     - lub —

    ```xml
    Style="Plain"
    ```

     Kształt

     Aby zastąpić kształt ikoną, ustaw właściwość na i ustaw właściwość na `Shape` `None` `Icon` ścieżkę za pomocą pliku ikony.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Aby zastosować styl niestandardowy do pojedynczego łącza

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. Znajdź element , który zawiera zarówno nazwy elementu kodu źródłowego, `<Link/>` jak i docelowy element kodu.

3. W `<Link/>` elemencie dodaj dowolny z następujących atrybutów, aby dostosować jego styl:

     Kolor konturu i grotu strzałki

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Grubość konturu

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Styl konturu

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     Na przykład:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Aby zastosować style niestandardowe do grupy elementów kodu lub linków

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. Jeśli `<Styles></Styles>` element nie istnieje, dodaj go pod `<DirectedGraph></DirectedGraph>` elementem po `<Links></Links>` elemencie .

3. W `<Styles></Styles>` elemencie pod `<Style/>` elementem określ następujące atrybuty:

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*NameInLegendBox*`"`

   - `ValueLabel="`*NameInStylePickerBox*`"`

     Aby zastosować niestandardowy styl do wszystkich typów docelowych, nie należy używać warunku.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Aby zastosować styl warunkowy do grup elementów kodu lub linków

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. W elemencie dodaj element zawierający atrybut , aby `<Style/>` `<Condition/>` określić `Expression` wyrażenie, które zwraca wartość logiczną.

    Na przykład:

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - lub —

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - lub —

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    Wyrażenie to używa następującej składni notacji Backusa-Naura (BNF):

    \<Expression> ::= \<BinaryExpression> &#124; \<UnaryExpression> &#124; "(" \<Expression> ")" &#124; &#124; \<MemberBindings> \<Literal> &#124; \<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression> ::= "!" \<Expression> &#124; "+" \<Expression> &#124; "-" \<Expression>

    \<Operator> ::= "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "!=" &#124; "or" &#124; "and" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings> ::= \<MemberBindings> &#124; \<MemberBinding> "." \<MemberBinding>

    \<MemberBinding> ::= \<MethodCall> &#124; \<PropertyGet>

    \<MethodCall> ::= \<Identifier> "(" \<MethodArgs> ")"

    \<PropertyGet> ::= Identyfikator

    \<MethodArgs> ::= \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124; \<empty>

    \<Identifier> ::= [^. ]*

    \<Literal> ::= literał ciągu z pojedynczym lub podwójnym cudzysłowem

    \<Number> ::= ciąg cyfr z opcjonalnym separatorem dziesiętnym

    Można określić wiele `<Condition/>` elementów, które muszą mieć wartość true, aby zastosować styl.

3. W następnym wierszu po elemencie dodaj jeden lub wiele elementów, aby określić atrybut i stały atrybut lub obliczony atrybut do zastosowania do mapy, elementów kodu lub linków, które spełniają `<Condition/>` `<Setter/>` `Property` `Value` `Expression` warunek.

    Na przykład:

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   W prostym kompletnym przykładzie następujący warunek określa, że element kodu jest wyświetlany w kolorze zielonym lub czerwonym w zależności od tego, czy jego kategoria `Passed` jest ustawiona `True` na lub `False` :

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 Poniższa tabela zawiera niektóre przykładowe warunki, których można użyć:

 Ustaw rozmiar czcionki jako funkcję liczby wierszy kodu, co również zmienia rozmiar elementu kodu. W tym przykładzie użyto pojedynczego wyrażenia warunkowego do ustawienia wielu właściwości `FontSize` i `FontFamily` .

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 Ustaw kolor tła elementu kodu na podstawie `Coverage` właściwości . Style są oceniane w kolejności, w których się pojawiają, podobnie jak `if-else` instrukcje .

 W tym przykładzie:

1. Jeśli `Coverage` wartość > 80, ustaw właściwość `Background` na zielony.

2. W przypadku wartości > 50 ustaw dla właściwości odcień pomarańczowego `Coverage` `Background` na podstawie wartości `Coverage` właściwości.

3. W innym przypadku `Background` ustaw dla właściwości odcień koloru czerwonego na podstawie wartości `Coverage` właściwości.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 Ustaw właściwość `Shape` na wartość , aby ikona `None` zastąpiła kształt. Użyj `Icon` właściwości , aby określić lokalizację ikony.

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

## <a name="assign-properties-to-code-elements-and-links"></a><a name="AssignProperties"></a> Przypisywanie właściwości do elementów kodu i linków
 Elementy kodu i linki można organizować, przypisując do nich właściwości. Na przykład możesz wybrać elementy kodu, które mają określone właściwości, aby można było je zgrupować, zmienić ich styl lub ukryć.

#### <a name="to-assign-a-property-to-a-code-element"></a>Aby przypisać właściwość do elementu kodu

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. Znajdź `<Node/>` element dla tego elementu kodu. Określ nazwę właściwości i jej wartość. Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. Dodaj `<Property/>` element do sekcji , aby określić atrybuty, takie jak `<Properties>` widoczna nazwa i typ danych:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Aby przypisać właściwość do łącza

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. Znajdź element , który zawiera zarówno nazwy elementu kodu źródłowego, `<Link/>` jak i docelowy element kodu.

3. W `<Node/>` elemencie określ nazwę właściwości i jej wartość. Na przykład:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. Dodaj `<Property/>` element do sekcji , aby określić atrybuty, takie jak `<Properties>` widoczna nazwa i typ danych:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a> Przypisywanie kategorii do elementów kodu i linków
 W poniższych sekcjach pokazano, jak można organizować elementy kodu, przypisując im kategorie, oraz jak można tworzyć kategorie hierarchiczne, które ułatwiają organizowanie elementów kodu i dodawanie atrybutów do kategorii podrzędnej przy użyciu dziedziczenia.

#### <a name="to-assign-a-category-to-a-code-element"></a>Aby przypisać kategorię do elementu kodu

- Otwórz plik .dgml w edytorze tekstów lub XML.

- Znajdź `<Node/>` element dla elementu kodu, którego chcesz użyć.

- W `<Node/>` elemencie dodaj `Category` atrybut , aby określić nazwę kategorii. Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Dodaj element do sekcji , aby można było użyć atrybutu , `<Category/>` aby określić tekst wyświetlany dla tej `<Categories>` `Label` kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Przypisywanie kategorii do łącza

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. Znajdź element , który zawiera zarówno nazwy elementu kodu źródłowego, `<Link/>` jak i docelowy element kodu.

3. W `<Link/>` elemencie dodaj `Category` atrybut , aby określić nazwę kategorii. Na przykład:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. Dodaj element do sekcji , aby można było użyć atrybutu , `<Category/>` aby określić tekst wyświetlany dla tej `<Categories>` `Label` kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Tworzenie kategorii hierarchicznych

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. Dodaj `<Category/>` element dla kategorii nadrzędnej, a następnie dodaj atrybut do elementu `BasedOn` kategorii `<Category/>` podrzędnej.

     Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     W tym przykładzie tło jest `MyFirstNode` zielone, ponieważ jego `Category` atrybut dziedziczy `Background` atrybut `MyParentCategory` .

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a> Łączenie dokumentów lub adresów URL z elementami kodu i linkami
 Dokumenty lub adresy URL można połączyć z elementami kodu lub linkami, edytując plik .dgml mapy i dodając atrybut do elementu dla elementu kodu lub elementu `Reference` `<Node/>` `<Link/>` linku. Następnie możesz otworzyć i wyświetlić zawartość z elementu kodu lub linku. Atrybut `Reference` określa ścieżkę tej zawartości. Może to być ścieżka względem lokalizacji pliku .dgml lub ścieżka bezwzględna.

> [!CAUTION]
> Jeśli używane są ścieżki względne, a plik .dgml zostanie przeniesiony do innej lokalizacji, ścieżki te nie zostaną rozpoznane. Podczas próby otwarcia i wyświetlenia połączonej zawartości pojawi się komunikat o błędzie z informacją, że nie można wyświetlić zawartości.

 Na przykład możesz chcieć połączyć następujące elementy kodu:

- Aby opisać zmiany w klasie, możesz połączyć adres URL elementu kodu roboczego, dokumentu lub innego pliku .dgml z elementem kodu dla klasy.

- Diagram zależności można połączyć z elementem kodu grupy, który reprezentuje warstwę w architekturze logicznej oprogramowania.

- Aby wyświetlić więcej informacji o składniku, który uwidacznia interfejs, można połączyć diagram składnika z elementem kodu dla tego interfejsu.

- Połącz element kodu z elementem Team Foundation Server lub usterką albo inne informacje powiązane z elementem kodu.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Aby połączyć dokument lub adres URL z elementem kodu

1. Otwórz plik .dgml w edytorze tekstów lub XML.

2. Znajdź `<Node/>` element dla elementu kodu, którego chcesz użyć.

3. Wykonaj jedno z zadań z tabeli poniżej:

    Pojedynczy element kodu

   - W `<Node/>` elemencie lub `<Link/>` dodaj atrybut , aby określić `Reference` lokalizację elementu kodu.

     > [!NOTE]
     > Można mieć tylko jeden `Reference` atrybut na element.

     Na przykład:

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Wiele elementów kodu

   1. W `<Node/>` elemencie lub dodaj nowy atrybut , `<Link/>` aby określić lokalizację każdego odwołania.

   2. W `<Properties>` sekcji :

      1. Dodaj `<Property/>` element dla każdego nowego typu odwołania.

      2. Ustaw atrybut `Id` na nazwę nowego atrybutu odwołania.

      3. Dodaj atrybut i ustaw go na , aby odwołanie było wyświetlane w menu skrótów Przejdź do odwołania elementu `IsReference` `True` kodu. 

      4. Użyj `Label` atrybutu , aby określić tekst wyświetlany  w menu skrótów Przejdź do odwołania elementu kodu.

      Na przykład:

   ```xml
   <Nodes>
      <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
   </Nodes>
   <Properties>
      <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
      <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Na mapie nazwa elementu kodu jest podkreślona. Po otwarciu menu skrótów dla elementu kodu lub  linku zobaczysz menu skrótów Przejdź do odwołania, które zawiera połączone elementy kodu do wyboru.

4. Użyj atrybutu , aby określić wspólny ciąg, taki jak adres URL, który jest używany przez wiele odwołań, zamiast powtarzać ten `ReferenceTemplate` ciąg w odwołaniu.

    Atrybut `ReferenceTemplate` określa symbol zastępczy dla wartości odwołania. W poniższym przykładzie symbol zastępczy w atrybutze zostanie zastąpiony wartościami atrybutów i w elemencie w celu `{0}` `ReferenceTemplate` uzyskania `MyFirstReference` `MySecondReference` `<Node/>` pełnej ścieżki:

   ```xml
   <Nodes>
      <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
      <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
   </Nodes>
   <Properties>
      <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
      <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
   </Properties>
   ```

5. Aby wyświetlić element kodu lub elementy kodu, do których się odwołujesz, z mapy, otwórz menu skrótów dla elementu kodu lub linku. Wybierz **pozycję Przejdź do odwołania,** a następnie element kodu.

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dokumentacja języka DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)

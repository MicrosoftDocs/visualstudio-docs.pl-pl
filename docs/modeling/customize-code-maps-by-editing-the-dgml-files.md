---
title: Dostosowanie map kodu przez edycję plików DGML
description: Dowiedz się, jak dostosować mapę kodu, edytując jej plik DGML (Direct Markup Language).
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 47613a2f74ce1c89a6b032e46fa18b978c1c5f0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945295"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Dostosowanie map kodu przez edycję plików DGML

Aby dostosować mapę kodu, można edytować jej plik Directed Graph Markup Language (. dgml). Na przykład można edytować elementy, aby określić niestandardowe style, przypisać właściwości i kategorie do elementów kodu i linków lub połączyć dokumenty lub adresy URL z elementami kodu lub łączami. Aby uzyskać więcej informacji na temat elementów DGML, zobacz informacje o programie Direct [Graph Markup Language (dgml)](../modeling/directed-graph-markup-language-dgml-reference.md).

Edytuj plik. dgml mapy kodu w edytorze tekstu lub XML. Jeśli mapa jest częścią rozwiązania programu Visual Studio, wybierz ją w **Eksplorator rozwiązań**, otwórz menu skrótów, a następnie wybierz polecenie **Otwórz za pomocą**, **Edytor XML (tekst)**.

> [!NOTE]
> Aby utworzyć mapy kodu, musisz mieć wersję Visual Studio Enterprise. Podczas edytowania mapy kodu w programie Visual Studio czyści wszystkie nieużywane elementy DGML i atrybuty, usuwając je po zapisaniu pliku. dgml. Automatycznie tworzy również elementy kodu przy ręcznym dodawaniu nowych linków. Podczas zapisywania pliku .dgml wszelkie atrybuty, które są dodawane do elementu, mogą się ponownie rozmieszczać w kolejności alfabetycznej.

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a> Grupuj elementy kodu
 Możesz dodać nowe grupy lub przekonwertować istniejące węzły na grupę.

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. Aby skonwertować element kodu na grupę, Znajdź `<Node/>` element dla tego elementu kodu.

    \- oraz

    Aby dodać nową grupę, Znajdź `<Nodes>` sekcję. Dodaj nowy `<Node/>` element.

3. W `<Node/>` elemencie Dodaj `Group` atrybut, aby określić, czy grupa jest rozwinięta, czy zwinięta. Na przykład:

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. W `<Links>` sekcji upewnij się, że element o `<Link/>` następujących atrybutach istnieje dla każdej relacji między elementem kodu grupy a jego podrzędnymi elementami kodu:

   - `Source`Atrybut, który określa element kodu grupy

   - `Target`Atrybut, który określa podrzędny element kodu

   - `Category`Atrybut, który określa `Contains` relację między elementem kodu grupy a jego podrzędnym elementem kodu

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

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a> Zmiana stylu mapy
 Możesz zmienić kolor tła i kolor obramowania mapy, edytując plik. dgml mapy. Aby zmienić styl elementów kodu i linków, zobacz [zmiana stylu elementów kodu i linków](#Highlight).

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. W `<DirectedGraph>` elemencie Dodaj dowolny z następujących atrybutów, aby zmienić jego styl:

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

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a> Zmiana stylu elementów kodu i linków

### <a name="CreateCustomStyles"></a>
 Style niestandardowe można stosować do następujących elementów kodu:

- Elementy i linki z pojedynczym kodem

- Grupy elementów i linków kodu

- Grupy elementów kodu i linki na podstawie określonych warunków

> [!TIP]
> Jeśli masz powtarzające się style dla wielu elementów kodu lub linków, możesz rozważyć zastosowanie kategorii do tych elementów kodu lub linków, a następnie zastosować styl do tej kategorii. Aby uzyskać więcej informacji, zobacz [Przypisywanie kategorii do elementów kodu i linków](#AssignCategories) i [Przypisywanie właściwości do elementów kodu i linków](#AssignProperties).

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Aby zastosować styl niestandardowy do pojedynczego elementu kodu

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. Znajdź `<Node/>` element kodu. Dodaj dowolny z tych atrybutów, aby dostosować jego styl:

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

     Na przykład można określić `Italic` styl tekstu.

     Tekstura

    ```xml
    Style="Glass"
    ```

     - oraz

    ```xml
    Style="Plain"
    ```

     Kształt

     Aby zastąpić kształt ikoną, ustaw `Shape` Właściwość na `None` i ustaw `Icon` Właściwość na ścieżkę przy użyciu pliku ikony.

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

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. Znajdź `<Link/>` element, który zawiera zarówno nazwę elementu kodu źródłowego, jak i docelowy element kodu.

3. W `<Link/>` elemencie Dodaj dowolny z następujących atrybutów, aby dostosować jego styl:

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

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Aby zastosować niestandardowe style do grupy elementów kodu lub linków

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. Jeśli `<Styles></Styles>` element nie istnieje, Dodaj go pod `<DirectedGraph></DirectedGraph>` elementem po `<Links></Links>` elemencie.

3. W `<Styles></Styles>` elemencie pod `<Style/>` elementem i określ następujące atrybuty:

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*NameInLegendBox*`"`

   - `ValueLabel="`*NameInStylePickerBox*`"`

     Aby zastosować niestandardowy styl do wszystkich typów docelowych, nie należy używać warunku.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Aby zastosować styl warunkowy do grup elementów kodu lub linków

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. W `<Style/>` elemencie Dodaj `<Condition/>` element, który zawiera `Expression` atrybut, aby określić wyrażenie zwracające wartość logiczną.

    Na przykład:

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - oraz

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - oraz

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    Wyrażenie to używa następującej składni notacji Backusa-Naura (BNF):

    \<Expression> :: = \<BinaryExpression> &#124; \<UnaryExpression> &#124; "(" \<Expression> ")" &#124; \<MemberBindings> &#124; \<Literal> &#124; \<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression> ::= "!" \<Expression> &#124; "+" \<Expression> &#124; "-" \<Expression>

    \<Operator> :: = "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "lub" &#124; "i" &#124; "+" &#124; "*" &#124; "/" &#124; ""

    \<MemberBindings> :: = \<MemberBindings> &#124; \<MemberBinding> "." \<MemberBinding>

    \<MemberBinding> :: = \<MethodCall> &#124; \<PropertyGet>

    \<MethodCall> ::= \<Identifier> "(" \<MethodArgs> ")"

    \<PropertyGet> :: = Identyfikator

    \<MethodArgs> :: = \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124; \<empty>

    \<Identifier> ::= [^. ]*

    \<Literal> :: = literał typu Single lub Double w cudzysłowie

    \<Number> :: = ciąg cyfr z opcjonalnym punktem dziesiętnym

    Można określić wiele `<Condition/>` elementów, które muszą być spełnione, aby zastosować styl.

3. W następnym wierszu po `<Condition/>` elemencie Dodaj jeden lub wiele `<Setter/>` elementów, aby określić `Property` atrybut i stały `Value` atrybut lub obliczany `Expression` atrybut, który ma zostać zastosowany do mapy, elementów kodu lub linków, które spełniają warunek.

    Na przykład:

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   Prostym przykładem jest poniższy warunek określający, że element kodu jest zielony lub czerwony w zależności od tego, czy jego `Passed` Kategoria jest ustawiona na `True` lub `False` :

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

 Ustaw rozmiar czcionki jako funkcję liczby wierszy kodu, która również zmienia rozmiar elementu kodu. W tym przykładzie jest stosowane pojedyncze wyrażenie warunkowe do ustawiania wielu właściwości `FontSize` i `FontFamily` .

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

 Ustaw kolor tła elementu kodu na podstawie `Coverage` właściwości. Style są oceniane w kolejności, w jakiej są wyświetlane, podobnie jak w przypadku `if-else` instrukcji.

 W tym przykładzie:

1. Jeśli `Coverage` > 80, ustaw `Background` Właściwość na zielony.

2. W przeciwnym razie `Coverage` , jeśli jest > 50, ustaw `Background` Właściwość na odcień pomarańcza na podstawie wartości `Coverage` właściwości.

3. W przeciwnym razie ustaw `Background` Właściwość na odcień czerwieni na podstawie wartości `Coverage` właściwości.

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

 Ustaw `Shape` Właściwość na `None` tak, aby ikona zastąpiła kształt. Użyj `Icon` właściwości, aby określić lokalizację ikony.

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
 Elementy kodu i linki można organizować, przypisując do nich właściwości. Na przykład można wybrać elementy kodu, które mają określone właściwości, aby można je było grupować, zmienić ich styl lub ukryć.

#### <a name="to-assign-a-property-to-a-code-element"></a>Aby przypisać właściwość do elementu kodu

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. Znajdź `<Node/>` element dla tego elementu kodu. Określ nazwę właściwości i jej wartość. Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. Dodaj `<Property/>` element do sekcji, `<Properties>` Aby określić atrybuty, takie jak wyświetlana nazwa i typ danych:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Aby przypisać właściwość do łącza

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. Znajdź `<Link/>` element, który zawiera zarówno nazwę elementu kodu źródłowego, jak i docelowy element kodu.

3. W `<Node/>` elemencie Określ nazwę właściwości i jej wartość. Na przykład:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. Dodaj `<Property/>` element do sekcji, `<Properties>` Aby określić atrybuty, takie jak wyświetlana nazwa i typ danych:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a> Przypisywanie kategorii do elementów kodu i linków
 W poniższych sekcjach pokazano, jak można organizować elementy kodu, przypisując do nich kategorie, a także jak tworzyć kategorie hierarchiczne, które ułatwiają organizowanie elementów kodu i Dodawanie atrybutów do kategorii podrzędnych przy użyciu dziedziczenia.

#### <a name="to-assign-a-category-to-a-code-element"></a>Aby przypisać kategorię do elementu kodu

- Otwórz plik. dgml w edytorze tekstu lub XML.

- Znajdź `<Node/>` element dla żądanego elementu kodu.

- W `<Node/>` elemencie Dodaj `Category` atrybut, aby określić nazwę kategorii. Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Dodaj `<Category/>` element do sekcji, aby `<Categories>` można było użyć `Label` atrybutu, aby określić tekst wyświetlany dla tej kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Przypisywanie kategorii do łącza

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. Znajdź `<Link/>` element, który zawiera zarówno nazwę elementu kodu źródłowego, jak i docelowy element kodu.

3. W `<Link/>` elemencie Dodaj `Category` atrybut, aby określić nazwę kategorii. Na przykład:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. Dodaj `<Category/>` element do sekcji, aby `<Categories>` można było użyć `Label` atrybutu, aby określić tekst wyświetlany dla tej kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Tworzenie kategorii hierarchicznych

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. Dodaj `<Category/>` element dla kategorii nadrzędnej, a następnie Dodaj `BasedOn` atrybut do elementu kategorii podrzędnej `<Category/>` .

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

     W tym przykładzie tło `MyFirstNode` jest zielone, ponieważ jego `Category` atrybut dziedziczy `Background` atrybut `MyParentCategory` .

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a> Połącz dokumenty lub adresy URL z elementami kodu i łączami
 Można połączyć dokumenty lub adresy URL z elementami kodu lub łącza, edytując plik. dgml mapy i dodając `Reference` atrybut do `<Node/>` elementu dla elementu kodu lub `<Link/>` elementu łącza. Następnie można otworzyć i wyświetlić tę zawartość z elementu kodu lub łącza. Ten `Reference` atrybut określa ścieżkę do tej zawartości. Może to być ścieżka względem lokalizacji pliku .dgml lub ścieżka bezwzględna.

> [!CAUTION]
> Jeśli używane są ścieżki względne, a plik .dgml zostanie przeniesiony do innej lokalizacji, ścieżki te nie zostaną rozpoznane. Podczas próby otwarcia i wyświetlenia połączonej zawartości pojawi się komunikat o błędzie z informacją, że nie można wyświetlić zawartości.

 Na przykład możesz chcieć połączyć następujące elementy kodu:

- Aby opisać zmiany w klasie, można połączyć adres URL elementu kodu służbowego, dokumentu lub innego pliku. dgml do elementu kodu dla klasy.

- Można połączyć diagram zależności z elementem kodu grupy, który reprezentuje warstwę w architekturze logicznej oprogramowania.

- Aby wyświetlić więcej informacji na temat składnika, który uwidacznia interfejs, można połączyć diagram składników z elementem kodu dla tego interfejsu.

- Połącz element kodu z Team Foundation Server elementem roboczym lub usterką lub innymi informacjami związanymi z elementem kodu.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Aby połączyć dokument lub adres URL z elementem kodu

1. Otwórz plik. dgml w edytorze tekstu lub XML.

2. Znajdź `<Node/>` element dla żądanego elementu kodu.

3. Wykonaj jedno z zadań z tabeli poniżej:

    Pojedynczy element kodu

   - W `<Node/>` elemencie lub `<Link/>` Dodaj `Reference` atrybut, aby określić lokalizację elementu kodu.

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

   1. W `<Node/>` elemencie lub `<Link/>` Dodaj nowy atrybut, aby określić lokalizację każdego odwołania.

   2. W `<Properties>` sekcji:

      1. Dodaj `<Property/>` element dla każdego nowego typu odwołania.

      2. Ustaw `Id` atrybut na nazwę nowego atrybutu odwołania.

      3. Dodaj `IsReference` atrybut i ustaw go tak `True` , aby odwołanie pojawiło się w menu kontekstowym elementu  kodu.

      4. Użyj `Label` atrybutu, aby określić tekst wyświetlany dla elementu kodu **Przejdź do** menu skrótów.

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

    Na mapie nazwa elementu kodu pojawia się podkreślona. Gdy otworzysz menu skrótów dla elementu kodu lub łącza, zobaczysz menu skrótów **Przejdź do odwołania** zawierającego połączone elementy kodu, które chcesz wybrać.

4. Użyj `ReferenceTemplate` atrybutu, aby określić wspólny ciąg, taki jak adres URL, który jest używany przez wiele odwołań zamiast powtarzania tego ciągu w odwołaniu.

    `ReferenceTemplate`Atrybut określa symbol zastępczy dla wartości odwołania. W poniższym przykładzie `{0}` symbol zastępczy w `ReferenceTemplate` atrybucie zostanie zastąpiony przez wartości `MyFirstReference` `MySecondReference` atrybutów i w `<Node/>` elemencie, aby utworzyć pełną ścieżkę:

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

5. Aby wyświetlić przywoływany element kodu lub elementy kodu z mapy, otwórz menu skrótów dla elementu kodu lub łącza. Wybierz **Przejdź do odwołania** , a następnie element kodu.

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dokumentacja języka DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)

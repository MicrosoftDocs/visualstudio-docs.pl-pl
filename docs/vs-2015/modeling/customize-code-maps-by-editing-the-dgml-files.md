---
title: Dostosowanie map kodu przez edycję plików DGML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
ms.assetid: a2e141f4-4fd8-4611-b236-6b9e7bc54fc1
caps.latest.revision: 93
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c5976f2d701ecf051625c93ab6b70fb88ed15108
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433329"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Dostosowanie map kodu przez edycję plików DGML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby dostosować mapę kodu, można edytować plik Directed Graph Markup Language (.dgml) mapy. Na przykład można edytować elementy, aby określić niestandardowe style, przypisać właściwości i kategorie elementów kodu i linki, lub Połącz dokumenty lub adresy URL, aby elementy kodu lub łącza. Aby uzyskać więcej informacji dotyczących elementów DGML, zobacz [odwołania kierowane Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md).  
  
 Edytuj plik .dgml mapy kodu w edytorze tekstu lub edytorze XML. Jeśli mapa jest częścią rozwiązania programu Visual Studio, wybierz ją w **Eksploratora rozwiązań**, otwórz menu skrótów i wybierz **Otwórz za pomocą**, **Edytor (tekstu) XML**.  
  
> [!NOTE]
> Aby utworzyć map kodu, musi mieć program Visual Studio Enterprise. Podczas edytowania mapy kodu w programie Visual Studio go czyści wszelkie atrybuty i nieużywane elementy DGML, usuwając je podczas zapisywania pliku .dgml. Tworzy również elementy kodu automatycznie podczas ręcznego dodawania nowych łączy. Podczas zapisywania pliku .dgml wszelkie atrybuty, które są dodawane do elementu, mogą się ponownie rozmieszczać w kolejności alfabetycznej.  
  
## <a name="OrganizeNodes"></a> Grupować elementy kodu  
 Można dodać nowe grupy lub przekonwertować istniejące węzły w grupie.  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. Aby przekonwertować element kodu z grupą, Znajdź `<Node/>` element dla tego elementu kodu.  
  
    \- lub —  
  
    Aby dodać nową grupę, Znajdź `<Nodes>` sekcji. Dodaj nową `<Node/>` elementu.  
  
3. W `<Node/>` elementu Dodawanie `Group` atrybutu, aby określić, czy grupa pojawia się rozwinięta czy zwinięta. Na przykład:  
  
   ```xml  
   <Nodes>  
      <Node Id="MyFirstGroup" Group="Expanded" />  
      <Node Id="MySecondGroup" Group="Collapsed" />  
   </Nodes>  
   ```  
  
4. W `<Links>` sekcji, upewnij się, że `<Link/>` element, który ma następujące atrybuty, istnieje dla każdej relacji między elementem grupy kodu i jego elementy podrzędne w kodzie:  
  
   - A `Source` atrybut, który określa element kodu grupy  
  
   - A `Target` atrybut, który określa element podrzędny kodu  
  
   - A `Category` atrybut, który określa `Contains` relacji między elementem kodu grupy i jego podrzędny element kodu  
  
     Na przykład:  
  
   ```xml  
   <Links>  
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />  
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />  
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />  
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />  
   </Links>  
   ```  
  
    Aby uzyskać więcej informacji na temat `Category` atrybutów, zobacz [przypisywać kategorie elementów kodu i linków](#AssignCategories).  
  
## <a name="ChangeGraphStyle"></a> Zmień styl mapy  
 Możesz zmienić kolor tła i koloru obramowania mapy, edytując plik .dgml mapy. Aby zmienić styl elementów kodu i linków, zobacz [Zmienianie stylu elementów kodu i linków](#Highlight).  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. W `<DirectedGraph>` elementu, Dodaj dowolny z następujących atrybutów, aby zmienić jego styl:  
  
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
  
## <a name="Highlight"></a> Zmienianie stylu elementów kodu i linków  
  
### <a name="CreateCustomStyles"></a>   
 Style niestandardowe można stosować do następujących elementów kodu:  
  
- Elementy jednego kodu i linki  
  
- Grupy elementów kodu i linki  
  
- Grupy elementów kodu i linków na podstawie określonych warunków  
  
> [!TIP]
> Jeśli masz powtarzające się style w wielu elementów kodu lub łączy, można rozważyć zastosowanie kategorii do tych elementów kodu lub łącza, a następnie zastosowanie stylu do tej kategorii. Aby uzyskać więcej informacji, zobacz [Przypisz kategorie do elementów kodu i linków](#AssignCategories) i [przypisz właściwości do elementów kodu i linków](#AssignProperties).  
  
##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Aby zastosować styl niestandardowy do pojedynczego elementu kodu  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. Znajdź element kodu `<Node/>` elementu. Dodaj dowolny z tych atrybutów, aby dostosować jego styl:  
  
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
  
     Typ tekstu  
  
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
  
     Na przykład można określić `Italic` jako styl tekstu.  
  
     Tekstura  
  
    ```xml  
    Style="Glass"  
    ```  
  
     - lub —  
  
    ```xml  
    Style="Plain"  
    ```  
  
     Kształt  
  
     Aby zamienić kształt ikony, należy ustawić `Shape` właściwości `None` i ustaw `Icon` właściwość ścieżkę z plikiem ikony.  
  
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
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. Znajdź `<Link/>` element, który zawiera nazwy elementu kodu źródłowego i docelowego elementu kodu.  
  
3. W `<Link/>` elementu, Dodaj dowolny z następujących atrybutów, aby dostosować jego styl:  
  
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
  
##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Aby zastosować niestandardowe style do grupy elementów kodu lub łączy  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. Jeśli `<Styles></Styles>` element nie istnieje, należy dodać go pod `<DirectedGraph></DirectedGraph>` elementu po `<Links></Links>` elementu.  
  
3. W `<Styles></Styles>` elementu w obszarze `<Style/>` elementu i określić następujące atrybuty:  
  
   - `TargetType="Node` &#124; `Link | Graph"`  
  
   - `GroupLabel="` *NameInLegendBox* `"`  
  
   - `ValueLabel="` *NameInStylePickerBox* `"`  
  
     Aby zastosować niestandardowy styl do wszystkich typów docelowych, nie należy używać warunku.  
  
##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Aby zastosować styl warunkowy do grupy elementów kodu lub łączy  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. W `<Style/>` elementu Dodawanie `<Condition/>` element, który zawiera `Expression` atrybutu, aby określić wyrażenie zwracające wartość logiczną.  
  
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
  
    \<Expression> ::= \<BinaryExpression> &#124; \<UnaryExpression> &#124; "("\<Expression>")" &#124; \<MemberBindings> &#124; \<Literal> &#124; \<Number>  
  
    \<BinaryExpression> ::= \<Expression> \<Operator> \<Expression>  
  
    \<UnaryExpression >:: = "!" \<Expression> &#124; "+" \<Expression> &#124; "-" \<Expression>  
  
    \<Operator >:: = "<" &#124; "\<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "or" &#124; "i" &#124; "+" &#124; "*" &#124; "/" &#124; "-"  
  
    \<MemberBindings >:: = \<MemberBindings > &#124; \<MemberBinding > "." \<MemberBinding >  
  
    \<MemberBinding> ::= \<MethodCall> &#124; \<PropertyGet>  
  
    \<Format strumienia MethodCall >:: = \<identyfikator > "(" \<MethodArgs > "")""  
  
    \<Propertyget — >:: = identyfikator  
  
    \<MethodArgs> ::= \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124; \<empty>  
  
    \<Identyfikator >:: = [^. ]*  
  
    \<Literal >:: = literał ciągu pojedynczym lub podwójnym cudzysłowem  
  
    \<Liczba >:: = ciąg cyfr z opcjonalnym przecinkiem dziesiętnym  
  
    Można określić wiele `<Condition/>` elementy, które muszą być spełnione, aby zastosować styl.  
  
3. W następnym wierszu po `<Condition/>` elementu, Dodaj jeden lub wiele `<Setter/>` elementy, aby określić `Property` atrybut i stałym `Value` atrybutu lub obliczanej `Expression` atrybutu, aby zastosować do mapy, elementy kodu lub łączy, które spełniają warunek.  
  
    Na przykład:  
  
   ```xml  
   <Setter Property="BackGround" Value="Green"/>  
   ```  
  
   Jako prosty, kompletny przykład, następujący warunek określa, że element kodu pojawi się jako zielony lub czerwony, w zależności od tego, czy jego `Passed` kategoria jest ustawiona na `True` lub `False`:  
  
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
  
 Ustaw rozmiar czcionki jako funkcję liczby linii kodu, która zmienia także rozmiar elementu kodu. W tym przykładzie używa pojedynczego wyrażenia warunkowego do ustawiania wielu właściwości `FontSize` i `FontFamily`.  
  
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
  
 Ustaw kolor tła elementu kodu, na podstawie `Coverage` właściwości. Style są obliczane w kolejności, w jakiej się pojawiają, podobnie jak `if-else` instrukcji.  
  
 W tym przykładzie:  
  
1. Jeśli `Coverage` wynosi > 80, a następnie ustaw `Background` właściwości na zielony.  
  
2. Jeśli nie `Coverage` wynosi > 50, a następnie ustaw `Background` właściwości na odcień koloru pomarańczowego na podstawie wartości z `Coverage` właściwości.  
  
3. Ustaw inne `Background` właściwości na odcień czerwieni na podstawie wartości z `Coverage` właściwości.  
  
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
  
 Ustaw `Shape` właściwość `None` tak, aby ikona została zamieniona na kształt. Użyj `Icon` właściwość, aby określić lokalizację ikony.  
  
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
  
## <a name="AssignProperties"></a> Przypisywanie właściwości do elementów kodu i łączy  
 Elementy kodu i łącza można organizować przez przypisywanie im właściwości. Na przykład można wybrać elementy kodu, które mają szczególne właściwości, tak aby można je pogrupować, zmienić ich styl lub je ukryć.  
  
#### <a name="to-assign-a-property-to-a-code-element"></a>Aby przypisać właściwość do elementu kodu  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. Znajdź `<Node/>` element dla tego elementu kodu. Określ nazwę właściwości i jego wartość. Na przykład:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" MyPropertyName="PropertyValue" />  
    </Nodes>  
    ```  
  
3. Dodaj `<Property/>` elementu `<Properties>` sekcji, aby określić atrybuty, takie jak jego widoczna nazwa i typ danych:  
  
    ```xml  
    <Properties>  
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>  
    </Properties>  
    ```  
  
#### <a name="to-assign-a-property-to-a-link"></a>Aby przypisać właściwość do łącza  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. Znajdź `<Link/>` element, który zawiera nazwy elementu kodu źródłowego i docelowego elementu kodu.  
  
3. W `<Node/>` elementu, określ nazwę właściwości i jego wartość. Na przykład:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />  
    </Links>  
    ```  
  
4. Dodaj `<Property/>` elementu `<Properties>` sekcji, aby określić atrybuty, takie jak jego widoczna nazwa i typ danych:  
  
    ```xml  
    <Properties>  
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>  
    </Properties>  
    ```  
  
## <a name="AssignCategories"></a> Przypisywanie kategorii do elementów kodu i łączy  
 W poniższych sekcjach przedstawiono, jak można organizować elementy kodu przez przypisywanie kategorii do nich i w jaki sposób można utworzyć hierarchiczne kategorie, które pomagają organizować elementy kodu i dodawanie atrybutów do kategorii podrzędnych za pomocą dziedziczenia.  
  
#### <a name="to-assign-a-category-to-a-code-element"></a>Aby przypisać kategorię do elementu kodu  
  
- Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
- Znajdź `<Node/>` elementu dla elementu kodu, który ma.  
  
- W `<Node/>` elementu Dodawanie `Category` atrybutu, aby określić nazwę kategorii. Na przykład:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" Category="MyCategory" />  
    </Nodes>  
    ```  
  
     Dodaj `<Category/>` elementu `<Categories>` sekcji tak, aby można było używać `Label` atrybutu, aby określić tekst wyświetlany dla tej kategorii:  
  
    ```xml  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" />  
    </Categories>  
    ```  
  
#### <a name="to-assign-a-category-to-a-link"></a>Przypisywanie kategorii do łącza  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. Znajdź `<Link/>` element, który zawiera nazwy elementu kodu źródłowego i docelowego elementu kodu.  
  
3. W `<Link/>` elementu Dodawanie `Category` atrybutu, aby określić nazwę kategorii. Na przykład:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"  
    </Links>  
    ```  
  
4. Dodaj `<Category/>` elementu `<Categories>` sekcji tak, aby można było używać `Label` atrybutu, aby określić tekst wyświetlany dla tej kategorii:  
  
    ```xml  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" />  
    </Categories>  
    ```  
  
#### <a name="to-create-hierarchical-categories"></a>Tworzenie kategorii hierarchicznych  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. Dodaj `<Category/>` element dla kategorii nadrzędnej, a następnie dodaj `BasedOn` atrybutów do kategorii podrzędnych `<Category/>` elementu.  
  
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
  
     W tym przykładzie tło `MyFirstNode` zielony ponieważ jej `Category` dziedziczy atrybut `Background` atrybutu `MyParentCategory`.  
  
## <a name="AddReferences"></a> Połączyć dokumenty lub adresy URL elementów kodu i linków  
 Możesz połączyć dokumenty lub adresy URL do elementów kodu lub łącza, edytując plik .dgml mapy i dodawanie `Reference` atrybutu `<Node/>` elementu dla elementu kodu lub `<Link/>` dla łącza. Następnie można otworzyć i wyświetlić tę zawartość z elementu kodu lub łącza. `Reference` Atrybut określa ścieżkę tej zawartości. Może to być ścieżka względem lokalizacji pliku .dgml lub ścieżka bezwzględna.  
  
> [!CAUTION]
> Jeśli używane są ścieżki względne, a plik .dgml zostanie przeniesiony do innej lokalizacji, ścieżki te nie zostaną rozpoznane. Podczas próby otwarcia i wyświetlenia połączonej zawartości pojawi się komunikat o błędzie z informacją, że nie można wyświetlić zawartości.  
  
 Na przykład można połączyć następujące elementy kodu:  
  
- Aby opisać zmiany w klasie, można połączyć element roboczy kodu, dokument lub inny plik .dgml adres URL do elementu kodu dla klasy.  
  
- Można połączyć diagram warstwy do elementu kodu grupy, który reprezentuje warstwę w logicznej architekturze oprogramowania.  
  
- Aby wyświetlić więcej informacji na temat składnika, który udostępnia interfejs, można połączyć diagram składników do elementu kodu dla tego interfejsu.  
  
- Połącz element kodu do elementu pracy Team Foundation Server lub usterki lub inne informacje dotyczące elementu kodu.  
  
#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Aby połączyć element kodu dokumentu lub adresu URL  
  
1. Otwórz plik .dgml w edytorze tekstu lub edytorze XML.  
  
2. Znajdź `<Node/>` elementu dla elementu kodu, który ma.  
  
3. Wykonaj jedno z zadań z tabeli poniżej:  
  
    Pojedynczego elementu kodu  
  
   - W `<Node/>` lub `<Link/>` elementu Dodawanie `Reference` atrybutu, aby określić lokalizację elementu kodu.  
  
     > [!NOTE]
     > Może mieć tylko jeden `Reference` atrybutu dla każdego elementu.  
  
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
  
   1. W `<Node/>` lub `<Link/>` elementu, Dodaj nowy atrybut, aby określić lokalizację każdego odwołania.  
  
   2. W `<Properties>` sekcji:  
  
      1. Dodaj `<Property/>` elementu dla każdego nowego typu odwołania.  
  
      2. Ustaw `Id` atrybutu na nazwę nowego atrybutu odwołania.  
  
      3. Dodaj `IsReference` atrybutu i ustaw ją na `True` aby odwołanie pojawiało się w elemencie kod **przejdź do odwołania** menu skrótów.  
  
      4. Użyj `Label` atrybutu, aby określić tekst wyświetlany w elemencie kod **przejdź do odwołania** menu skrótów.  
  
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
  
    Na mapie nazwa elementu kodu jest podkreślana. Po otwarciu menu skrótów dla elementu kodu lub link, zostanie wyświetlony **przejdź do odwołania** menu skrótów, które zawierają elementy kodu połączone, można wybrać.  
  
4. Użyj `ReferenceTemplate` atrybutu, aby określić wspólny ciąg, takie jak adres URL, który jest używany przez wiele odwołań zamiast powtarzania tego ciągu w odwołaniu.  
  
    `ReferenceTemplate` Atrybut Określa symbol zastępczy dla wartości odwołania. W poniższym przykładzie `{0}` symbol zastępczy w `ReferenceTemplate` atrybut zostanie zastąpiona przez wartości `MyFirstReference` i `MySecondReference` atrybutów w `<Node/>` elementu, aby utworzyć pełną ścieżkę:  
  
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
  
5. Aby wyświetlić kod przywoływanego elementu lub elementów kodu z mapy, otwórz menu skrótów dla elementu kodu lub łącza. Wybierz **przejdź do odwołania** i następnie elementu kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)   
 [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Przeglądanie i rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)   
 [Dokumentacja języka DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
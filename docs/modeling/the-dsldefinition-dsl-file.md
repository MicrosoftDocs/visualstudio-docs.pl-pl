---
title: Plik DslDefinition.dsl
description: Dowiedz się więcej o strukturze pliku DslDefinition.dsl w projekcie Dsl rozwiązania DSL Tools, które definiuje język specyficzny dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f2e2ae6e406b8967cb7de49573ce5b26377806e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388636"
---
# <a name="the-dsldefinitiondsl-file"></a>Plik DslDefinition.dsl

W tym temacie opisano strukturę pliku DslDefinition.dsl w projekcie Dsl rozwiązania, który definiuje język [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] *specyficzny dla domeny*. Plik DslDefinition.dsl opisuje klasy i relacje języka specyficznego dla domeny, wraz z diagramem,  kształtami, łącznikami, formatem serializacji i przybornikem języka specyficznego dla domeny i jego narzędzi do edycji. W rozwiązaniu języka specyficznego dla domeny kod, który definiuje te narzędzia, jest generowany zgodnie z informacjami w pliku DslDefinition.dsl.

Ogólnie rzecz biorąc, do *edytowania projektant języka specyficznego dla domeny* DslDefinition.dsl używa się pliku . Jednak jego nieprzetworzczony formularz to XML i można otworzyć plik DslDefinition.dsl w edytorze XML. Przydatne może okazać się zrozumienie, jakie informacje zawiera plik i jak jest zorganizowany na potrzeby debugowania i rozszerzenia.

Przykłady w tym temacie są brane z szablonu rozwiązania diagramu składników. Aby wyświetlić przykład, utwórz rozwiązanie języka specyficzne dla domeny oparte na szablonie rozwiązania Modele składników. Po utworzeniu rozwiązania plik DslDefinition.dsl zostanie wyświetlony w Domain-Specific Language Designer. Zamknij plik, kliknij go prawym przyciskiem myszy w Eksplorator rozwiązań , wskaż polecenie Otwórz **za** pomocą **,** kliknij pozycję Edytor **XML,** a następnie kliknij przycisk **OK.**

## <a name="sections-of-the-dsldefinitiondsl-file"></a>Sekcje pliku DslDefinition.dsl

Element główny to , a jego atrybuty identyfikują nazwę języka specyficznego dla domeny, przestrzeń nazw oraz główne i pomocnicze numery wersji do \<Dsl> wersjonarowania. Schemat `DslDefinitionModel` definiuje zawartość i strukturę prawidłowego pliku DslDefinition.dsl.

Elementy podrzędne elementu \<Dsl> głównego są następujące:

### <a name="classes"></a>Klasy

W tej sekcji zdefiniowano każdą klasę domeny, która generuje klasę w wygenerowanym kodzie.

### <a name="relationships"></a>Relacje

W tej sekcji zdefiniowano każdą relację w modelu. Źródło i obiekt docelowy reprezentują dwie strony relacji.

### <a name="types"></a>Typy

W tej sekcji zdefiniowano każdy typ i jego przestrzeń nazw. Właściwości domeny mają dwa typy. `DomainEnumerations` są definiowane w modelu i generują typy do domeny DomainModel.cs. `ExternalTypes` odwołują się do typów zdefiniowanych w innym miejscu (takich jak `String` lub ) i nie generują `Int32` niczego.

### <a name="shapes"></a>Kształty

W tej sekcji zdefiniowano kształty, które opisują sposób, w jaki model pojawia się w projektancie. Te kształty geometryczne są mapowane na klasy w modelu w sekcji Diagram.

### <a name="connectors"></a>Łączniki

W tej sekcji zdefiniowano wygląd łączników wyświetlanych w projektancie. Te opisy stylu geometrycznego są mapowane na określone relacje w modelu w sekcji Diagram.

### <a name="xmlserializationbehavior"></a>XmlSerializationBehavior

Ta sekcja definiuje schemat serializacji i zawiera dodatkowe informacje o poszczególnych klasach jest zapisywany w pliku.

### <a name="explorerbehavior"></a>Explorerbehavior

W tej sekcji zdefiniowano sposób, w jaki **okno eksploratora DSL** jest wyświetlane, gdy użytkownik edytuje model.

### <a name="connectionbuilders"></a>ConnectionBuilders

W tej sekcji zdefiniowano konstruktor połączeń dla każdego narzędzia łącznika (narzędzie do tworzenia linków między dowolnymi dwiema klasami, które mogą być połączone). Ta sekcja określa, czy można połączyć klasę źródłową i docelową.

### <a name="diagram"></a>Diagram

Ta sekcja definiuje diagram i służy do określania właściwości, takich jak kolor tła i klasa główna. (Klasa główna jest klasą domeny reprezentowaną przez diagram jako całość). Sekcja Diagram zawiera również elementy ShapeMap i ConnectorMap, które określają kształt lub łącznik reprezentujący każdą klasę domeny lub relację.

### <a name="designer"></a>Projektant

W tej sekcji zdefiniowano projektanta (edytora), który łączy przybornik, ustawienia weryfikacji, diagram i schemat serializacji. Sekcja Projektant definiuje również klasę główną modelu, która zazwyczaj jest również klasą główną diagramu.

### <a name="explorer"></a>Eksplorator

Ta sekcja identyfikuje zachowanie **eksploratora DSL** (zdefiniowane w sekcji XmlSerializationBehavior).

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Monikers w pliku DslDefinition.dsl

W całym pliku DslDefinition.dsl można używać monikerów do odwołań krzyżowych do określonych elementów. Na przykład każda definicja relacji zawiera podsekcję Source i podsekcję Target. Każda podsekcja zawiera moniker klasy obiektu, który można powiązać z tym relacją:

```xml
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

Zazwyczaj przestrzeń nazw elementu, do których istnieje odwołanie (w tym przykładzie jest to klasa domeny) jest taka sama jak element odwołujący się (w tym przypadku relacja domeny `Library` LibraryHasMembers). W takich przypadkach monikera musi podać tylko nazwę klasy. W przeciwnym razie należy użyć pełnej postaci /Namespace/Name:

```xml
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

System moniker wymaga, aby elementy równorzędne w drzewie XML miał różne nazwy. Z tego powodu błędy walidacji występują w przypadku próby zapisania definicji języka specyficznej dla domeny, która ma na przykład dwie klasy o tej samej nazwie. Takie błędy zduplikowanej nazwy należy zawsze poprawić przed zapisaniem pliku DslDefinition.dsl, aby można było go ponownie załadować później.

Każdy typ ma własny typ moniker: DomainClassMoniker, DomainRelationshipMoniker i tak dalej.

## <a name="types"></a>Typy

Sekcja Types (Typy) określa wszystkie typy, które zawiera plik DslDefinition.dsl jako typy właściwości. Te typy można liczyć na dwa rodzaje: typy zewnętrzne, takie jak System.String, i typy wyliczane.

### <a name="external-types"></a>Typy zewnętrzne

Przykład diagramu składników zawiera zestaw standardowych typów pierwotnych, chociaż używane są tylko niektóre z nich.

Każda definicja typu zewnętrznego składa się tylko z nazwy i przestrzeni nazw, takiej jak Ciąg i System:

```xml
<ExternalType Name="String" Namespace="System" />
```

Zamiast równoważnych słów kluczowych kompilatora, takich jak "ciąg", używane są pełne nazwy typów.

Typy zewnętrzne nie są ograniczone do standardowych typów bibliotek.

### <a name="enumerations"></a>Wyliczenia

Typowa specyfikacja wyliczenia przypomina ten przykład:

```xml
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

Atrybut określa, czy wygenerowany kod jest poprzedzony atrybutem clr (Common Language Runtime), który określa, czy wartości wyliczenia mogą być łączone `IsFlags` `[Flags]` bitowo. Jeśli ten atrybut ma wartość true, należy określić wartość power-of-two dla wartości literału.

## <a name="classes"></a>Klasy

Większość elementów w dowolnej definicji języka specyficznego dla domeny to bezpośrednio lub pośrednio wystąpienia `DomainClass` klasy . Podklasy `DomainClass` obejmują , , i `DomainRelationship` `Shape` `Connector` `Diagram` . Sekcja `Classes` pliku DslDefinition.dsl zawiera listę klas domeny.

Każda klasa ma zestaw właściwości i może mieć klasę bazową. W przykładzie diagramu składników klasa jest klasą abstrakcyjną, `NamedElement` która ma `Name` właściwość, której typem jest ciąg:

```xml
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">
  <Properties>
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
</DomainClass>
```

`NamedElement` jest podstawą kilku innych klas, takich jak , które mają własne właściwości oprócz właściwości `Component` `Name` dziedziczonej z klasy `NamedElement` . Węzeł podrzędny BaseClass zawiera odwołanie do monikera. Ponieważ klasa, do których istnieje odwołanie, znajduje się w tej samej przestrzeni nazw, w monikrze jest wymagana tylko jej nazwa:

```xml
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">
  <BaseClass>
    <DomainClassMoniker Name="NamedElement" />
  </BaseClass>
  <Properties>
    <DomainProperty Name="Kind" DisplayName="Kind" >
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
```

Każda klasa domeny (w tym relacje, kształty, łączniki i diagramy) może mieć następujące atrybuty i węzły podrzędne:

- **Identyfikator.** Ten atrybut jest identyfikatorem GUID. Jeśli nie potworzymy wartości w pliku, projektant języka Domain-Specific utworzy wartość. (Na ilustracjach w tym dokumencie ten atrybut jest zwykle pomijany, aby zaoszczędzić miejsce).

- **Nazwa i przestrzeń nazw.** Te atrybuty określają nazwę i przestrzeń nazw klasy w wygenerowanym kodzie. Razem muszą być unikatowe w języku specyficznym dla domeny.

- **InheritanceModifier.** Ten atrybut jest "abstrakcyjny", "zapieczętowany" lub brak.

- **Displayname.** Ten atrybut to nazwa wyświetlana w **oknie** Właściwości. Atrybut DisplayName może zawierać spacje i inne znaki interpunkacji.

- **GenerujeDoubleDerived.** Jeśli ten atrybut ma wartość true, generowane są dwie klasy, a jedna jest podklasą drugiej. Wszystkie wygenerowane metody znajdują się w bazie, a konstruktory znajdują się w podklasie. Ustawiając ten atrybut, można zastąpić dowolną wygenerowaną metodę w kodzie niestandardowym.

- **HasCustomConstructor**. Jeśli ten atrybut ma wartość true, konstruktor zostanie pominięty w wygenerowanym kodzie, aby można było napisać własną wersję.

- **Atrybuty**. Ten atrybut zawiera atrybuty CLR wygenerowanej klasy.

- **BaseClass**. Jeśli określisz klasę bazową, musi ona być tego samego typu. Na przykład klasa domeny musi mieć inną klasę domeny jako podstawową, a kształt przedziału musi mieć kształt przedziału. Jeśli nie określisz klasy bazowej, klasa w wygenerowanym kodzie pochodzi od standardowej klasy struktury. Na przykład klasa domeny pochodzi od `ModelElement` klasy .

- **Właściwości**. Ten atrybut zawiera właściwości, które są utrzymywane pod kontrolą transakcji i utrwalane po zapisaniu modelu.

- **ElementMergeDirectives**. Każda dyrektywa scalania elementów steruje tym, jak inne wystąpienie innej klasy jest dodawane do wystąpienia klasy nadrzędnej. Więcej szczegółów na temat dyrektyw scalania elementów można znaleźć w dalszej części tego tematu.

- Klasa C# jest generowana dla każdej klasy domeny wymienionej w `Classes` sekcji . Klasy języka C# są generowane w pliku Dsl\GeneratedCode\DomainClasses.cs.

### <a name="properties"></a>Właściwości

Każda właściwość domeny ma nazwę i typ. Nazwa musi być unikatowa w obrębie klasy domeny i jej przechodniej bazy.

Typ musi odwoływać się do jednego z wymienionych w `Types` sekcji . Ogólnie rzecz biorąc, moniker musi zawierać przestrzeń nazw .

```xml
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Każda właściwość domeny może mieć również następujące atrybuty:

- **IsBrowsable**. Ten atrybut określa, czy właściwość jest wyświetlana w **oknie Właściwości,** gdy użytkownik kliknie obiekt klasy nadrzędnej.

- **IsUIReadOnly**. Ten atrybut określa, czy użytkownik może zmienić właściwość w oknie **Właściwości,** czy za pomocą dekoratora, w którym jest przedstawiana właściwość.

- **Rodzaj**. Możesz ustawić ten atrybut na Wartość normalna, Obliczona lub CustomStorage. W przypadku ustawienia tego atrybutu na Wartość obliczeniowa należy podać kod niestandardowy, który określa wartość, a właściwość będzie tylko do odczytu. W przypadku ustawienia tego atrybutu na wartość CustomStorage należy podać kod, który pobiera i ustawia wartości.

- **IsElementName**. Jeśli ten atrybut ma wartość true, jego wartość jest automatycznie ustawiana na unikatową wartość po utworzeniu wystąpienia klasy nadrzędnej. Ten atrybut można ustawić na wartość true tylko dla jednej właściwości w każdej klasie, która musi mieć typ ciągu. W przykładzie diagramu składników właściwość `Name` w obiekcie `NamedElement` ma wartość `IsElementName` true. Za każdym razem, gdy użytkownik tworzy element (który dziedziczy z elementu ), nazwa jest automatycznie inicjowana do `Component` `NamedElement` elementu podobnego do "Component6".

- `DefaultValue`. Jeśli określono ten atrybut, określona wartość jest przypisywana do tego atrybutu dla nowych wystąpień tej klasy. Jeśli `IsElementName` jest ustawiona, DefaultValue atrybut określa początkową część nowego ciągu.

- **Kategoria** to nagłówek, w którym właściwość będzie wyświetlana w **oknie** Właściwości.

## <a name="relationships"></a>Relacje

Sekcja `Relationships` zawiera listę wszystkich relacji w języku specyficznym dla domeny. Każdy `Domain Relationship` element jest binarny i skierowany, łącząc składowe klasy źródłowej z składową klasy docelowej. Klasy źródłowe i docelowe są zazwyczaj klasami domeny, ale relacje z innymi relacjami również są dozwolone.

Na przykład relacja połączenia łączy składowe klasy OutPort z członkami klasy InPort. Każde wystąpienie łącza relacji łączy wystąpienie obiektu OutPort z wystąpieniem obiektu InPort. Ponieważ relacja jest relacją wiele-do-wielu, każdy port wychodzący może mieć wiele linków połączenia ze źródłami, a każde wystąpienie inport może mieć wiele linków połączenia, które są dla niego docelowe.

### <a name="source-and-target-roles"></a>Role źródłowe i docelowe

Każda relacja zawiera role źródłowe i docelowe, które mają następujące atrybuty:

- Atrybut `RolePlayer` odwołuje się do klasy domeny połączonych wystąpień: OutPort dla źródła, InPort dla obiektu docelowego.

- Atrybut `Multiplicity` ma cztery możliwe wartości (ZeroMany, ZeroOne, One i OneMany). Ten atrybut odnosi się do liczby linków tej relacji, które można skojarzyć z jednym odtwarzaczem roli.

- Atrybut określa nazwę używaną w klasie fabularne do uzyskiwania dostępu `PropertyName` do obiektów na drugim końcu. Ta nazwa jest używana w szablonie lub kodzie niestandardowym do przechodzenia przez relację. Na przykład `PropertyName` atrybut roli źródłowej jest ustawiony na `Targets` wartość . W związku z tym będzie działać następujący kod:

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Według konwencji nazwy właściwości są w liczbie mnogiej, jeśli liczebność to ZeroMany lub OneMany.

     Liczebność roli odnosi się do tego, ile roli przeciwległej można skojarzyć z każdym wystąpieniem tej roli. Na przykład w relacji ComponentHasPorts rola docelowa ma atrybut Port, atrybut ustawiony na Component i atrybut `RolePlayer` `PropertyName` `Multiplicity` ZeroOne. W związku z tym odpowiedni kod do użycia tej roli to:

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

- Rola to nazwa, która jest używana w klasie Relationship do odwoływać się do `Name` tego końca linku. Według konwencji nazwa roli jest zawsze pojedynczej, ponieważ każdy link ma tylko jedno wystąpienie na każdym końcu. Następujący kod będzie działać:

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

- Domyślnie atrybut `IsPropertyGenerator` ma wartość true. Jeśli ustawiono wartość false, żadna właściwość nie jest tworzona w klasie Role Player. (W takim przypadku `op.Targets` na przykład nie będzie działać). Jednak nadal można użyć kodu niestandardowego w celu przechodzenia przez relację lub uzyskania dostępu do samych linków, jeśli kod niestandardowy jawnie używa relacji:

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>Atrybuty relacji

Oprócz atrybutów i węzłów podrzędnych, które są dostępne dla wszystkich klas, każda relacja ma następujące atrybuty:

- **IsEmbedding**. Ten atrybut logiczny określa, czy relacja jest częścią drzewa osadzania. Każdy model musi tworzyć drzewo z jego relacjami osadzania. W związku z tym każda klasa domeny musi być obiektem docelowym co najmniej jednej relacji osadzania, chyba że jest to element główny modelu.

- **AllowsDuplicates**. Ten atrybut logiczny, domyślnie fałsz, ma zastosowanie tylko do relacji, które mają liczebność "wiele" zarówno w źródle, jak i w miejscu docelowym. Określa, czy użytkownicy języka mogą łączyć jedną parę elementów źródłowych i docelowych za pomocą więcej niż jednego linku tej samej relacji.

## <a name="designer-and-toolbox-tabs"></a>Projektant i karty przybornika

Główną częścią sekcji **Projektant** pliku DslDefinition.dsl są elementy **PrzybornikTab.** Jeden projektant może mieć kilka z tych elementów, z których każdy reprezentuje sekcję kierowaną w przyborniku wygenerowanego **projektanta.** Każdy **element ToolboxTab** może zawierać co najmniej jeden **element ElementTool,** elementy **ConnectionTool** lub oba te elementy.

Narzędzia elementów mogą tworzyć wystąpienia określonej klasy domeny. Gdy użytkownik przeciąga narzędzie elementu na diagram, wynik jest określany przez dyrektywy scalania elementów zgodnie z opisem w sekcji dotyczącej dyrektyw scalania elementów w dalszej części tego tematu.

Każde narzędzie połączenia może wywołać określonego konstruktora połączeń. Jeden konstruktor połączeń może utworzyć więcej niż jeden typ relacji, w zależności od tego, gdzie użytkownik kliknie mysz, zgodnie z opisem w sekcji dotyczącej konstruktorów połączeń.

Żaden typ narzędzia nie tworzy bezpośrednio kształtów ani łączników. Każdy wystąpienia klasy domeny lub relacji domeny; Mapowania kształtów i łączników określają sposób, w jaki jest wyświetlana ta klasa domeny lub relacja domeny.

## <a name="paths"></a>Ścieżki

Ścieżki domeny są wyświetlane w kilku lokalizacjach w pliku DslDefinition.dsl. Te ścieżki określają serię linków z jednego elementu w modelu (czyli wystąpienia języka specyficznego dla domeny) do innego. Składnia ścieżki jest prosta, ale szczegółowa.

Ścieżki są wyświetlane w pliku DslDefinition.dsl w `<DomainPath>...</DomainPath>` tagach. Mimo że ścieżki mogą przechodzić przez wiele linków, większość przykładów w praktyce przechodzi tylko przez jedno łącze.

Ścieżka składa się z sekwencji segmentów. Każdy segment to przeskok z obiektu do linku lub z linku do obiektu. W związku z tym przeskoki zwykle są alternatywne w długiej ścieżce. Pierwszy przeskok pochodzi z obiektu do łącza, drugi przeskok jest do obiektu na drugim końcu łącza, trzeci przeskok jest do następnego linku i tak dalej. Sporadycznym wyjątkiem od tej sekwencji jest sytuacja, w której relacja jest źródłem lub obiektem docelowym innej relacji.

Każdy segment rozpoczyna się od nazwy relacji. W przeskoku typu obiekt-link relacja poprzedza kropkę i nazwę właściwości: " `Relationship . Property` ". W przeskoku link do obiektu relacja poprzedza wykrzyknik i nazwę roli: " `Relationship ! Role` ".

Przykład diagramu składników zawiera ścieżkę w ścieżce ParentElementPath elementu ShapeMap for InPort. Ta ścieżka rozpoczyna się w następujący sposób:

```
    ComponentHasPorts.Component
```

W tym przykładzie InPort jest podklasą componentPort i ma relację ComponentHasPorts. Właściwość nosi nazwę Component.

Podczas pisania w języku C# względem tego modelu można przejść przez link w jednym kroku przy użyciu właściwości, która jest generowana przez relację dla każdej z klas, które się z nim wiąże:

```
     InPort port; ...  Component c = port.Component;
```

Jednak oba przeskoki należy wykonać jawnie w składni ścieżki. Ze względu na to wymaganie można łatwiej uzyskać dostęp do linku pośredniego. Poniższy kod kończy przeskok z linku do składnika :

```
    ComponentHasPorts.Component / ! Component
```

(Możesz pominąć nazwę relacji, gdzie jest taka sama jak w poprzednim segmencie).

## <a name="element-merge-directives"></a>Dyrektywy scalania elementów

Gdy użytkownik języka przeciąga element  z przybornika na diagram, konstruowane jest wystąpienie klasy narzędzia. Ponadto są łącza między tym wystąpieniem i istniejącymi elementami modelu. Niektóre elementy, takie jak składniki lub komentarze, są tworzone,  gdy użytkownik języka przeciąga je z przybornika do pustej części diagramu. Inne elementy są tworzone, gdy użytkownik języka przeciąga je na inne elementy hosta. Na przykład dane OutPort lub InPort są tworzone, gdy użytkownik języka przeciąga je na składnik.

Potencjalna klasa hosta, taka jak Component, będzie akceptować nowy element tylko wtedy, gdy klasa hosta ma dyrektywę scalania elementu dla klasy nowego elementu. Na przykład węzeł DomainClass o nazwie Name="Component" zawiera:

```xml
<DomainClass Name="Component" ...> ...
    <ElementMergeDirective>
      <Index>
        <DomainClassMoniker Name="ComponentPort" />
      </Index>
      <LinkCreationPaths>
        <DomainPath>ComponentHasPorts.Ports</DomainPath>
      </LinkCreationPaths>
    </ElementMergeDirective> ...
```

Monikera klasy, która znajduje się w węźle Index, odwołuje się do klasy elementu, która może zostać zaakceptowana. W tym przypadku ComponentPort jest abstrakcyjną klasą bazową InPort i OutPort. W związku z tym można zaakceptować jeden z tych elementów.

ComponentModel, klasa główna języka, ma dyrektywy scalania elementów dla składników i komentarzy. Użytkownik języka może przeciągać elementy dla tych klas bezpośrednio na diagram, ponieważ puste części diagramu reprezentują klasę główną. Jednak model ComponentModel nie ma dyrektywy scalania elementów dla składnika ComponentPort. W związku z tym użytkownik języka nie może przeciągać operacji InPorts ani OutPorts bezpośrednio do diagramu.

Dyrektywa scalania elementu określa, jakie łącze lub łącza są tworzone, aby nowy element można zintegrować lub scalić z istniejącym modelem. W przypadku składnika ComponentPort tworzone jest wystąpienie componentHasPorts. DomainPath identyfikuje zarówno relację, jak i właściwość klasy nadrzędnej Ports, do której zostanie dodany nowy element.

Można utworzyć więcej niż jedno łącze w dyrektywie scalania elementu, uwzględniając więcej niż jedną ścieżkę tworzenia łącza. Jedna ze ścieżek musi być osadzona.

W ścieżce tworzenia linku można użyć więcej niż jednego segmentu. W tym przypadku ostatni segment definiuje, który link należy utworzyć. Wcześniejsze segmenty nawigają z klasy nadrzędnej do obiektu, z którego ma zostać utworzone nowe łącze.

Na przykład można dodać tę dyrektywę scalania elementu do klasy Component:

```xml
<DomainClass Name="Component" ...> ...
  <ElementMergeDirective>
    <Index>
       <DomainClassMoniker Name="Comment"/>
    </Index>
    <LinkCreationPaths>
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>
    </LinkCreationPaths>
  </ElementMergeDirective>
```

Użytkownicy języka mogą następnie przeciągnąć komentarz do składnika i automatycznie utworzyć nowy komentarz z linkiem do składnika.

Pierwsza ścieżka tworzenia linku przechodzi od obiektu do obiektu , a następnie tworzy wystąpienie `Component` `ComponentModel` relacji osadzania `ComponentModelHasComments` . Druga ścieżka tworzenia linku tworzy połączenie relacji odwołania CommentsReferenceComponents ze składnika hosta do nowego komentarza. Wszystkie ścieżki tworzenia linków muszą rozpoczynać się od klasy hostów i kończyć się łączem prowadzącym do nowo utworzonej klasy.

## <a name="xmlclassdata"></a>Xmlclassdata

Każda klasa domeny (w tym relacje i inne podtypy) może mieć dodatkowe informacje podane w węźle, który jest wyświetlany w sekcji `XmlClassData` `XmlSerializationBehavior` pliku DslDefinition.dsl. Te informacje dotyczą konkretnie sposobu przechowywania wystąpień klasy w postaci serializowanej, gdy model jest zapisywany w pliku.

Większość wygenerowanego kodu, który `XmlSerializationBehavior` ma wpływ, znajduje się w . `Dsl\GeneratedCode\Serializer.cs`

Każdy `XmlClassData` węzeł zawiera następujące węzły podrzędne i atrybuty:

- Węzeł moniker, który odwołuje się do klasy, do której mają zastosowanie dane.

- **XmlPropertyData** dla każdej właściwości zdefiniowanej w klasie .

- **XmlRelationshipData** dla każdej relacji, która jest źródłową w klasie . (Relacje mają również własne węzły XmlClassData).

- **Atrybut ciągu TypeName,** który określa nazwę klasy pomocnika serializacji w wygenerowanym kodzie.

- **Ciąg ElementName,** który określa tag XML serializowanych wystąpień tej klasy. Zgodnie z konwencją elementName jest zwykle taki sam jak nazwa klasy, z tą różnicą, że pierwsza litera jest mała. Na przykład przykładowy plik modelu rozpoczyna się od następującego:

    ```xml
    <componentModel ...
    ```

- **MonikerElementName** w plikach modelu serializowanego użytkownika. Ten atrybut wprowadza monikera, która odwołuje się do tej klasy.

- **MonikerAttributeName**, który identyfikuje nazwę atrybutu XML w moniker. W tym fragmencie pliku serializowanego użytkownika autor języka specyficznego dla domeny zdefiniował element **MonikerElementName** jako "inPortMoniker", a **monikerAttributeName** jako "path":

    ```xml
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilders

Konstruktor połączeń jest definiowany dla każdego narzędzia połączenia. Każdy konstruktor połączeń składa się z jednego lub większej liczby elementów LinkConnectDirective, z których każdy zawiera co najmniej jeden element SourceDirective i co najmniej jeden element TargetDirective. Po kliknięciu narzędzia połączenia użytkownik może rozpocząć połączenie z dowolnego kształtu zamapego na element modelu, który pojawia się na liście elementów SourceDirective. Połączenie można następnie na nawiązaniu na kształcie zamapowany na element, który pojawia się na liście TargetDirective elementów. Klasa wystąpienia relacji zależy od elementu LinkConnectDirective wyznaczonego przez miejsce, w którym zostało uruchomione połączenie.

### <a name="xmlpropertydata"></a>Xmlpropertydata

Atrybut **DomainPropertyMoniker** identyfikuje właściwość, do której odnoszą się dane. Ten atrybut musi być właściwością otaczającej klasy ClassData.

Atrybut **XmlName** nadaje odpowiadającą mu nazwę atrybutu, która powinna być wyświetlana w pliku XML. Zgodnie z konwencją ten ciąg jest taki sam jak nazwa właściwości, z tą różnicą, że pierwsza litera jest mała.

Domyślnie atrybut **Reprezentacja** jest ustawiony na wartość Atrybut. Jeśli **representation** jest ustawiona na element, węzeł podrzędny jest tworzony w XML. Jeśli **representation** jest ustawiona na Ignoruj, właściwość nie jest serializowana.

Atrybuty **IsMonikerKey** i **IsMonikerQualifier** zapewniają właściwości rolę w identyfikowaniu wystąpień klasy nadrzędnej. Właściwość **IsMonikerKey** można ustawić na wartość true dla jednej właściwości zdefiniowanej w klasie lub dziedziczonej przez klasę. Ten atrybut identyfikuje pojedyncze wystąpienie klasy nadrzędnej. Właściwość ustawiona na to `IsMonikerKey` zazwyczaj jest nazwą lub innym identyfikatorem klucza. Na przykład właściwość `Name` string jest kluczem moniker elementu NamedElement i jego klas pochodnych. Gdy użytkownik zapisuje model do pliku, ten atrybut musi zawierać unikatowe wartości dla każdego wystąpienia, wśród elementów równorzędnych w drzewie osadzania relacji.

W serializowanym pliku modelu pełna moniker elementu jest ścieżką od katalogu głównego modelu do drzewa osadzania relacji i przytłacza klucza moniker w każdym punkcie. Na przykład inports są osadzone w składniki, które są z kolei osadzone w katalogu głównym modelu. W związku z tym prawidłową moniker jest:

```xml
<inPortMoniker name="//Component2/InPort1" />
```

Można ustawić atrybut **IsMonikerQualifier** dla właściwości ciągu i zapewnić dodatkowy sposób konstruowania pełnej nazwy elementu. Na przykład w pliku DslDefinition.dsl przestrzeń **nazw** jest kwalifikatorem moniker.

### <a name="xmlrelationshipdata"></a>Xmlrelationshipdata

W pliku serializowanego modelu linki (zarówno relacji osadzania, jak i odwoływać się) są reprezentowane przez węzły podrzędne źródłowego końca relacji. W przypadku osadzania relacji węzeł podrzędny zawiera poddrzewo. W przypadku relacji odwołań węzeł podrzędny zawiera moniker, który odwołuje się do innej części drzewa.

Atrybut **XmlRelationshipData** w **atrybutze XmlClassData** definiuje dokładnie sposób zagnieżdżenia węzłów podrzędnych w elemencie źródłowym. Każda relacja, która jest źródłem klasy domeny, ma jeden **atrybut XmlRelationshipData.**

Atrybut **DomainRelationshipMoniker** identyfikuje jedną z relacji źródlenych w klasie .

Atrybut **RoleElementName** zawiera nazwę tagu XML, który zawiera węzeł podrzędny w serializowanych danych.

Na przykład plik DslDefinition.dsl zawiera:

```xml
<XmlClassData ElementName="component" ...>
  <DomainClassMoniker Name="Component" />
  <ElementData>
    <XmlRelationshipData RoleElementName="ports">
      <DomainRelationshipMoniker Name="ComponentHasPorts" />
    </XmlRelationshipData>
```

Dlatego serializowany plik zawiera:

```xml
<component name="Component1"> <!-- parent -->
   <ports> <!-- role -->
     <outPort name="OutPort1"> <!-- child element -->
       ...
     </outPort>
   </ports> ...
```

Jeśli atrybut **UseFullForm** ma wartość true, zostanie wprowadzona dodatkowa warstwa zagnieżdżania. Ta warstwa reprezentuje samą relację. Jeśli relacja ma właściwości, atrybut musi mieć wartość true.

```xml
<XmlClassData ElementName="outPort">
   <DomainClassMoniker Name="OutPort" />
   <ElementData>
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">
       <DomainRelationshipMoniker Name="Connection" />
     </XmlRelationshipData>
   </ElementData>
 </XmlClassData>
```

Serializowany plik zawiera:

```xml
<outPort name="OutPort1">  <!-- Parent -->
   <targets>  <!-- role -->
     <connection sourceRoleName="X">  <!-- relationship link -->
         <inPortMoniker name="//Component2/InPort1" /> <!-- child -->
     </connection>
    </targets>
  </outPort>
```

(Relacja połączenia ma własne dane klasy XML, które zapewniają nazwy elementów i atrybutów).

Jeśli **atrybut OmitElement** ma wartość true, nazwa roli relacji zostanie pominięta, która skraca serializowany plik i jest jednoznaczna, jeśli dwie klasy mają nie więcej niż jedną relację. Na przykład:

```xml
<component name="Component3">
  <!-- only one relationship could get here: -->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Serializacja definicji Domain-Specific językowego

Plik DslDefinition.dsl jest sam w sobie serializowanym plikiem i jest zgodny z definicją języka specyficzną dla domeny. Poniżej przedstawiono kilka przykładów definicji serializacji XML:

- **Dsl** to węzeł RootClass i klasa diagramu. DomainClass, DomainRelationship i inne elementy są osadzone w obszarze `Dsl` .

- **Klasy** to **element RoleElementName** relacji między klasami Domain-Specific Language i DomainClass.

```xml
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

- Atrybut **XmlSerializationBehavior** jest osadzony w ramach atrybutu , ale atrybut OmitElement został ustawiony dla `Dsl` relacji osadzania.  W związku z `RoleElementName` tym żaden atrybut nie interweniuje. Natomiast atrybut **ClassData** jest atrybutem relacji osadzania między atrybutem `RoleElementName` **XmlSerializationBehavior** i **atrybutem XmlClassData.**

```xml
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

- ConnectorHasDecorators to relacja osadzania między i `Connector` `Decorator` . `UseFullForm` Został ustawiony tak, aby nazwa relacji była wyświetlana wraz z listą właściwości dla każdego linku z obiektu łącznika. Jednak został również ustawiony tak, aby nie ująć w sobie wielu linków osadzonych `OmitElement` `RoleElementName` wewnątrz obiektu `Connector` :

```xml
<Connector Name="AssociationLink" ...>
  <ConnectorHasDecorators Position="TargetTop" ...>
    <TextDecorator Name="TargetRoleName"   />
  </ConnectorHasDecorators>
  <ConnectorHasDecorators Position="SourceTop" ...>
    <TextDecorator Name="SourceRoleName"   />
  </ConnectorHasDecorators>
</Connector>
```

## <a name="shapes-and-connectors"></a>Kształty i łączniki

Definicje kształtów i łączników dziedziczą atrybuty i węzły podrzędne z klas domeny, oprócz następujących:

- `Color` i `Line``Style` atrybuty.

- **ExposesFillColorAsProperty** i kilka podobnych atrybutów. Te atrybuty logiczne sprawiają, że odpowiednia zmienna właściwości jest przez użytkownika. Ogólnie rzecz biorąc, gdy użytkownik języka kliknie kształt na  diagramie, właściwości wyświetlane w oknie Właściwości są właściwościami wystąpienia klasy domeny, do którego jest mapowany kształt. Jeśli `ExposesFillColorAsProperty` wartość jest ustawiona na wartość true, zostanie również wyświetlona właściwość kształtu.

- **ShapeHasDecorators .** Wystąpienie tego atrybutu występuje dla każdego tekstu, ikony lub dekoratora rozwijania/zwijania. (W pliku DslDefinition.dsl relacja `ShapeHasDecorators` jest ustawiona `UseFullForm` na wartość true).

## <a name="shape-maps"></a>Mapy kształtów

Mapy kształtów określają sposób, w jaki wystąpienia danej klasy domeny są wyświetlane na ekranie reprezentowanym przez kształt. Mapy kształtów i łączników są wyświetlane `Diagram` w sekcji pliku DslDefinition.dsl.

Podobnie jak w poniższym przykładzie, elementy mają co najmniej monikera klasy domeny, monikera kształtu `ShapeMap` i `ParentElementPath` elementu:

```xml
<ShapeMap>
  <DomainClassMoniker Name="InPort" />
  <ParentElementPath>
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>
  </ParentElementPath>
  <PortMoniker Name="InPortShape" />
</ShapeMap>
```

Podstawową funkcją elementu jest to, że ta sama klasa obiektów może wyglądać jako `ParentElementPath` inny kształt w różnych kontekstach. Jeśli na przykład można również osadzić element w komentarzu, obiekt może wyglądać w tym celu `InPort` `InPort` jako inny kształt.

Po drugie ścieżka określa relację kształtu z jego elementem nadrzędnym. Między kształtami w pliku DslDefinition.dsl nie zdefiniowano struktury osadzania. Strukturę należy wywnioskować z map kształtów. Element nadrzędny kształtu jest kształtem mapowany na element domeny, który identyfikuje ścieżka elementu nadrzędnego. W tym przypadku ścieżka identyfikuje składnik, do którego `InPort` należy. W innej mapie kształtów klasa Component jest mapowana na element ComponentShape. W związku z `InPort` tym nowy kształt jest kształtem podrzędnym elementu . `ComponentShape`

Jeśli zamiast tego dołączono kształt InPort do diagramu, ścieżka elementu nadrzędnego będzie musiała zrobić kolejny krok do modelu składników, który jest mapowany na diagram:

```
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel
```

Katalog główny modelu nie ma mapy kształtów. Zamiast tego katalog główny jest przywołyny bezpośrednio z diagramu, który ma `Class` element :

```xml
<Diagram Name="ComponentDiagram" >
    <Class>
      <DomainClassMoniker Name="ComponentModel" />
    </Class>...
```

### <a name="decorator-maps"></a>Mapy dekoratora

Mapa dekoratora kojarzy właściwość w zamapowanych klasach z dekoratorem na kształcie. Jeśli właściwość jest typem wyliczany lub logicznym, jej wartość może określić, czy dekorator jest widoczny. Jeśli dekorator jest dekoratorem tekstu, może pojawić się wartość właściwości i użytkownik może ją edytować.

### <a name="compartment-shape-maps"></a>Mapy kształtów przedziałów

Mapy kształtów przedziałów to podtypy map kształtów.

## <a name="connector-maps"></a>Mapy łączników

Minimalna mapa łącznika odwołuje się do łącznika i relacji:

```xml
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Mapy łączników mogą również zawierać mapy dekoratora.

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)
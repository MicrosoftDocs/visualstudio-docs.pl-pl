---
title: Plik DslDefinition.dsl
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 893f39149a9000f3672c5b3043551bcbd53e6b87
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808958"
---
# <a name="the-dsldefinitiondsl-file"></a>Plik DslDefinition.dsl

W tym temacie opisano strukturę pliku DslDefinition. DSL w projekcie DSL [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] rozwiązania, które definiuje *Język specyficzny dla domeny*. Plik DslDefinition. DSL opisuje klasy i relacje języka specyficznego dla domeny, wraz z diagramem, kształtami, łącznikami, formatem serializacji i **przybornikiem** języka specyficznego dla domeny i jego narzędziami do edycji. W przypadku rozwiązania dotyczącego języka specyficznego dla domeny kod definiujący te narzędzia jest generowany zgodnie z informacjami w pliku DslDefinition. DSL.

Ogólnie rzecz biorąc, użyj *Projektant języka specyficznego dla domeny* , aby edytować plik DslDefinition. DSL. Jednak jego pierwotna postać to XML, a plik DslDefinition. DSL można otworzyć w edytorze XML. Przydatne może być zrozumienie, jakie informacje zawiera plik i jak są zorganizowane na potrzeby debugowania i rozszerzania.

Przykłady w tym temacie są pobierane z szablonu rozwiązania diagram składników. Aby zapoznać się z przykładem, Utwórz rozwiązanie dotyczące języka specyficznego dla domeny, które jest oparte na szablonie rozwiązania model składników. Po utworzeniu rozwiązania plik DslDefinition. DSL zostanie wyświetlony w projektant języka specyficznego dla domeny. Zamknij plik, kliknij go prawym przyciskiem myszy w **Eksplorator rozwiązań**, wskaż polecenie **Otwórz za pomocą**, kliknij **Edytor XML**, a następnie kliknij przycisk **OK**.

## <a name="sections-of-the-dsldefinitiondsl-file"></a>Sekcje pliku DslDefinition. DSL

Element główny jest \<Dsl> i jego atrybuty identyfikują nazwę języka specyficznego dla domeny, przestrzeń nazw oraz główne i pomocnicze numery wersji dla wersji. `DslDefinitionModel`Schemat definiuje zawartość i strukturę prawidłowego pliku DslDefinition. DSL.

Elementy podrzędne \<Dsl> elementu głównego są następujące:

### <a name="classes"></a>Klasy

Ta sekcja definiuje każdą klasę domeny, która generuje klasę w wygenerowanym kodzie.

### <a name="relationships"></a>Relacje

Ta sekcja definiuje każdą relację w modelu. Źródło i cel reprezentują dwie strony relacji.

### <a name="types"></a>Typy

Ta sekcja definiuje każdy typ i jego przestrzeń nazw. Właściwości domeny mają dwa typy. `DomainEnumerations` są zdefiniowane w modelu i generują typy w DomainModel.cs. `ExternalTypes` odnosi się do typów, które są zdefiniowane w innym miejscu (na przykład `String` lub `Int32` ) i nie generują żadnych elementów.

### <a name="shapes"></a>Kształty

W tej sekcji zdefiniowano kształty opisujące, jak model pojawia się w projektancie. Te kształty geometryczne są mapowane na klasy w modelu w sekcji diagramu.

### <a name="connectors"></a>Łączniki

Ta sekcja definiuje wygląd łączników, które pojawiają się w projektancie. Te opisy stylów geometrycznych są mapowane na określone relacje w modelu w sekcji diagramu.

### <a name="xmlserializationbehavior"></a>XmlSerializationBehavior

Ta sekcja definiuje schemat serializacji i zawiera dodatkowe informacje na temat sposobu zapisywania każdej klasy w pliku.

### <a name="explorerbehavior"></a>ExplorerBehavior

Ta sekcja definiuje, jak okno **Eksploratora DSL** pojawia się, gdy użytkownik edytuje model.

### <a name="connectionbuilders"></a>ConnectionBuilders

Ta sekcja definiuje konstruktora połączeń dla każdego narzędzia łącznika (narzędzia do tworzenia linków między dowolnymi dwiema klasami, które mogą być połączone). Ta sekcja określa, czy można nawiązać połączenie z klasą źródłową i docelową.

### <a name="diagram"></a>Diagram

Ta sekcja definiuje diagram i służy do określania właściwości, takich jak kolor tła i Klasa główna. (Klasa główna jest klasą domeny, która jest reprezentowana przez diagram jako całość). Sekcja diagramu zawiera również elementy ShapeMap i ConnectorMap, które określają kształt lub łącznik reprezentujący każdą klasę lub relację domeny.

### <a name="designer"></a>Projektant

Ta sekcja definiuje projektanta (Edytor), który łączy **Przybornik**, ustawienia walidacji, diagram i schemat serializacji. Sekcja Projektant definiuje również klasę główną modelu, która jest zazwyczaj klasą główną diagramu.

### <a name="explorer"></a>Eksplorator

W tej sekcji przedstawiono zachowanie **Eksploratora DSL** (zdefiniowane w sekcji XmlSerializationBehavior).

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Monikery w pliku DslDefinition. DSL

W pliku DslDefinition. DSL można użyć monikerów, aby wprowadzić odsyłacze do określonych elementów. Na przykład każda definicja relacji zawiera podsekcję źródłową i podsekcję docelową. Każda podsekcja zawiera Moniker klasy obiektu, która może być połączona z tą relacją:

```xml
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

Zazwyczaj przestrzeń nazw przywoływanego elementu (w tym przykładzie `Library` Klasa domeny) jest taka sama jak odwołanie do elementu (w tym przypadku relacji domeny LibraryHasMembers). W takich przypadkach moniker musi zawierać tylko nazwę klasy. W przeciwnym razie należy użyć pełnej formy/Namespace/Name:

```xml
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

System monikera wymaga, aby elementy równorzędne w drzewie XML miały odrębne nazwy. Z tego powodu błędy walidacji występują w przypadku próby zapisania definicji języka specyficznego dla domeny, która ma na przykład dwie klasy o tej samej nazwie. Należy zawsze skorygować takie błędy duplikatów nazw przed zapisaniem pliku DslDefinition. DSL, aby można było ponownie załadować go prawidłowo.

Każdy typ ma swój własny typ monikera: DomainClassMoniker, DomainRelationshipMoniker i tak dalej.

## <a name="types"></a>Typy

Sekcja typy określa wszystkie typy, które plik DslDefinition. DSL zawiera jako typy właściwości. Te typy dzielą się na dwa rodzaje: typy zewnętrzne, takie jak system. String i typy wyliczeniowe.

### <a name="external-types"></a>Typy zewnętrzne

Przykład diagramu składników zawiera zestaw standardowych typów pierwotnych, chociaż są używane tylko niektóre z nich.

Każda definicja typu zewnętrznego składa się tylko z nazwy i przestrzeni nazw, takiej jak ciąg i system:

```xml
<ExternalType Name="String" Namespace="System" />
```

Są używane pełne nazwy typów, zamiast odpowiedników słów kluczowych kompilatora, takich jak "String".

Typy zewnętrzne nie są ograniczone do standardowych typów bibliotek.

### <a name="enumerations"></a>Wyliczenia

Typowa Specyfikacja wyliczenia przypomina ten przykład:

```xml
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

Ten `IsFlags` atrybut określa, czy wygenerowany kod jest poprzedzony `[Flags]` atrybutem środowiska uruchomieniowego języka wspólnego (CLR), który określa, czy wartości wyliczenia mogą być połączone jako bitowe. Jeśli ten atrybut ma wartość true, należy określić potęgi dla wartości literału.

## <a name="classes"></a>Klasy

Większość elementów w każdej definicji języka specyficznego dla domeny jest bezpośrednio lub pośrednio wystąpieniami `DomainClass` . Podklasy `DomainClass` include `DomainRelationship` , `Shape` , `Connector` , i `Diagram` . `Classes`Sekcja pliku DslDefinition. DSL zawiera listę klas domen.

Każda klasa ma zestaw właściwości i może mieć klasę bazową. W przykładzie diagramu składników `NamedElement` jest klasą abstrakcyjną, która ma `Name` Właściwość, której typem jest ciąg:

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

`NamedElement` jest podstawą kilku innych klas, takich jak `Component` , które mają własne właściwości oprócz `Name` właściwości, która dziedziczy z `NamedElement` . Węzeł podrzędny BaseClass zawiera odwołanie do monikera. Ponieważ Klasa, do której istnieje odwołanie, znajduje się w tej samej przestrzeni nazw, nazwa jest wymagana tylko w monikerze:

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

Każda klasa domeny (w tym relacje, kształty, łączniki i diagramy) może mieć te atrybuty i węzły podrzędne:

- **Identyfikator.** Ten atrybut jest identyfikatorem GUID. Jeśli nie podasz wartości w pliku, projektant języka specyficznego dla domeny utworzy wartość. (Na ilustracjach w tym dokumencie ten atrybut jest zwykle pomijany w celu zaoszczędzenia miejsca).

- **Nazwa i przestrzeń nazw.** Te atrybuty określają nazwę i przestrzeń nazw klasy w wygenerowanym kodzie. Ze sobą muszą być unikatowe w języku specyficznym dla domeny.

- **InheritanceModifier.** Ten atrybut to "abstract", "Sealed" lub "none".

- **Nazwa.** Ten atrybut jest nazwą, która pojawia się w oknie **Właściwości** . Atrybut DisplayName może zawierać spacje i inne znaki interpunkcyjne.

- **GeneratesDoubleDerived.** Jeśli ten atrybut ma wartość true, generowane są dwie klasy i jedna z nich jest podklasą innych. Wszystkie wygenerowane metody znajdują się w bazie, a konstruktory znajdują się w podklasie. Ustawiając ten atrybut, można przesłonić każdą wygenerowaną metodę w kodzie niestandardowym.

- **HasCustomConstructor**. Jeśli ten atrybut ma wartość true, Konstruktor zostanie pominięty z wygenerowanego kodu, dzięki czemu można napisać własną wersję.

- **Atrybuty**. Ten atrybut zawiera atrybuty CLR wygenerowanej klasy.

- **BaseClass**. Jeśli określisz klasę bazową, musi ona być tego samego typu. Na przykład Klasa domeny musi mieć inną klasę domeny jako podstawową, a kształt przedziału musi mieć kształt przedziału. Jeśli nie określisz klasy bazowej, Klasa w wygenerowanym kodzie pochodzi z standardowej klasy Framework. Na przykład Klasa domeny pochodzi od `ModelElement` .

- **Właściwości**. Ten atrybut zawiera właściwości, które są utrzymywane w ramach kontroli transakcji i utrwalane, gdy model jest zapisywany.

- **ElementMergeDirectives**. Każda dyrektywa scalania elementów kontroluje, w jaki sposób inne wystąpienie innej klasy jest dodawane do wystąpienia klasy nadrzędnej. Więcej szczegółów na temat dyrektyw scalania elementów można znaleźć w dalszej części tego tematu.

- Klasa języka C# jest generowana dla każdej klasy domeny, która jest wymieniona w `Classes` sekcji. Klasy języka C# są generowane w Dsl\GeneratedCode\DomainClasses.cs.

### <a name="properties"></a>Właściwości

Każda właściwość domeny ma nazwę i typ. Nazwa musi być unikatowa w obrębie klasy domeny i jej przechodnich baz.

Typ musi odwoływać się do jednego z wymienionych w `Types` sekcji. Na ogół moniker musi zawierać przestrzeń nazw.

```xml
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Każda właściwość domeny może mieć również następujące atrybuty:

- **Jest przeglądalna**. Ten atrybut określa, czy właściwość pojawia się w oknie **Właściwości** , gdy użytkownik kliknie obiekt klasy nadrzędnej.

- **IsUIReadOnly**. Ten atrybut określa, czy użytkownik może zmienić właściwość w oknie **Właściwości** lub za pomocą dekoratora, w którym jest wyświetlana właściwość.

- **Rodzaju**. Można ustawić ten atrybut na normalny, obliczony lub CustomStorage. Jeśli ustawisz ten atrybut na obliczony, musisz podać niestandardowy kod określający wartość i właściwość będzie tylko do odczytu. Jeśli ten atrybut zostanie ustawiony na CustomStorage, należy podać kod, który pobiera i ustawia wartości.

- **IsElementName**. Jeśli ten atrybut jest ustawiony na wartość true, jego wartość jest automatycznie ustawiana na wartość unikatową podczas tworzenia wystąpienia klasy nadrzędnej. Ten atrybut może być ustawiony na wartość true dla jednej właściwości w każdej klasie, która musi mieć typ ciągu. W przykładzie diagramu składników `Name` Właściwość w `NamedElement` ma `IsElementName` ustawioną wartość true. Za każdym razem, gdy użytkownik tworzy `Component` element (który dziedziczy z `NamedElement` ), nazwa jest automatycznie inicjowana na przykład "Component6".

- `DefaultValue`. Jeśli określono ten atrybut, określona wartość zostanie przypisana do tego atrybutu dla nowych wystąpień tej klasy. Jeśli `IsElementName` jest ustawiona, atrybut DefaultValue określa początkową część nowego ciągu.

- **Kategoria** to nagłówek, pod którym Właściwość pojawi się w oknie **Właściwości** .

## <a name="relationships"></a>Relacje

`Relationships`Sekcja zawiera listę wszystkich relacji w języku specyficznym dla domeny. Każdy `Domain Relationship` jest binarny i kierowany, łączący elementy członkowskie klasy źródłowej z elementami członkowskimi klasy docelowej. Klasy źródłowe i docelowe są zazwyczaj klasami domeny, ale relacje z innymi relacjami są również dozwolone.

Na przykład relacja połączenia łączy elementy członkowskie klasy InPort z elementami członkowskimi klasy InPort. Każde wystąpienie linku relacji łączy wystąpienie elementu wychodzącego z wystąpieniem elementu InPort. Ze względu na to, że relacja jest wiele-wielu, każdy z nich może mieć wiele linków połączenia ze źródłami, a każde wystąpienie portu może mieć wiele linków połączeń przeznaczonych dla niego.

### <a name="source-and-target-roles"></a>Role źródłowe i docelowe

Każda relacja zawiera role źródłowe i docelowe, które mają następujące atrybuty:

- `RolePlayer`Atrybut odwołuje się do klasy domeny połączonych wystąpień: element unport dla elementu docelowego.

- `Multiplicity`Atrybut ma cztery możliwe wartości (wartości ZeroMany, ZeroOne, one i OneMany). Ten atrybut odnosi się do liczby linków tej relacji, które mogą być skojarzone z jednym obiektem pełniącego rolę.

- Ten `PropertyName` atrybut określa nazwę, która jest używana w klasie odgrywanej przez rolę do uzyskiwania dostępu do obiektów na drugim końcu. Ta nazwa jest używana w szablonie lub w niestandardowym kodzie do przechodzenia między relacjami. Na przykład `PropertyName` atrybut roli źródła jest ustawiony na `Targets` . W związku z tym Poniższy kod będzie działał:

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Według Konwencji nazwy właściwości są plural, Jeśli liczebność to wartości ZeroMany lub OneMany.

     Liczebność roli odnosi się do liczby ról odwrotnych, które można skojarzyć z każdym wystąpieniem tej roli. Na przykład w elementu ComponentHasPorts relacji rola docelowa ma `RolePlayer` atrybut ustawiony na port, `PropertyName` atrybut ustawiony na składnik, a `Multiplicity` atrybut ustawiony na ZeroOne. W związku z tym odpowiedni kod służący do korzystania z tej roli to:

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

- Rola `Name` jest nazwą, która jest używana w klasie relacji do odwoływania się do tego końca łącza. Zgodnie z Konwencją nazwa roli zawsze jest pojedyncza, ponieważ każdy z nich ma tylko jedno wystąpienie na każdym końcu. Następujący kod będzie działał:

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

- Domyślnie `IsPropertyGenerator` atrybut ma wartość true. Jeśli jest ustawiona na false, nie jest tworzona żadna właściwość w klasie obiektu pełniącego rolę. (W tym przypadku, `op.Targets` na przykład nie będzie działał). Jednak nadal jest możliwe użycie niestandardowego kodu w celu przechodzenia między relacjami lub uzyskania dostępu do samych linków, jeśli niestandardowy kod używa relacji jawnie:

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>Atrybuty relacji

Oprócz atrybutów i węzłów podrzędnych, które są dostępne dla wszystkich klas, każda relacja ma następujące atrybuty:

- **Isosadzenia**. Ten atrybut Boolean Określa, czy relacja jest częścią drzewa osadzania. Każdy model musi utworzyć drzewo z relacjami osadzania. W związku z tym każda klasa domeny musi być celem co najmniej jednej relacji osadzania, chyba że jest to katalog główny modelu.

- **AllowsDuplicates**. Ten atrybut logiczny, który domyślnie ma wartość false, ma zastosowanie tylko do relacji, które mają liczebność "wiele" zarówno w źródłowym, jak i docelowym. Określa, czy użytkownicy języka mogą łączyć pojedynczą parę elementów źródłowych i docelowych przez więcej niż jedno połączenie z tą samą relacją.

## <a name="designer-and-toolbox-tabs"></a>Zakładki projektanta i przybornika

Główną częścią sekcji **projektanta** pliku DslDefinition. DSL jest elementy **ToolboxTab** . Jeden Projektant może mieć kilka z tych elementów, z których każdy reprezentuje sekcję w **przyborniku**wygenerowanego projektanta. Każdy element **ToolboxTab** może zawierać jeden lub więcej elementów **Narzędzie ElementTool** , elementów **ConnectionTool** lub obu.

Narzędzia elementów mogą tworzyć wystąpienia określonej klasy domeny. Gdy użytkownik przeciągnie narzędzie elementu na diagram, wynik jest określany przez dyrektywy scalania elementów zgodnie z opisem w sekcji dyrektywy scalania elementów w dalszej części tego tematu.

Każde narzędzie połączenia może wywoływać określonego konstruktora połączeń. Jeden Konstruktor połączeń może utworzyć więcej niż jeden typ relacji, w zależności od tego, gdzie użytkownik kliknie mysz, zgodnie z opisem w sekcji dotyczącej konstruktorów połączeń.

Żaden typ narzędzia bezpośrednio konstruuje kształty lub łączniki. Każdy tworzy wystąpienie klasy domeny lub relacji domeny; mapowania kształtu i łącznika następnie określają sposób wyświetlania tej klasy domeny lub relacji domeny.

## <a name="paths"></a>Ścieżki

Ścieżki domen są wyświetlane w kilku lokalizacjach w pliku DslDefinition. DSL. Ścieżki te określają serię łączy z jednego elementu w modelu (czyli wystąpienie języka specyficznego dla domeny) do innej. Składnia ścieżki jest prosta, ale pełna.

Ścieżki są wyświetlane w pliku DslDefinition. DSL w `<DomainPath>...</DomainPath>` znacznikach. Mimo że ścieżki mogą przechodzić przez wiele linków, większość przykładów w ramach ćwiczenia przechodzą tylko jeden link.

Ścieżka składa się z sekwencji segmentów. Każdy segment jest przeskokiem z obiektu do linku lub łącza do obiektu. W związku z tym przeskoki zwykle są alternatywne w długim ścieżce. Pierwszy przeskok pochodzi z obiektu do łącza, drugi przeskoku do obiektu na drugim końcu łącza, trzeci przeskok to następny link i tak dalej. Sporadyczny wyjątek od tej sekwencji polega na tym, że relacja jest w relacji źródłowej lub docelowej innej relacji.

Każdy segment rozpoczyna się od nazwy relacji. W przypadku skoku obiektu do łącza relacja poprzedza kropkę i nazwę właściwości: " `Relationship . Property` ". W przeskoku link-obiekt relacja poprzedza znak wykrzyknika i nazwę roli: " `Relationship ! Role` ".

Przykład diagramu składników zawiera ścieżkę w ParentElementPath ShapeMap dla nieportu. Ta ścieżka jest uruchamiana w następujący sposób:

```
    ComponentHasPorts.Component
```

W tym przykładzie InPort jest podklasą elementu ComponentPort i ma relację elementu ComponentHasPorts. Właściwość jest wywoływana jako składnik.

Podczas pisania języka C# względem tego modelu można przechodzić przez łącze w jednym kroku, używając właściwości, która jest generowana przez relację na każdej z klas, z którą się odnoszą:

```
     InPort port; ...  Component c = port.Component;
```

Jednak w składni ścieżki należy jawnie wykonać oba przeskoki. Ze względu na to wymaganie można łatwiej uzyskać dostęp do pośredniego linku. Poniższy kod uzupełnia przeskok z linku do składnika:

```
    ComponentHasPorts.Component / ! Component
```

(Możesz pominąć nazwę relacji, w której jest taka sama jak w poprzednim segmencie).

## <a name="element-merge-directives"></a>Dyrektywy scalania elementów

Gdy użytkownik języka przeciągnie element z **przybornika** na diagram, wystąpienie klasy narzędzi zostało skonstruowane. Ponadto są tworzone linki między tym wystąpieniem a istniejącymi elementami modelu. Niektóre elementy, takie jak składniki lub komentarze, są tworzone, gdy użytkownik języka przeciągnie je z **przybornika** na pustą część diagramu. Inne elementy są tworzone, gdy użytkownik języka przeciągnie je na inne elementy hosta. Na przykład, w przypadku, gdy użytkownik języka przeciągnie go na składnik.

Potencjalna Klasa hosta, taka jak składnik, będzie akceptować nowy element tylko wtedy, gdy Klasa hosta ma dyrektywę scalania elementów dla klasy nowego elementu. Na przykład węzeł DomainClass o nazwie "Component" zawiera:

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

Moniker klasy, który znajduje się pod węzłem indeksu, odwołuje się do klasy elementu, który można zaakceptować. W tym przypadku ComponentPort jest abstrakcyjną klasą bazową dla elementu InPort i unport. W związku z tym można zaakceptować dowolny z tych elementów.

ComponentModel, główna Klasa języka, zawiera dyrektywy scalania elementów dla składników i komentarzy. Użytkownik języka może przeciągać elementy dla tych klas bezpośrednio do diagramu, ponieważ puste części diagramu reprezentują klasę główną. Jednak ComponentModel nie ma dyrektywy scalania elementów dla ComponentPort. W związku z tym użytkownik języka nie może przeciągać danych o portach ani transportach bezpośrednio na diagramie.

Dyrektywa scalania elementów określa, jakie łącza lub łącza są tworzone, aby nowy element mógł zintegrować lub scalić z istniejącym modelem. Dla ComponentPort jest tworzone wystąpienie elementu elementu ComponentHasPorts. DomainPath identyfikuje zarówno relację, jak i właściwość klasy nadrzędnej, porty, do których zostanie dodany nowy element.

Można utworzyć więcej niż jedno łącze w dyrektywie scalania elementów przez uwzględnienie więcej niż jednej ścieżki tworzenia linku. Jedna ze ścieżek musi być osadzona.

W ścieżce tworzenia linku można użyć więcej niż jednego segmentu. W tym przypadku ostatni segment definiuje, jakie łącze należy utworzyć. Poprzednie segmenty nawigują od klasy nadrzędnej do obiektu, z którego ma zostać utworzony nowy link.

Na przykład można dodać tę dyrektywę scalenia elementów do klasy Component:

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

Pierwsza ścieżka tworzenia linku przechodzi od `Component` do `ComponentModel` a, a następnie tworzy wystąpienie relacji osadzania `ComponentModelHasComments` . Druga ścieżka tworzenia linku tworzy łącze do relacji odwołania CommentsReferenceComponents ze składnika hosta do nowego komentarza. Wszystkie ścieżki tworzenia linków muszą zaczynać się od klasy hosta i muszą kończyć się linkiem, który prowadzi do nowo utworzonej klasy.

## <a name="xmlclassdata"></a>XmlClassData

Każda klasa domeny (w tym relacje i inne podtypy) może mieć dodatkowe informacje podane w `XmlClassData` węźle, który jest wyświetlany w `XmlSerializationBehavior` sekcji pliku DslDefinition. DSL. Informacje te zależą od tego, jak wystąpienia klasy są przechowywane w serializowanej formie, gdy model jest zapisywany w pliku.

Większość wygenerowanego kodu, którego `XmlSerializationBehavior` dotyczy wpływ, znajduje się w `Dsl\GeneratedCode\Serializer.cs` .

Każdy `XmlClassData` węzeł zawiera następujące węzły podrzędne i atrybuty:

- Węzeł monikera, który odwołuje się do klasy, do której stosują się dane.

- **XmlPropertyData** dla każdej właściwości, która jest zdefiniowana w klasie.

- **Element XmlRelationshipData** dla każdej relacji, która jest źródłem w klasie. (Relacje mają także własne węzły XmlClassData).

- **TypeName** — atrybut ciągu, który określa nazwę klasy pomocnika serializacji w wygenerowanym kodzie.

- Ciąg **ElementName** , który określa tag XML serializowanych wystąpień tej klasy. Zgodnie z Konwencją, ElementName jest zwykle taka sama jak nazwa klasy, z wyjątkiem pierwszej litery jest małymi literami. Przykładowo przykładowy plik modelu rozpoczyna się od następującego:

    ```xml
    <componentModel ...
    ```

- **MonikerElementName** w serializowanych plikach modelu użytkownika. Ten atrybut wprowadza moniker odwołujący się do tej klasy.

- **MonikerAttributeName**, który identyfikuje nazwę atrybutu XML w monikerze. W tym fragmencie pliku serializowanego przez użytkownika autor języka specyficznego dla domeny zdefiniowany **MonikerElementName** jako "inPortMoniker" i **MonikerAttributeName** jako "ścieżka":

    ```xml
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilders

Konstruktor połączeń został zdefiniowany dla każdego narzędzia połączenia. Każdy Konstruktor połączeń składa się z co najmniej jednego elementu dyrektywa LinkConnectDirective, z którego każdy zawiera jeden lub więcej elementów SourceDirective i jeden lub więcej elementów TargetDirective. Po kliknięciu narzędzia połączenia użytkownik może uruchomić połączenie z dowolnego kształtu zamapowanego do elementu modelu, który pojawia się na liście elementów SourceDirective. Połączenie można następnie wykonać na kształcie, który jest mapowany do elementu, który pojawia się na liście elementów TargetDirective. Klasa relacji jest zależna od elementu dyrektywa LinkConnectDirective wyoznaczonego przez miejsce uruchomienia połączenia.

### <a name="xmlpropertydata"></a>XmlPropertyData

Atrybut **DomainPropertyMoniker** identyfikuje właściwość, do której odwołują się dane. Ten atrybut musi być właściwością klasy otaczającej ClassData.

Atrybut **xmlname** daje odpowiadającą nazwę atrybutu, który powinien pojawić się w pliku XML. Według Konwencji ten ciąg jest taka sama jak nazwa właściwości, z wyjątkiem pierwszej litery jest małymi literami.

Domyślnie atrybut **reprezentacja** ma wartość Attribute. Jeśli **reprezentacja** jest ustawiona na element, w kodzie XML zostaje utworzony węzeł podrzędny. Jeśli **reprezentacja** jest ustawiona na wartość Ignoruj, właściwość nie jest serializowana.

Atrybuty **IsMonikerKey** i **IsMonikerQualifier** dają właściwość rolę w identyfikowaniu wystąpień klasy nadrzędnej. Można ustawić **IsMonikerKey** na true dla jednej właściwości, która jest zdefiniowana w lub dziedziczona przez klasę. Ten atrybut identyfikuje pojedyncze wystąpienie klasy nadrzędnej. Właściwość, którą ustawisz, `IsMonikerKey` jest zazwyczaj nazwą lub innym identyfikatorem klucza. Na przykład `Name` właściwość String jest kluczem monikera dla nazwanego i jego klasy pochodne. Gdy użytkownik zapisuje model do pliku, ten atrybut musi zawierać unikatowe wartości dla każdego wystąpienia, między jego elementami równorzędnymi w drzewie relacji osadzania.

W pliku serializowanego modelu pełny moniker elementu jest ścieżką z katalogu głównego w dół drzewa relacji osadzania, co powoduje wystąpienie klucza monikera w każdym punkcie. Na przykład elementy InPorts są osadzone w składnikach, które są z kolei osadzone w katalogu głównym modelu. Prawidłowy moniker jest więc:

```xml
<inPortMoniker name="//Component2/InPort1" />
```

Można ustawić atrybut **IsMonikerQualifier** dla właściwości String i podać dodatkowy sposób konstruowania pełnej nazwy elementu. Na przykład w pliku DslDefinition. DSL **przestrzeń nazw** jest kwalifikatorem monikera.

### <a name="xmlrelationshipdata"></a>Element XmlRelationshipData

W serializowanym pliku modelu linki (zarówno relacji osadzania, jak i odwołania) są reprezentowane przez węzły podrzędne końcowego końca relacji. W przypadku osadzania relacji węzeł podrzędny zawiera poddrzewo. W przypadku relacji odwołania węzeł podrzędny zawiera moniker, który odwołuje się do innej części drzewa.

Atrybut **element XmlRelationshipData** w atrybucie **XmlClassData** definiuje dokładnie sposób zagnieżdżenia węzłów podrzędnych w elemencie źródłowym. Każda relacja, która jest źródłem w klasie domeny, ma jeden atrybut **element XmlRelationshipData** .

Atrybut **DomainRelationshipMoniker** identyfikuje jedną z relacji źródłowych w klasie.

Atrybut **RoleElementName** zawiera nazwę tagu XML, który obejmuje węzeł podrzędny w serializowanych danych.

Na przykład plik DslDefinition. DSL zawiera następujące:

```xml
<XmlClassData ElementName="component" ...>
  <DomainClassMoniker Name="Component" />
  <ElementData>
    <XmlRelationshipData RoleElementName="ports">
      <DomainRelationshipMoniker Name="ComponentHasPorts" />
    </XmlRelationshipData>
```

W związku z tym serializowany plik zawiera:

```xml
<component name="Component1"> <!-- parent -->
   <ports> <!-- role -->
     <outPort name="OutPort1"> <!-- child element -->
       ...
     </outPort>
   </ports> ...
```

Jeśli atrybut **UseFullForm** ma wartość true, zostaje wprowadzona dodatkowa warstwa zagnieżdżania. Ta warstwa reprezentuje relację. Atrybut musi być ustawiony na wartość true, jeśli relacja ma właściwości.

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

(Relacja połączenia ma własne dane klasy XML, które zawierają nazwy elementów i atrybutów).

Jeśli atrybut **pomijaelement** ma wartość true, nazwa roli relacji zostanie pominięta, co skraca serializowany plik i jest niejednoznaczna, jeśli dwie klasy nie mają więcej niż jednej relacji. Na przykład:

```xml
<component name="Component3">
  <!-- only one relationship could get here: -->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Serializacja definicji języka specyficznego dla domeny

Plik DslDefinition. DSL jest samym zserializowanym plikiem i jest zgodny z definicją języka specyficznego dla domeny. Poniżej przedstawiono kilka przykładów definicji serializacji XML:

- **DSL** jest węzłem RootClass i klasą diagramu. DomainClass, DomainRelationship i inne elementy są osadzone w kategorii `Dsl` .

- **Klasy** to **RoleElementName** relacji między językiem specyficznym dla domeny a DomainClass.

```xml
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

- Atrybut **XmlSerializationBehavior** jest osadzony w `Dsl` atrybucie, ale atrybut **pomijaelement** został ustawiony w relacji osadzania. W związku z tym żaden atrybut nie jest `RoleElementName` interweniowany. Z kolei atrybut **ClassData** jest `RoleElementName` atrybutem relacji osadzania między atrybutem **XmlSerializationBehavior** a atrybutem **XmlClassData** .

```xml
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

- ConnectorHasDecorators jest relacją osadzania między `Connector` i `Decorator` . `UseFullForm` został ustawiony tak, aby nazwa relacji była wyświetlana z listą właściwości dla każdego łącza z obiektu łącznika. Jednak program został `OmitElement` również ustawiony tak, aby nie `RoleElementName` otaczał wielu linków, które są osadzone w `Connector` :

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

Definicje kształtów i łączników dziedziczą atrybuty i węzły podrzędne z klas domen, a także następujące elementy:

- `Color` i `Line``Style` atrybuty.

- **ExposesFillColorAsProperty** i kilka podobnych atrybutów. Te atrybuty logiczne tworzą odpowiednią zmienną właściwości dla użytkownika. Ogólnie rzecz biorąc, gdy użytkownik języka kliknie kształt na diagramie, właściwości, które pojawiają się w oknie **Właściwości** , są tymi z wystąpienia klasy domeny, do którego jest mapowany kształt. Jeśli `ExposesFillColorAsProperty` jest ustawiona na wartość true, zostanie wyświetlona również właściwość kształtu.

- **ShapeHasDecorators**. Wystąpienie tego atrybutu występuje dla każdego tekstu, ikony lub rozwijania/zwijania dekoratora. (W pliku DslDefinition. DSL, `ShapeHasDecorators` jest relacją z `UseFullForm` ustawioną na wartość true).

## <a name="shape-maps"></a>Mapy kształtów

Mapowania kształtów określają, jak wystąpienia danej klasy domeny pojawiają się na ekranie, reprezentowane przez kształt. Zarówno mapowanie kształtów, jak i łączników pojawiają się w `Diagram` sekcji pliku DslDefinition. DSL.

Tak jak w poniższym przykładzie `ShapeMap` elementy mają, na co najmniej Moniker klasy domeny, moniker kształtu i `ParentElementPath` element:

```xml
<ShapeMap>
  <DomainClassMoniker Name="InPort" />
  <ParentElementPath>
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>
  </ParentElementPath>
  <PortMoniker Name="InPortShape" />
</ShapeMap>
```

Podstawowa funkcja `ParentElementPath` elementu jest tak, że ta sama Klasa obiektów może być wyświetlana jako inny kształt w różnych kontekstach. Na przykład jeśli `InPort` może być również osadzony w komentarzu, `InPort` może pojawić się jako inny kształt w tym celu.

Następnie ścieżka Określa, jak kształt odnosi się do jego elementu nadrzędnego. Nie zdefiniowano struktury osadzania między kształtami w pliku DslDefinition. DSL. Należy wywnioskować strukturę z map kształtów. Element nadrzędny kształtu jest kształtem mapowanym na element domeny, który identyfikuje ścieżka elementu nadrzędnego. W takim przypadku ścieżka identyfikuje składnik, do którego `InPort` należy. W innej mapie kształtów Klasa składnika jest mapowana na ComponentShape. W związku z tym nowy `InPort` kształt zostanie utworzony jako kształt podrzędny składnika `ComponentShape` .

Po dołączeniu kształtu InPort do diagramu, ścieżka elementu nadrzędnego będzie musiała wykonać kolejny krok do modelu składnika, który jest mapowany na diagram:

```
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel
```

Katalog główny modelu nie ma mapy kształtów. Zamiast tego, do elementu głównego jest przywoływany bezpośrednio z diagramu, który ma `Class` element:

```xml
<Diagram Name="ComponentDiagram" >
    <Class>
      <DomainClassMoniker Name="ComponentModel" />
    </Class>...
```

### <a name="decorator-maps"></a>Mapy Dekoratora

Mapa dekoratora kojarzy właściwość w mapowanej klasie z dekoratora na kształcie. Jeśli właściwość jest typu wyliczeniowego lub logicznego, jego wartość może określić, czy dekoratora jest widoczny. Jeśli dekoratora jest tekstem dekoratora, wartość właściwości może pojawić się, a użytkownik może ją edytować.

### <a name="compartment-shape-maps"></a>Mapowania kształtów przedziału

Mapowania kształtów przedziału to podtypy map kształtów.

## <a name="connector-maps"></a>Mapy łączników

Mapa minimalnej łącznika odwołuje się do łącznika i relacji:

```xml
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Mapy łączników mogą również zawierać mapy dekoratora.

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)
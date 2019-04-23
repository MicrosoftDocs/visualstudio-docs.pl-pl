---
title: Plik DslDefinition.dsl | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: f3fc3ed7-2438-4e5a-b3d7-fe7e0e8a134c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c7294a0a835b4797424d1f736405a0488db28587
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070189"
---
# <a name="the-dsldefinitiondsl-file"></a>Plik DslDefinition.dsl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano strukturę plik DslDefinition.dsl w projekcie języka Dsl [!INCLUDE[dsl](../includes/dsl-md.md)] rozwiązania, które definiuje *języka specyficznego dla domeny*. Plik DslDefinition.dsl opis klas i relacji języka specyficznego dla domeny, wraz z diagramu, kształty, łączniki, format serializacji i **przybornika** języka specyficznego dla domeny i jego narzędzia do edycji. W rozwiązaniu języka dotyczącego określonej domeny jest generowany kod, który definiuje tych narzędzi, zgodnie z informacjami w plik DslDefinition.dsl.  
  
 Ogólnie rzecz biorąc, możesz użyć *projektanta języka specyficznego dla domeny* do edycji plik DslDefinition.dsl. Jednak język XML jest w postaci pierwotnej i plik DslDefinition.dsl można otworzyć w edytorze XML. Może być przydatna zrozumieć, jakie informacje zawiera plik i sposób organizowania dla celów debugowania i rozszerzenia.  
  
 Przykłady w niniejszym temacie są pobierane z szablonu rozwiązania Diagram składników. Aby zobaczyć przykład, tworzenie rozwiązań języka dotyczącego określonej domeny, które jest oparty na szablonie rozwiązania modeli składnika. Po utworzeniu rozwiązania, plik DslDefinition.dsl pojawia się w projektanta języka specyficznego dla domeny. Zamknij plik, kliknij go prawym przyciskiem myszy **Eksploratora rozwiązań**, wskaż polecenie **Otwórz za pomocą**, kliknij przycisk **edytora XML**, a następnie kliknij przycisk **OK**.  
  
## <a name="sections-of-the-dsldefinitiondsl-file"></a>Sekcje plik DslDefinition.dsl  
 Element główny jest \<Dsl >, jego atrybuty Określ nazwę języka specyficznego dla domeny, obszaru nazw i wersji głównych i pomocniczych numerów wersji. `DslDefinitionModel` Schemat definiuje zawartości i struktury, aby uzyskać prawidłowy plik DslDefinition.dsl.  
  
 Elementy podrzędne \<Dsl > element główny są następujące:  
  
 Klasy  
 Ta sekcja definiuje klasę każdej domeny, która generuje klasę w wygenerowanym kodzie.  
  
 Relacje  
 Ta sekcja definiuje każdej relacji w modelu. Źródłowy i docelowy reprezentować dwie strony relacji.  
  
 Types  
 Ta sekcja definiuje każdego typu i jego przestrzeń nazw. Właściwości domeny ma dwa typy. `DomainEnumerations` są zdefiniowane w modelu i wygenerować typy do DomainModel.cs. `ExternalTypes` odnoszą się do typów, które są zdefiniowane w innym miejscu (takie jak `String` lub `Int32`) i nie generują żadnych.  
  
 Kształty  
 Ta sekcja definiuje kształty, które opisują, jak model pojawia się w projektancie. Te kształty geometryczne są mapowane do klas w modelu w sekcji dla diagramu.  
  
 Łączniki  
 Ta sekcja definiuje wygląd elementów łączników, które pojawiają się w projektancie. Opisy te style geometrycznych są mapowane na relacji w modelu w sekcji diagramu.  
  
 XmlSerializationBehavior  
 Ta sekcja definiuje schemat serializacji i zawiera dodatkowe informacje na temat sposobu każdej klasy są zapisywane do pliku.  
  
 ExplorerBehavior  
 Ta sekcja definiuje sposób, w jaki **Eksplorator DSL** okna jest wyświetlany, gdy użytkownik edytuje modelu.  
  
 ConnectionBuilders  
 Ta sekcja definiuje konstruktora połączeń dla każdego narzędzia connector (narzędzie do tworzenia łączy między wszystkie dwóch klas, które mogą zostać połączone). W tej sekcji określa, czy można połączyć źródłowy i klasę docelową.  
  
 Diagram  
 Ta sekcja definiuje diagram, i jej używać do określania właściwości, takich jak kolor tła i Klasa główna. (Klasa główna jest klasy domeny, który jest reprezentowany przez diagram jako całość). Sekcja Diagram zawiera również elementy mapy ShapeMap i mapy ConnectorMap, określających, kształtu lub łącznik, który reprezentuje każdej klasy domeny lub relacji.  
  
 Projektant  
 Ta sekcja definiuje projektanta (Edytor), który umożliwia połączenie ze sobą **przybornika**, ustawienia sprawdzania poprawności, diagram i schematu serializacji. Sekcja projektanta definiuje również klasę głównego modelu, który zazwyczaj jest również Klasa główna diagramu.  
  
 Eksplorator  
 W tej sekcji wymieniono **Eksplorator DSL** zachowanie (zdefiniowane w sekcji elementu XmlSerializationBehavior).  
  
## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Monikery w plik DslDefinition.dsl  
 Przez cały plik DslDefinition.dsl umożliwia monikerów wprowadzić odsyłacze do określonych elementów. Na przykład każda definicja relacji zawiera podsekcja źródła i podsekcji docelowego. Każdej podsekcji zawiera moniker klasę obiektu, który może zostać powiązany z tej relacji:  
  
```  
<DomainRelationship …        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole …>  
       <RolePlayer>  
         <DomainClassMoniker Name="Library" />  
       </RolePlayer>  
     </DomainRole>  
   </Source>  
```  
  
 Zazwyczaj przestrzeń nazw elementu odwołania (w tym przykładzie `Library` klasy domeny) jest taka sama jak element odwołujący się (w tym przypadku LibraryHasMembers relacji domeny). W takich przypadkach moniker Podaj tylko nazwę klasy. W przeciwnym razie należy użyć /Namespace/Name pełnej postaci:  
  
```  
  
<DomainClassMoniker Name="/ExampleNameSpace/Library" />  
  
```  
  
 Moniker system wymaga, że elementów równorzędnych w drzewie XML mają różne nazwy. Z tego powodu błędy walidacji występują, jeśli zostanie podjęta próba zapisania definicji języka specyficznego dla domeny, który, na przykład dwóch klas o takiej samej nazwie. Zawsze należy poprawić błędy takie zduplikowana nazwa, zanim zapiszesz plik DslDefinition.dsl, dzięki czemu możesz ponownie załadować je poprawnie później.  
  
 Każdy typ ma swój własny typ monikera: DomainClassMoniker DomainRelationshipMoniker i tak dalej.  
  
## <a name="types"></a>Types  
 Sekcja: typy określa wszystkie typy, które zawiera plik DslDefinition.dsl jako typy właściwości. Te typy można podzielić na dwa rodzaje: typy zewnętrzne, np. System.String oraz typach wyliczeniowych.  
  
### <a name="external-types"></a>Typy zewnętrzne  
 Przykładowy Diagram składników zawiera zestaw standardowych typów pierwotnych, mimo że tylko niektóre z nich są używane.  
  
 Każda definicja typu zewnętrznego składa się z tylko nazwę i przestrzeń nazw, takich jak parametry i systemu:  
  
```  
<ExternalType Name="String" Namespace="System" />  
```  
  
 Pełne nazwy typów są używane zamiast słowa kluczowe równoważne kompilatora, takich jak "string".  
  
 Typy zewnętrzne nie są ograniczone do typów biblioteki standardowej.  
  
### <a name="enumerations"></a>Wyliczenia  
 Typowe specyfikacji wyliczenie podobna do poniższego przykładu:  
  
```  
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">  
  <Literals>  
    <EnumerationLiteral Name="Start" Value="1"/>  
    <EnumerationLiteral Name="Decision" Value="2"/>  
  </Literals>  
</DomainEnumeration>  
```  
  
 `IsFlags` Atrybutu formanty czy wygenerowany kod jest poprzedzony `[Flags]` atrybutu środowisko uruchomieniowe języka wspólnego (CLR), który określa, czy wartości wyliczenia można łączyć alternatywy bitowej. Jeśli ten atrybut jest ustawiony na wartość true, należy określić wartości zasilania z dwóch wartości literału.  
  
## <a name="classes"></a>Klasy  
 Większość elementów w żadnych definicji języka specyficznego dla domeny są bezpośrednio lub pośrednio wystąpień `DomainClass`. Podklasy `DomainClass` obejmują `DomainRelationship`, `Shape`, `Connector`, i `Diagram`. `Classes` Sekcji plik DslDefinition.dsl zawiera klasy domeny.  
  
 Każda klasa ma zestaw właściwości i może mieć klasy bazowej. W tym przykładzie Diagram składników `NamedElement` jest klasą abstrakcyjną, która ma `Name` właściwości, których typ to ciąg:  
  
```  
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
  
 `NamedElement` jest podstawą kilka innych klas, takich jak `Component`, który ma własne właściwości oprócz `Name` właściwość, która ono odziedziczone `NamedElement`. Węzeł podrzędny BaseClass zawiera odwołanie krótkiej nazwy. Ponieważ klasy odwołania znajduje się w tej samej przestrzeni nazw, tylko jego nazwa jest wymagana w moniker:  
  
```  
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
  
 Każda klasa domeny (w tym relacje, kształty, łączników i diagramy) może mieć tych atrybutów i węzłów podrzędnych:  
  
- **Id.** Ten atrybut jest identyfikatorem GUID. Jeśli nie zostanie określona wartość w pliku, projektanta języka specyficznego dla domeny utworzy wartość. (Na ilustracjach w tym dokumencie, ten atrybut jest zwykle pominąć, aby zaoszczędzić miejsce.)  
  
- **Nazwa i Namespace.** Te atrybuty Określ nazwę i przestrzeń nazw, klasy w wygenerowanym kodzie. Razem muszą być unikatowe w obrębie języka specyficznego dla domeny.  
  
- **InheritanceModifier.** Ten atrybut to "abstrakcyjnego", "sealed" lub Brak.  
  
- **DisplayName.** Ten atrybut jest nazwą, która jest wyświetlana w **właściwości** okna. Atrybut DisplayName może zawierać spacje i inne znaki interpunkcyjne.  
  
- **GeneratesDoubleDerived.** Jeśli ten atrybut jest ustawiony na wartość true, dwóch klas są generowane i jeden jest podklasą drugiego. Wygenerowane metody są w podstawowym, a konstruktory znajdują się w podklasy. Przez ustawienie tego atrybutu, można zastąpić dowolną metodę wygenerowanego w kodzie niestandardowym.  
  
- **HasCustomConstructor**. Jeśli ten atrybut jest ustawiony na wartość true, Konstruktor pominięcia z wygenerowanego kodu, aby napisać własną wersję.  
  
- **Atrybuty**. Ten atrybut zawiera atrybuty CLR wygenerowanej klasy.  
  
- **BaseClass**. Jeśli określono klasy bazowej, musi to być tego samego typu. Na przykład klasa domeny musi mieć innej klasy domeny jako jego podstawowy i kształt przedziału musi mieć kształtu przedziału. Jeśli klasa bazowa nie jest określona, klasy w wygenerowanym kodzie pochodzi od klasy framework standardowych. Na przykład klasy domeny jest pochodną `ModelElement`.  
  
- **Właściwości**. Ten atrybut zawiera właściwości, które są obsługiwane pod kontrolą transakcji i zachowywane po zapisaniu modelu.  
  
- **ElementMergeDirectives**. Każda dyrektywa scalania Określa, jak inne wystąpienie innej klasy jest dodawany do wystąpienia klasy nadrzędnej. Więcej szczegółów na temat dyrektywy scalania elementów można znaleźć w dalszej części tego tematu.  
  
- Klasa C# jest generowane dla każdej klasy domeny, który znajduje się w `Classes` sekcji. Klas języka C# są generowane w Dsl\GeneratedCode\DomainClasses.cs.  
  
### <a name="properties"></a>Właściwości  
 Każda właściwość domeny ma nazwy i typu. Nazwa musi być unikatowa w obrębie klasy domeny i jego przechodnie klasy podstawowe.  
  
 Typ musi odwoływać się do jednej z tych na liście `Types` sekcji. Ogólnie rzecz biorąc moniker musi zawierać przestrzeń nazw.  
  
```  
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
  <Type>  
    <ExternalTypeMoniker Name="/System/String" />  
  </Type>  
</DomainProperty>  
```  
  
 Każda właściwość domeny może mieć również te atrybuty:  
  
- **IsBrowsable**. Ten atrybut określa, czy właściwość pojawia się w **właściwości** okna, gdy użytkownik kliknie obiekt klasy nadrzędnej.  
  
- **IsUIReadOnly**. Ten atrybut określa, czy użytkownik może zmienić właściwość **właściwości** okna lub za pośrednictwem dekoratora, w której jest prezentowane właściwości.  
  
- **Rodzaj**. Ten atrybut zostanie ustawiony na normalny, obliczona lub wartości CustomStorage. Jeśli ten atrybut jest ustawiony na obliczeniowe, musi podać kod niestandardowy, który określa wartość, a właściwość będzie tylko do odczytu. Jeśli ten atrybut jest ustawiony na wartości CustomStorage, musisz podać kod, który pobiera i ustawia wartości.  
  
- **IsElementName**. Jeśli ten atrybut jest ustawiony na wartość true, wartość jest automatycznie ustawiona na unikatową wartość po utworzeniu wystąpienia klasy nadrzędnej. Ten atrybut można ustawić wartość true dla tylko jednej właściwości w każdej klasie i musi mieć typ ciągu. W tym przykładzie Diagram składników `Name` właściwość `NamedElement` ma `IsElementName` ma wartość true. Zawsze, gdy użytkownik tworzy `Component` — element (który dziedziczy z `NamedElement`), jest inicjowana automatycznie na wartość podobną "Component6."  
  
- `DefaultValue`. Jeśli ten atrybut został określony, wartość określona zostanie przypisany do tego atrybutu dla nowych wystąpień tej klasy. Jeśli `IsElementName` jest ustawiony atrybut DefaultValue Określa początkowy część nowego ciągu znaków.  
  
- **Kategoria** jest nagłówkiem, w którym właściwość pojawi się w **właściwości** okna.  
  
## <a name="relationships"></a>Relacje  
 `Relationships` Sekcji przedstawiono wszystkie relacje w języku specyficznym dla domeny. Każdy `Domain Relationship` jest binarny i bezpośredniego łączenia elementów członkowskich klasy źródłowej do elementów członkowskich klasy docelowej. Klas źródłowych i docelowych zwykle są klasami domeny, ale relacje z innymi relacje są również dozwolone.  
  
 Na przykład relacji połączenia łączy elementów członkowskich klasy elementu OutPort składowe klasy elementu InPort. Każde wystąpienie łącza relacji łączy z wystąpienia elementu OutPort do wystąpienia elementu InPort. Ponieważ jest w relacji wiele wiele każdego elementu OutPort może mieć wiele łączy połączenia ze źródłami na nim i każdego wystąpienia elementu InPort może mieć wiele łączy połączenia, które go wykorzystać.  
  
### <a name="source-and-target-roles"></a>Role źródłowe i docelowe  
 Każda relacja zawiera role źródłowe i docelowe, które mają następujące atrybuty:  
  
- `RolePlayer` Atrybut odwołuje się do klasy domeny połączonych wystąpień: Elementu outPort źródła InPort dla obiektu docelowego.  
  
- `Multiplicity` Atrybut ma czterech możliwych wartości (wartości ZeroMany, wartość ZeroOne, co i OneMany). Ten atrybut odwołuje się do liczby łączy tę relację, która może być skojarzony z jednego obiektu pełniącego rolę.  
  
- `PropertyName` Atrybut określa nazwę, która jest używana w fabularne klasy dostępu do obiektów na drugim końcu. Ta nazwa jest używana w szablonie lub niestandardowego kodu na przechodzenie przez relację. Na przykład `PropertyName` ma ustawioną wartość atrybutu roli źródłowej `Targets`. W związku z tym poniższy kod będzie działać:  
  
    ```  
    OutPort op = …; foreach (InPort ip in op.Targets) ...  
    ```  
  
     Zgodnie z Konwencją plural, jeśli liczebność jest wartości ZeroMany ani OneMany są nazwy właściwości.  
  
     Liczebność roli odwołuje się do liczby rolę odwrotną mogą być skojarzone z każdym wystąpieniem tej roli. Na przykład w relacji elementu ComponentHasPorts, docelowa rola ma `RolePlayer` atrybut ustawiony na Port, `PropertyName` atrybut ustawiony na składnik, a `Multiplicity` atrybut ustawiony na wartość ZeroOne. Dlatego jest odpowiedni kod, aby użyć tej roli:  
  
    ```  
    ComponentPort p = …; Component c = p.Component; if (c != null) …  
    ```  
  
- Rola `Name` jest nazwa, która jest używana w ramach klasy relacji do odwoływania się do końca tego łącza. Według Konwencji nazwy roli jest zawsze pojedynczej, ponieważ każde połączenie ma tylko jedno wystąpienie na każdym końcu. Poniższy kod będzie działać:  
  
    ```  
    Connection connectionLink = …; OutPort op = connectionLink.Source;  
    ```  
  
- Domyślnie `IsPropertyGenerator` atrybut jest ustawiony na wartość true. Jeśli ma wartość false, nie ma właściwości zostanie utworzony dla klasy obiektu pełniącego rolę. (W takim przypadku `op.Targets`, na przykład, nie będzie działać). Jednak nadal możliwe jest przechodzenie relacji lub uzyskania dostępu do łączy się, jeśli kod niestandardowy używa relacji jawnie przy użyciu niestandardowego kodu:  
  
    ```  
    OutPort op = …; foreach (InPort ip in Connection.GetTargets(op)) …  
    foreach (Connection link in Connection.GetLinksToTargets(op)) …  
    ```  
  
### <a name="relationship-attributes"></a>Atrybuty relacji  
 Oprócz atrybutów i węzłów podrzędnych, które są dostępne dla wszystkich klas każda relacja ma następujące atrybuty:  
  
- **IsEmbedding**. Ten atrybut logiczny określa, czy relacja jest częścią drzewa osadzania. Każdy model musi tworzą drzewa za pomocą jego relacji osadzania. Każda klasa domeny musi być celem co najmniej jednej relacji osadzania, w związku z tym, chyba że jest to główny modelu.  
  
- **AllowsDuplicates**. Ta logiczna atrybut, który ma wartość false, domyślnie, dotyczy tylko relacje, które mają liczebność "many" w pliku źródłowym i docelowym. Określa, czy użytkownicy języka mogą się łączyć jedna para elementów źródłowych i docelowych przez więcej niż jednego połączenia w tej samej relacji.  
  
## <a name="designer-and-toolbox-tabs"></a>Projektant i karty przybornika  
 Główna część **projektanta** sekcja plik DslDefinition.dsl **ToolboxTab** elementów. Projektant co może mieć kilka z tych elementów, z których każdy reprezentuje kapusty sekcji w wygenerowanym projektancie **przybornika**. Każdy **ToolboxTab** element może zawierać jeden lub więcej **narzędzie ElementTool** elementów **elementu ConnectionTool** elementy i / lub.  
  
 Element narzędzia można utworzyć wystąpienia klasy określonej domeny. Gdy użytkownik przeciągnie narzędziem elementu na diagram, wynik jest określany przez dyrektywy scalania elementów zgodnie z opisem w sekcji o dyrektywy scalania elementów w dalszej części tego tematu.  
  
 Każde narzędzie połączenia można wywołać konstruktora określonego połączenia. Jednego konstruktora połączeń można utworzyć więcej niż jeden typ relacji, w zależności od tego, gdy użytkownik kliknie przycisk myszy, zgodnie z opisem w sekcji o konstruktory połączeń.  
  
 Ani typ narzędzia bezpośrednio konstrukcje kształtów i łączników. Każdy tworzy wystąpienie klasy domeny lub relacji domeny; mapowania kształtów i łączników następnie określają sposób wyświetlania tej klasy domeny lub relacji domeny.  
  
## <a name="paths"></a>Ścieżki  
 Ścieżki domeny są wyświetlane w kilku lokalizacjach w plik DslDefinition.dsl. Te ścieżki Określ szereg linki z jednego elementu w modelu (oznacza to, że wystąpienie języka specyficznego dla domeny) do innego. Składnia ścieżki jest prosty, lecz pełne.  
  
 Ścieżki zostaną wyświetlone w plik DslDefinition.dsl w `<DomainPath>…</DomainPath>` tagów. Mimo że ścieżek nawigować przez kilka łączy, większość przykładów w praktyce przechodzić tylko jedno połączenie.  
  
 Ścieżka składa się z sekwencji segmentów. Każdy z segmentów jest przeskoku od obiektu do łącza lub link do obiektu. W związku z tym przeskoków alternatywne zwykle długie ścieżki. Pierwszym przeskokiem jest z obiektu do łącza, drugim przeskokiem jest obiektem na drugim końcu łącza, trzeci przeskoku jest następny link i tak dalej. Sporadyczne wyjątkiem od tej sekwencji jest, gdzie relacji jest sam źródłowych lub docelowych innej relacji.  
  
 Każdy z segmentów rozpoczyna się od nazwy relacji. W przeskoku łącze obiektu relacji poprzedza kropkę i nazwę właściwości: "`Relationship . Property`". W przeskoku obiekt łącza relacji poprzedza znak wykrzyknika i nazwa roli: "`Relationship ! Role`".  
  
 Przykładowy Diagram składników zawiera ścieżkę w ParentElementPath z mapy ShapeMap InPort. Ta ścieżka rozpoczyna się w następujący sposób:  
  
```  
    ComponentHasPorts.Component  
```  
  
 W tym przykładzie InPort jest podklasą elementu ComponentPort oraz ma ustanowioną relację elementu ComponentHasPorts. Właściwość nosi nazwę składnika.  
  
 Podczas pisania C# dla tego modelu, możesz przejść przez łącze w jednym kroku, za pomocą właściwości, która generuje relacji na każdą z klas, które odnosi się:  
  
```  
     InPort port; ...  Component c = port.Component;  
```  
  
 Jednak należy wykonać obie przeskoków jawnie przy użyciu składni ścieżki. Ze względu na to wymaganie jest dostępny link pośredni łatwiejsze. Poniższy kod wykonuje przeskoku z łącza do składnika:  
  
```  
    ComponentHasPorts.Component / ! Component  
```  
  
 (Pomiń Nazwa relacji, w której jest taka sama, jak poprzedniego segmentu).  
  
## <a name="element-merge-directives"></a>Dyrektywy scalania elementów  
 Gdy użytkownik języka element zostanie przeciągnięty z **przybornika** na diagram, wystąpienia klasy tego narzędzia jest tworzony. Łącza są również między tego wystąpienia i istniejące elementy modelu. Niektóre elementy, takie jak składniki lub komentarze są tworzone podczas przeciągania przez użytkownika języka ich z **przybornika** na pustą część diagramu. Inne elementy są tworzone, gdy użytkownik języka przeciągnie je do innych elementów hosta. Na przykład elementu OutPort lub InPort jest tworzony podczas języka przeciągania go przez użytkownika na składnik.  
  
 Potencjalne klasy obsługującej, takich jak składnik będzie akceptować nowego elementu, tylko wtedy, gdy klasy obsługującej dyrektywa scalania dla klasy nowego elementu. Na przykład węzeł DomainClass o nazwie = "Component" zawiera:  
  
```  
<DomainClass Name="Component" …> …  
    <ElementMergeDirective>  
      <Index>  
        <DomainClassMoniker Name="ComponentPort" />  
      </Index>  
      <LinkCreationPaths>  
        <DomainPath>ComponentHasPorts.Ports</DomainPath>  
      </LinkCreationPaths>  
    </ElementMergeDirective> …  
```  
  
 Klasa elementu, który może zostać zaakceptowany odwołuje się do krótkiej nazwy klasy, która znajduje się w węźle indeksu. W tym przypadku elementu ComponentPort jest abstrakcyjna klasa bazowa InPort i elementu OutPort. W związku z tym jedną z tych elementów mogą być akceptowane.  
  
 ComponentModel, Klasa główna języka, ma dyrektywy scalania elementów dla składników i komentarze. Użytkownik języka można przeciągać elementy dla tych klas bezpośrednio na diagram, ponieważ puste części diagramu reprezentuje klasę głównego. Jednak ComponentModel nie ma żadnych dyrektywa scalania dla elementu ComponentPort. W związku z tym użytkownik języka nie można przeciągnąć InPorts lub OutPorts bezpośrednio na diagramie.  
  
 Dyrektywa scalania Określa, jakie łącza lub łącza są tworzone tak, aby nowy element można zintegrować lub scalić istniejący model. Dla elementu ComponentPort tworzone jest wystąpienie elementu ComponentHasPorts. DomainPath identyfikuje zarówno relacji, jak i właściwość klasy nadrzędnej, portów, do których zostanie dodany nowy element.  
  
 Można utworzyć więcej niż jednego połączenia w dyrektywie scalania elementów, tym więcej niż jednej ścieżki tworzenia linku. Jedna ze ścieżek muszą być osadzone.  
  
 W ścieżce tworzenia linku, można użyć więcej niż jednego segmentu. W tym przypadku ostatni element definiuje, jakie łącza muszą być tworzone. Wcześniej segmentów przejdź z klasy nadrzędnej obiektu, z którego można utworzyć nowy link.  
  
 Na przykład można dodać tej dyrektywy scalenia elementów do klasy składników:  
  
```  
<DomainClass Name="Component" …> …  
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
  
 Użytkownicy języka można przeciągnąć składnik komentarz i mają nowy komentarz, które są tworzone automatycznie za pomocą łącza do składnika.  
  
 Pierwszy ścieżki tworzenia linku powoduje przejście z `Component` do `ComponentModel` , a następnie tworzy wystąpienie relacji osadzania `ComponentModelHasComments`. Drugi ścieżki tworzenia linku tworzy łącze relacji odwołania CommentsReferenceComponents z hosta składnika nowy komentarz. Wszystkie ścieżki tworzenia linku musi rozpoczynać się od klasy obsługującej i musi kończyć łącza tego kroków prowadzących do nowo skonkretyzowaną klasę.  
  
## <a name="xmlclassdata"></a>XmlClassData  
 Każda klasa domeny (w tym relacji i innych podtypów) może mieć dodatkowe informacje zawarte w `XmlClassData` węzła, który pojawia się w obszarze `XmlSerializationBehavior` sekcji plik DslDefinition.dsl. Te informacje dotyczy w szczególności, jak wystąpienia klasy są przechowywane w postaci serializowanej, gdy model jest zapisywany do pliku.  
  
 Większość wygenerowany kod, który `XmlSerializationBehavior` trwa wpływa `Dsl\GeneratedCode\Serializer.cs`.  
  
 Każdy `XmlClassData` węzła zawiera następujące węzły podrzędne i atrybuty:  
  
- Węzeł monikera, która odwołuje się do klasy, do której stosują się dane.  
  
- **XmlPropertyData** dla każdej właściwości, która jest zdefiniowana w klasie.  
  
- **Element XmlRelationshipData** dla każdej relacji, który jest rozwijani w klasie. (Relacje również mieć własne węzłów XmlClassData).  
  
- **Element TypeName** atrybut ciągu, który określa nazwę klasy pomocnika serializacji w wygenerowanym kodzie.  
  
- **ElementName** ciąg, który określa tagu XML serializacji wystąpienia tej klasy. Zgodnie z Konwencją ElementName jest zwykle taka sama jak nazwa klasy z wyjątkiem pierwszej litery jest pisana małymi literami. Na przykład plik przykładowy model rozpoczyna się następująco:  
  
    ```  
    <componentModel …  
    ```  
  
- **MonikerElementName** w plikach modelu serializowane przez użytkownika. Ten atrybut wprowadza moniker elementu, który odwołuje się do tej klasy.  
  
- **Elementu MonikerAttributeName**, który identyfikuje nazwę atrybutu XML w ramach krótka. W tym fragmencie pliku Zserializowany użytkownika Autor języka specyficznego dla domeny zdefiniowane **MonikerElementName** jako "inPortMoniker" i **elementu MonikerAttributeName** jako "path":  
  
    ```  
    <inPortMoniker path="//Component2/InPort1" />  
    ```  
  
### <a name="connectionbuilders"></a>ConnectionBuilders  
 Konstruktor połączeń jest zdefiniowana dla każdego narzędzia połączenia. Każdy konstruktora połączeń składa się z co najmniej jeden element LinkConnectDirective, z których każdy zawiera jeden lub więcej elementów SourceDirective i jeden lub więcej elementów TargetDirective. Po kliknięciu przycisku narzędzia połączenia, użytkownik może uruchomić połączenia z dowolnym kształcie mapowany do elementu modelu, który pojawia się na liście elementów SourceDirective. Następnie można zakończyć połączenia dla kształtu, który jest mapowany na element, który pojawia się na liście elementów TargetDirective. Klasy relacji wystąpienia zależy od elementu LinkConnectDirective wyznaczony, gdy połączenie zostało uruchomione.  
  
### <a name="xmlpropertydata"></a>XmlPropertyData  
 A **DomainPropertyMoniker** atrybut określa właściwość, do którego odwołuje się dane. Ten atrybut musi być właściwością klasy otaczającej danych klas.  
  
 **XmlName** atrybutu daje odpowiedniej nazwy atrybutu, który powinien być widoczny w pliku XML. Umownie ten ciąg jest taka sama jak nazwa właściwości z wyjątkiem pierwszej litery jest pisana małymi literami.  
  
 Domyślnie **reprezentacji** atrybut jest ustawiony na wartość Attribute. Jeśli **reprezentacji** jest ustawiona na Element podrzędny jest tworzony węzeł w pliku XML. Jeśli **reprezentacji** jest ustawić wartość Ignore, właściwość nie jest serializowana.  
  
 **IsMonikerKey** i **IsMonikerQualifier** atrybuty nadać właściwości roli do identyfikowania wystąpienia klasy nadrzędnej. Możesz ustawić **IsMonikerKey** na wartość true dla jednej właściwości, która jest zdefiniowana w lub dziedziczone przez klasy. Ten atrybut identyfikuje poszczególne wystąpienia klasy nadrzędnej. Właściwość, której możesz ustawić `IsMonikerKey` jest zazwyczaj nazwę lub inny identyfikator klucza. Na przykład `Name` właściwość ciągu jest kluczem monikera NamedElement i jej klasy pochodne. Gdy użytkownik zapisuje model do pliku, ten atrybut musi zawierać unikatowe wartości dla każdego wystąpienia wśród elementów równorzędnych w drzewie relacji osadzania.  
  
 W pliku modelu serializowane pełną moniker elementu jest ścieżka z katalogu głównego modelu niżej na drzewie osadzania relacji cytowanie kluczem monikera w każdym punkcie. Na przykład InPorts są osadzone w ramach składników, które z kolei są osadzone w głównym modelu. Nieprawidłowy moniker jest w związku z tym:  
  
```  
<inPortMoniker name="//Component2/InPort1" />  
```  
  
 Możesz ustawić **IsMonikerQualifier** atrybutu dla właściwości ciągu i podaj dodatkowe sposobem konstruowania pełną nazwę elementu. Na przykład w plik DslDefinition.dsl **Namespace** jest kwalifikatorem monikera.  
  
### <a name="xmlrelationshipdata"></a>XmlRelationshipData  
 W pliku modelu serializowane łącza (relacji osadzania i odwołania) są reprezentowane przez węzły podrzędne końca źródło relacji. Aby osadzić relacje, węzeł podrzędny zawiera poddrzewo. W przypadku relacji odwołania węzeł podrzędny zawiera moniker elementu, który odwołuje się do innej części drzewa.  
  
 **XmlRelationshipData** atrybutu w **XmlClassData** atrybut definiuje dokładnie, jak węzły podrzędne są zagnieżdżone w obrębie elementu źródłowego. Każda relacja, który jest źródłem dla klasy domeny ma jeden **XmlRelationshipData** atrybutu.  
  
 **DomainRelationshipMoniker** atrybut identyfikuje w jednej z relacji źródło w klasie.  
  
 **RoleElementName** atrybutu daje nazwa tagu XML, który otacza węzeł podrzędny w danych serializacji.  
  
 Na przykład plik DslDefinition.dsl zawiera:  
  
```  
<XmlClassData ElementName="component" …>  
  <DomainClassMoniker Name="Component" />  
  <ElementData>  
    <XmlRelationshipData RoleElementName="ports">  
      <DomainRelationshipMoniker Name="ComponentHasPorts" />  
    </XmlRelationshipData>  
```  
  
 W związku z tym Zserializowany plik zawiera:  
  
```  
<component name="Component1"> <!-- parent ->  
   <ports> <!-- role ->  
     <outPort name="OutPort1"> <!-- child element ->  
       …  
     </outPort>  
   </ports> …  
```  
  
 Jeśli **atrybutu UseFullForm** atrybut jest ustawiony na wartość true, dodatkową warstwę zagnieżdżenia został wprowadzony. Ta warstwa reprezentuje samą relację. Ten atrybut musi być równa true, jeśli relacja ma właściwości.  
  
```  
<XmlClassData ElementName="outPort">  
   <DomainClassMoniker Name="OutPort" />  
   <ElementData>  
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">  
       <DomainRelationshipMoniker Name="Connection" />  
     </XmlRelationshipData>  
   </ElementData>  
 </XmlClassData>  
```  
  
 Zserializowany plik zawiera:  
  
```  
<outPort name="OutPort1">  <!-- Parent ->  
   <targets>  <!-- role ->  
     <connection sourceRoleName="X">  <!-- relationship link ->  
         <inPortMoniker name="//Component2/InPort1" /> <!-- child ->  
     </connection>  
    </targets>  
  </outPort>  
```  
  
 (Relacja połączenie ma swój własny danych klasy XML, co zapewnia jego nazw elementów i atrybutów).  
  
 Jeśli **OmitElement** atrybut jest ustawiony na wartość true, relacja nazwy roli zostanie pominięty, który wyświetla trzyliterowy skrót pliku serializowane i jest jednoznaczna, jeśli dwie klasy mieć nie więcej niż jedną relację. Na przykład:  
  
```  
<component name="Component3">  
  <!-- only one relationship could get here: ->  
  <outPort name="OutPort1">    
     <targets> …  
```  
  
### <a name="serialization-of-a-domain-specific-language-definition"></a>Serializacja definicji języka specyficznego dla domeny  
 Plik DslDefinition.dsl jest sam to Zserializowany plik i jest zgodny z definicji języka specyficznego dla domeny. Poniżej przedstawiono kilka przykładów definicji serializacji XML:  
  
- **Język DSL** jest węzeł klasy RootClass i klasa diagramu. Klasa DomainClass, relacji DomainRelationship i inne elementy są osadzone w obszarze `Dsl`.  
  
- **Klasy** jest **RoleElementName** relacji między języka specyficznego dla domeny i DomainClass.  
  
```  
<Dsl Name="CmptDsl5" …>  
  <Classes>  
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" …  
```  
  
- **Elementu XmlSerializationBehavior** atrybutu jest osadzony w obszarze `Dsl` atrybutu, ale **OmitElement** atrybut został ustawiony w relacji osadzania. W związku z tym, bez `RoleElementName` uczestniczyło atrybutu. Z drugiej strony **danych klas** atrybut jest `RoleElementName` atrybut relacja osadzania między **elementu XmlSerializationBehavior** atrybutu i **XmlClassData** atrybutu.  
  
```  
<Dsl Name="CmptDsl5" …> …  
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >  
    <ClassData>  
      <XmlClassData …>…</XmlClassData>  
      <XmlClassData …>…</XmlClassData>  
```  
  
- ConnectorHasDecorators jest relacja osadzania między `Connector` i `Decorator`. `UseFullForm` zostało ustawione tak, aby nazwa relacji pojawia się z listą właściwości dla każdego linku z obiektu łącznika. Jednak `OmitElement` ma również ustawienie, aby nie `RoleElementName` zawiera wiele łączy, które są osadzone wewnątrz `Connector`:  
  
```  
<Connector Name="AssociationLink" …>  
  <ConnectorHasDecorators Position="TargetTop" …>  
    <TextDecorator Name="TargetRoleName"   />  
  </ConnectorHasDecorators>  
  <ConnectorHasDecorators Position="SourceTop" …>  
    <TextDecorator Name="SourceRoleName"   />  
  </ConnectorHasDecorators>  
</Connector>  
```  
  
## <a name="shapes-and-connectors"></a>Kształty i łączniki  
 Definicje kształtów i łączników atrybutów i węzłów podrzędnych dziedziczyć klasy domeny, oprócz następujących czynności:  
  
- `Color` i `Line``Style` atrybutów.  
  
- **ExposesFillColorAsProperty** i kilku atrybutów podobne. Te atrybuty typu Boolean wprowadź odpowiednią zmienną właściwości przez użytkownika. Ogólnie rzecz biorąc, gdy użytkownik języka kliknie kształt na diagramie, właściwości wyświetlanych w **właściwości** okna są zależne od wystąpienia klasy domeny, na który jest mapowany kształt. Jeśli `ExposesFillColorAsProperty` ma wartość true, właściwość kształt pojawia się również.  
  
- **ShapeHasDecorators**. Wystąpienie tego atrybutu jest wykonywana dla każdego typu text, ikony lub dekoratora Rozwiń/Zwiń. (W plik DslDefinition.dsl `ShapeHasDecorators` relację z `UseFullForm` ma wartość true.)  
  
## <a name="shape-maps"></a>Mapowania kształtów  
 Mapowania kształtów określają, jak wystąpień klasy danej domeny są wyświetlane na ekranie, reprezentowane przez kształty. Mapowań zarówno kształtów i łączników są wyświetlane w obszarze `Diagram` sekcji plik DslDefinition.dsl.  
  
 Jak w poniższym przykładzie `ShapeMap` elementów ma co najmniej, moniker klasy domeny, moniker kształtu, a `ParentElementPath` elementu:  
  
```  
<ShapeMap>  
  <DomainClassMoniker Name="InPort" />  
  <ParentElementPath>  
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>  
  </ParentElementPath>  
  <PortMoniker Name="InPortShape" />  
</ShapeMap>  
```  
  
 Podstawową funkcją `ParentElementPath` element jest tak, aby w tej samej klasie obiekty mogą być wyświetlane jako innego kształtu w różnych kontekstach. Na przykład jeśli `InPort` można również osadzić w komentarzu, `InPort` może się pojawić jako innego kształtu, w tym celu.  
  
 Po drugie ścieżka Określa, jak kształt odnosi się do elementu nadrzędnego. Nie osadzania struktura jest zdefiniowana między kształtami na plik DslDefinition.dsl. Musi wywnioskować struktury z mapowań kształtów. Kształt nadrzędny jest kształtu, który jest mapowany na element domeny, który identyfikuje ścieżka elementu nadrzędnego. W tym przypadku ścieżki identyfikuje składnika, do którego `InPort` należy. W innym mapowanie kształtów klasa składnika jest zamapowana na ComponentShape. W związku z tym, nowe `InPort` kształt następuje element podrzędny kształt z jego składników `ComponentShape`.  
  
 Jeśli zamiast tego dołączonego elementu InPort kształtu na diagramie, ścieżka elementu nadrzędnego musiałby wykonać kolejny krok w celu modelu składnika, który jest mapowany do diagramu:  
  
```  
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel  
```  
  
 Korzeń modelu ma mapowanie kształtów. Zamiast tego główny odwołuje się bezpośrednio z diagramu, który ma `Class` elementu:  
  
```  
<Diagram Name="ComponentDiagram" >  
    <Class>  
      <DomainClassMoniker Name="ComponentModel" />  
    </Class>…  
```  
  
### <a name="decorator-maps"></a>Mapowania dekoratorów  
 Mapowanie dekoratora kojarzy właściwości w klasie mapowanego do dekoratora dla kształtu. Jeśli właściwość jest typu wyliczeniowego lub wartość logiczna, wartość można określić, czy dekorator jest widoczny. Jeśli dekorator jest dekoratora tekstu, wartości właściwości mogą być wyświetlane, a użytkownik może edytować go.  
  
### <a name="compartment-shape-maps"></a>Mapowania kształtów przedziału  
 Mapowania kształtów przedziału są podtypy mapowania kształtów.  
  
## <a name="connector-maps"></a>Mapowania łączników  
 Mapowanie łącznika minimalny odwołuje się łącznikiem i relacją:  
  
```  
<ConnectorMap>  
  <ConnectorMoniker Name="CommentLink" />  
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />  
</ConnectorMap>  
```  
  
 Mapowania łączników może również zawierać mapowania dekoratorów.  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Jak zdefiniować języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)   
 [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)

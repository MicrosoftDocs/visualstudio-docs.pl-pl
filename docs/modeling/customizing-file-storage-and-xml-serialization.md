---
title: Dostosowywanie przechowywania plików i serializacji XML
description: Dowiedz się więcej o pliku XML utworzonym lub zaktualizowanym podczas zapisywania wystąpienia lub modelu języka specyficznego dla domeny (DSL) w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b3026010e37108ca1b19096d48a3c8d88ab6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389374"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Dostosowywanie przechowywania plików i serializacji XML

Gdy użytkownik zapisuje wystąpienie lub *model* języka specyficznego dla domeny (DSL) w języku Visual Studio, tworzony lub aktualizowany jest plik XML. Plik można ponownie załadować, aby ponownie utworzyć model w magazynie.

Schemat serializacji można dostosować, dostosowując ustawienia w obszarze **Zachowanie serializacji XML w** eksploratorze DSL. Istnieje węzeł w obszarze **Zachowanie serializacji Xml** dla każdej klasy domeny, właściwości i relacji. Relacje znajdują się w ich klasach źródłowych. Istnieją również węzły odpowiadające klasom kształtów, łączników i diagramów.

Możesz również napisać kod programu w celu bardziej zaawansowanego dostosowywania.

> [!NOTE]
> Jeśli chcesz zapisać model w określonym formacie, ale nie musisz ponownie ładować go z tego formularza, rozważ użycie szablonów tekstowych do generowania danych wyjściowych z modelu, a nie niestandardowego schematu serializacji. Aby uzyskać więcej informacji, zobacz [Generowanie kodu z Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Pliki modelu i diagramu

Każdy model jest zwykle zapisywany w dwóch plikach:

- Plik modelu ma nazwę taką jak **Model1.mydsl.** Przechowuje elementy modelu i relacje oraz ich właściwości. Rozszerzenie pliku, takie **jak .mydsl,** jest określane przez właściwość **FileExtension** węzła **Edytor** w definicji DSL.

- Plik diagramu ma nazwę taką jak **Model1.mydsl.diagram**. Przechowuje kształty, łączniki i ich położenia, kolory, grubość linii i inne szczegóły wyglądu diagramu. Jeśli użytkownik usunie plik **diagramu,** podstawowe informacje w modelu nie utracą. Utracony jest tylko układ diagramu. Po otwarciu pliku modelu zostanie utworzony domyślny zestaw kształtów i łączników.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Aby zmienić rozszerzenie pliku DSL

1. Otwórz definicję DSL. W Eksploratorze DSL kliknij węzeł Edytor.

2. W okno Właściwości edytuj właściwość **FileExtension.** Nie dołączaj początkowego "." rozszerzenia nazwy pliku.

3. W Eksplorator rozwiązań zmień nazwę dwóch plików szablonów elementów w pliku **DslPackage\ProjectItemTemplates.** Te pliki mają nazwy zgodne z tym formatem:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Domyślny schemat serializacji

Aby utworzyć przykład dla tego tematu, została użyta następująca definicja DSL.

![Diagram definicji DSL &#45; modelu drzewa rodziny](../modeling/media/familyt_person.png)

Ten DSL został użyty do utworzenia modelu, który ma następujący wygląd na ekranie.

![Diagram drzewa rodziny, przybornik i eksplorator](../modeling/media/familyt_instance.png)

Ten model został zapisany, a następnie ponownie otwarty w edytorze tekstów XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

Zwróć uwagę na następujące kwestie dotyczące serializowanego modelu:

- Każdy węzeł XML ma nazwę, która jest taka sama jak nazwa klasy domeny, z tą różnicą, że początkowa litera jest mała. Na przykład `familyTreeModel` i `person`.

- Właściwości domeny, takie jak Name i BirthYear, są serializowane jako atrybuty w węzłach XML. Ponownie początkowy znak nazwy właściwości jest konwertowany na małe litery.

- Każda relacja jest serializowana jako węzeł XML zagnieżdżony wewnątrz źródłowego końca relacji. Węzeł ma taką samą nazwę jak właściwość roli źródłowej, ale z początkowym znakiem małe liter.

     Na przykład w definicji DSL rola o nazwie **People** pochodzi z klasy **FamilyTree.**  W pliku XML jest on reprezentowany przez węzeł o nazwie `people` zagnieżdżony wewnątrz `familyTreeModel` węzła.

- Docelowy koniec każdej relacji osadzania jest serializowany jako węzeł zagnieżdżony w relacji. Na przykład węzeł `people` zawiera kilka `person` węzłów.

- Docelowy koniec każdej relacji odwołania jest serializowany jako *moniker*, który koduje odwołanie do elementu docelowego.

     Na przykład w `person` węźle może być `children` relacja. Ten węzeł zawiera monikery, takie jak:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Opis monikerów

Monikery są używane do reprezentowania odwołań krzyżowych między różnymi częściami plików modelu i diagramu. Są one również używane w `.diagram` pliku do odwoływać się do węzłów w pliku modelu. Istnieją dwie formy monikera:

- *Identyfikatory monikerów* cytują identyfikator GUID elementu docelowego. Na przykład:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *Monikery kluczy kwalifikowanych* identyfikują element docelowy według wartości wyznaczonej właściwości domeny o nazwie klucz moniker. Monikera elementu docelowego jest poprzedzona monikerem jego elementu nadrzędnego w drzewie osadzania relacji.

     Poniższe przykłady są brane z DSL, w którym istnieje klasa domeny o nazwie Dsl, która ma relację osadzania z klasą domeny o nazwie Song:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Monikery klucza kwalifikowanego będą używane, jeśli klasa docelowa ma właściwość domeny, dla której opcja Jest **kluczem moniker** jest ustawiona na wartość w zachowaniu `true` **serializacji XML.** W tym przykładzie ta opcja jest ustawiana dla właściwości domeny o nazwach "Title" w klasach domeny "Do" i "Song".

Monikery kwalifikowanych kluczy są łatwiejsze do odczytania niż monikery identyfikatorów. Jeśli zamierzasz, aby kod XML plików modelu był odczytywany przez ludzi, rozważ użycie kwalifikowanych monikerów kluczy. Użytkownik może jednak ustawić więcej niż jeden element tak, aby miał ten sam klucz moniker. Zduplikowane klucze mogą spowodować, że plik nie zostanie poprawnie ponownie załadowany. W związku z tym w przypadku definiowania klasy domeny, która jest przywołyowana przy użyciu monikerów klucza kwalifikowanego, należy rozważyć sposoby uniemożliwienia użytkownikowi zapisania pliku, który zawiera zduplikowane monikery.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Aby ustawić klasę domeny, która ma być przywołyowana przez monikery identyfikatorów

1. Upewnij się, **że właściwość Is Moniker Key** jest dla każdej właściwości domeny w klasie i jej `false` klasach bazowych.

    1. W eksploratorze DSL rozwiń **element Xml Serialization Behavior\Class Data \\ \<the domain class> \Element Data**.

    2. Sprawdź, **czy element Is Moniker Key (Klucz moniker)** jest `false` wartością dla każdej właściwości domeny.

    3. Jeśli klasa domeny ma klasę bazową, powtórz procedurę w tej klasie.

2. Ustaw **identyfikator serializacji**  =  `true` dla klasy domeny.

     Tę właściwość można znaleźć w obszarze **Zachowanie serializacji XML**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Aby ustawić klasę domeny, która ma być przywołyowana przez monikery kwalifikowanego klucza

- Ustaw **wartość Jest kluczem moniker** dla właściwości domeny istniejącej klasy domeny. Typem właściwości musi być `string` .

    1. W Eksploratorze DSL **rozwiń pozycję Xml Serialization Behavior\Class Data \\ \<the domain class> \Element Data**, a następnie wybierz właściwość domeny.

    2. W okno Właściwości dla ustawienia **Is Moniker Key (Jest kluczem moniker)** ustaw wartość `true` .

- \- lub —

     Utwórz nową klasę domeny za pomocą **narzędzia klasy nazwanej** domeny.

     To narzędzie tworzy nową klasę, która ma właściwość domeny o nazwie Nazwa. Właściwości **Is Element Name** i Is **Moniker Key** tej właściwości domeny są inicjowanie do elementu `true` .

- \- lub —

     Utwórz relację dziedziczenia z klasy domeny do innej klasy, która ma właściwość klucza moniker.

### <a name="avoid-duplicate-monikers"></a>Unikaj duplikowania monikerów

Jeśli używasz monikerów klucza kwalifikowanego, możliwe, że dwa elementy w modelu użytkownika mogą mieć taką samą wartość we właściwości klucza. Jeśli na przykład DSL ma klasę Person, która ma właściwość Name, użytkownik może ustawić nazwy dwóch elementów na takie same. Mimo że model można zapisać w pliku, nie zostałby poprawnie ponownie załadowany.

Istnieje kilka metod, które pomagają uniknąć tej sytuacji:

- Ustaw **wartość to nazwa elementu** dla właściwości domeny  =  `true` klucza. Wybierz właściwość domeny na diagramie definicji DSL, a następnie ustaw wartość w okno Właściwości.

     Gdy użytkownik tworzy nowe wystąpienie klasy, ta wartość powoduje automatyczne przypisanie innej wartości właściwości domeny. Domyślne zachowanie powoduje dodanie liczby na końcu nazwy klasy. Nie uniemożliwia to użytkownikowi zmiany nazwy na duplikat, ale pomaga w przypadku, gdy użytkownik nie ustawi wartości przed zapisaniem modelu.

- Włącz weryfikację dla DSL. W eksploratorze DSL wybierz pozycję Editor\Validation i ustaw właściwości **Uses...** na `true` wartość .

     Istnieje automatycznie wygenerowana metoda walidacji, która sprawdza niejednoznaczności. Metoda należy do kategorii `Load` walidacji. Daje to pewność, że użytkownik zostanie ostrzec, że ponowne otwarcie pliku może nie być możliwe.

     Aby uzyskać więcej informacji, zobacz Validation in a Domain-Specific Language (Walidacja [w Domain-Specific Języku ).](../modeling/validation-in-a-domain-specific-language.md)

### <a name="moniker-paths-and-qualifiers"></a>Moniker Paths and Qualifiers

Kwalifikowaną moniker klucza kończy się kluczem moniker i ma prefiks moniker jego elementu nadrzędnego w drzewie osadzania. Na przykład, jeśli monikera cyka to:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Następnie jedną z utworów w tym the The The Przemysieć może być:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Jeśli jednak zamiast tego przywoływuje się do nich identyfikator, monikery będą następujące:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Należy zauważyć, że ponieważ identyfikator GUID jest unikatowy, nigdy nie jest poprzedzony przez monikera jego elementu nadrzędnego.

Jeśli wiesz, że właściwość określonej domeny zawsze będzie mieć unikatową wartość w modelu, możesz ustawić właściwość **Is Moniker Qualifier** na `true` wartość dla tej właściwości. Spowoduje to użycie go jako kwalifikatora bez użycia monikera elementu nadrzędnego. Jeśli na przykład ustawisz wartości **Is Moniker Qualifier** (Kwalifikator monikera) i Is Moniker Key (Klucz jest kluczem **monikera)** dla właściwości domain (Tytuł) klasy Sol, nazwa lub identyfikator modelu nie będzie używana w monikerach dla obiektu Aiker i jego osadzonych obiektów głównych:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Dostosowywanie struktury kodu XML

Aby wprowadzić następujące dostosowania, rozwiń **xml zachowanie serializacji** węzła w Eksploratorze DSL. W obszarze klasy domeny rozwiń węzeł Dane elementu, aby wyświetlić listę właściwości i relacji, które pochodzą z tej klasy. Wybierz relację i dostosuj jej opcje w okno Właściwości.

- Ustaw **wartość "Pomiń element"** na true, aby pominąć węzeł roli źródłowej, pozostawiając tylko listę elementów docelowych. Nie należy ustawiać tej opcji, jeśli istnieje więcej niż jedna relacja między klasami źródłowymi i docelowymi.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- Ustaw **ustawienie Użyj pełnego formularza,** aby osadzić węzły docelowe w węzłach reprezentujących wystąpienia relacji. Ta opcja jest ustawiana automatycznie podczas dodawania właściwości domeny do relacji domeny.

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

- Ustaw **element**  =  **reprezentacji,** aby właściwość domeny została zapisana jako element, a nie jako wartość atrybutu.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Aby zmienić kolejność, w której atrybuty i relacje są serializowane, kliknij  prawym przyciskiem myszy element w obszarze dane elementu, a następnie użyj Przenieś w górę lub **Przenieś w** dół poleceń menu.

## <a name="major-customization-using-program-code"></a>Główne dostosowywanie przy użyciu kodu programu

Można zastąpić części lub wszystkie algorytmy serializacji.

Zalecamy zapoznanie się z kodem w **katalogu Dsl\Generated Code\Serializer.cs** i **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Aby dostosować serializacji określonej klasy

1. Ustaw **jest niestandardowy** w węźle dla tej klasy w obszarze Zachowanie **serializacji XML**.

2. Przekształć wszystkie szablony, skompilować rozwiązanie i zbadać wynikowe błędy kompilacji. Komentarze obok każdego błędu wyjaśniają, jaki kod należy podać.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Aby zapewnić własną serializacji dla całego modelu

1. Przesłanianie metod w dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Opcje w zachowaniu serializacji XML

W Eksploratorze DSL węzeł Zachowanie serializacji XML zawiera węzeł podrzędny dla każdej klasy domeny, relacji, kształtu, łącznika i klasy diagramu. W ramach każdego z tych węzłów znajduje się lista właściwości i relacji źródle dla tego elementu. Relacje są reprezentowane zarówno we własnym prawach, jak i w klasach źródłowych.

W poniższej tabeli przedstawiono podsumowanie opcji, które można ustawić w tej sekcji definicji DSL. W każdym przypadku wybierz element w eksploratorze DSL i ustaw opcje w okno Właściwości.

### <a name="xml-class-data"></a>Dane klasy XML

Te elementy znajdują się w Eksploratorze DSL w **obszarze Zachowanie serializacji XML\Dane klasy**.

|Właściwość|Opis|
|-|-|
|Ma niestandardowy schemat elementu|Wartość True oznacza, że klasa domeny ma niestandardowy schemat elementu|
|Jest niestandardowy|Ustaw tę wartość **na True,** jeśli chcesz napisać własny kod serializacji i deserializacji dla tej klasy domeny.<br /><br /> Skompilowanie rozwiązania i zbadanie błędów w celu odnajdywania szczegółowych instrukcji.|
|Klasa domeny|Klasa domeny, do której odnosi się ten węzeł danych klasy. Tylko do odczytu.|
|Nazwa elementu|Nazwa węzła XML dla elementów tej klasy. Wartość domyślna to wersja małe liter nazwy klasy domeny.|
|Nazwa atrybutu moniker|Nazwa atrybutu używanego w elementach moniker do zawierania odwołania. Jeśli pole jest puste, używana jest nazwa właściwości klucza lub identyfikatora.<br /><br /> W tym przykładzie jest to "name":  `<personMoniker name="/Mike Nash"/>`|
|Nazwa elementu moniker|Nazwa elementu xml używane dla monikerów, które odwołują się do elementów tej klasy.<br /><br /> Wartość domyślna to mała wersja nazwy klasy z sufiksem "Moniker". Na przykład `personMoniker`.|
|Nazwa typu monikera|Nazwa typu xsd wygenerowanego dla monikerów dla elementów tej klasy. XSD znajduje się w **pliku Dsl\Generated Code \\ \* Schema.xsd**|
|Serializowanie identyfikatora|W przypadku wartości True identyfikator GUID elementu jest uwzględniony w pliku . Musi to być prawda, jeśli nie ma właściwości, która jest oznaczona jest klucz **moniker** i DSL definiuje relacji odwołania do tej klasy.|
|Nazwa typu|Nazwa typu xml wygenerowany w xsd z wyznaczonej klasy domeny.|
|Uwagi|Notatki nieformalne skojarzone z tym elementem|

### <a name="xml-property-data"></a>Dane właściwości XML

Węzły właściwości XML znajdują się w węzłach klasy.

|Właściwość|Opis|
|-|-|
|Właściwość domeny|Właściwość, do której mają zastosowanie dane konfiguracji serializacji XML. Tylko do odczytu.|
|Jest kluczem moniker|W przypadku wartości True właściwość jest używana jako klucz do tworzenia monikerów, które odwołują się do wystąpień tej klasy domeny.|
|Czy kwalifikator monikera|W przypadku wartości True właściwość jest używana do tworzenia kwalifikatora w monikerach. Jeśli wartość false, a wartość SerializeId nie jest prawdziwa dla tej klasy domeny, monikery są kwalifikowane za pomocą monikera elementu nadrzędnego w drzewie osadzania.|
|Reprezentacja|Jeśli atrybutu, właściwość jest serializowana jako atrybut XML; If, element jest serializowany jako element; Jeśli Ignoruj, nie jest serializowany.|
|Nazwa XML|Nazwa używana dla atrybutu xml lub elementu reprezentującego właściwość. Domyślnie jest to wersja małe liter nazwy właściwości domeny.|
|Uwagi|Notatki nieformalne skojarzone z tym elementem|

### <a name="xml-role-data"></a>Dane roli XML

Węzły danych roli znajdują się w węzłach klasy źródłowej.

|Właściwość|Opis|
|-|-|
|Ma niestandardową moniker|Ustaw tę wartość na true, jeśli chcesz podać własny kod do generowania i rozwiązywania monikerów, które przechodziły przez tę relację.<br /><br /> Aby uzyskać szczegółowe instrukcje, skompilować rozwiązanie, a następnie kliknij dwukrotnie komunikaty o błędach.|
|Relacja domeny|Określa relację, do której te opcje mają zastosowanie. Tylko do odczytu.|
|Omit, element|W przypadku wartości true węzeł XML odpowiadający roli źródłowej zostanie pominięty w schemacie.<br /><br /> Jeśli istnieje więcej niż jedna relacja między klasami źródłowymi i docelowymi, ten węzeł roli rozróżnia łącza należące do dwóch relacji. W związku z tym zaleca się, aby nie ustawiać tej opcji w tym przypadku.|
|Nazwa elementu roli|Określa nazwę elementu XML, który pochodzi od roli źródłowej. Wartość domyślna to nazwa właściwości roli.|
|Używanie pełnego formularza|W przypadku wartości true każdy element docelowy lub moniker jest ujęty w węzeł XML reprezentujący relację. Ta wartość powinna być ustawiona na wartość true, jeśli relacja ma własne właściwości domeny.|

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)

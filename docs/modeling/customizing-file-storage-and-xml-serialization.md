---
title: Dostosowywanie przechowywania plików i serializacji XML
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51173fcf2e8f6785b61bfd348178a59b5fb933dc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654015"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Dostosowywanie przechowywania plików i serializacji XML

Gdy użytkownik zapisuje wystąpienie lub *model*w języku specyficznym dla domeny (DSL) w programie Visual Studio, zostanie utworzony lub zaktualizowany plik XML. Plik można ponownie załadować, aby ponownie utworzyć model w sklepie.

Można dostosować schemat serializacji, dostosowując ustawienia w obszarze **zachowanie serializacji kodu XML** w Eksploratorze DSL. Istnieje węzeł w ramach **zachowania serializacji kodu XML** dla każdej klasy domeny, właściwości i relacji. Relacje znajdują się w obszarze ich klas źródłowych. Istnieją również węzły odpowiadające klasom kształtu, łącznika i diagramu.

Możesz również napisać kod programu, aby uzyskać bardziej zaawansowane dostosowywanie.

> [!NOTE]
> Jeśli chcesz zapisać model w określonym formacie, ale nie musisz go ponownie załadować z tego formularza, rozważ użycie szablonów tekstowych do wygenerowania danych wyjściowych z modelu zamiast niestandardowego schematu serializacji. Aby uzyskać więcej informacji, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Pliki modelu i diagramu

Każdy model jest zwykle zapisywany w dwóch plikach:

- Plik modelu ma nazwę, taką jak **Model1. mydsl**. Przechowuje elementy modelu i relacje oraz ich właściwości. Rozszerzenie pliku, takie jak **. mydsl** , jest określane przez właściwość **FileExtension** węzła **edytora** w definicji DSL.

- Plik diagramu ma nazwę, taką jak **Model1. mydsl. diagram**. Przechowuje kształty, łączniki i ich pozycje, kolory, grubości linii oraz inne szczegóły wyglądu diagramu. Jeśli użytkownik usunie plik **diagramu** , podstawowe informacje w modelu nie zostaną utracone. Tylko układ diagramu zostanie utracony. Po otwarciu pliku modelu zostanie utworzony domyślny zestaw kształtów i łączników.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Aby zmienić rozszerzenie pliku DSL

1. Otwórz definicję DSL. W Eksploratorze DSL kliknij węzeł Edytor.

2. W okno Właściwości Edytuj Właściwość **FileExtension** . Nie dodawaj początkowego "." rozszerzenia nazwy pliku.

3. W Eksplorator rozwiązań Zmień nazwę dwóch plików szablonów elementów w **DslPackage\ProjectItemTemplates**. Te pliki mają nazwy, które są zgodne z tym formatem:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Domyślny schemat serializacji

Do utworzenia przykładu dla tego tematu użyto następującej definicji DSL.

![Model drzewa rodziny &#45; diagramów definicji DSL](../modeling/media/familyt_person.png)

Ten DSL został użyty do utworzenia modelu, który ma następujący wygląd na ekranie.

![Diagram drzewa rodzin, Przybornik i Eksplorator](../modeling/media/familyt_instance.png)

Ten model został zapisany, a następnie ponownie otwarty w edytorze tekstu XML:

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

- Każdy węzeł XML ma nazwę, która jest taka sama jak nazwa klasy domeny, z tą różnicą, że inicjał jest pisany małymi literami. Na przykład `familyTreeModel` i `person`.

- Właściwości domeny, takie jak Name i BirthYear, są serializowane jako atrybuty w węzłach XML. Ponownie początkowy znak nazwy właściwości jest konwertowany na małe litery.

- Każda relacja jest serializowana jako węzeł XML zagnieżdżony w źródłowym końcu relacji. Węzeł ma taką samą nazwę jak właściwość roli źródłowej, ale z znakiem początkowym małymi literami.

     Na przykład w definicji DSL rola o nazwie **ludzie** jest źródłem w klasie **FamilyTree** .  W kodzie XML jest to reprezentowane przez węzeł o nazwie `people` zagnieżdżony w węźle `familyTreeModel`.

- Zakończenie każdej relacji osadzania jest serializowane jako węzeł zagnieżdżony w relacji. Na przykład węzeł `people` zawiera kilka węzłów `person`.

- Koniec elementu docelowego każdej relacji odwołania jest serializowany jako *moniker*, który koduje odwołanie do elementu docelowego.

     Na przykład w węźle `person` może istnieć relacja `children`. Ten węzeł zawiera monikery, takie jak:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Zrozumienie monikerów

Monikery służą do reprezentowania odwołań między różnymi częściami modelu i plików diagramu. Są one również używane w pliku `.diagram` w celu odwoływania się do węzłów w pliku modelu. Istnieją dwie formy monikera:

- *Monikery identyfikatorów* wyznaczają identyfikator GUID elementu docelowego. Na przykład:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *Kwalifikowane monikery kluczy* identyfikują element docelowy przez wartość wydaną właściwość domeny o nazwie klucz monikera. Moniker elementu docelowego jest poprzedzony monikerem jego elementu nadrzędnego w drzewie relacji osadzania.

     Poniższe przykłady są pobierane z linii DSL, w której istnieje Klasa domeny o nazwie album, która ma relację osadzania do klasy domeny o nazwie Song:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     W przypadku, gdy Klasa docelowa ma właściwość domeny, dla której opcja **jest kluczem monikera** jest ustawiona na `true` w **zachowaniu serializacji XML**. W tym przykładzie ta opcja jest ustawiona dla właściwości domeny o nazwie "title" w klasach domeny "album" i "utwór".

Kwalifikowane monikery kluczy są łatwiejsze do odczytania niż monikery identyfikatorów. Jeśli zamierzasz odczytać XML plików modelu przez osoby, rozważ użycie kwalifikowanych krótkich monikerów. Jednak użytkownik może ustawić więcej niż jeden element, aby mieć ten sam klucz monikera. Zduplikowane klucze mogą spowodować, że plik nie zostanie poprawnie załadowany. Dlatego w przypadku zdefiniowania klasy domeny, do której odwołuje się monikery kluczy, należy rozważyć sposoby uniemożliwiania użytkownikowi zapisania pliku, który ma zduplikowane monikery.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Aby ustawić klasę domeny, do której mają być przywoływane monikery identyfikatorów

1. Upewnij się, że **klucz moniker** jest `false` dla każdej właściwości domeny w klasie i jej klasach bazowych.

    1. W Eksploratorze DSL rozwiń kolejno pozycje **XML serializacji Behavior\Class dane \\ \<the klasy domeny > \Element danych**.

    2. Sprawdź, czy **klucz moniker** jest `false` dla każdej właściwości domeny.

    3. Jeśli klasa domeny ma klasę bazową, Powtórz procedurę w tej klasie.

2. Ustaw **Identyfikator serializacji**  =  `true` dla klasy domeny.

     Tę właściwość można znaleźć w obszarze **zachowanie serializacji kodu XML**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Aby ustawić klasę domeny, do której mają być przywoływane kwalifikowane monikery kluczy

- Set **jest kluczem monikera** dla właściwości domeny istniejącej klasy domeny. Typ właściwości musi być `string`.

    1. W Eksploratorze DSL rozwiń kolejno pozycje **XML serializacji Behavior\Class dane \\ \<the klasy domeny > \Element dane**, a następnie wybierz właściwość domena.

    2. W okno Właściwości ustaw **klucz moniker** , aby `true`.

- \- lub-

     Utwórz nową klasę domeny za pomocą narzędzia **klasy nazwanej domeny** .

     To narzędzie tworzy nową klasę, która ma właściwość domeny o nazwie name. **Nazwa elementu is** i **ma właściwości klucza monikera** tej właściwości domeny są inicjowane w celu `true`.

- \- lub-

     Utwórz relację dziedziczenia z klasy domeny do innej klasy, która ma właściwość klucza monikera.

### <a name="avoid-duplicate-monikers"></a>Unikaj duplikowania monikerów

Jeśli używasz krótkich monikerów kluczy, możliwe jest, że dwa elementy w modelu użytkownika mogą mieć taką samą wartość we właściwości klucza. Jeśli na przykład DSL ma osobę klasy, która ma nazwę właściwości, użytkownik może ustawić nazwy dwóch elementów jako takie same. Mimo że model może zostać zapisany w pliku, nie zostanie poprawnie załadowany.

Istnieje kilka metod, które pomagają uniknąć tej sytuacji:

- Zestaw **jest nazwą elementu**  =  `true` właściwości domena klucza. Wybierz właściwość domena na diagramie definicji DSL, a następnie ustaw wartość w okno Właściwości.

     Gdy użytkownik tworzy nowe wystąpienie klasy, ta wartość powoduje, że właściwość domeny ma automatycznie przypisaną inną wartość. Zachowanie domyślne dodaje numer na końcu nazwy klasy. Nie uniemożliwia to użytkownikowi zmiany nazwy na duplikat, ale w przypadku, gdy użytkownik nie ustawi wartości przed zapisaniem modelu, może to zrobić.

- Włącz sprawdzanie poprawności dla DSL. W Eksploratorze DSL wybierz pozycję Editor\Validation, a następnie ustaw `true` właściwości **Użyj...** .

     Jest automatycznie generowana Metoda walidacji, która sprawdza, czy niejasności. Metoda jest w kategorii Walidacja `Load`. Pozwala to upewnić się, że użytkownik otrzyma ostrzeżenie, że może nie być możliwe ponowne otwarcie pliku.

     Aby uzyskać więcej informacji, zobacz [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Ścieżki i kwalifikatory monikera

Kwalifikowana moniker klucza zamyka się z kluczem monikera i jest poprzedzony krótką monikerem elementu nadrzędnego w drzewie osadzania. Na przykład, jeśli moniker albumu jest:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Następnie jednym z piosenek w tym albumie może być:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Jeśli jednak w zamian odwołuje się do nich albumy, monikery byłyby następujące:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Należy zauważyć, że identyfikator GUID jest unikatowy, nigdy nie jest poprzedzony przez moniker jego elementu nadrzędnego.

Jeśli wiesz, że właściwość konkretnej domeny zawsze ma unikatową wartość w ramach modelu, możesz ustawić **kwalifikator monikera** do `true` dla tej właściwości. Spowoduje to, że będzie on używany jako kwalifikator, bez używania monikera elementu nadrzędnego. Jeśli na przykład ustawisz obie wartości **kwalifikator monikera** i **jest to klucz moniker** dla właściwości domena tytułu klasy albumu, nazwa lub Identyfikator modelu nie jest używany w monikerach dla albumu i jego osadzonych elementów podrzędnych:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Dostosuj strukturę XML

Aby wprowadzić następujące dostosowania, rozwiń węzeł **zachowanie serializacji XML** w Eksploratorze DSL. W obszarze Klasa domeny rozwiń węzeł dane elementu, aby wyświetlić listę właściwości i relacji, które są źródłem w tej klasie. Wybierz relację i dostosuj jej opcje w okno Właściwości.

- Aby pominąć węzeł roli źródłowej, należy ustawić wartość " **Pomiń** ", pozostawiając tylko listę elementów docelowych. Nie należy ustawiać tej opcji, jeśli istnieje więcej niż jedna relacja między klasą źródłową i docelową.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- Ustaw **użycie pełnego formularza** do osadzenia węzłów docelowych w węzłach reprezentujących wystąpienia relacji. Ta opcja jest ustawiana automatycznie po dodaniu właściwości domeny do relacji domeny.

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

- Ustaw **reprezentację** **elementu**  = , aby właściwość domeny została zapisana jako element, a nie jako wartość atrybutu.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Aby zmienić kolejność, w której atrybuty i relacje są serializowane, kliknij prawym przyciskiem myszy element w obszarze dane elementu i Użyj poleceń menu **Przenieś w górę** lub **Przenieś w dół** .

## <a name="major-customization-using-program-code"></a>Główne dostosowanie przy użyciu kodu programu

Można zastąpić części lub wszystkie algorytmy serializacji.

Zalecamy zbadanie kodu w **Dsl\Generated Code\Serializer.cs** i **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Aby dostosować serializację określonej klasy

1. Zestaw **jest niestandardowy** w węźle dla tej klasy w ramach **zachowania serializacji kodu XML**.

2. Przekształć wszystkie szablony, Kompiluj rozwiązanie i zbadaj powstające błędy kompilacji. Komentarze obok każdego błędu wyjaśniają kod, który należy podać.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Aby zapewnić własną serializację dla całego modelu

1. Zastąp metody w Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Opcje zachowania serializacji kodu XML

W Eksploratorze DSL węzeł zachowania serializacji XML zawiera węzeł podrzędny dla każdej klasy domeny, relacji, kształtu, łącznika i klasy diagramu. W każdym z tych węzłów znajduje się lista właściwości i relacji źródłowych w tym elemencie. Relacje są reprezentowane we własnych prawach i w ramach ich klas źródłowych.

Poniższa tabela zawiera podsumowanie opcji, które można ustawić w tej sekcji definicji DSL. W każdym przypadku wybierz element w Eksploratorze DSL i ustaw opcje w okno Właściwości.

### <a name="xml-class-data"></a>Dane klasy XML

Te elementy są dostępne w Eksploratorze DSL w obszarze **dane serializacji XML Behavior\Class**.

|||
|-|-|
|Właściwość|Opis|
|Ma niestandardowy schemat elementu|W przypadku wartości true oznacza, że Klasa domeny ma niestandardowy schemat elementu|
|Jest niestandardowy|Ustaw tę **wartość na true (prawda** ), jeśli chcesz napisać własny kod serializacji i deserializacji dla tej klasy domeny.<br /><br /> Skompiluj rozwiązanie i zbadaj błędy, aby poznać szczegółowe instrukcje.|
|Klasa domeny|Klasa domeny, do której stosuje się ten węzeł danych klasy. Tylko do odczytu.|
|Nazwa elementu|Nazwa węzła XML dla elementów tej klasy. Wartością domyślną jest mała wersja klasy domeny.|
|Nazwa atrybutu monikera|Nazwa atrybutu używanego w elementach monikera, który będzie zawierać odwołanie. Jeśli pole pozostanie puste, zostanie użyta nazwa właściwości klucza lub identyfikatora.<br /><br /> W tym przykładzie jest to "name": `<personMoniker name="/Mike Nash"/>`|
|Nazwa elementu monikera|Nazwa elementu XML używanego dla monikerów odwołujących się do elementów tej klasy.<br /><br /> Wartość domyślna to mała wersja nazwy klasy z sufiksem "moniker". Na przykład `personMoniker`.|
|Nazwa typu monikera|Nazwa typu XSD wygenerowanego dla monikerów elementów tej klasy. XSD jest w **kodzie Dsl\Generated \\ \*Schema. xsd**|
|Identyfikator serializacji|W przypadku wartości true identyfikator GUID elementu jest dołączany do pliku. Musi to być prawdziwe, jeśli nie istnieje właściwość, która jest oznaczona jako **klucz monikera** , a DSL definiuje relacje odwołania do tej klasy.|
|Nazwa typu|Nazwa typu XML wygenerowanego w formacie XSD z wytworzonej klasy domeny.|
|Uwagi|Nieformalne uwagi skojarzone z tym elementem|

### <a name="xml-property-data"></a>Dane właściwości XML

Węzły właściwości XML znajdują się w węzłach klas.

|||
|-|-|
|Właściwość|Opis|
|Właściwość domeny|Właściwość, do której stosują się dane konfiguracji serializacji kodu XML. Tylko do odczytu.|
|Jest kluczem monikera|W przypadku wartości true właściwość jest używana jako klucz do tworzenia monikerów, które odwołują się do wystąpień tej klasy domeny.|
|Jest kwalifikatorem monikera|W przypadku wartości true właściwość jest używana do tworzenia kwalifikatora w monikerach. Jeśli wartość jest równa false, a jeśli SerializeId nie ma wartości true dla tej klasy domeny, monikery są kwalifikowane przez moniker elementu nadrzędnego w drzewie osadzania.|
|Reprezentowana|Jeśli atrybut, właściwość jest serializowana jako atrybut XML; Jeśli element, jest serializowany jako element; w przypadku ignorowania nie jest serializowana.|
|Nazwa XML|Nazwa używana dla atrybutu XML lub elementu reprezentującego właściwość. Domyślnie jest to niższa wersja nazwy właściwości domeny.|
|Uwagi|Nieformalne uwagi skojarzone z tym elementem|

### <a name="xml-role-data"></a>Dane roli XML

Węzły danych roli znajdują się w węzłach klasy źródłowej.

|Właściwość|Opis|
|-|-|
|Ma niestandardową moniker|Ustaw tę wartość na true (prawda), jeśli chcesz podać własny kod do generowania i rozpoznawania monikerów, które przechodzą tę relację.<br /><br /> Aby uzyskać szczegółowe instrukcje, skompiluj rozwiązanie, a następnie kliknij dwukrotnie komunikaty o błędach.|
|Relacja domeny|Określa relację, do której mają zastosowanie te opcje. Tylko do odczytu.|
|Pomiń element|W przypadku wartości true węzeł XML odpowiadający roli źródłowej jest pomijany ze schematu.<br /><br /> Jeśli istnieje więcej niż jedna relacja między klasą źródłową i docelową, ten węzeł roli rozróżnia linki należące do dwóch relacji. Dlatego zalecamy, aby nie ustawiać tej opcji w tym przypadku.|
|Nazwa elementu roli|Określa nazwę elementu XML, który jest pochodną roli źródłowej. Wartość domyślna to nazwa właściwości roli.|
|Użyj pełnego formularza|W przypadku wartości true każdy element docelowy lub moniker jest ujęty w węźle XML reprezentującym relację. Ta wartość powinna być ustawiona na true, jeśli relacja ma własne właściwości domeny.|

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
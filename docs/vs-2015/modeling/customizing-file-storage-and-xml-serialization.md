---
title: Dostosowywanie przechowywania plików i serializacji XML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b41f5f6a3d937f23db1039fdab5e1cf7e36960ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433264"
---
# <a name="customizing-file-storage-and-xml-serialization"></a>Dostosowywanie przechowywania plików i serializacji XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy użytkownik zapisuje wystąpienia lub *modelu*, języka specyficznego dla domeny (DSL), w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], plik XML jest tworzony lub aktualizowany. Plik można wykorzystać w celu ponownego utworzenia modelu w Store.  
  
 Schemat serializacji można dostosować, zmieniając ustawienia w obszarze **zachowanie serializacji kodu Xml** w Eksplorator DSL. Istnieje węzeł w węźle **zachowanie serializacji kodu Xml** dla każdej klasy domeny, właściwości i relacji. Relacje znajdują się w ramach ich klas źródłowych. Dostępne są także węzłów odpowiadający kształt, łącznik i diagramu klas.  
  
 Można także napisać kod programu do bardziej zaawansowane dostosowania.  
  
> [!NOTE]
> Jeśli chcesz zapisać modelu w określonym formacie, ale nie trzeba go załadować ponownie z tego formularza, należy wziąć pod uwagę przy użyciu szablonów tekstowych do generowania danych wyjściowych z modelem, zamiast schematu niestandardowej serializacji. Aby uzyskać więcej informacji, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="model-and-diagram-files"></a>Model i pliki diagramu  
 Każdy model jest zazwyczaj zapisywany w dwóch plikach:  
  
- Plik modelu ma nazwę **Model1.mydsl**. Przechowuje elementy modelu i relacji i ich właściwości. Rozszerzenie pliku, takie jak **.mydsl** jest określana przez **FileExtension** właściwość **edytora** węzła w definicji DSL.  
  
- Plik diagramu ma nazwę **Model1.mydsl.diagram**. Przechowuje kształty, łączniki i ich pozycje, kolory, falistej linii i inne szczegóły wygląd diagramu. Jeśli użytkownik usunie **.diagram** pliku, niezbędne informacje w modelu nie zostaną utracone. Układ diagramu zostaną utracone. Po otwarciu pliku modelu domyślny zestaw kształtów i łączników zostaną utworzone.  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>Aby zmienić rozszerzenie języka DSL  
  
1. Otwórz definicję DSL. W Eksploratorze DSL kliknij węzeł edytora.  
  
2. W oknie dialogowym Właściwości Edytuj **FileExtension** właściwości. Nie dołączaj początkowej "." rozszerzenie nazwy pliku.  
  
3. W Eksploratorze rozwiązań, zmienianie nazwy plików szablonów dwóch elementów w **DslPackage\ProjectItemTemplates**. Te pliki mają nazwy, które należy wykonać następujący format:  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>Domyślny schemat serializacji  
 Aby utworzyć przykład w tym temacie, użyto następujących definicji DSL.  
  
 ![Diagramem definicji DSL &#45; model drzewa rodziny](../modeling/media/familyt-person.png "FamilyT_Person")  
  
 Tego języka DSL został użyty do utworzenia modelu, który ma następujący wygląd na ekranie.  
  
 ![Diagram drzewa rodziny, przybornika i Eksplorator](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 Ten model został zapisany i ponownym otwarciu w edytorze tekstu XML:  
  
```  
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
  
 Zwróć uwagę na następujące kwestie dotyczące modelu serializowane:  
  
- Każdy węzeł XML ma nazwę, która jest taka sama jak nazwa klasy domeny, z tą różnicą, że początkowej litery jest pisana małymi literami. Na przykład `familyTreeModel` i `person`.  
  
- Właściwości domeny, takie jak nazwa i rokurodzenia są serializowane jako atrybuty w węzłach XML. Ponownie początkowy znak nazwy właściwości są konwertowane na małe litery.  
  
- Każda relacja jest serializowany jako węzeł XML zagnieżdżonych w końcu źródło relacji. Węzeł ma taką samą nazwę właściwości roli źródła, ale z małą literę początkowej.  
  
     Na przykład w definicji DSL roli, który nosi nazwę **osób** rozwijani w modelu jest **FamilyTree** klasy.  W pliku XML, jest reprezentowane przez węzeł o nazwie `people` zagnieżdżone wewnątrz `familyTreeModel` węzła.  
  
- Docelowe zakończenie każdej relacji osadzania jest serializowany jako węzeł zagnieżdżony w relacji. Na przykład `people` węzeł zawiera kilka `person` węzłów.  
  
- Docelowe zakończenie każdego relacja odwołania jest serializowany jako *moniker*, które koduje odwołanie do elementu docelowego.  
  
     Na przykład w obszarze `person` węzła, mogą być `children` relacji. Ten węzeł zawiera krótkie nazwy, takie jak:  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>Monikery opis  
 Monikery są używane do reprezentowania odsyłacze między poszczególnymi częściami modelu i diagram plików. Są one także używane w `.diagram` pliku do odwoływania się do węzłów w pliku modelu. Istnieją dwa rodzaje monikera:  
  
- *Identyfikator monikerów* oferta identyfikator GUID elementu docelowego. Na przykład:  
  
  ```  
  <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
  ```  
  
- *Kwalifikowana klucza monikerów* zidentyfikować elementu docelowego na podstawie wartości właściwości wyznaczoną domeną, nazywany kluczem monikera. Moniker elementu docelowego jest poprzedzony moniker odpowiedniego elementu nadrzędnego w drzewie relacji osadzania.  
  
   Poniższe przykłady są pobierane z DSL w którym jest klasą domeny o nazwie fotograficzne, mającej relacji osadzania do domeny klasy o nazwie utworu:  
  
  ```  
  <albumMoniker title="/My Favorites/Jazz after Teatime" />  
  <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
  ```  
  
   Kwalifikowana monikerów kluczy zostaną użyte, jeśli Klasa docelowa ma właściwość domeny, dla którego opcja **jest kluczem monikera** ustawiono `true` w **zachowanie serializacji kodu Xml**. W tym przykładzie ta opcja jest ustawiona dla właściwości domeny o nazwie "Title" w klasach domeny "Albumu" i "Utwór".  
  
  Kwalifikowana klucza krótkie nazwy to łatwiejsza do odczytania niż identyfikator monikerów. Jeśli planujesz XML plików modelu zostanie odczytany przez osoby, należy rozważyć użycie kwalifikowanej monikerów klucza. Jednak jest użytkownik, który może ustawić więcej niż jeden element do mają taki sam klucz krótkiej nazwy. Zduplikowane klucze może spowodować pliku nie można prawidłowo załadować ponownie. W związku z tym Jeśli zdefiniujesz klasę domeny, do którego odwołuje się przy użyciu kwalifikowanej monikerów klucza, należy rozważyć sposób zapobiegania użytkownika nie można zapisać pliku, który ma zduplikowane monikerów.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Aby ustawić odwoływać się monikerów identyfikator klasy domeny  
  
1. Upewnij się, że **jest kluczem monikera** jest `false` dla każdej właściwości domeny w tej klasy i jej klasy bazowe.  
  
    1. W Eksploratorze DSL rozwiń **dane Behavior\Class serializacji kodu Xml\\**_\<klasy domeny >_**\Element danych**.  
  
    2. Upewnij się, że **jest kluczem monikera** jest `false` dla każdej właściwości domeny.  
  
    3. Jeśli klasa domeny ma klasę bazową, powtórz procedurę opisaną w tej klasy.  
  
2. Ustaw **serializacji identyfikatora**  =  `true` dla klasy domeny.  
  
     Tej właściwości można znaleźć w obszarze **zachowanie serializacji kodu Xml**.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Aby ustawić odwoływać się kwalifikowaną monikerów klucza klasy domeny  
  
- Ustaw **jest kluczem monikera** dla właściwości domeny w istniejącej klasy domeny. Typ właściwości musi być `string`.  
  
    1. W Eksploratorze DSL rozwiń **dane Behavior\Class serializacji kodu Xml\\**_\<klasy domeny >_**\Element danych**, a następnie wybierz pozycję Właściwość domeny.  
  
    2. W oknie właściwości ustaw **jest kluczem monikera** do `true`.  
  
- \- lub —  
  
     Utwórz nową klasę domeny, za pomocą **klasy domeny o nazwie** narzędzia.  
  
     To narzędzie tworzy nową klasę, który ma właściwość domeny o nazwie Name. **Jest nazwa elementu** i **jest kluczem monikera** właściwości właściwości domeny są inicjowane na wartość `true`.  
  
- \- lub —  
  
     Utwórz relację dziedziczenia z klasy domeny do innej klasy, która ma właściwość klucza krótkiej nazwy.  
  
### <a name="avoiding-duplicate-monikers"></a>Avoiding Duplicate Monikers  
 Jeśli używasz kwalifikowaną monikerów klucza, istnieje możliwość, dwa elementy w modelu użytkownika mają taką samą wartość właściwości klucza. Na przykład jeśli DSL ma klasę osoby, która ma właściwość Name, użytkownika można ustawić nazwy dwóch elementów w taki sam. Mimo że modelu może być zapisana w pliku, go czy nie zostanie odświeżona poprawnie.  
  
 Istnieje kilka metod, które pomagają uniknąć tej sytuacji:  
  
- Ustaw **jest nazwa elementu**  =  `true` dla właściwości domeny klucza. Wybierz właściwość domeny na diagramem definicji DSL, a następnie ustaw wartość w oknie dialogowym właściwości.  
  
     Gdy użytkownik tworzy nowe wystąpienie klasy, ta wartość powoduje, że właściwość domeny automatycznie przypisać inną wartość. Domyślne zachowanie dodaje numer na końcu nazwy klasy. To nie uniemożliwia użytkownikowi zmianę nazwy, aby duplikat, ale pomaga w przypadku, gdy użytkownik nie ustawiać wartości przed zapisaniem modelu.  
  
- Włącz weryfikację język DSL. W Eksploratorze DSL wybierz Editor\Validation, a następnie ustaw **używa...**  właściwości `true`.  
  
     Jest generowany automatycznie Walidacja metodę, która sprawdza, czy dla niejednoznaczności. Metoda ta jest `Load` kategorii sprawdzania poprawności. To sprawia, że się upewnić, że użytkownik będzie wyświetlane ostrzeżenie, może nie być możliwe do ponownego otwarcia pliku.  
  
     Aby uzyskać więcej informacji, zobacz [weryfikacji języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).  
  
### <a name="moniker-paths-and-qualifiers"></a>Moniker ścieżki i kwalifikatory  
 Kwalifikowana moniker klucza kończy się wraz z kluczem monikera i jest poprzedzony znakiem moniker elementu nadrzędnego w drzewie osadzania. Na przykład, jeśli moniker albumu:  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 Następnie utworów muzycznych, w tym albumu może być:  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 Jednak jeśli albumów odwołują się identyfikator zamiast tego, monikerów będzie następujący:  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 Należy zauważyć, że identyfikator GUID jest unikatowy, że jest nigdy nie poprzedzona przez moniker elementu nadrzędnego.  
  
 Jeśli znasz właściwości określonej domeny zawsze będzie unikatową wartość w modelu, można ustawić **jest kwalifikatorem monikera** do `true` dla tej właściwości. To spowoduje, że może być ona używana jako kwalifikator, bez używania moniker elementu nadrzędnego. Na przykład jeśli ustawisz zarówno **jest kwalifikatorem monikera** i **jest kluczem monikera** dla właściwości domeny tytuł klasy fotograficzne, nazwa lub identyfikator modelu nie jest używany w monikerów do albumów i swoich osadzony elementy podrzędne:  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>Dostosowywanie struktury pliku XML  
 Aby wykonać następujące dostosowania, rozwiń **zachowanie serializacji kodu Xml** węzła w Eksploratorze DSL. W ramach klasy domeny rozwiń węzeł danych elementu, aby wyświetlić listę właściwości i relacje, które biorą się w tej klasie. Wybierz relację i dostosować jego opcje w oknie dialogowym właściwości.  
  
- Ustaw **pominięto Element** na wartość true, aby pominąć węzeł roli źródłowej, pozostawiając tylko lista elementów docelowych. Nie należy ustawić tę opcję, jeśli istnieje więcej niż jedną relację między klas źródłowych i docelowych.  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
- Ustaw **użyj pełnej formy** do osadzenia węzły docelowe w węzłów reprezentujących wystąpienia relacji. Ta opcja jest ustawiana automatycznie po dodaniu właściwości domeny do relacji domeny.  
  
    ```  
  
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
  
- Ustaw **reprezentacji** = **elementu** mieć właściwość domeny zapisany jako element zamiast jako wartość atrybutu.  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
- Aby zmienić kolejność serializacji atrybutów i relacji, kliknij prawym przyciskiem myszy element w obszarze danych elementu i użyj **Przenieś w górę** lub **Przenieś w dół** poleceń menu.  
  
## <a name="major-customization-using-program-code"></a>Dostosowywanie głównych przy użyciu kodu programu  
 Możesz zastąpić części lub całości algorytmów serializacji.  
  
 Zaleca się Przestudiowanie kod w **Dsl\Generated Code\Serializer.cs** i **SerializationHelper.cs**.  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>Aby dostosować serializacji danej klasy  
  
1. Ustaw **jest niestandardowa** w węźle dla tej klasy w obszarze **zachowanie serializacji kodu Xml**.  
  
2. Transformuj wszystkie szablony, skompilować rozwiązanie i zbadaj wynikowe błędy kompilacji. Jaki kod, musisz podać zostało wyjaśnione w komentarzach, prawie każdy błąd.  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Aby podać własne serializacji dla całego modelu  
  
1. Przesłaniaj metody w Dsl\GeneratedCode\SerializationHelper.cs  
  
## <a name="options-in-xml-serialization-behavior"></a>Opcje w zachowanie serializacji kodu Xml  
 W Eksploratorze DSL węzeł zachowanie serializacji kodu Xml zawiera węzeł podrzędny dla każdej klasy domeny, relacji, kształt, łącznik i diagramu klasy. W każdym z tych węzłów jest lista właściwości i relacje rozwijani w tym elementem. Relacje są reprezentowane w ich własnych prawo i w ramach ich klas źródłowych.  
  
 W poniższej tabeli przedstawiono opcje, które można ustawić w tej sekcji definicji DSL. W każdym przypadku wybierz element w Eksploratorze DSL i ustaw opcje w oknie dialogowym właściwości.  
  
### <a name="xml-class-data"></a>Dane klasy XML  
 Te elementy znajdują się w Eksplorator DSL w obszarze **dane Behavior\Class serializacji kodu Xml**.  
  
|||  
|-|-|  
|Właściwość|Opis|  
|Ma niestandardowy schemat elementu|W przypadku opcji True wskazuje, czy klasa domeny ma niestandardowy schemat elementu|  
|Jest niestandardowe|Ustaw tę opcję na **True** chcesz napisać własny kod serializacji i deserializacji dla tej klasy domeny.<br /><br /> Skompiluj rozwiązanie, a następnie zbadaj błędy, aby odnaleźć szczegółowe informacje.|  
|Klasa domeny|Klasa domeny, do którego odnosi się ten węzeł danych klasy. Tylko do odczytu.|  
|Nazwa elementu|Nazwa węzła XML dla elementów tej klasy. Wartość domyślna to małe wersję Nazwa klasy domeny.|  
|Nazwa atrybutu monikera|Nazwa atrybutu używanego w elementach monikera, aby zawierała odwołanie. Jeśli pole pozostanie puste, nazwa właściwości klucza lub identyfikatora jest używany.<br /><br /> W tym przykładzie jest to, "name":  `<personMoniker name="/Mike Nash"/>`|  
|Nazwa elementu monikera|Nazwa elementu xml używana dla monikerów, które odwołują się do elementów tej klasy.<br /><br /> Wartość domyślna to małe wersję Nazwa klasy sufiks "Moniker". Na przykład `personMoniker`.|  
|Nazwa typu monikera|Nazwa typu xsd wygenerowanego dla monikerów elementów tej klasy. Trwa XSD **kodu Dsl\Generated\\\*Schema.xsd**|  
|Identyfikator serializacji|W przypadku opcji True element identyfikatora GUID znajduje się w pliku. Musi to być wartość true, jeśli nie ma właściwości, która jest oznaczona **jest kluczem monikera** i język DSL definiuje relacje odniesienia do tej klasy.|  
|Nazwa typu|Nazwa typu xml wygenerowanego w kodzie xsd z wyznaczonej klasy domeny.|  
|Uwagi|Uwagi informacyjne skojarzone z tym elementem|  
  
### <a name="xml-property-data"></a>Dane właściwości XML  
 Właściwości XML węzły znajdują się w węzłach klasy.  
  
|||  
|-|-|  
|Właściwość|Opis|  
|Właściwości domeny|Właściwość, do której stosują się dane konfiguracji serializacji kodu xml. Tylko do odczytu.|  
|Jest kluczem monikera|W przypadku opcji True właściwość jest używana jako klucz przy tworzeniu monikerów, które odwołują się wystąpienia tej klasy domeny.|  
|Jest kwalifikatorem monikera|W przypadku opcji True właściwość jest używana w tworzeniu kwalifikatora w monikerach. Jeśli wartość to false, a element SerializeId nie jest prawdziwe dla tej klasy domeny, monikerów są kwalifikowane przez moniker elementu nadrzędnego w drzewie osadzania.|  
|Reprezentacja|Jeśli atrybut, właściwość jest serializowana jako atrybut xml; Jeśli Element jest serializowana jako element; Jeśli Ignoruj, nie jest serializowana.|  
|Nazwa XML|Nazwa używana dla atrybutu xml lub elementu reprezentującego właściwość. Domyślnie jest to wersja małe, nazwa właściwości domeny.|  
|Uwagi|Uwagi informacyjne skojarzone z tym elementem|  
  
### <a name="xml-role-data"></a>Dane XML roli  
 Węzły danych roli znajdują się w węzłach klasy źródłowej.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|Ma monikera niestandardowych.|Ustaw na wartość true, jeśli chcesz określić własny kod do generowania i rozpoznawania monikerów, które przemierzają tej relacji.<br /><br /> Aby uzyskać szczegółowe instrukcje Skompiluj rozwiązanie, a następnie kliknij dwukrotnie komunikaty o błędach.|  
|Relacja domeny|Określa relację, do którego te opcje są stosowane. Tylko do odczytu.|  
|Pominięto Element|W przypadku opcji true węzła XML odpowiadający roli źródłowej jest pomijany w schemacie.<br /><br /> Jeśli istnieje więcej niż jedną relację między klas źródłowych i docelowych, ten węzeł roli rozróżnia łączy, które należą do dwie relacje. Dlatego zaleca się, że nie ustawisz tę opcję, w tym przypadku.|  
|Nazwa elementu roli|Określa nazwę elementu XML, który jest tworzony na podstawie roli źródłowej. Wartość domyślna to nazwa właściwości roli.|  
|Użyj pełnej formy|W przypadku opcji true każdego elementu docelowego lub krótkiej nazwy jest ujęty w węźle XML reprezentujący relacji. Powinno to można ustawić wartość true, jeśli relacja ma swoje własne właściwości domeny.|  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)

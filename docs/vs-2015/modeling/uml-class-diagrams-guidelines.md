---
title: 'Diagramy klas UML: Wytyczne dotyczące | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 363a9eda86a55da2dd773a2cef5a40fc53f0a81e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424497"
---
# <a name="uml-class-diagrams-guidelines"></a>Diagramy klas UML: Wytyczne dotyczące
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio, można użyć *diagram klas UML* do opisu typów danych i ich relacji, niezależnie od ich implementacji. Diagram pozwala skupić się na logicznych aspektach klas, a nie na ich implementacji.  
  
 Aby utworzyć diagram klasy UML na **architektury** menu, wybierz **nowego diagramu UML lub diagramu warstwowego**.  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
> Ten temat dotyczy diagramów klas UML. Istnieje inny rodzaj diagramów klas, które można tworzyć i używać w celu wizualizacji kodu programu. Zobacz [projektowanie i wyświetlanie klas i typów](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
## <a name="Using"></a> Używanie diagramów klas UML  
 Można używać diagramu klas UML do różnych celów:  
  
- Aby dostarczyć niezależny od implementacji opis typów, które są używane w systemie i przekazywane pomiędzy jego składnikami.  
  
     Na przykład typ Zamówienie posiłku może być zaimplementowany w kodzie .NET w warstwie biznesowej, w języku XML w interfejsie między składnikami, w języku SQL w bazie danych i w języku HTML w interfejsie użytkownika. Chociaż szczegóły tych implementacji różnią się, relacje między typem Zamówieniem posiłku a innymi typami, takimi jak Menu lub Zapłata, są zawsze takie same. Diagram klas UML umożliwia omówienia tych relacji niezależnie od implementacji.  
  
- Aby objaśnić terminy używane do komunikacji między aplikacją i jej użytkownikami oraz w opisie potrzeb użytkownika. Zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).  
  
     Na przykład można wziąć pod uwagę historie użytkownika, przypadki użycia lub inne opisy wymagań dla aplikacji restauracji. W takim opisie można znaleźć terminy, takie jak Menu, Zamówienie, Posiłek, Cena, Zapłata, i tak dalej. Można narysować diagram klas UML, który zdefiniuje relacje pomiędzy tymi terminami. Zmniejszy to ryzyko wystąpienia niespójności w opisach wymagań oraz w interfejsie użytkownika i dokumentach pomocy.  
  
### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  
 Diagram klas UML jest zazwyczaj rysowany wraz z innymi diagramami modelującymi, aby dostarczyć opisy typów, których używają. W każdym przypadku fizyczna reprezentacja typów nie jest implikowana przez żaden z diagramów.  
  
 Diagramu aktywności  
  
 Typu danych przekazywanych przez Węzeł obiektu.  
  
 Typów styków wejściowych i wyjściowych oraz węzłów parametrów aktywności.  
  
 Zobacz [diagramy aktywności UML: Wytyczne dotyczące](../modeling/uml-activity-diagrams-guidelines.md).  
  
 Diagramów sekwencji  
  
 Typów parametrów i wartości zwracanych wiadomości.  
  
 Typów linii życia. Klasa linii życia powinna zawierać operacje dla wszystkich wiadomości, które może otrzymać.  
  
 Zobacz [diagramy sekwencji UML: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Diagramów składników  
  
 Składników komponentów, poprzez wypisanie ich operacji.  
  
 Zobacz [diagramy składników UML: Wytyczne dotyczące](../modeling/uml-component-diagrams-guidelines.md).  
  
 Diagramów przypadków użycia  
  
 Typów, wspomnianych w opisach celów oraz kroków w przypadku użycia.  
  
 Zobacz [diagramy przypadków użycia UML: Wytyczne dotyczące](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="BasicSteps"></a> Podstawowe kroki rysowania diagramów klas  
 Aby uzyskać informacje na temat elementów na diagramach klas UML, zobacz [diagramów klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md).  
  
> [!NOTE]
> Szczegółowe kroki tworzenia dowolnego diagramu modelowania zawiera są opisane w [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-uml-class-diagram"></a>Aby utworzyć diagram klas UML  
  
1. Na **architektury** menu, wybierz **nowe UML lub diagramu warstwowego**.  
  
2. W obszarze **szablony**, wybierz **Diagram klas UML**.  
  
3. Nadaj nazwę diagramowi.  
  
4. W **Dodaj do projektu modelowania**, wybierz istniejący projekt modelowania w rozwiązaniu, lub **Utwórz nowy projekt modelowania**, a następnie wybierz **OK**.  
  
     Pojawi się nowy diagram klas **UMLClass Diagram** przybornika. Przybornik zawiera wymagane elementy i relacje.  
  
#### <a name="to-draw-a-uml-class-diagram"></a>Aby narysować diagram klas UML  
  
1. Aby utworzyć typ, wybierz opcję **klasy**, **interfejsu** lub **wyliczenie** narzędzie w przyborniku, a następnie kliknij pustą część diagramu. (Jeśli przybornik jest niewidoczny, naciśnij klawisze CTRL+ALT+X.)  
  
2. Aby dodać atrybuty lub operacje do typów lub literały do wyliczenia, wybierz **atrybuty**, **operacji** lub **literały** nagłówka w typie, a następnie naciśnij klawisz ENTER.  
  
     Można napisać podpis, taki jak `f(x:Boolean):Integer`. Zobacz [atrybuty i operacje](#AttributesAndOperations).  
  
     Aby szybko dodać kilka elementów, naciśnij klawisz ENTER dwa razy na końcu każdego elementu. Można użyć klawiszy strzałek, aby przemieszczać się w górę i w dół listy.  
  
3. Aby rozwinąć lub zwinąć typ, wybierz ikonę pagonu w jego lewym górnym rogu. Można również rozwijać i zwijać **atrybuty** i **operacji** części klasy lub interfejsu.  
  
4. Aby narysować asocjacje, dziedziczenie lub łącza zależności między typami, kliknij odpowiednie narzędzie, następnie typ źródłowy a następnie na typ docelowy.  
  
5. Aby utworzyć typy w pakiecie, Utwórz pakiet przy użyciu **pakietu** narzędzia, a następnie utwórz nowe typy i pakiety w pakiecie. Można również użyć polecenia kopiuj do skopiowania typów i wklejenia ich do pakietu.  
  
6. Każdy diagram jest widokiem modelu, który jest współdzielony przez inne diagramy w tym samym projekcie. Aby wyświetlić widok drzewa pełnego modelu, wybierz **widoku**, **Windows inne**, **Eksploratora modelu UML**.  
  
## <a name="UsingTypes"></a> Za pomocą klasy, interfejsy i wyliczenia  
 W przyborniku dostępne są trzy standardowe rodzaje klasyfikatorów. Są one określane jako *typy* w tym dokumencie.  
  
 ![Klasa, wyliczenia i interfejs](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")  
  
- Użyj **klasy** (1) do reprezentowania typów danych lub obiektów w większości przypadków.  
  
- Użyj **interfejsów** (2) w kontekście, w którym trzeba odróżnić czyste interfejsy od konkretnych klas, które mają wewnętrzne implementacje. Różnica ta jest przydatna, gdy diagram służy do opisywania implementacji oprogramowania. Mniej przydatna jest, kiedy modelowane są dane pasywne lub kiedy definiuje się koncepcje używane do opisu wymagań użytkownika.  
  
- Użyj **wyliczenie** (3) do reprezentacji typu, który ma ograniczoną liczbę wartości literałowych, na przykład `Stop` i `Go`.  
  
  - Dodaj wartości literałów do wyliczenia. Każdemu z nich nadaj odrębną nazwę.  
  
  - W razie potrzeby możesz również podać wartość liczbową dla każdej wartości literału. Otwórz menu skrótów dla literału w wyliczeniu, wybierz opcję **właściwości**, a następnie wpisz liczbę w **wartość** pole **właściwości** okna.  
  
  Każdemu typowi nadaj unikatową nazwę.  
  
### <a name="getting-types-from-other-diagrams"></a>Pobieranie typów z innych diagramów  
 Można spowodować pojawienie się typów z innego diagramu w diagramie klas UML.  
  
 Diagram klas UML  
  
 Można wymusić pojawienie się klasy na więcej niż jednym diagramie klas UML. Po utworzeniu klasy na jednym diagramie, przeciągnij ją z **Eksploratora modelu UML** na inny diagram.  
  
 Jest to przydatne, jeśli każdy diagram ma się koncentrować na konkretnej grupie relacji.  
  
 Na przykład, na jednym diagramie można pokazać asocjację pomiędzy Zamówieniem posiłku i Menu restauracji, a na innym asocjację pomiędzy Zamówieniem posiłku a Zapłatą.  
  
 Diagramów składników  
  
 Jeżeli zdefiniowano interfejsy na składnikach w diagramie składników, można przeciągnąć interfejs z **Eksploratora modelu UML** na diagram klas. Na diagramie klasy można zdefiniować metody, które zawiera interfejs.  
  
 Zobacz [diagramy składników UML: Wytyczne dotyczące](../modeling/uml-component-diagrams-guidelines.md).  
  
 Diagram sekwencji UML  
  
 Można utworzyć klasy i interfejsy z linii życia w diagramie sekwencji, a następnie przeciągnij klasy z **Eksploratora modelu UML** do diagramu klas UML. Każda linia życia w diagramie sekwencji reprezentuje wystąpienie obiektu, składnika lub aktora.  
  
 Aby utworzyć klasę z linii życia, otwórz menu skrótów dla linii życia, a następnie wybierz **Utwórz klasę** lub **Utwórz interfejs**. Zobacz [diagramy sekwencji UML: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md).  
  
## <a name="AttributesAndOperations"></a> Atrybuty i operacje  
 Atrybut (4) jest nazwaną wartością, którą może mieć każde wystąpienie typu. Dostęp do atrybutu nie zmienia stanu wystąpienia.  
  
 Operacja (5) jest metodą albo funkcją, którą wystąpienia danego typu mogą wykonywać. Może zwracać wartość. Jeśli jej **isQuery** właściwość ma wartość true, to nie może zmienić stanu wystąpienia.  
  
 Aby dodać atrybut lub operację do typu, otwórz menu skrótów dla typu, wybierz polecenie **Dodaj**, a następnie wybierz **atrybut** lub **operacji**.  
  
 Aby wyświetlić jego właściwości, otwórz menu skrótów dla atrybutu lub operacji, a następnie wybierz **właściwości**. Właściwości są wyświetlane w **właściwości** okna.  
  
 Aby wyświetlić właściwości parametrów operacji, wybierz opcję <strong>[...]</strong> w **parametry** właściwości. Zostanie wyświetlone nowe okno dialogowe właściwości.  
  
 Aby uzyskać szczegółowe informacje dotyczące wszystkich właściwości, które można ustawiać, zobacz:  
  
- [Właściwości atrybutów w diagramach klas UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [Właściwości operacji w diagramach klas UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
### <a name="types-of-attributes-and-operations"></a>Typy atrybutów i operacji  
 Każdy *typu* atrybutu lub operacji i każdy typ parametru może być jedną z następujących czynności:  
  
- **(Brak)**  — Można zostawić typ nieokreślony w podpisie, pomijając poprzedzający dwukropek (`:`).  
  
- Jeden ze standardowych typów pierwotnych: **Wartość logiczna**, **całkowitą**, **ciąg**.  
  
- Typem zdefiniowanym w modelu.  
  
- Sparametryzowaną wartością typu szablonowego, zapisaną w postaci szablon\<parametr >. Zobacz [typy szablonów](#Templates).  
  
  Możesz także wpisać nazwę typu, który nie został jeszcze zdefiniowany w modelu. Nazwa będzie wyświetlana w obszarze **nieokreślonym** w Eksploratorze modelu UML.  
  
> [!NOTE]
> Jeśli klasa lub interfejs o tej nazwie zostaną następnie zdefiniowane w modelu, starsze atrybuty i operacje będą nadal odwoływały się do elementu o typie Nieokreślonym. Jeśli chcesz, ab odwoływały się do nowej klasy, dla każdego atrybutu lub operacji musisz zresetować typ, wybierając nową klasę z menu rozwijalnego.  
  
#### <a name="multiple-types"></a>Typy wielokrotne  
 Można ustawić liczebność dowolnego atrybutu, operacji lub typu parametru.  
  
 Dozwolone są następujące wartości:  
  
 `[1]`  
  
 Jedną z wartości danego typu. Domyślnie włączone.  
  
 `[0..1]`  
  
 **Wartość null** lub wartość danego typu.  
  
 `[*]`  
  
 Kolekcję dowolnej liczby wystąpień danego typu.  
  
 `[1..*]`  
  
 Kolekcję przynajmniej jednego wystąpienia danego typu.  
  
 `[n..m]`  
  
 Kolekcję między `n` i `m` wystąpień danego typu.  
  
 Jeśli liczebność jest większa niż 1, można też ustawić następujące właściwości:  
  
- **IsOrdered** — Jeśli to ustawienie ma wartość true, kolekcja ma zdefiniowaną kolejność.  
  
- **IsUnique** — Jeśli to ustawienie ma wartość true, istnieją zduplikowane wartości w kolekcji.  
  
### <a name="visibility"></a>Widoczność  
 *Widoczność* wskazuje, czy atrybut lub operację można uzyskać dostęp poza definicją klasy. Dozwolone są następujące wartości:  
  
 **Public**  
  
 **+**  
  
 Dostępny dla wszystkich typów.  
  
 **Private**  
  
 **-**  
  
 Dostępny tylko dla wewnętrznej definicji tego typu.  
  
 **Pakiet**  
  
 **~**  
  
 Dostępny tylko w ramach pakietu zawierającego ten typ oraz w dowolnych innych pakietach, które jawnie go importują. Zobacz [definiowanie przestrzeni nazw oraz pakietów](#Packages).  
  
 **Protected**  
  
 **#**  
  
 Dostępny tylko dla danego typu i typów, które po nim dziedziczą. Zobacz [dziedziczenia](#Inheritance).  
  
### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Ustawianie podpisu atrybutu lub operacji  
 Podpis atrybutu lub operacji jest kolekcją właściwości, zawierającą widoczność, nazwę, parametry (dla operacji) oraz typ.  
  
 Podpis można zapisać bezpośrednio na diagramie. Kliknij atrybut lub operację, aby ją zaznaczyć, a następnie kliknij ją ponownie.  
  
 Wpisz podpis w formie:  
  
```  
visibility attribute-name : Type  
```  
  
 \- lub —  
  
```  
visibility operation-name (parameter1 : Type1, ...) : Type  
```  
  
 Na przykład:  
  
```  
+ AddItem (item : MenuItem, quantity : Integer) : Boolean  
```  
  
 Można użyć krótkiej formy widoczności. Wartość domyślna to `+` (publicznego).  
  
 Każdy typ może być typem zdefiniowanym w modelu, typem standardowym, takim jak Integer albo String, lub nazwą nowego typu, który nie został jeszcze zdefiniowany.  
  
> [!NOTE]
> Jeśli na liście parametrów zostanie wpisana nazwa bez typu, wskazuje ona nazwę parametru, a nie jego typ. W tym przykładzie MenuItem oraz Integer stają się nazwami dwóch parametrów o nieokreślonych typach:  
>   
> `AddItem(MenuItem, Integer) /* parameter names, not types! */`  
  
 Aby ustawić liczebności typu w podpisie, wpisz liczebność w nawiasach kwadratowych po nazwie typu, na przykład:  
  
```  
+ AddItems (items : MenuItem [1..*])  
+ MenuContent : MenuItem [*]  
```  
  
 Jeżeli atrybut lub operacja są statyczne, ich nazwy będą wyświetlane w podpisie z podkreśleniem. Jeśli są abstrakcyjne, nazwa będzie napisana kursywą.  
  
 Jednak można ustawić tylko **Is Static** i **jest abstrakcyjny** właściwości w **właściwości** okna.  
  
#### <a name="full-signature"></a>Pełny podpis  
 Podczas edycji podpisu atrybutu lub operacji niektóre dodatkowe właściwości mogą być wyświetlane na końcu wiersza, po każdym z parametrów. Pojawiają się one w nawiasach {...}. Można edytować lub dodawać te właściwości. Na przykład:  
  
```  
+ AddItems (items: MenuItem [1..*] {unique, ordered})  
+ GetItems (filter: String) : MenuItem [*] {ordered, query}  
```  
  
 Właściwości są następujące:  
  
 `unique`  
  
 **Jest unikatowa**  
  
 Nie istnieją zduplikowane wartości w kolekcji. Dotyczy typów, których liczebność jest większa niż 1.  
  
 `ordered`  
  
 **Jest uporządkowany**  
  
 Kolekcja jest sekwencją. Jeśli ma wartość false, nie jest określony pierwszy element. Dotyczy typów, których liczebność jest większa niż 1.  
  
 `query`  
  
 **Zapytanie**  
  
 Operacja nie zmienia stanu jego wystąpienia. Dotyczy tylko operacji.  
  
 `/`  
  
 **Jest tworzony**  
  
 Atrybut jest obliczany na podstawie wartości innych atrybutów lub asocjacji.  
  
 Przed nazwą atrybutu jest wyświetlane "/". Na przykład:  
  
```  
/TotalPrice: Integer  
```  
  
 Zwykle pełny podpis pojawia się na diagramie tylko podczas jego edytowania. Po zakończeniu edycji dodatkowe właściwości są ukryte. Jeśli chcesz zobaczyć pełny podpis przez cały czas, otwórz menu skrótów dla typu, a następnie wybierz **Pokaż pełny podpis**.  
  
## <a name="Associations"></a> Rysowanie i używanie Asocjacji  
 Można użyć asocjacji do reprezentacji dowolnego rodzaju powiązania pomiędzy dwoma elementami, niezależnie od tego, jak połączenie jest zaimplementowane w oprogramowaniu. Na przykład można użyć asocjacji do reprezentacji wskaźnika w języku C#, relacji w bazie danych lub odwołania z jednej części pliku XML do innej. Może ona reprezentować asocjacje pomiędzy obiektami w świecie rzeczywistym, takimi jak ziemia i słońce. Asocjacja nie określa, w jaki sposób połączenie jest reprezentowane, określa jedynie, że taka informacja istnieje.  
  
### <a name="properties-of-an-association"></a>Właściwości asocjacji  
 Po utworzeniu asocjacji należy ustawić jej właściwości. Otwórz menu skrótów dla asocjacji, a następnie wybierz **właściwości**.  
  
 Oprócz właściwości asocjacji jako całości każdy *roli*, oznacza to, że każdy koniec asocjacji, ma pewne własne właściwości. Aby je wyświetlić, rozwiń węzeł **pierwsza rola** i **druga rola** właściwości.  
  
 Niektóre właściwości poszczególnych ról są bezpośrednio widoczne na diagramie. Są one następujące:  
  
- Nazwa roli. Pojawia się na odpowiednim końcu asocjacji na diagramie. Można ustawić na diagramie lub w **właściwości** okna.  
  
- **Element multiplicity**, które domyślnie używa **1**. Również pojawia się na diagramie, w pobliżu odpowiedniego końca asocjacji.  
  
- **Agregacja**. Pojawia się jako kształt rombu na jednym końcu łącznika. Można jej używać do wskazania, że wystąpienia w roli agregacji posiadają lub zawierają wystąpienia innych.  
  
- **Można nawigować**. Jeśli ma wartość true dla tylko jednej roli, pojawia się strzałka w kierunku, dla którego nawigacja jest możliwa. Służy to do wskazania możliwości nawigacji dla łączy i relacji bazodanowych w oprogramowaniu.  
  
  Aby uzyskać szczegółowe informacje o tych i innych właściwości, zobacz [właściwości skojarzeń w UML, diagramy klas](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
### <a name="navigability"></a>Możliwość nawigacji  
 Podczas rysowania asocjacji, ma ona strzałkę na jednym końcu, oznaczającą, że nawigacja jest możliwa w tym kierunku. Jest to przydatne, jeśli diagram klas reprezentuje klasy w oprogramowaniu, a asocjacje reprezentują wskaźniki lub odwołania. Ale kiedy diagram klas służy do reprezentacji obiektów i relacji lub koncepcji biznesowych, reprezentacja możliwości nawigacji jest mniej znacząca. W takim przypadku można preferować rysowanie asocjacji bez strzałek. Możesz to zrobić, ustawiając **jest Nawigowalna** właściwości na obu końcach asocjacji na wartość True. Aby to ułatwić, możesz pobrać przykładowy kod [modelowanie domeny UML](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4).  
  
### <a name="attributes-and-associations"></a>Atrybuty i asocjacje  
 Asocjacja jest obrazowym sposobem przedstawiania atrybutu. Na przykład, zamiast tworzenia klasy Restauracja z atrybutem typu Menu można narysować asocjację z Restauracji do Menu.  
  
 Każda nazwa atrybutu staje się nazwą roli. Pojawia się na przeciwległym końcu asocjacji względem typu, będącego właścicielem. Przyjrzyj się, na przykład `myMenu` na ilustracji.  
  
 Ogólnie rzecz biorąc, lepiej jest używać atrybutów tylko dla typów, które nie będą rysowane na diagramie, takich jak typy pierwotne.  
  
 ![Równoważne skojarzenie i atrybuty](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")  
  
## <a name="Inheritance"></a> Dziedziczenie  
 Użyj **dziedziczenia** narzędzia do tworzenia się następująco:  
  
- A *Generalizacja* relację między typem wyspecjalizowanym a typem ogólnym  
  
   \- lub —  
  
- A *realizacja* relacji między klasą a interfejsem, który implementuje.  
  
  Nie można tworzyć pętli w relacjach dziedziczenia.  
  
### <a name="generalization"></a>Generalizacja  
 Generalizacja oznacza, że typ wyspecjalizowany lub pochodny dziedziczy atrybuty, operacje i asocjacje typu ogólnego lub podstawowego.  
  
 Typ ogólny znajduje się na końcu relacji oznaczonym strzałką.  
  
 Operacje i atrybuty dziedziczone zazwyczaj nie są wyświetlane w typach wyspecjalizowanych. Można dodać odziedziczone operacje do listy operacji typu wyspecjalizowanego. Jest to przydatne, gdy chcesz zastąpić niektóre właściwości operacji w typie wyspecjalizowanym, lub jeśli chcesz wskazać, że powinno to zostać zrobione w kodzie implementującym.  
  
##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Aby zastąpić definicję operacji w typie wyspecjalizowanym  
  
1. Kliknij relację generalizacji.  
  
    Pojawi się wyróżniona, a tag Akcja zostanie wyświetlony w pobliżu.  
  
2. Kliknij tag akcji, a następnie kliknij przycisk **Zastąp operacje**.  
  
    **Zastąp operacje** pojawi się okno dialogowe.  
  
3. Wybierz operacje, które mają być wyświetlane w typie wyspecjalizowanym, a następnie kliknij przycisk **OK**.  
  
   Operacje, które wybrano, pojawią się w typie wyspecjalizowanym.  
  
### <a name="realization"></a>Realizacja  
 Realizacja oznacza, że klasa implementuje atrybuty i operacje, określone przez interfejs. Interfejs znajduje się na końcu łącznika ze strzałką.  
  
 Po utworzeniu łącznika realizacji operacje interfejsu są automatycznie replikowane w klasie, która go realizuje. Jeśli nowe operacje zostaną dodane do interfejsu, zostaną zreplikowane w realizujących go klasach.  
  
 Po utworzeniu relacji realizacji można przekonwertować ją do notacji typu lizak. Kliknij prawym przyciskiem myszy relację i wybierz polecenie **Pokaż jako lizak**.  
  
 Pozwala to na pokazanie interfejsów, które implementuje klasa, bez zaśmiecania diagramu klas łączami realizacji. Można również pokazać interfejs i realizujące go klasy na oddzielnym diagramie.  
  
 ![Realizacja pokazana z łącznikiem i lollipop](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")  
  
## <a name="Templates"></a> Typy szablonów  
 Można zdefiniować typ generyczny lub szablonu, który może być sparametryzowany poprzez inne typy lub wartości.  
  
 Na przykład można utworzyć generyczny Słownik sparametryzowany przez typy klucza i wartości:  
  
 ![Klasa szablonu z dwoma parametrami](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")  
  
#### <a name="to-create-a-template-type"></a>Aby utworzyć typ szablonu  
  
1. Utwórz klasę lub interfejs. Będzie to typ szablonu. Nadaj mu odpowiednią nazwę, na przykład `Dictionary`.  
  
2. Otwórz menu skrótów dla nowego typu, a następnie wybierz **właściwości**.  
  
3. W **właściwości** okna, kliknij przycisk **[...]**  w **parametry szablonu** pola.  
  
    **Edytor kolekcji parametrów szablonu** pojawi się okno dialogowe.  
  
4. Wybierz **Dodaj**.  
  
5. Na przykład ustaw właściwość nazwa na nazwę parametru swojego typu szablonu `Key`.  
  
6. Ustaw **rodzaj parametru**. Wartość domyślna to **klasy**.  
  
7. Jeśli chcesz, aby parametr ma akceptować tylko klasy pochodne konkretnej klasy bazowej, ustaw **wartość ograniczona** na wybraną klasę bazową.  
  
8. Dodaj tyle parametrów, ile potrzebujesz, następnie wybierz **OK**.  
  
9. Dodaj atrybuty i operacje do typu szablonu, tak jak w przypadku innych klas.  
  
     Można używać parametrów, których rodzaje to **klasy**, **interfejsu** lub **wyliczenie** w definicji atrybutów i operacji. Na przykład przy użyciu klas parametrów `Key` i `Value`, można zdefiniować następującą operację w `Dictionary`:  
  
     `Get(k : Key) : Value`  
  
     Można użyć parametru, którego rodzaj jest **całkowitą** jako granicę liczebności. Na przykład, całkowitoliczbowy parametr max może służyć do definiowania liczebności atrybutu jako `[0..max]`.  
  
   Po utworzeniu typów szablonu, można ich używać do definiowania powiązań szablonów:  
  
   ![Klasy związane z szablonu słownika](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")  
  
#### <a name="to-use-a-template-type"></a>Aby użyć typu szablonu  
  
1. Tworzenie nowego typu, na przykład `AddressTable`.  
  
2. Otwórz menu skrótów dla nowego typu, a następnie wybierz **właściwości**.  
  
3. W **powiązanie szablonów** właściwości, wybierz typ szablonu, na przykład `Dictionary`, z listy rozwijanej.  
  
4. Rozwiń **powiązanie szablonów** właściwości.  
  
     Dla każdego parametru typu szablonu pojawi się wiersz.  
  
5. Ustaw każdy parametr na odpowiednią wartość. Na przykład ustawić `Key` parametr do klasy o nazwie `Name`.  
  
## <a name="Packages"></a> Pakiety  
 Pakiety można przeglądać na diagramie klas UML. Pakiet jest kontenerem dla innych elementów modelu. Można utworzyć dowolny element wewnątrz pakietu. Na diagramie elementy wewnątrz pakietu będą się poruszały podczas przesuwania pakietu.  
  
 Można użyć formantu zwiń/rozwiń, aby ukryć lub pokazać zawartość pakietu.  
  
 Zobacz [Definiowanie pakietów i przestrzeni nazw](../modeling/define-packages-and-namespaces.md).  
  
## <a name="generating"></a> Generowanie kodu z diagramów klas UML  
 Aby rozpocząć implementację klas na diagramie klas UML, można wygenerować kod w języku C# lub dostosować szablony do generacji kodu. Aby rozpocząć generację kodu przy użyciu dostarczonych szablonów w języku C#:  
  
- Otwórz menu skrótów diagramu lub elementu, wybierz opcję **Generuj kod**, a następnie ustaw niezbędne właściwości.  
  
     Aby uzyskać więcej informacji na temat ustawiania tych właściwości i dostosowania dostarczonych szablonów, zobacz [generowanie kodu z diagramów klas UML](../modeling/generate-code-from-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)

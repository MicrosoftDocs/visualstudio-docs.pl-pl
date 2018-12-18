---
title: Tworzenie niestandardowych widoków obiektów macierzystych
description: Użyć struktury Natvis pozwala dostosować sposób, że program Visual Studio Wyświetla typy natywne w debugerze
ms.custom: ''
ms.date: 10/31/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 937692f11cbd642da823d6f7d13bcd90de59b388
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000864"
---
# <a name="create-custom-views-of-native-objects-in-the-debugger"></a>Tworzenie niestandardowych widoków obiektów macierzystych w debugerze

Visual Studio *Natvis* framework dostosowuje sposób, w typach natywnych są wyświetlane w oknach zmiennych debugera, takie jak **lokalne** i **Obejrzyj** systemu windows w **DataTips**. Wizualizacje Natvis sprawić, że typy, które możesz utworzyć bardziej widoczne podczas debugowania. 

Zastępuje Natvis *autoexp.dat —* pliku we wcześniejszych wersjach programu Visual Studio przy użyciu składni XML lepszą diagnostykę, przechowywanie wersji i obsłudze wielu plików.  

Natvis nie działa w przypadku:

- Projekty pulpitu Windows C++, przy użyciu **typ debugera** równa **mieszany** w obszarze **właściwości konfiguracji** > **debugowanie**. 
- [Debugowanie trybu mieszanego](how-to-debug-in-mixed-mode.md) dla aplikacji komputerowych Windows w trybie zgodności zarządzanego (**narzędzia** > **opcje** > **debugowania**  >  **Ogólne** > **Użyj zarządzanego trybu zgodności**).

## <a name="BKMK_Why_create_visualizations_"></a>Wizualizacje Natvis

Możesz użyć struktury Natvis do tworzenia reguł wizualizacji dla typów tworzonego, dzięki czemu deweloperzy mogą zobaczyć je łatwiej podczas debugowania.  

Na przykład poniższa ilustracja przedstawia zmienną typu [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) w oknie debugera bez zastosowania żadnych niestandardowych wizualizacji.  

![Wizualizacja domyślne pole tekstowe](../debugger/media/dbg_natvis_textbox_default.png "wizualizacji domyślnej wpisania TextBox")  

W wierszu wyróżnionym przedstawiono `Text` właściwość `TextBox` klasy. Złożona hierarchia klas sprawia, że trudnych do znalezienia tej właściwości. Debuger nie wie, jak interpretować typ niestandardowy ciągu, więc nie można zobaczyć ciągu przechowywanego wewnątrz pola tekstowego.  

Taki sam `TextBox` wygląda dużo prostsze w oknie zmiennej, po zastosowaniu reguły niestandardowego wizualizatora Natvis. Ważne elementy członkowskie klasy są wyświetlane razem i debuger pokazuje wartość ciągu bazowego typu ciąg niestandardowy.  

![Pole tekstowe danych za pomocą wizualizatora](../debugger/media/dbg_natvis_textbox_visualizer.png "pola tekstowego danych za pomocą wizualizatora")  

##  <a name="BKMK_Using_Natvis_files"></a>Użyj plikami .natvis dostępnymi w projektach C++  

Używa Natvis *.natvis* pliki do określania reguł wizualizacji. A *.natvis* plik jest plikiem XML z *.natvis* rozszerzenia. Schemat Natvis jest zdefiniowany w *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.  

Podstawowa struktura *.natvis* plik znajduje się co najmniej jeden `Type` elementów reprezentujących wpisach wizualizacji. W pełni kwalifikowaną nazwę każdego `Type` element jest określony w jej `Name` atrybutu.  

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
  <Type Name="MyNamespace::CFoo">  
    .  
    .  
  </Type>  

  <Type Name="...">  
    .  
    .  
  </Type>  
</AutoVisualizer>  
```  

Program Visual Studio zawiera pewne *.natvis* pliki *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* folderu. Te pliki mają reguły wizualizacji wielu powszechnie używanych typów i może służyć jako przykłady dotyczące pisania wizualizacji dla nowych typów.  

### <a name="add-a-natvis-file-to-a-c-project"></a>Dodaj plik .natvis do projektu w języku C++  

Możesz dodać *.natvis* plików do każdego projektu C++.  

**Aby dodać nowy *.natvis* pliku:**

1. Wybierz węzeł projektu C++ w **Eksploratora rozwiązań**i wybierz **projektu** > **Dodaj nowy element**, lub kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj**   >  **Nowy element**.
   
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Visual C++** > **narzędzie** > **plik wizualizacji debugera (.natvis)**. 
   
1. Nadaj plikowi nazwę i wybierz **Dodaj**.
   
   Nowy plik zostanie dodany do **Eksploratora rozwiązań**i zostanie otwarty w okienku dokument Visual Studio. 

Debuger programu Visual Studio ładuje *.natvis* plików w projektach C++ i automatycznie domyślnie obejmuje również je w *.pdb* plików, gdy projekt zostanie skompilowany. Jeśli debugujesz skompilowanych aplikacji, debuger ładuje *.natvis* plik wchodzącej w skład *.pdb* plików, nawet jeśli nie masz otwarty projekt. Jeśli nie chcesz *.natvis* plik dołączony *.pdb*, możesz je wykluczyć z wbudowanej *.pdb* pliku.

**Aby wykluczyć *.natvis* plik wchodzącej w skład *.pdb*:**

1. Wybierz *.natvis* w pliku **Eksploratora rozwiązań**i wybierz **właściwości** ikonę, lub kliknij prawym przyciskiem myszy plik i wybierz pozycję **właściwości**.
   
1. Listę rozwijaną strzałkę obok pozycji **wyłączone z kompilacji** i wybierz **tak**, a następnie wybierz pozycję **OK**.  

>[!NOTE]
>Do debugowania pliku wykonywalnego projektów, użyj elementy rozwiązania, aby dodać dowolne *.natvis* pliki, które nie znajdują się w *.pdb*, ponieważ brak projektów C++.  

>[!NOTE]
>Reguły Natvis ładowane z *.pdb* mają zastosowanie tylko do typów w modułach, *.pdb* odwołuje się do. Na przykład jeśli *Module1.pdb* zawiera wpis dla typu o nazwie Natvis `Test`, dotyczy to tylko `Test` klasy w *Module1.dll*. Jeśli inny moduł definiuje również klasę o nazwie `Test`, *Module1.pdb* wpis Natvis nie ma zastosowania do niego.  

### <a name="BKMK_natvis_location"></a> Lokalizacje plików Natvis  

Możesz dodać *.natvis* pliki do katalogu użytkownika lub w katalogu systemu, jeśli chcesz, aby zastosować do wielu projektów.  

*.Natvis* pliki są obliczane w następującej kolejności:  

1. Wszelkie *.natvis* pliki, które są osadzone w *.pdb* debugowania, chyba że istnieje plik o takiej samej nazwie w załadowanego projektu.  

1. Wszelkie *.natvis* pliki, które znajdują się w załadowanego projektu C++ lub rozwiązanie najwyższego poziomu. Ta grupa zawiera wszystkie załadowane projektów języka C++, w tym bibliotek klas, ale nie projektów w innych językach. 

1.  Katalog Natvis specyficzne dla użytkownika (na przykład *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).  

1.  Katalog Natvis systemowe (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Ten katalog ma *.natvis* pliki, które są instalowane z programem Visual Studio. Jeśli masz uprawnienia administratora, możesz dodawać pliki do tego katalogu.  

## <a name="modify-natvis-files-while-debugging"></a>Zmodyfikuj pliki .natvis podczas debugowania  

Możesz zmodyfikować *.natvis* pliku w środowisku IDE podczas debugowania jego projektu. Otwórz plik w tym samym wystąpieniu programu Visual Studio, w przypadku debugowania za pomocą, zmodyfikuj go i zapisz go. Po zapisaniu pliku **Obejrzyj** i **lokalne** windows update, aby odzwierciedlić zmiany. 

Można również dodawać lub usuwać *.natvis* pliki w rozwiązaniu, debugowania i programu Visual Studio dodaje lub usuwa odpowiednie wizualizacje.  

Nie można zaktualizować *.natvis* pliki, które są osadzone w *.pdb* pliki podczas debugowania.  

Jeśli zmodyfikujesz *.natvis* pliku poza programem Visual Studio, zmiany nie zostały wprowadzone automatycznie. Aby zaktualizować okien debugera, można ponownie oceń **.natvisreload** polecenia w pliku **Obejrzyj** okna. Następnie zmiany zaczęły obowiązywać bez ponownego uruchamiania sesji debugowania.  

Również użyć **.natvisreload** polecenie, aby uaktualnić *.natvis* pliku do nowszej wersji. Na przykład *.natvis* plików może zostać sprawdzone w formancie źródła i chcesz wczytać najnowsze zmiany tej osobie inne wprowadzone. 

##  <a name="BKMK_Expressions_and_formatting"></a> Wyrażenia i formatowanie  
Wizualizacje Natvis umożliwia określenie elementów danych do wyświetlenia wyrażeń języka C++. Oprócz ulepszeń i ograniczeń związanych z wyrażeniami języka C++ w debugerze, które są opisane w [operator kontekstu (C++)](../debugger/context-operator-cpp.md), należy pamiętać o następujących kwestiach:  

- Wyrażenia Natvis są oceniane w kontekście wizualizowanego obiektu, nie bieżącej ramki stosu. Na przykład `x` w Natvis wyrażenie odwołuje się do pola o nazwie **x** w wizualizowanym obiekcie, nie do zmiennej lokalnej o nazwie **x** w bieżącej funkcji. Nie masz dostępu do zmiennych lokalnych w wyrażenia Natvis, mimo że zmienne globalne są dostępne.  

- Wyrażenia Natvis nie zezwalają funkcji oceny lub uboczne. Wywołania funkcji i operatory przypisania są ignorowane. Ponieważ [funkcje wewnętrzne debugera](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) są efekt uboczny wolnej one mogą być swobodnie wywoływane z dowolnego wyrażenia Natvis, nawet jeśli inne wywołania funkcji są niedozwolone.  

- Aby sterować sposobem wyświetlania wyrażenia, można użyć innych specyfikatorów formatu opisanego w [Specyfikatory w języku C++ formatu](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Specyfikatory formatu są ignorowane, gdy wpis jest używana wewnętrznie przez Natvis, takich jak `Size` wyrażenia w [rozszerzenie elementów arrayitems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).  

## <a name="natvis-views"></a>Widoki Natvis  

Można zdefiniować różne widoki Natvis, aby wyświetlić typy w różny sposób. Na przykład poniżej przedstawiono wizualizację `std::vector` definiujący uproszczony widok o nazwie `simple`. `DisplayString` i `ArrayItems` elementy wyświetlane w widoku domyślnego i `simple` widoku, podczas gdy `[size]` i `[capacity]` elementów nie pokazuj w `simple` widoku. 

```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  


W **Obejrzyj** oknie, użyj **, widok** specyfikatora, aby określić alternatywny widok formatu. Widok prosty pojawia się jako **vec,view(simple)**:  

![Okno czujki z widokiem prostym](../debugger/media/watch-simpleview.png "okno czujki z widokiem prostym")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Błędów Natvis  

Gdy debuger napotka błędy we wpisie wizualizacji, ignoruje je. Jego Wyświetla typ w postaci pierwotnej, albo pobiera inną odpowiednią wizualizację. Diagnostyka Natvis można użyć, aby zrozumieć, dlaczego debuger ignorowany wpis wizualizacji, a także zobaczyć podstawowej składni i błędy analizy. 

**Aby włączyć Diagnostyka Natvis:**

- W obszarze **narzędzia** > **opcje** (lub **debugowania** > **opcje**) > **debugowania**  >  **Okno danych wyjściowych**ustaw **komunikaty diagnostyczne plików Natvis (tylko C++)** do **błąd**, **ostrzeżenie**, lub  **Pełne**, a następnie wybierz pozycję **OK**. 

Błędy są wyświetlane w **dane wyjściowe** okna.  

##  <a name="BKMK_Syntax_reference"></a> Dokumentacja składni Natvis  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer element  
`AutoVisualizer` Element jest węzeł główny *.natvis* plik i zawiera przestrzeń nazw `xmlns:` atrybutu. 

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

`AutoVisualizer` Element może mieć [typu](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer), i [CustomVisualizer](#BKMK_CustomVisualizer) elementów podrzędnych. 

###  <a name="BKMK_Type"></a> Typ elementu  

Podstawowy `Type` wygląda następująco:  

```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  

 `Type` Element określa:  

1. Jaki typ wizualizacji powinny być używane ( `Name` atrybutu).  
   
2. Jak powinna wyglądać wartość obiektu tego typu ( `DisplayString` elementu).  
   
3. Elementy członkowskie tego typu powinny wyglądać po użytkownik rozwija typu w oknie zmiennych ( `Expand` węzła).  
   
#### <a name="templated-classes"></a>Klasy oparte na szablonach
`Name` Atrybutu `Type` akceptuje gwiazdkę `*` jako symbolu wieloznacznego, który może służyć do nazw klas opartych na szablonach.  

W poniższym przykładzie jest używany tej samej wizualizacji, czy obiekt jest `CAtlArray<int>` lub `CAtlArray<float>`. Jeśli istnieje określony wpis wizualizacji dla `CAtlArray<float>`, a następnie pierwszeństwo przed ogólnym wpisem.  

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

Można odwoływać się do parametrów szablonu we wpisie wizualizacji przy użyciu makr $t1, $t2 i tak dalej. Aby znaleźć przykłady tych makr, zobacz *.natvis* pliki dostarczane z programem Visual Studio.  

####  <a name="BKMK_Visualizer_type_matching"></a> Dopasowanie typu wizualizatora  
Jeśli wpis wizualizacji nie powiedzie się sprawdzić poprawność, jest używana następna dostępna wizualizacja.  

#### <a name="inheritable-attribute"></a>Atrybut dziedziczne  
Opcjonalny `Inheritable` atrybut określa, czy wizualizacja dotyczy tylko typu podstawowego, do typu podstawowego, a wszystkie typy pochodne. Wartość domyślna `Inheritable` jest `true`.  

W poniższym przykładzie wizualizacja dotyczy tylko `BaseClass` typu:  

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

#### <a name="priority-attribute"></a>Atrybut Priorytet  

Opcjonalny `Priority` atrybut określa kolejność, w której można używać alternatywnego definicje, jeśli definicja nie powiedzie się, można przeanalizować. Możliwe wartości `Priority` są: `Low`, `MediumLow`,`Medium`, `MediumHigh`, i `High`. Wartość domyślna to `Medium`. `Priority` Atrybutu tylko odróżnia na priorytety, w tym samym *.natvis* pliku.  

Poniższy przykład analizuje pierwszy wpis odpowiadający 2015 STL. W przypadku niepowodzenia można przeanalizować używa alternatywne wpisu dla wersji 2013 STL:  

```xml
<!-- VC 2013 -->  
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">  
     <DisplayString>{_Callee}</DisplayString>  
    <Expand>  
        <ExpandedItem>_Callee</ExpandedItem>  
    </Expand>  
</Type>  

<!-- VC 2015 -->  
<Type Name="std::reference_wrapper&lt;*&gt;">  
    <DisplayString>{*_Ptr}</DisplayString>  
    <Expand>  
        <Item Name="[ptr]">_Ptr</Item>  
    </Expand>  
</Type>  
```  

### <a name="optional-attribute"></a>Opcjonalny atrybut  
Możesz umieścić `Optional` atrybutu w każdym węźle. Jeśli podwyrażenia wewnątrz węzła opcjonalne nie można przeanalizować, debuger ignoruje ten węzeł, ale ma zastosowanie w pozostałej części `Type` reguły. W następujący typ `[State]` jest Nieopcjonalne, ale `[Exception]` jest opcjonalne.  Jeśli `MyNamespace::MyClass` zawiera pole o nazwie _`M_exceptionHolder`, zarówno `[State]` węzła i `[Exception]` węzła pojawia się, ale jeśli istnieje nie `_M_exceptionHolder` pole tylko `[State]` węzeł jest dostępny.

```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Atrybut warunek  

Opcjonalny `Condition` atrybut jest dostępny dla wielu elementów wizualizacji i określa, kiedy należy używać reguły wizualizacji. Jeśli wyrażenie wewnątrz atrybutu warunku jest rozpoznawany jako `false`, reguła wizualizacji nie ma zastosowania. Jeśli daje w wyniku `true`, lub nie `Condition` atrybutu, dotyczy wizualizacji. Ten atrybut służy do logiki if else we wpisach wizualizacji. 

Na przykład poniższa wizualizacja ma dwa `DisplayString` elementy dla typu inteligentnego wskaźnika. Gdy `_Myptr` elementu członkowskiego jest pusta, warunek pierwszego `DisplayString` element jest rozpoznawany jako `true`, dlatego w tym formularzu są wyświetlane. Podczas `_Myptr` elementu członkowskiego nie jest pusty, warunek jest `false`, a druga `DisplayString` element Wyświetla.  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

### <a name="includeview-and-excludeview-attributes"></a>Atrybuty IncludeView i ExcludeView  

`IncludeView` i `ExcludeView` atrybuty określają elementów do wyświetlenia lub wyświetlaj w określonych widoków. Na przykład w następujących specyfikacji Natvis `std::vector`, `simple` widok nie zawiera `[size]` i `[capacity]` elementów.

```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  

Możesz użyć `IncludeView` i `ExcludeView` atrybuty dla typów i na poszczególnych elementów członkowskich.  

###  <a name="BKMK_Versioning"></a> Wersja elementu  
`Version` Element zakresów wpis wizualizacji do określonego modułu i wersji. `Version` Element pomaga uniknąć konfliktów nazw, zmniejsza przypadkowego niezgodności i umożliwia różne wizualizacje dla wersji innego typu.  

Jeśli wspólnego pliku nagłówka, który jest używany przez różne moduły definiuje typ, numerów wersji wizualizacji jest wyświetlana tylko wtedy, gdy typ jest w wersji określonego modułu.  

W poniższym przykładzie wizualizacja dotyczy to tylko `DirectUI::Border` typ odnaleziony w `Windows.UI.Xaml.dll` z wersji 1.0 i 1.5. 

```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

###  <a name="BKMK_DisplayString"></a> Klasa DisplayString — element 
`DisplayString` Element określa ciąg wyświetlany jako wartość zmiennej. Akceptuje dowolny łańcuchów mieszanych wyrażeń. Wszystko wewnątrz nawiasów klamrowych jest interpretowane jako wyrażenie. Na przykład następujące `DisplayString` wpis:  

```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
```  

Oznacza, że tego zmiennych typu `CPoint` wyświetlane tak jak na tej ilustracji:  

 ![Użyj elementu klasy DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Użyj elementu klasy DisplayString")  

W `DisplayString` wyrażenie `x` i `y`, które są członkami `CPoint`, są umieszczone w nawiasach klamrowych, dlatego ich wartości są obliczane. W przykładzie pokazano, jak można udosłownić nawias klamrowy za pomocą podwójnego nawiasu klamrowego ( `{{` lub `}}` ).  

> [!NOTE]
> `DisplayString` Element jest jedynym elementem, który akceptuje dowolne ciągi i składnię nawiasu klamrowego. Wszystkie inne elementy wizualizacji akceptują tylko wyrażenia, które można ocenić debugera.  

###  <a name="BKMK_StringView"></a> StringView element 

`StringView` Element definiuje wartość, która jest debugera można wysyłać do wbudowanego wizualizatora tekstu. Na przykład, biorąc pod uwagę następującą wizualizację dla `ATL::CStringT` typu:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  

`CStringT` Obiekt wyświetla w oknie zmiennych, takich jak w tym przykładzie:   

![Element klasy CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "element klasy CStringT DisplayString")  

Dodawanie `StringView` element informuje debuger umożliwia wyświetlanie wartości jako wizualizację tekstu.  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

Podczas debugowania, użytkownik może wybrać ikonę szkła powiększającego obok zmiennej, a następnie wybierz **Wizualizator tekstu** do wyświetlenia ciągu, **m_pszData** wskazuje.  

 ![CStringT danych za pomocą wizualizatora StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT danych za pomocą wizualizatora StringView")  

Wyrażenie `{m_pszData,su}` specyfikator formatu języka C++ **su**, aby wyświetlić wartość jako ciąg Unicode. Aby uzyskać więcej informacji, zobacz [Specyfikatory w języku C++ formatu](../debugger/format-specifiers-in-cpp.md).  

###  <a name="BKMK_Expand"></a> Rozwiń element 

Opcjonalny `Expand` węzła dostosowuje elementów podrzędnych typu zwizualizowanego, po rozwinięciu typu w oknie zmiennej. `Expand` Węzła akceptuje listę węzłów podrzędnych, które definiują elementy podrzędne.  

- Jeśli `Expand` węzeł nie jest określony we wpisie wizualizacji, elementy podrzędne Użyj domyślnych reguł rozszerzenia.  
  
- Jeśli `Expand` węzeł został określony bez węzłów podrzędnych pod nim, typu nie można rozwijać w oknach debugera.  

####  <a name="BKMK_Item_expansion"></a> Rozszerzenie elementu  

 `Item` Element jest najbardziej podstawowa i wspólne elementem w `Expand` węzła. `Item` definiuje jeden typ elementów podrzędnych. Na przykład `CRect` klasy z polami `top`, `left`, `right`, i `bottom` ma następującym wpisem wizualizacji:  

```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
```  

W oknie debugera `CRect` typu wygląda następująco:  

![CRect, za pomocą rozszerzenie elementu elementu](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect za pomocą rozszerzenie elementu elementu")  

Debuger ocenia wyrażenia określone w `Width` i `Height` elementy i przedstawiono wartości w **wartość** kolumny w oknie zmiennej. 

Debuger automatycznie tworzy **[widok nieprzetworzony]** węzła dla każdego rozszerzenia niestandardowe. Wyświetla na poprzednim zrzucie ekranu **[widok nieprzetworzony]** rozwinięty węzeł, aby pokazać, jak surowy widok domyślny obiektu różni się od jego wizualizacji Natvis. Domyślne rozszerzenie tworzy poddrzewo klasy podstawowej i wyświetla listę wszystkich danych członków klasy podstawowej jako elementy podrzędne.  

> [!NOTE]
> Jeśli wyrażenie elementu wskazuje typ złożony, **elementu** sam węzeł jest rozwijany.  

####  <a name="BKMK_ArrayItems_expansion"></a> Rozszerzenie elementów arrayitems  
Użyj `ArrayItems` węzeł, aby debuger programu Visual Studio interpretował typ jako tablicę i wyświetlał jego poszczególne elementy. Wizualizacja dla `std::vector` jest dobrym przykładem:  

```xml
<Type Name="std::vector&lt;*&gt;">  
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mylast - _Myfirst</Item>  
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>  
    <ArrayItems>  
      <Size>_Mylast - _Myfirst</Size>  
      <ValuePointer>_Myfirst</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  

A `std::vector` pokazuje poszczególne elementy po rozwinięciu w oknie zmiennej:  

![za pomocą elementów arrayitems STD::Vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector przy użyciu elementów arrayitems")  

`ArrayItems` Węzeł musi mieć:  

- A `Size` wyrażenia (który musi być liczbą całkowitą) dla debugera, pozwalające zrozumieć długość tablicy.  
- A `ValuePointer` wyrażenia, który wskazuje na pierwszy element (który musi być wskaźnikiem typu elementu, który nie jest `void*`).  

Wartość domyślna dolnej granicy tablicy to 0. Aby zastąpić wartość, użyj `LowerBound` elementu. *.Natvis* pliki, które są dostarczane z Visual Studio mają przykłady.  

>[!NOTE]
>Możesz użyć `[]` operatora, na przykład `vector[i]`, przy użyciu dowolnej wizualizacji Jednowymiarowa tablica, która używa `ArrayItems`, nawet jeśli samego typu (na przykład `CATLArray`) nie zezwala na tego operatora.  

Można również określić tablic wielowymiarowych. W takim przypadku debuger wymaga nieco więcej informacji do poprawnego wyświetlania elementów podrzędnych:  

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Direction>Forward</Direction>  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  

- `Direction` Określa, czy tablica jest w porządku główna wierszy lub kolumn. 
- `Rank` Określa rangę tablicy. 
- `Size` Element akceptuje niejawny `$i` parametr, który zastępuje indeksem wymiaru w celu znalezienia długości tablicy w tym wymiarze. W poprzednim przykładzie wyrażenie `_M_extent.M_base[0]` powinno dawać długość 0 wymiaru `_M_extent._M_base[1]` 1 i tak dalej.  

Oto jak dwuwymiarowy `Concurrency::array` obiektu wygląda w oknie debugera:  

![Dwuwymiarową tablicę z elementów arrayitems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "dwuwymiarową tablicę z elementów arrayitems")  

####  <a name="BKMK_IndexListItems_expansion"></a> Rozszerzenie indexlistitems  

Możesz użyć `ArrayItems` rozszerzenia tylko wtedy, gdy elementy tablicy są ułożone w sposób ciągły w pamięci. Debuger pobiera następny element po prostu przez zwiększenie swojego wskaźnika. Jeśli zachodzi potrzeba manipulowania indeksem w węźle wartości, użyj `IndexListItems` węzłów. Poniżej przedstawiono wizualizację z `IndexListItems` węzła:  

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">  
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_M_vector._M_index</Item>  
    <IndexListItems>  
      <Size>_M_vector._M_index</Size>  
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>  
    </IndexListItems>  
  </Expand>  
</Type>  
```  

Jedyną różnicą między `ArrayItems` i `IndexListItems` jest `ValueNode`, która oczekuje pełnego wyrażenia dla elementu i<sup>th</sup> z niejawnym `$i` parametru.  

>[!NOTE]
>Możesz użyć `[]` operatora, na przykład `vector[i]`, przy użyciu dowolnej wizualizacji Jednowymiarowa tablica, która używa `IndexListItems`, nawet jeśli samego typu (na przykład `CATLArray`) nie zezwala na tego operatora.  

####  <a name="BKMK_LinkedListItems_expansion"></a> Rozszerzenie linkedlistitems  

Jeśli typ wizualizowany reprezentuje listę połączoną, debuger może wyświetlić jego elementy podrzędne przy użyciu `LinkedListItems` węzła. Poniższa wizualizacja dla `CAtlList` typu używa `LinkedListItems`:  

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">  
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
  <Expand>  
    <Item Name="Count">m_nElements</Item>  
    <LinkedListItems>  
      <Size>m_nElements</Size>  
      <HeadPointer>m_pHead</HeadPointer>  
      <NextPointer>m_pNext</NextPointer>  
      <ValueNode>m_element</ValueNode>  
    </LinkedListItems>  
  </Expand>  
</Type>  
```  

`Size` Element odwołuje się do długości listy. `HeadPointer` wskazuje na pierwszy element `NextPointer` odwołuje się do następnego elementu i `ValueNode` odnosi się do wartości elementu.  

Ocenia debuger `NextPointer` i `ValueNode` wyrażenia w kontekście `LinkedListItems` elementu węzła, nie typu listy nadrzędnej. W powyższym przykładzie `CAtlList` ma `CNode` klasa (znalezione w `atlcoll.h`) czyli węzeł listy łączonej. `m_pNext` i `m_element` pól tego `CNode` klasy, nie `CAtlList` klasy.  

`ValueNode` może być puste lub użyj `this` do odwoływania się do `LinkedListItems` sam węzeł.  

#### <a name="customlistitems-expansion"></a>Rozszerzenie CustomListItems  
`CustomListItems` Rozszerzenia umożliwia pisanie logiki niestandardowej do przechodzenia przez strukturę danych, takich jak tablica skrótów. Użyj `CustomListItems` wizualizacja struktury danych, których można używać wyrażeń języka C++ dla wszystko, czego potrzebujesz do oceny, ale jeszcze nie mieści się w pleśnią dla `ArrayItems`, `IndexListItems`, lub `LinkedListItems`.  

Następujące Wizualizator dla `CAtlMap` znajduje się przykład doskonałą gdzie `CustomListItems` jest odpowiednia.  

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">  
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>  
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>  
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
    <Expand>  
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">  
        <Variable Name="iBucket" InitialValue="-1" />  
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />  
        <Variable Name="iBucketIncrement" InitialValue="-1" />  

        <Size>m_nElements</Size>  
        <Exec>pBucket = nullptr</Exec>  
        <Loop>  
          <If Condition="pBucket == nullptr">  
            <Exec>iBucket++</Exec>  
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>  
            <Break Condition="iBucketIncrement == -1" />  
            <Exec>iBucket += iBucketIncrement</Exec>  
            <Exec>pBucket = m_ppBins[iBucket]</Exec>  
          </If>  
          <Item>pBucket,na</Item>  
          <Exec>pBucket = pBucket->m_pNext</Exec>  
        </Loop>  
      </CustomListItems>  
    </Expand>  
</Type>  
```  

Możesz użyć `Exec` na wykonanie kodu wewnątrz `CustomListItems` rozszerzenia, używając zmiennych i obiektów zdefiniowanych w rozwoju. Można użyć operatorów logicznych, operatory arytmetyczne i operatory przypisania z `Exec`. Nie można użyć `Exec` można obliczyć wartości funkcji.

`CustomListItems` obsługuje następujące funkcje wewnętrzne:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

####  <a name="BKMK_TreeItems_expansion"></a> Rozszerzenie elementów treeitems  
 Jeśli typ wizualizowany reprezentuje drzewo, debuger może przejść przez drzewo i wyświetlić jego elementy podrzędne przy użyciu `TreeItems` węzła. Oto wizualizacja dla `std::map` typu przy użyciu `TreeItems` węzła:  

```xml
<Type Name="std::map&lt;*&gt;">  
  <DisplayString>{{size = {_Mysize}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mysize</Item>  
    <Item Name="[comp]">comp</Item>  
    <TreeItems>  
      <Size>_Mysize</Size>  
      <HeadPointer>_Myhead->_Parent</HeadPointer>  
      <LeftPointer>_Left</LeftPointer>  
      <RightPointer>_Right</RightPointer>  
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>  
    </TreeItems>  
  </Expand>  
</Type>  
```  

Składnia jest podobne do `LinkedListItems` węzła. `LeftPointer`, `RightPointer`, i `ValueNode` są oceniane w kontekście klasy węzła drzewa. `ValueNode` może być puste lub użyj `this` do odwoływania się do `TreeItems` sam węzeł.  

####  <a name="BKMK_ExpandedItem_expansion"></a> Rozszerzenie expandeditem  
 `ExpandedItem` Element generuje zagregowanego widoku podrzędnego, wyświetlając właściwości podstawowej klasy lub elementów członkowskich danych tak, jakby były elementami podrzędnymi typu zwizualizowanego. Oblicza określone wyrażenie debugera i dołącza węzły podrzędne wyniku do listy podrzędnej typu zwizualizowanego. 

Na przykład typ inteligentnego wskaźnika `auto_ptr<vector<int>>` zwykle wyświetla się jako:  

 ![automatyczne&#95;ptr&#60;wektor&#60;int&#62; &#62; domyślne rozszerzenie](../debugger/media/dbg_natvis_expand_expandeditem_default.png "domyślne rozszerzenie")  

 Aby wyświetlić wartości wektora, musisz przejść do szczegółów dwa poziomy głębiej w oknie zmiennych, przechodzi przez `_Myptr` elementu członkowskiego. Dodając `ExpandedItem` elementu, można wyeliminować `_Myptr` zmiennej z hierarchii i bezpośrednio wyświetlać elementy wektorów:  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

 ![automatyczne&#95;ptr&#60;wektor&#60;int&#62; &#62; rozszerzenie expandeditem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "rozszerzenie expandeditem")  

Poniższy przykład pokazuje sposób agregacji właściwości z klasy podstawowej w klasie pochodnej. Załóżmy, że `CPanel` klasa pochodzi od `CFrameworkElement`. Zamiast powtarzania właściwości, które pochodzą od podstawy `CFrameworkElement` klasy `ExpandedItem` wizualizacji węzeł dołącza tych właściwości podrzędnej listy `CPanel` klasy. 

```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  

**Nd** specyfikatora formatu, który wyłącza dopasowywanie dla klasy pochodnej wizualizacja, w tym miejscu jest konieczne. W przeciwnym wypadku wyrażenie `*(CFrameworkElement*)this` spowodowałoby `CPanel` wizualizację można zastosować ponownie, ponieważ wizualizacji domyślnej wpisania typu reguł dopasowania uważają to za najbardziej odpowiednie. Użyj **nd** specyfikatora w celu poinstruowania debugerowi użycie wizualizacji klasy podstawowej lub rozszerzenia domyślnej, jeśli klasa bazowa nie ma żadnych wizualizacji formatu.  

####  <a name="BKMK_Synthetic_Item_expansion"></a> Rozszerzenie elementu syntetycznego  
 Gdy `ExpandedItem` element zapewnia bardziej płaski widok danych poprzez wyeliminowanie hierarchii, `Synthetic` węzeł ma odwrotne. Umożliwia ona tworzenie elementu podrzędnego sztuczne, który nie jest wynikiem wyrażenia. Sztuczne element może mieć elementów podrzędnych swój własny. W poniższym przykładzie, wizualizacji dla `Concurrency::array` typu używa `Synthetic` węzeł, aby wyświetlić komunikat diagnostyczny dla użytkownika:  

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">  
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>  
    </Synthetic>  
  </Expand>  
</Type>  
```  

 ![CONCURRENCY::Array przy użyciu elementu syntetyczne rozszerzenie](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array przy użyciu syntetycznych element rozszerzenia")  

###  <a name="BKMK_HResult"></a> HResult element 
 `HResult` Element umożliwia dostosowanie informacji wyświetlanych dla **HRESULT** w oknach debugera. `HRValue` Element musi zawierać 32-bitową wartość **HRESULT** który ma zostać dostosowana. `HRDescription` Element zawiera informacje, które mają być wyświetlane w oknie debugera.  

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> UIVisualizer element 
Element `UIVisualizer` elementu rejestruje wtyczkę wizualizatora graficznego z debugerem. Wizualizatora graficznego tworzy okno dialogowe lub innego interfejsu, który pokazuje zmiennej lub obiektu w sposób zgodny z jego typu danych. Wtyczka wizualizatora musi zostać utworzona jako [pakietu VSPackage](../extensibility/internals/vspackages.md)i musi uwidaczniać usługę, którą może wykorzystać debugera. *.Natvis* plik zawiera informacje rejestracyjne dodatku typu plug-in, takie jak jego nazwa, identyfikator GUID narażonych usługi oraz typy, może ona wizualizować.  

Poniżej przedstawiono przykładowy element UIVisualizer:  

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="1" MenuName="Vector Visualizer"/>  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="2" MenuName="List Visualizer"/>  
.  
.  
</AutoVisualizer>  
```  

- A `ServiceId`  -  `Id` pary atrybut identyfikuje `UIVisualizer`. `ServiceId` Jest identyfikatorem GUID usługi wizualizatora ujawnia pakietu. `Id` jest unikatowy identyfikator, który odróżnia wizualizatorów, jeśli usługa oferuje więcej niż jeden. W powyższym przykładzie ten sam Wizualizator dostarcza dwóch wizualiztorów.  
  
- `MenuName` Atrybut definiuje nazwę wizualizatora, aby wyświetlić listy rozwijanej obok ikony lupy w debugerze. Na przykład:  

  ![Menu skrótów menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer menu skrót menu")  

Każdy typ zdefiniowany w *.natvis* pliku musi wyraźnie określać wizualizatory interfejsu użytkownika, wszystkie, które mogą go wyświetlać. Debuger dopasowuje odwołania do wizualizatorów we wpisach typów z zarejestrowanymi wizualizatorami. Na przykład, następujący wpis dla typu `std::vector` odwołania `UIVisualizer` w poprzednim przykładzie.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Możesz zobaczyć przykład `UIVisualizer` w [Obejrzyj obraz](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) rozszerzenia używane do wyświetlania mapy bitowe w pamięci. 

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer element  
 `CustomVisualizer` jest punktem rozszerzalności, która określa rozszerzenie VSIX, który można zapisać do kontrolowania wizualizacje w programie Visual Studio code. Aby uzyskać więcej informacji na temat pisania rozszerzenia VSIX, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md). 

Jest znacznie więcej pracy można zapisać niestandardowego wizualizatora niż definicji XML Natvis, ale możesz z ograniczenia, o czym Natvis ani nie obsługuje. Wizualizatory niestandardowe mają dostęp do pełnego zestawu rozszerzalności debugera interfejsów API, które można zbadać i modyfikowanie obiektu debugowanego procesu lub komunikowania się z innymi częściami programu Visual Studio.  

 Możesz użyć `Condition`, `IncludeView`, i `ExcludeView` atrybuty na `CustomVisualizer` elementów.

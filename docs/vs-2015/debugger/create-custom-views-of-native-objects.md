---
title: Tworzenie niestandardowych widoków obiektów macierzystych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- natvis
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff03e5e07c07b4516009c7606f8a8ea183c57298
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732497"
---
# <a name="create-custom-views-of-native-objects"></a>Tworzenie niestandardowych widoków obiektów macierzystych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Struktura Natvis usługi Visual Studio pozwala dostosować sposób, w programie Visual Studio Wyświetla typy natywne w oknach zmiennych debugera (na przykład **Obejrzyj**, **lokalne**, i **porady dotyczące danych** systemu windows.  

 Zastępuje Natvis **autoexp.dat —** pliku, który został użyty we wcześniejszych wersjach programu Visual Studio i oferuje składni XML lepszą diagnostykę, przechowywanie wersji i obsługę wielu plików.  

> [!NOTE]
>  Nie można użyć struktury Natvis do wizualizacji po:  
> 
> - Debugowania projektu pulpitu Windows C++ o typie debugera **mieszane**.  
>   -   Robią w aplikacji pulpitu Windows w trybie zgodności zarządzanego debugowania w trybie mieszanym (**narzędzia / Opcje / Debugowanie / ogólne / Użyj trybu zgodności zarządzanej**).  
>   -   Debugowania w aplikacji pulpitu Windows w trybie macierzystym zgodności (**narzędzia / Opcje / Debugowanie / ogólne / Użyj trybu zgodności natywnych**).  

##  <a name="BKMK_Why_create_visualizations_"></a> Dlaczego tworzenie wizualizacji Natvis?  
 Można użyć struktury Natvis do tworzenia reguł wizualizacji dla typów, że utworzono, dzięki czemu deweloperzy mogą zobaczyć je łatwo podczas debugowania.  

 Na przykład poniższy obraz przedstawia zmienną typu [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) wyświetlonej w debugerze bez zastosowania żadnych niestandardowych wizualizacji.  

 ![Wizualizacja domyślne pole tekstowe](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 W wierszu wyróżnionym przedstawiono `Text` właściwość `TextBox` klasy. Złożona hierarchia klas sprawia, że trudno znaleźć tę wartość; Ponadto debuger nie wie, jak interpretować typ niestandardowy ciągu używany przez obiekt, więc nie można zobaczyć ciągu przechowywanego wewnątrz pola tekstowego.  

 Taki sam `TextBox` wygląda dużo prostsze n oknie zmiennej, po zastosowaniu reguł niestandardowych wizualizacji. Ważne elementy członkowskie klasy można wyświetlać razem i debuger pokazuje wartość ciągu bazowego typu ciąg niestandardowy.  

 ![Pole tekstowe danych za pomocą wizualizatora](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

##  <a name="BKMK_Using_Natvis_files"></a> Używanie plików Natvis  
 pliki natvis są plikami XML z rozszerzeniem .natvis. Schemat jest zdefiniowany w **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  

 Podstawowa struktura pliku .natvis jest co najmniej jeden `Type` elementów, gdzie każdy `Type` element reprezentuje wizualizację wpisu dla typu, w których w pełni kwalifikowana nazwa jest określona w `Name` atrybutu.  

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

 Program Visual Studio udostępnia kilkoma plikami .natvis dostępnymi w **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** folderu. Te pliki zawierają reguły wizualizacji wielu powszechnie używanych typów i mogą zostać wykorzystane jako przykłady podczas pisania wizualizacji dla nowych typów.  

## <a name="adding-natvis-files-to-your-projects"></a>Dodawanie plików .natvis do swoich projektów  
 Możesz dodać pliki natvis do każdego projektu C++.  

 Aby dodać nowy plik .natvis z otwartym projekcie C++, wybierz węzeł projektu w **Eksploratora rozwiązań**i kliknij przycisk **Add / nowy element / Visual C++ / narzędzia / plik wizualizacji (natvis) debugera**. Debuger będzie ładował plików Natvis automatycznie z projektów w języku C++. Domyślnie pliki Natvis do projektu są również wstawione do pliku .pdb, skompilowany na podstawie projektu. Oznacza to, że Jeśli debugujesz kod binarny stworzonej przez ten projekt, debuger ładuje plików Natvis z .pdb, nawet jeśli nie masz otwarty projekt. Jeśli chcesz, aby plik .natvis, które mają zostać uwzględnione w .pdb, kliknij prawym przyciskiem myszy plik .natvis w **Eksploratora rozwiązań**i w **właściwości konfiguracji** zestaw okna **wyłączone z kompilacji**  do **tak**.  

 Zaleca się, że edytować pliki Natvis przy użyciu programu Visual Studio wszystkie wprowadzone podczas debugowania zaczęły obowiązywać automatycznie po zapisaniu pliku. Możesz także uzyskać lepszą obsługę edycji z technologii IntelliSense.  

 Pliki Natvis, które są ładowane z .pdb mają zastosowanie tylko do typów w module, do którego odwołuje się pliku pdb. Na przykład, jeśli Module1.pdb definiuje wpis dla typu o nazwie `Test`, ten wpis, stosowane tylko do **testu** klasy w Module1.dll. Jeśli inny moduł definiuje również klasę o nazwie **testu**, wpis natvis Module1.pdb firmy nie ma zastosowania do niego.  

##  <a name="BKMK_natvis_location"></a> Wdrażanie plików .natvis  
 Jeśli plik .natvis ma zastosowanie tylko do typów, które tworzysz w projekcie programu Visual Studio, nie trzeba wykonywać żadnych czynności; .natvis znajduje się w .pdb. Jednak można dodać pliki natvis do swojego katalogu użytkownika lub w katalogu systemu, jeśli chcesz, aby zastosować do wielu projektów.  

 Kolejność, w której .natvis pliki są oceniane następująco:  

1.  pliki natvis osadzone w .pdb, który debugujesz (chyba że istnieje plik o takiej samej nazwie w załadowanego projektu)  

2.  pliki .natvis, które są częścią załadowanych projektów w języku C++ lub element najwyższego poziomu rozwiązania. Obejmuje to wszystkie załadowane projektów języka C++, w tym bibliotek klas, ale nie zawiera projekty innych języków (np. nie można załadować pliku .natvis z projektu języka C#). Dla pliku wykonywalnego projektów należy użyć elementy rozwiązania do obsługi wszystkie pliki .natvis, które nie są już obecne w .pdb, ponieważ brak projektów C++.  

3.  Katalog natvis specyficzne dla użytkownika (**%USERPROFILE%\My 2015\Visualizers Documents\Visual Studio**  

4.  Katalog Natvis systemowe (**%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). Jest to, gdzie są kopiowane pliki .natvis, które są instalowane z programem Visual Studio. Jeśli masz uprawnienia administratora, można dodać do tego katalogu, jak również inne pliki.  

## <a name="modifying-natvis-files-while-debugging"></a>Modyfikowanie plikami .natvis dostępnymi podczas debugowania  
 Podczas debugowania projektu, w której jest dołączony, można zmodyfikować pliku .natvis w środowisku IDE. Otwórz plik w środowisku IDE (przy użyciu tego samego wystąpienia programu Visual Studio, na którym wykonujesz debugowanie za pomocą), zmodyfikuj go i zapisz go. Po zapisaniu pliku **Obejrzyj** i **lokalne** system windows powinien zostać zaktualizowany w celu odzwierciedlenia zmiany. Jeśli zmodyfikujesz plik .natvis poza IDE, zmiany nie zostały wprowadzone automatycznie. Aby zaktualizować systemu windows, możesz ocenić **.natvisreload** polecenia w pliku **Obejrzyj** okna. Powoduje to zmiany zaczęły obowiązywać bez ponownego uruchamiania sesji debugowania.  

 Można również dodawać lub usuwać pliki natvis do rozwiązania debugowania i programu Visual Studio spowoduje dodanie lub usunięcie odpowiednich wizualizacji.  

 Nie można zmodyfikować plik .natvis, podczas debugowania, jeśli jest osadzony w .pdb.  

 Użyj **.natvisreload** polecenia podczas uaktualniania plików natvis do nowszej wersji (na przykład, jeśli są sprawdzane w systemie kontroli źródła i chcesz wczytać najnowsze zmiany tej osobie inne wprowadzone w pliku). Zaleca się, że edytować pliki natvis, za pomocą edytora xml programu Visual Studio.  

##  <a name="BKMK_Expressions_and_formatting"></a> Wyrażenia i formatowanie  
 Wizualizacje Natvis umożliwia określenie elementów danych do wyświetlenia wyrażeń języka C++. Oprócz ulepszeń i ograniczenia dotyczące wyrażeń języka C++ w debugerze, które są opisane w [kontekstu — Operator (C++)](../debugger/context-operator-cpp.md), należy pamiętać o następujących różnicach:  

- Wyrażenia Natvis są oceniane w kontekście wizualizowanego obiektu, nie bieżącej ramki stosu. Na przykład, jeśli używasz `x` w wyrażeniu Natvis, odnosi się do pola o nazwie `x` w wizualizowanym obiekcie, nie do zmiennej lokalnej o nazwie `x` w trakcie wykonywania funkcji. Nie masz dostępu do zmiennych lokalnych w wyrażenia Natvis, mimo że zmienne globalne są dostępne.  

- Wyrażenia Natvis nie zezwalają funkcji oceny lub skutków ubocznych. Oznacza to, że wywołania funkcji i operatory przypisania są ignorowane. Ponieważ [funkcje wewnętrzne debugera](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) są efekt uboczny wolnej one mogą być swobodnie wywoływane z dowolnego wyrażenia Natvis, nawet jeśli inne wywołania funkcji są niedozwolone.  

  Aby kontrolować sposób wyświetlania wyrażenia w oknie zmiennej, można użyć innych specyfikatorów formatu, które są opisane w [specyfikatorów formatu](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) części [specyfikatory formatu w C++](../debugger/format-specifiers-in-cpp.md) tematu. Należy pamiętać, że specyfikatory formatu są ignorowane w gdy wejście wirtualizacji jest używana wewnętrznie przez Natvis, takich jak `Size` wyrażenia w rozszerzenie elementów arrayitems.  

## <a name="natvis-views"></a>Widoki Natvis  
 Widoki Natvis pozwalają zobaczyć dowolnego typu w więcej niż jeden sposób. Na przykład można zdefiniować widoku o nazwie **proste** zapewnia uproszczony widok typu. Na przykład poniżej przedstawiono wizualizację `std::vector`:  

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

 `DisplayString` i `ArrayItems` elementy są używane w widoku domyślnego i widokiem prostym, podczas gdy `[size]` i `[capacity]` elementy zostaną wykluczone z widokiem prostym. Możesz użyć **, widok** specyfikatora, aby określić alternatywny widok formatu. W **Obejrzyj** okna, należy określić widok prosty jako **vec,view(simple)**:  

 ![Okno czujki z widokiem prostym](../debugger/media/watch-simpleview.png "SimpleView wyrażenie kontrolne")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Diagnozowanie błędów Natvis  
 Diagnostyka Natvis służy do rozwiązywania składni oraz błędy analizy. Gdy debuger napotka błędy we wpisie wizualizacji, ignoruje błędy i albo Wyświetla typ w nieprzetworzonej postaci lub pobiera inną odpowiednią wizualizację. Aby zrozumieć, dlaczego jest ignorowany wpis wizualizacji i zobaczyć, jakie są podstawowe błędy, można włączyć Diagnostyka Natvis **narzędzia / Opcje / Debugowanie / dane wyjściowe okna / Diagnostyka Natvis wiadomości (tylko C++)** opcji. Błędy są wyświetlane w **dane wyjściowe** okna.  

##  <a name="BKMK_Syntax_reference"></a> Dokumentacja składni Natvis  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer element  
 `AutoVisualizer` Element jest węzeł główny pliku .natvis i zawiera przestrzeń nazw `xmlns:` atrybutu.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

###  <a name="BKMK_Type"></a> Typ elementu  
 Typ podstawowy wygląda następująco:  

```xml  
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  

```  

 Określa:  

1. Jaki typ tej wizualizacji powinien być używany dla ( `Type Name` atrybutu).  

2. Jak powinna wyglądać wartość obiektu tego typu ( `DisplayString` elementu).  

3. Elementy członkowskie tego typu powinny wyglądać po użytkownik rozwija go w oknie zmiennych ( `Expand` węzła).  

   **Klasy oparte na szablonach** `Name` atrybutu `Type` akceptuje gwiazdkę `*` jako symbolu wieloznacznego, który może służyć do nazw klas opartych na szablonach:  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 W tym przykładzie posłuży tej samej wizualizacji, czy obiekt jest `CAtlArray<int>` lub `CAtlArray<float>`. Jeśli istnieje określony wpis wizualizacji dla `CAtlArray<float>` , ma pierwszeństwo przed ogólnym wpisem.  

 Należy zauważyć, że parametry szablonu można odwoływać w zapisie wizualizacji przy użyciu makr $t1, $t2 i tak dalej. Aby znaleźć przykłady tych makr, zobacz pliki .natvis dostarczane z programem Visual Studio.  

####  <a name="BKMK_Visualizer_type_matching"></a> Dopasowanie typu wizualizatora  
 Jeśli wpis wizualizacji nie powiedzie się sprawdzić poprawność, jest używana następna dostępna wizualizacja.  

#### <a name="inheritable-attribute"></a>Atrybut dziedziczne  
 Można określić, czy wizualizacje dotyczy tylko typu podstawowego lub typem podstawowym i wszystkie typy pochodne z opcjonalnym `Inheritable` atrybutu. Poniższa wizualizacja ma zastosowanie tylko do `BaseClass` typu:  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 Wartość domyślna `Inheritable` jest `true`.  

#### <a name="priority-attribute"></a>Atrybut Priorytet  
 `Priority` Atrybut określa kolejność używania definicje alternatywnego, jeśli definicja nie powiedzie się, można przeanalizować. Możliwe wartości `Priority` są: `Low`, `MediumLow`,`Medium`, `MediumHigh`, i `High`, a wartość domyślna to `Medium`.  

 Atrybut priorytetu powinien być używany tylko w rozróżnienie między priorytety w obrębie tego samego pliku .natvis nie między różne pliki.  

 W poniższym przykładzie możemy zostanie najpierw przeanalizować wpis odpowiadający 2015 STL, a w przypadku niepowodzenia można przeanalizować użyjemy wpis alternatywnej wersję 2013 STL:  

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

####  <a name="BKMK_Versioning"></a> Wersja elementu  
 Użyj `Version` element do zawężania wizualizacji do określonych modułów i ich wersji, tak że Kolizje nazw można zminimalizować a różne wizualizacje mogą służyć do różnych wersji typów. Na przykład:  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 W tym przykładzie wizualizacja dotyczy to tylko `DirectUI::Border` typ odnaleziony w `Windows.UI.Xaml.dll` z wersji 1.0 i 1.5. Pamiętaj, że dodawania elementy wersji zakres wejścia wizualizacji danego modułu i wersji i zmniejsza przypadkowego niezgodności, ale jeśli typ jest zdefiniowany w typowych pliku nagłówkowym, który jest używany przez różne moduły, numerów wersji wizualizacji nie stosowana, jeśli Typ nie jest w określonym module.  

#### <a name="optional-attribute"></a>Opcjonalny atrybut  
 `Optional` Atrybut może znajdować się w każdym węźle. W przypadku niepowodzenia dowolne wyrażenie podrzędne wewnątrz węzła Opcjonalnie można przeanalizować tego węzła jest ignorowany, ale pozostałe Type element jest nadal ważny. W następujący typ `[State]` jest Nieopcjonalne, ale `[Exception]` jest opcjonalne.  Oznacza to, że jeśli `MyNamespace::MyClass` zawiera pole o nazwie _`M_exceptionHolder`, jednocześnie nadal będzie `[State]` węzła i `[Exception]` węzła, ale jeśli `_M_exceptionHolder` są spełnione, zostanie wyświetlony tylko `[State]` węzła.  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Atrybut warunek  
 Opcjonalny `Condition` atrybut jest dostępny dla wielu elementów wizualizacji i określa, kiedy należy użyć reguły wizualizacji. Jeśli wyrażenie wewnątrz atrybutu warunku jest rozpoznawany jako `false`, a następnie nie została zastosowana reguła wizualizacji określona przez element. Czy jest spełniony, czy istnieje nie `Condition` atrybutu, a następnie reguła wizualizacji jest stosowana do typu. Można użyć tego atrybutu, aby uzyskać `if-else` logiki we wpisach wizualizacji. Na przykład wizualizacja poniżej ma dwa `DisplayString` elementy dla typu inteligentnego wskaźnika:  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 Gdy `_Myptr` element członkowski jest `null`, warunek pierwszego `DisplayString` element jest rozpoznawany jako `true`, dzięki czemu zostanie wyświetlony formularz. Podczas `_Myptr` członek nie jest `null`, warunek jest `false`, a druga `DisplayString` element jest wyświetlany.  

### <a name="includeview-and-excludeview-attributes"></a>Atrybuty IncludeView i ExcludeView  
 Te atrybuty Określ elementy, które mają być wyświetlane lub nie są wyświetlane w różnych widokach. Na przykład, biorąc pod uwagę specyfikację Natvis `std::vector`:  

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

 Widok prosty nie są wyświetlane [rozmiar] i [pojemności] elementy w widoku uproszczonym. Jeśli firma Microsoft była używana `IncludeView="simple"` zamiast `ExcludeView`, `[size]` i `[capacity]` elementy zostaną pokazane w widoku uproszczonym, a nie w domyślnym widoku.  

 Możesz użyć `IncludeView` i `ExcludeView` atrybuty dla typów, a także na poszczególnych elementów członkowskich.  

###  <a name="BKMK_DisplayString"></a> Klasa DisplayString  
 A `DisplayString` element określa ciąg znaków, które mają być wyświetlane jako wartości zmiennej. Akceptuje dowolny łańcuchów mieszanych wyrażeń. Wszystko wewnątrz nawiasów klamrowych jest interpretowane jako wyrażenie. Na przykład `DisplayString` wpis podobny do tego:  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 Oznacza, że tego zmiennych typu `CPoint` są wyświetlane w następujący sposób:  

 ![Przy użyciu elementu klasy DisplayString](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 W `DisplayString` wyrażenie `x` i `y`, które są członkami `CPoint`, są umieszczone w nawiasach klamrowych i dlatego ich wartości są obliczane. Wyrażenie pokazuje również, jak można udosłownić nawias klamrowy za pomocą podwójnego nawiasu klamrowego ( `{{` lub `}}` ).  

> [!NOTE]
>  `DisplayString` Element jest jedynym elementem, który akceptuje dowolne ciągi i składnię nawiasu klamrowego. Wszystkie inne elementy wizualizacji akceptują tylko wyrażenia, które są sprawdzane przez debugera.  

###  <a name="BKMK_StringView"></a> StringView  
 `StringView` Element definiuje wyrażenie, którego wartość ma być wysyłane do wbudowanego wizualizatora tekstu. Załóżmy, że mamy następującą wizualizację dla `ATL::CStringT` typu:  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 `CStringT` Obiektu wygląda następująco:  

 ![Element klasy CStringT DisplayString](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 Wizualizacja Wyświetla `CStringT` obiektu w oknie zmiennych w następujący sposób:  

 Dodawanie `StringView` element wskaże do debugera, że ta wartość mogą być wyświetlane przez wizualizację tekstu:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Zwróć uwagę na ikonę szkła powiększającego obok wartości poniżej. Wybranie ikony uruchomi Wizualizator tekstu, co spowoduje wyświetlenie ciągu, `m_pszData` wskazuje.  

 ![CStringT danych za pomocą wizualizatora StringView](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
>  Należy pamiętać, że wyrażenie `{m_pszData,su}` specyfikator formatu języka C++ `su` Aby wyświetlić wartość jako ciąg Unicode. Zobacz [specyfikatory formatu w C++](../debugger/format-specifiers-in-cpp.md) Aby uzyskać więcej informacji.  

###  <a name="BKMK_Expand"></a> Rozwiń węzeł  
 `Expand` Węzeł służy do dostosowywania elementów podrzędnych typu zwizualizowanego, gdy użytkownik rozwija go w oknach zmiennych. Przyjmuje listę węzłów podrzędnych, które definiują elementy podrzędne.  

 `Expand` Węzeł jest opcjonalne.  

-   Jeśli `Expand` węzła nie określono we wpisie wizualizacji, są używane domyślne reguły rozwijania — Visual Studio.  

-   Jeśli `Expand` węzeł został określony bez węzłów podrzędnych pod nim, typu, nie będzie można rozwinąć w oknach debugera.  

####  <a name="BKMK_Item_expansion"></a> Rozszerzenie elementu  
 `Item` Element jest najbardziej podstawowym i najczęściej element ma być używany w `Expand` węzła. `Item` definiuje jeden typ elementów podrzędnych. Na przykład załóżmy, że masz `CRect` klasy `top`, `left`, `right`, i `bottom` jej pola oraz następującym wpisem wizualizacji:  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 `CRect` Typu będzie wyglądać następująco:  

 ![CRect, za pomocą rozszerzenie elementu elementu](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 Wyrażenia określone w `Width` i `Height` elementy są obliczane i wyświetlane w kolumnie wartości. `[Raw View]` Węzła jest automatycznie tworzona przez debuger zawsze wtedy, gdy jest używane rozszerzenie niestandardowe. Jest on rozwinięty na zrzucie ekranu powyżej, aby pokazać, jak surowy widok tego obiektu jest inny niż jego wizualizacja. Domyślne rozszerzenie programu Visual Studio tworzy poddrzewo klasy podstawowej i wyświetla listę wszystkich elementów członkowskich danych klasy podstawowej jako elementy podrzędne.  

> [!NOTE]
>  Jeśli wyrażenie elementu wskazuje typ złożony, `Item` sam węzeł jest rozwijany.  

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

 ![za pomocą elementów arrayitems STD::Vector](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 Co najmniej `ArrayItems` węzeł musi mieć:  

1. A `Size` wyrażenia (który musi być liczbą całkowitą) dla debugera, pozwalające zrozumieć długość tablicy  

2. A `ValuePointer` wyrażenie, które powinno wskazywać pierwszy element (który musi być wskaźnikiem typu elementu, który nie jest `void*`).  

   Wartość domyślna dolnej granicy tablicy to 0. Wartość można zastąpić za pomocą `LowerBound` — element (przykłady można znaleźć w plikach .natvis dostarczanych z programem Visual Studio).  

   Teraz możesz używać `[]` operator `ArrayItems` rozszerzenia, na przykład `vector[i]`. [] — Operator mogą być używane z dowolnej wizualizacji Jednowymiarowa tablica, która używa `ArrayItems` lub `IndexListItems`nawet wtedy, gdy ten operator nie zezwala na samego typu (na przykład `CATLArray`).  

   Wielowymiarowe tablice można również określić. Debuger potrzebuje tylko trochę więcej informacji do poprawnego wyświetlania elementów podrzędnych w takiej sytuacji:  

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

 `Direction` Określa, czy tablica dotyczy kolejności główna wierszy lub kolumn. `Rank` Określa rangę tablicy. `Size` Element akceptuje niejawny `$i` parametr, który zastępuje indeksem wymiaru w celu znalezienia długości tablicy w tym wymiarze. Na przykład w poprzednim przykładzie powyżej wyrażenie `_M_extent.M_base[0]` powinno dawać długość 0 wymiaru `_M_extent._M_base[1]` 1 i tak dalej.  

 Oto jak dwóch wymiarów `Concurrency::array` obiektu wyglądają w debugerze:  

 ![Dwa tablicą wielowymiarową przy użyciu elementów arrayitems](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

####  <a name="BKMK_IndexListItems_expansion"></a> Rozszerzenie indexlistitems  
 Możesz użyć `ArrayItems` rozszerzenia, tylko wtedy, gdy elementy tablicy są ułożone w sposób ciągły w pamięci. Debuger pobiera następny element po prostu przez zwiększenie swojego wskaźnika do bieżącego elementu. Aby obsługiwać przypadki, w których trzeba manipulowania indeksem w węźle wartości `IndexListItems` węzły mogą być używane. Poniżej przedstawiono wizualizację za pomocą `IndexListItems` węzła:  

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

 Teraz możesz używać `[]` operator `IndexListItems` rozszerzenia, na przykład `vector[i]`. `[]` Operator może być używany z dowolnej wizualizacji Jednowymiarowa tablica, która używa `ArrayItems` lub `IndexListItems`nawet wtedy, gdy ten operator nie zezwala na samego typu (na przykład `CATLArray`).  

 Jedyną różnicą między `ArrayItems` i `IndexListItems` jest fakt, że `ValueNode` oczekuje pełnego wyrażenia dla elementu i<sup>th</sup> z niejawnym `$i` parametru.  

####  <a name="BKMK_LinkedListItems_expansion"></a> Rozszerzenie linkedlistitems  
 Jeśli typ wizualizowany reprezentuje listę połączoną, debuger może wyświetlić jego elementy podrzędne przy użyciu `LinkedListItems` węzła. Oto wizualizacja dla `CAtlList` wpisać, korzystając z tej funkcji:  

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

-   `NextPointer` i `ValueNode` wyrażenia są obliczane w kontekście elementu węzła listy dwukierunkowej, a nie typu listy nadrzędnej. W powyższym przykładzie `CAtlList` ma `CNode` klasa (znalezione w `atlcoll.h`) reprezentująca węzeł listy łączonej. `m_pNext` i `m_element` pól tego `CNode` klasy, a nie `CAtlList` klasy.  

-   `ValueNode` Może być puste lub mieć `this` do odwoływania się do samego węzła listy dwukierunkowej.  

#### <a name="customlistitems-expansion"></a>Rozszerzenie CustomListItems  
 `CustomListItems` Rozszerzenia umożliwia pisanie logiki niestandardowej do przechodzenia przez strukturę danych, takich jak tablica skrótów. Należy używać `CustomListItems` do wizualizacji danych struktur, w którym wszystkie elementy należy ocenić jest można wyrazić za pomocą wyrażeń języka C++, ale jeszcze nie mieszczą się pleśnią dla `ArrayItems`, `TreeItems`, lub `LinkedListItems.`  

 Wizualizator dla CAtlMap jest przykładem doskonałe miejsce `CustomListItems` jest odpowiednia.  

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

####  <a name="BKMK_TreeItems_expansion"></a> Rozszerzenie elementów treeitems  
 Jeśli typ wizualizowany reprezentuje drzewo, debuger może przejść przez drzewo i wyświetlić jego elementy podrzędne przy użyciu `TreeItems` węzła. Oto wizualizacja dla `std::map` wpisać, korzystając z tej funkcji:  

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

 Składnia jest bardzo podobne do `LinkedListItems` węzła. `LeftPointer`, `RightPointer`, i `ValueNode` są oceniane w kontekście klasy węzła drzewa i `ValueNode` może być puste lub mieć `this` do odwoływania się do samego węzła drzewa.  

####  <a name="BKMK_ExpandedItem_expansion"></a> Rozszerzenie expandeditem  
 `ExpandedItem` Element może być użyty do wygenerowania zagregowanego widoku podrzędnego, wyświetlając właściwości podstawowej klasy lub elementów członkowskich danych tak, jakby były elementami podrzędnymi typu zwizualizowanego. Określone wyrażenie jest obliczane i węzły podrzędne wyniku są dołączane do listy podrzędnej typu zwizualizowanego. Załóżmy, że mamy typ inteligentnego wskaźnika `auto_ptr<vector<int>>` który zazwyczaj będzie wyświetlany jako:  

 ![automatyczne&#95;ptr&#60;wektor&#60;int&#62; &#62; domyślne rozszerzenie](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Aby wyświetlić wartości wektora, musisz przejść do szczegółów dwa poziomy głębiej w oknie zmiennej członkowskiej elementu _Myptr. Dodając `ExpandedItem` elementu, można wyeliminować `_Myptr` zmiennej z hierarchii i bezpośrednio wyświetlać elementy wektorów::  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![automatyczne&#95;ptr&#60;wektor&#60;int&#62; &#62; rozszerzenie expandeditem](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 W poniższym przykładzie pokazano sposób agregacji właściwości z klasy podstawowej w klasie pochodnej. Załóżmy, że `CPanel` klasa pochodzi od `CFrameworkElement`. Zamiast powtarzania właściwości, które pochodzą od podstawy `CFrameworkElement` klasy `ExpandedItem` węzeł pozwala te właściwości mają być dołączane do listy podrzędnej `CPanel` klasy. **Nd** specyfikatora, który wyłącza dopasowywanie wizualizacji dla klasy pochodnej jest tutaj formatu. W przeciwnym wypadku wyrażenie `*(CFrameworkElement*)this` spowoduje, że `CPanel` wizualizację można zastosować ponownie, ponieważ wizualizacji domyślnej wpisania typu reguł dopasowania uważają to za najbardziej odpowiednie. Za pomocą **nd** specyfikator formatu nakazuje debugerowi użycie wizualizacji klasy podstawowej lub rozszerzenia domyślnej klasy bazowej, jeśli klasa bazowa nie zawiera wizualizacji.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

####  <a name="BKMK_Synthetic_Item_expansion"></a> Syntetyczne rozszerzenie elementu  
 Gdzie `ExpandedItem` element zapewnia bardziej płaski widok danych poprzez wyeliminowanie hierarchii, `Synthetic` węzeł ma odwrotne. Umożliwia ona tworzenie elementu podrzędnego sztuczne (czyli element podrzędny nie jest wynikiem wyrażenia). Ten element podrzędny może zawierać elementy podrzędne swój własny. W poniższym przykładzie, wizualizacji dla `Concurrency::array` typu używa `Synthetic` węzeł, aby wyświetlić komunikat diagnostyczny dla użytkownika:  

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

 ![CONCURRENCY::Array z Sythentic element expansio](../debugger/media/dbg-natvis-expand-synthetic.png "DBG_NATVIS_Expand_Synthetic")  

###  <a name="BKMK_HResult"></a> Wartość HResult  
 `HResult` Elementu pozwala na dostosowanie informacje, które jest wyświetlane dla wartości HRESULT w oknach debugera. `HRValue` Element musi zawierać 32-bitową wartość HRESULT, która ma zostać dostosowana. `HRDescription` Element zawiera informacje, które jest wyświetlane w debugerze.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> UIVisualizer  
 Element `UIVisualizer` elementu rejestruje wtyczkę wizualizatora graficznego z debugerem. Wtyczka wizualizatora graficznego tworzy okno dialogowe lub inny interfejs do wyświetlania zmiennej lub obiektu w sposób, który jest odpowiedni do jego typu danych. Wtyczka wizualizatora musi zostać utworzona jako [pakietu VSPackage](../extensibility/internals/vspackages.md) i musi uwidaczniać usługę, które mogą być używane przez debuger. Plik .natvis zawiera informacje o rejestracji dla wtyczki, takie jak jego nazwa, identyfikator GUID usługi uwidacznianej i typy, które może ona wizualizować.  

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

 A `UIVisualizer` jest identyfikowane za pomocą `ServiceId`  -  `Id` atrybutu pary. `ServiceId` jest identyfikatorem GUID usługi uwidacznianej przez pakiet wizualizatora `Id` jest unikatowym identyfikatorem, który może służyć do odróżniania wizualizatorów, jeśli usługa oferuje więcej niż jednego wizualizatora. W powyższym przykładzie ten sam Wizualizator dostarcza dwóch wizualiztorów.  

 `MenuName` Atrybut jest, co użytkownicy widzą jako nazwę wizualizatora po otwarciu menu rozwijanego obok ikony lupy w oknach zmiennych debugera, na przykład:  

 ![Menu skrótów menu UIVisualizer](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 Każdy typ zdefiniowany w pliku .natvis musi wyraźnie określać wizualizatory interfejsu użytkownika, które mogą je wyświetlać. Debuger dopasowuje odwołania do wizualizatorów we wpisach typów do odpowiednich typów z zarejestrowanymi wizualizatorami. Na przykład, następujący wpis dla typu `std::vector` odwołuje się do elementu UIVisualizer w naszym przykładzie powyżej.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Możesz zobaczyć przykład UIVisualizer w rozszerzeniu Obejrzyj obraz używany do wyświetlania mapy bitowe w pamięci: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>CustomVisualizer element  
 `CustomVisualizer` jest punktem rozszerzalności, która określa rozszerzenie VSIX, który może zapisać do kontrolowania wizualizacji w kodzie, który działa w programie Visual Studio. Aby uzyskać więcej informacji na temat pisania rozszerzenia VSIX, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md). Pisanie wizualizatora niestandardowego jest o wiele więcej pracy niż pisania definicji natvis XML, ale możesz są wolne od ograniczenia, o jakich natvis obsługuje ani nie obsługuje. Wizualizatory niestandardowe mają dostęp do pełnego zestawu rozszerzalności debugera interfejsów API, który może służyć do kwerendy i modyfikowanie obiektu debugowanego procesu lub komunikowania się z innymi częściami programu Visual Studio.  

 Możesz użyć `Condition`, `IncludeView`, i `ExcludeView` atrybutów elementów CustomVisualizer.




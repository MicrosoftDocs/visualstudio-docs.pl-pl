---
title: Tworzenie niestandardowych widoków obiektów C++
description: Użyj struktury Natvis, aby dostosować sposób wyświetlania typów natywnych w programie Visual Studio w debugerze
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224514"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Tworzenie niestandardowych widoków obiektów języka C++ w debugerze przy użyciu struktury Natvis

Struktura Programu Visual Studio *Natvis* dostosowuje sposób, w jaki typy macierzyste pojawiają się w oknach zmiennych debugera, takich jak **okna Locals** i **Watch** oraz w **etykietkach dotyczących danych.** Wizualizacje Natvis mogą pomóc uczynić utworzone typy bardziej widoczne podczas debugowania.

Natvis zastępuje plik *autoexp.dat* we wcześniejszych wersjach programu Visual Studio składnią XML, lepszą diagnostyką, przechowywaniem wersji i obsługą wielu plików.

> [!NOTE]
> Dostosowania Natvis działają z klasami i strukturami, ale nie typedefs.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Wizualizacje Natvis

Struktura Natvis służy do tworzenia reguł wizualizacji dla typów, które tworzysz, dzięki czemu deweloperzy mogą je łatwiej zobaczyć podczas debugowania.

Na przykład na poniższej ilustracji przedstawiono zmienną typu [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) w oknie debugera bez stosowania żadnych wizualizacji niestandardowych.

![Domyślna wizualizacja textbox](../debugger/media/dbg_natvis_textbox_default.png "Domyślna wizualizacja textbox")

Wyróżniony wiersz pokazuje `Text` właściwość `TextBox` klasy. Hierarchia klas złożonych utrudnia znalezienie tej właściwości. Debuger nie wie, jak interpretować niestandardowy typ ciągu, więc nie widać ciągu przechowywane wewnątrz pola tekstowego.

To `TextBox` samo wygląda znacznie prostsze w oknie zmiennej, gdy stosowane są niestandardowe reguły wizualizatora Natvis. Ważne elementy członkowskie klasy pojawiają się razem, a debuger pokazuje podstawową wartość ciągu niestandardowego typu ciągu.

![Dane textbox przy użyciu wizualizatora](../debugger/media/dbg_natvis_textbox_visualizer.png "Dane textbox przy użyciu wizualizatora")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Używanie plików natvis w projektach języka C++

Natvis używa plików *.natvis* do określania reguł wizualizacji. Plik *.natvis* to plik XML z rozszerzeniem *.natvis.* Schemat Natvis jest zdefiniowany w *pliku %VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

Podstawowa struktura pliku *.natvis* jest `Type` jednym lub kilkoma elementami reprezentującymi wpisy wizualizacji. W pełni kwalifikowana `Type` nazwa każdego `Name` elementu jest określona w jego atrybucie.

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

Program Visual Studio udostępnia niektóre pliki *.natvis* w folderze *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers.* Pliki te mają reguły wizualizacji dla wielu typowych typów i mogą służyć jako przykłady do pisania wizualizacji dla nowych typów.

### <a name="add-a-natvis-file-to-a-c-project"></a>Dodawanie pliku natvis do projektu języka C++

Plik *.natvis* można dodać do dowolnego projektu języka C++.

**Aby dodać nowy plik *natvis:***

1. Wybierz węzeł projektu C++ w **Eksploratorze rozwiązań**i wybierz pozycję Dodaj**nowy element** **projektu** > lub kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Visual **C++** > **Utility** > **Debugger visual file visual (.natvis)**

1. Nazwij plik i wybierz pozycję **Dodaj**.

   Nowy plik zostanie dodany do **Eksploratora rozwiązań**i zostanie otwarty w okienku dokumentu programu Visual Studio.

Debuger programu Visual Studio automatycznie ładuje pliki *.natvis* w projektach języka C++ i domyślnie zawiera je również w pliku *pdb* podczas kompilacji projektu. Jeśli debugujesz szeloną aplikację, debuger ładuje plik *.natvis* z pliku *pdb,* nawet jeśli projekt nie jest otwarty. Jeśli nie chcesz, aby plik *.natvis* był zawarty w *pliku pdb,* możesz go wykluczyć z wbudowanego pliku *pdb.*

**Aby wykluczyć plik *natvis* z *pliku pdb:***

1. Zaznacz plik *natvis* w **Eksploratorze rozwiązań**i wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy plik i wybierz polecenie **Właściwości**.

1. Rozwijana strzałka obok pozycji **Wykluczone z kompilacji** i wybierz pozycję **Tak**, a następnie wybierz przycisk **OK**.

>[!NOTE]
>W przypadku debugowania projektów wykonywalnych należy użyć elementów rozwiązania, aby dodać wszystkie pliki *.natvis,* które nie znajdują się w *pliku pdb*, ponieważ nie ma dostępnego projektu C++.

>[!NOTE]
>Reguły Natvis ładowane z *pliku pdb* dotyczą tylko typów w modułach, do których odwołuje się *plik .pdb.* Na przykład jeśli *module1.pdb* ma wpis Natvis `Test`dla typu o `Test` nazwie, dotyczy tylko klasy w *module1.dll*. Jeśli inny moduł definiuje również `Test`klasę o nazwie, wpis *Module1.pdb* Natvis nie ma do niego zastosowania.

**Aby zainstalować i zarejestrować plik *.natvis* za pośrednictwem pakietu VSIX:**

Pakiet VSIX można zainstalować i zarejestrować pliki *.natvis.* Bez względu na to, gdzie są zainstalowane, wszystkie zarejestrowane pliki *.natvis* są automatycznie pobierane podczas debugowania.

1. Dołącz plik *.natvis* do pakietu VSIX. Na przykład dla następującego pliku projektu:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Zarejestruj plik *.natvis* w pliku *source.extension.vsixmanifest:*
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Lokalizacje plików Natvis

Pliki *.natvis* można dodać do katalogu użytkownika lub do katalogu systemowego, jeśli mają być stosowane do wielu projektów.

Pliki *.natvis* są oceniane w następującej kolejności:

1. Wszystkie pliki *.natvis,* które są osadzone w *debugowaniu .pdb,* chyba że plik o tej samej nazwie istnieje w załadowanym projekcie.

2. Wszystkie pliki *.natvis,* które znajdują się w załadowanym projekcie C++ lub rozwiązaniu najwyższego poziomu. Ta grupa zawiera wszystkie załadowane projekty języka C++, w tym biblioteki klas, ale nie projekty w innych językach.

3. Wszystkie pliki *.natvis* zainstalowane i zarejestrowane za pośrednictwem pakietu VSIX.

::: moniker range="vs-2017"

4. Katalog Natvis specyficzny dla użytkownika (na przykład *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Katalog Natvis specyficzny dla użytkownika (na przykład *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. Katalog Natvis dla całego systemu (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Ten katalog ma pliki *.natvis,* które są zainstalowane w programie Visual Studio. Jeśli masz uprawnienia administratora, możesz dodać pliki do tego katalogu.

## <a name="modify-natvis-files-while-debugging"></a>Modyfikowanie plików .natvis podczas debugowania

Można zmodyfikować plik *.natvis* w IDE podczas debugowania jego projektu. Otwórz plik w tym samym wystąpieniu programu Visual Studio, za pomocą którego debugujesz, zmodyfikuj go i zapisz. Po zapisaniu pliku system **Windows Watch** i **Locals** są aktualizowane w celu odzwierciedlenia zmiany.

Można również dodać lub usunąć pliki *.natvis* w rozwiązaniu, które debugujesz, a program Visual Studio dodaje lub usuwa odpowiednie wizualizacje.

Nie można zaktualizować plików *.natvis,* które są osadzone w plikach *pdb* podczas debugowania.

Jeśli zmodyfikujesz plik *.natvis* poza programem Visual Studio, zmiany nie zostaną wprowadzone automatycznie. Aby zaktualizować okna debugera, można ponownie ocenić polecenie **.natvisreload** w oknie **Natychmiastowe.** Następnie zmiany zostaną wprowadzone bez ponownego uruchamiania sesji debugowania.

Użyj również polecenia **.natvisreload,** aby uaktualnić plik *.natvis* do nowszej wersji. Na przykład plik *.natvis* może być zaewidencjonowany do kontroli źródła i chcesz odebrać ostatnie zmiany wprowadzone przez inną osobę.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a>Wyrażenia i formatowanie
Wizualizacje Natvis używają wyrażeń C++ do określania elementów danych do wyświetlenia. Oprócz ulepszeń i ograniczeń wyrażeń C++ w debugerze, które są opisane w [context operator (C++),](../debugger/context-operator-cpp.md)należy pamiętać o następujących czynnościach:

- Wyrażenia Natvis są oceniane w kontekście obiektu wizualizowanego, a nie bieżącej ramki stosu. Na przykład `x` w wyrażeniu Natvis odnosi się do pola o nazwie **x** w obiektu, który jest wizualizowany, a nie do zmiennej lokalnej o nazwie **x** w bieżącej funkcji. Nie można uzyskać dostępu do zmiennych lokalnych w wyrażeniach Natvis, chociaż można uzyskać dostęp do zmiennych globalnych.

- Wyrażenia Natvis nie zezwalają na ocenę funkcji lub skutki uboczne. Wywołania funkcji i operatory przypisania są ignorowane. Ponieważ [funkcje wewnętrzne debugera](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) są wolne od efektów ubocznych, mogą być swobodnie wywoływane z dowolnego wyrażenia Natvis, nawet jeśli inne wywołania funkcji są niedozwolone.

- Aby kontrolować sposób wyświetlania wyrażenia, można użyć dowolnego specyfikatora formatu opisanego w [formacie specyfikatorów w języku C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Specyfikatory formatów są ignorowane, gdy wpis jest używany wewnętrznie `Size` przez Natvis, na przykład wyrażenie w [rozwinięciu ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Widoki Natvis

Można zdefiniować różne widoki Natvis, aby wyświetlać typy na różne sposoby. Na przykład tutaj jest `std::vector` wizualizacja, która definiuje widok `simple`uproszczony o nazwie . Elementy `DisplayString` i `ArrayItems` elementy są wyświetlane w `simple` widoku domyślnym `[capacity]` i widoku, podczas `simple` gdy `[size]` elementy i elementy nie są wyświetlane w widoku.

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

W oknie **Czujka** użyj specyfikatora formatu **widoku,** aby określić widok alternatywny. Prosty widok pojawia się jako **vec, view (simple)**:

![Okno zegarka z prostym widokiem](../debugger/media/watch-simpleview.png "Okno zegarka z prostym widokiem")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Błędy Natvis

Gdy debuger napotka błędy we wpisie wizualizacji, ignoruje je. Wyświetla typ w postaci nieprzetworzonej lub wybiera inną odpowiednią wizualizację. Diagnostyki Natvis można użyć, aby zrozumieć, dlaczego debuger zignorował wpis wizualizacji i aby zobaczyć podstawowe błędy składni i analizy.

**Aby włączyć diagnostykę Natvis:**

- W obszarze**Opcje** **narzędzi** > (lub**Opcje** **debugowania)** > > **Debugowanie** > **okna wyjściowego**ustaw **komunikaty diagnostyczne Natvis (tylko C++)** na **Błąd**, **Ostrzeżenie**lub **Pełne**, a następnie wybierz **ok**.

Błędy pojawiają się w oknie **Dane wyjściowe.**

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a>Odwołanie do składni Natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a>Element Autowizualizatora
Element `AutoVisualizer` jest węzłem głównym pliku *.natvis* i zawiera `xmlns:` atrybut obszaru nazw.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Element `AutoVisualizer` może mieć [type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)i [CustomVisualizer](#BKMK_CustomVisualizer) dzieci.

### <a name="type-element"></a><a name="BKMK_Type"></a>Element tekstowy

Podstawowy `Type` wygląda jak w tym przykładzie:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Element `Type` określa:

1. Do jakiego typu wizualizacja powinna `Name` być używana (atrybut).

2. Jak powinna wyglądać wartość obiektu tego typu `DisplayString` (element).

3. Jak powinny wyglądać elementy członkowskie typu, gdy użytkownik rozwija typ w `Expand` oknie zmiennej (węzeł).

#### <a name="templated-classes"></a>Klasy szablonów
Atrybut `Name` `Type` elementu akceptuje gwiazdkę `*` jako symbol wieloznaczny, który może służyć do nazw klas szablonów.

W poniższym przykładzie używana jest ta sama `CAtlArray<int>` wizualizacja, niezależnie od tego, czy obiekt jest obiektem `CAtlArray<float>`. Jeśli istnieje określony wpis wizualizacji `CAtlArray<float>`dla programu , ma pierwszeństwo przed ogólnym.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Parametry szablonu można odwoływać się do parametrów we wpisie wizualizacji przy użyciu makr $T1, $T2 itd. Aby znaleźć przykłady tych makr, zobacz pliki *.natvis* dostarczane z programem Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a>Dopasowanie typu wizualizatora
Jeśli wpis wizualizacji nie zostanie zweryfikowany, zostanie użyta następna dostępna wizualizacja.

#### <a name="inheritable-attribute"></a>Atrybut dziedziczny
Atrybut `Inheritable` opcjonalny określa, czy wizualizacja ma zastosowanie tylko do typu podstawowego, czy do typu podstawowego i wszystkich typów pochodnych. Wartością `Inheritable` domyślną `true`jest .

W poniższym przykładzie wizualizacja dotyczy `BaseClass` tylko typu:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Atrybut priorytetu

Atrybut `Priority` opcjonalny określa kolejność używania alternatywnych definicji, jeśli definicja nie może przeanalizować. Możliwe wartości `Priority` to: `Low` `MediumLow`,`Medium` `MediumHigh`, `High`, i . Wartością domyślną jest `Medium`. Atrybut `Priority` wyróżnia się tylko między priorytetami w tym samym pliku *.natvis.*

W poniższym przykładzie najpierw analizuje wpis, który pasuje do 2015 STL. Jeśli to nie powiedzie się przeanalizować, używa alternatywnego wpisu dla wersji 2013 STL:

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

### <a name="optional-attribute"></a>Atrybut opcjonalny
Atrybut można `Optional` umieścić w dowolnym węźle. Jeśli podwyrażenie wewnątrz węzła opcjonalnego nie może analizować, debuger ignoruje ten `Type` węzeł, ale stosuje pozostałe reguły. W następującym `[State]` typie nie jest `[Exception]` opcjonalne, ale jest opcjonalne.  Jeśli `MyNamespace::MyClass` ma pole`M_exceptionHolder`o nazwie `[State]` _ `[Exception]` , pojawi się zarówno węzeł, jak i węzeł, ale jeśli nie ma `_M_exceptionHolder` pola, pojawia się tylko `[State]` węzeł.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a>Atrybut Warunek

Opcjonalny `Condition` atrybut jest dostępny dla wielu elementów wizualizacji i określa, kiedy należy użyć reguły wizualizacji. Jeśli wyrażenie wewnątrz atrybutu warunek `false`jest rozpoznawane , reguła wizualizacji nie ma zastosowania. Jeśli zostanie obliczona na `true`, `Condition` lub nie ma atrybutu, wizualizacja ma zastosowanie. Tego atrybutu można użyć dla logiki if-else we wpisach wizualizacji.

Na przykład następująca wizualizacja `DisplayString` ma dwa elementy dla typu inteligentnego wskaźnika. Gdy `_Myptr` element członkowski jest pusty, `DisplayString` warunek pierwszego `true`elementu jest rozpoznawany na , tak aby zostanie wyświetlony formularz. Gdy `_Myptr` element członkowski nie jest pusty, warunek jest oblicza , `false`a drugi `DisplayString` element jest wyświetlany.

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

`IncludeView` Atrybuty `ExcludeView` i określają elementy do wyświetlania lub nie wyświetlania w określonych widokach. Na przykład w poniższej specyfikacji `std::vector`Natvis `simple` widok nie `[size]` `[capacity]` wyświetla elementów i.

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

Można użyć `IncludeView` i `ExcludeView` atrybuty na typy i na poszczególnych członków.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Element wersji
Element `Version` obejmuje wpis wizualizacji do określonego modułu i wersji. Element `Version` pomaga uniknąć kolizji nazw, zmniejsza przypadkowe niezgodności i umożliwia różne wizualizacje dla różnych wersji typu.

Jeśli wspólny plik nagłówka, który jest używany przez różne moduły definiuje typ, wersja wizualizacji pojawia się tylko wtedy, gdy typ znajduje się w określonej wersji modułu.

W poniższym przykładzie wizualizacja ma `DirectUI::Border` zastosowanie tylko `Windows.UI.Xaml.dll` do typu znalezionego w wersji od wersji 1.0 do 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Nie potrzebujesz obu `Min` i `Max`. Są to atrybuty opcjonalne. Nie są obsługiwane żadne symbole wieloznaczne.

Atrybut `Name` jest w formacie *filename.ext*, takich jak *hello.exe* lub *some.dll*. Nazwy ścieżek nie są dozwolone.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>Element DisplayString
Element `DisplayString` określa ciąg, który ma być pokazywalny jako wartość zmiennej. Akceptuje arbitralne ciągi zmieszane z wyrażeniami. Wszystko wewnątrz nawiasów klamrowych jest interpretowane jako wyrażenie. Na przykład następujący `DisplayString` wpis:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Oznacza, że zmienne typu `CPoint` wyświetlają się jak na tej ilustracji:

 ![Używanie elementu DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Używanie elementu DisplayString")

W `DisplayString` `x` wyrażeniu i `y`, `CPoint`które są członkami , znajdują się wewnątrz nawiasów klamrowych, więc ich wartości są oceniane. W przykładzie pokazano również, jak można uciec kręcone klamry `{{` `}}` za pomocą podwójnych nawiasów klamrowych ( lub ).

> [!NOTE]
> Element `DisplayString` jest jedynym elementem, który akceptuje dowolne ciągi i kręcące się składni nawiasów klamrowych. Wszystkie inne elementy wizualizacji akceptują tylko wyrażenia, które debuger może ocenić.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>Element StringView

Element `StringView` definiuje wartość, którą debuger można wysłać do wbudowanego wizualizatora tekstu. Na przykład, biorąc pod uwagę `ATL::CStringT` następującą wizualizację dla typu:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Obiekt `CStringT` jest wyświetlany w oknie zmiennej, tak jak w tym przykładzie:

![Element CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "Element CStringT DisplayString")

Dodanie `StringView` elementu informuje debugera, że może wyświetlać wartość jako wizualizację tekstu.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Podczas debugowania można wybrać ikonę lupy obok zmiennej, a następnie wybrać opcję **Wizualizator tekstu,** aby wyświetlić ciąg, na który **m_pszData** wskazuje.

 ![Dane CStringT z wizualizatorem StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Dane CStringT z wizualizatorem StringView")

Wyrażenie `{m_pszData,su}` zawiera specyfikator formatu **C++,** aby wyświetlić wartość jako ciąg Unicode. Aby uzyskać więcej informacji, zobacz [Formatowanie specyfikatorów w języku C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Rozwiń element

Węzeł `Expand` opcjonalny dostosowuje elementy podrzędne typu wizualizowanego podczas rozwijania typu w oknie zmiennej. Węzeł `Expand` akceptuje listę węzłów podrzędnych, które definiują elementy podrzędne.

- Jeśli `Expand` węzeł nie jest określony we wpisie wizualizacji, elementy podrzędne używają domyślnych reguł rozszerzania.

- Jeśli `Expand` węzeł jest określony bez węzłów podrzędnych pod nim, typ nie można rozwinąć w oknach debugera.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a>Rozszerzeń przedmiotu

 Element `Item` jest najbardziej podstawowym i typowym elementem w węźle. `Expand` `Item`definiuje pojedynczy element podrzędny. Na przykład `CRect` klasa z `top` `left`polami , `right`i `bottom` ma następujący wpis wizualizacji:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

W oknie debugera `CRect` typ wygląda następująco:

![CRect z rozwinięciem elementu elementu](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect z rozwinięciem elementu elementu")

Debuger ocenia wyrażenia określone w `Width` i `Height` elementów i pokazuje wartości w **kolumnie Wartość** okna zmiennej.

Debuger automatycznie tworzy węzeł **[Widok raw]** dla każdego niestandardowego rozszerzenia. Na poprzednim zrzucie ekranu jest wyświetlany węzeł **[Widok raw]** rozwinięty, aby pokazać, jak domyślny widok nieprzetworzony obiektu różni się od jego wizualizacji Natvis. Rozszerzenie domyślne tworzy poddrzewo dla klasy podstawowej i wyświetla listę wszystkich elementów członkowskich danych klasy podstawowej jako elementy podrzędne.

> [!NOTE]
> Jeśli wyrażenie elementu elementu wskazuje na typ złożony, sam węzeł **Element** można rozwinąć.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a>Rozszerzenie arrayitems
Użyj `ArrayItems` węzła, aby debuger programu Visual Studio interpretować typ jako tablicę i wyświetlać jego poszczególne elementy. Dobrym przykładem `std::vector` jest wizualizacja:

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

A `std::vector` pokazuje jego poszczególne elementy po rozwinięciu w oknie zmiennej:

![std::vector przy użyciu rozszerzenia ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector przy użyciu rozszerzenia ArrayItems")

Węzeł `ArrayItems` musi mieć:

- Wyrażenie `Size` (które musi ocenić do liczby całkowitej) dla debugera, aby zrozumieć długość tablicy.
- Wyrażenie `ValuePointer` wskazujące pierwszy element (który musi być wskaźnikiem typu `void*`elementu, który nie jest).

Domyślną wartością dolnej granicy tablicy jest 0. Aby zastąpić wartość, należy `LowerBound` użyć elementu. Pliki *.natvis* dostarczane z programem Visual Studio mają przykłady.

>[!NOTE]
>Można użyć `[]` operatora, na `vector[i]`przykład, z dowolnej wizualizacji tablicy `ArrayItems`jednowymiarowej, która `CATLArray`używa , nawet jeśli sam typ (na przykład ) nie zezwala na ten operator.

Można również określić tablice wielowymiarowe. W takim przypadku debuger potrzebuje nieco więcej informacji, aby prawidłowo wyświetlać elementy podrzędne:

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

- `Direction`określa, czy tablica jest w kolejności wiersza głównego lub głównego kolumny.
- `Rank`określa rangę tablicy.
- Element `Size` akceptuje parametr `$i` niejawny, który zastępuje indeksem wymiarów, aby znaleźć długość tablicy w tym wymiarze. W poprzednim przykładzie `_M_extent.M_base[0]` wyrażenie powinno nadać długość wymiaru `_M_extent._M_base[1]` 0, 1 i tak dalej.

Oto jak dwuwymiarowy `Concurrency::array` obiekt wygląda w oknie debugera:

![Tablica dwuwymiarowa z rozszerzeniem ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Tablica dwuwymiarowa z rozszerzeniem ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a>Rozszerzenie IndexListItems

Rozszerzenie można `ArrayItems` używać tylko wtedy, gdy elementy tablicy są rozmieszczone w pamięci. Debuger przechodzi do następnego elementu, po prostu zwiększanie jego wskaźnik. Jeśli chcesz manipulować indeksem do węzła `IndexListItems` wartości, użyj węzłów. Oto wizualizacja z węzłem: `IndexListItems`

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

Jedyną różnicą `IndexListItems` między `ValueNode` `ArrayItems` i jest , który oczekuje pełnego wyrażenia `$i` do i<sup>th</sup> element z parametru niejawne.

>[!NOTE]
>Można użyć `[]` operatora, na `vector[i]`przykład, z dowolnej wizualizacji tablicy `IndexListItems`jednowymiarowej, która `CATLArray`używa , nawet jeśli sam typ (na przykład ) nie zezwala na ten operator.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a>Rozszerzenie LinkedListItems

Jeśli zwizualizowany typ reprezentuje listę połączoną, debuger może wyświetlać jego elementy podrzędne przy użyciu węzła. `LinkedListItems` Następująca wizualizacja `CAtlList` dla typu `LinkedListItems`używa:

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

Element `Size` odnosi się do długości listy. `HeadPointer`wskazuje pierwszy element, `NextPointer` odwołuje się do następnego elementu i `ValueNode` odnosi się do wartości elementu.

Debuger ocenia `NextPointer` wyrażenia `ValueNode` i wyrażenia w kontekście elementu węzła, `LinkedListItems` a nie typ listy nadrzędnej. W poprzednim przykładzie `CAtlList` ma `CNode` klasę (znaleziono w `atlcoll.h`), która jest węzłem połączonej listy. `m_pNext`i `m_element` są polami tej `CNode` klasy, a `CAtlList` nie klasy.

`ValueNode`można pozostawić puste lub `this` użyć do `LinkedListItems` odwoływania się do samego węzła.

#### <a name="customlistitems-expansion"></a>Rozszerzenie CustomListItems

Rozwinięcie `CustomListItems` umożliwia pisanie niestandardowej logiki przechodzenia przez strukturę danych, takich jak tabela mieszania. Służy `CustomListItems` do wizualizacji struktur danych, które mogą używać wyrażeń C++ do wszystkiego, `ArrayItems`co `IndexListItems`trzeba `LinkedListItems`ocenić, ale nie do końca pasują do formy , lub .

Można użyć `Exec` do wykonania kodu `CustomListItems` wewnątrz rozszerzenia, przy użyciu zmiennych i obiektów zdefiniowanych w rozwinieniu. Operatory logiczne, operatory arytmetyczne i `Exec`operatory przypisania można używać za pomocą programu . Nie można użyć `Exec` do oceny funkcji, z wyjątkiem [funkcji wewnętrznych debugera obsługiwanych](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) przez oceniającego wyrażenie C++.

Poniższy wizualizator `CAtlMap` jest `CustomListItems` doskonałym przykładem, gdzie jest to właściwe.

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

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a>Rozszerzenie TreeItems
 Jeśli zwizualizowany typ reprezentuje drzewo, debuger może chodzić drzewa `TreeItems` i wyświetlić jego elementy podrzędne za pomocą węzła. Oto wizualizacja `std::map` typu przy użyciu `TreeItems` węzła:

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

Składnia jest podobna `LinkedListItems` do węzła. `LeftPointer`, `RightPointer`i `ValueNode` są oceniane w kontekście klasy węzła drzewa. `ValueNode`można pozostawić puste `this` lub użyć `TreeItems` do odwoływania się do samego węzła.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a>Rozbudowa ExpandedItem
 Element `ExpandedItem` generuje zagregowany widok podrzędny, wyświetlając właściwości klas podstawowych lub elementów członkowskich danych, tak jakby były elementami podrzędnymi typu wizualizowanego. Debuger ocenia określone wyrażenie i dołącza węzły podrzędne wyniku do listy podrzędnej zwizualizowanego typu.

Na przykład typ `auto_ptr<vector<int>>` inteligentnego wskaźnika jest zazwyczaj wyświetlany w następujący sposób:

 ![auto&#95;ptr&#60;wektor&#60;int&#62;&#62; domyślne rozszerzenie](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Domyślne rozszerzenie")

 Aby wyświetlić wartości wektora, należy przejść do szczegółów dwóch poziomów w `_Myptr` oknie zmiennej, przechodząc przez element członkowski. Dodając element, `ExpandedItem` można wyeliminować `_Myptr` zmienną z hierarchii i bezpośrednio wyświetlić elementy wektorowe:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;ptr&#60;&#60;int&#62;&#62; ExpandedItem expansion](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Rozbudowa ExpandedItem")

W poniższym przykładzie pokazano, jak agregować właściwości z klasy podstawowej w klasie pochodnej. Załóżmy, `CPanel` że `CFrameworkElement`klasa pochodzi od . Zamiast powtarzać właściwości, które pochodzą z `CFrameworkElement` klasy `ExpandedItem` podstawowej, wizualizacja węzła dołącza te właściwości `CPanel` do listy podrzędnej klasy.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Specyfikator **formatu nd,** który wyłącza dopasowanie wizualizacji dla klasy pochodnej, jest tutaj konieczny. W przeciwnym `*(CFrameworkElement*)this` razie wyrażenie `CPanel` spowodowałoby wizualizacji do ponownego zastosowania, ponieważ domyślne reguły dopasowywania typu wizualizacji uważają za najbardziej odpowiednie. Użyj specyfikatora formatu **ND,** aby poinstruować debugera, aby używał wizualizacji klasy podstawowej, lub domyślnego rozszerzenia, jeśli klasa podstawowa nie ma wizualizacji.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>Rozszerzenie produktu syntetycznego
 Podczas `ExpandedItem` gdy element zapewnia bardziej płaski widok danych przez `Synthetic` wyeliminowanie hierarchii, węzeł robi odwrotnie. Umożliwia utworzenie sztucznego elementu podrzędnego, który nie jest wynikiem wyrażenia. Sztuczny element może mieć własne elementy podrzędne. W poniższym przykładzie wizualizacja `Concurrency::array` dla typu `Synthetic` używa węzła, aby wyświetlić komunikat diagnostyczny dla użytkownika:

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

 ![Współbieżność::Tablica z rozwinięciem elementu syntetycznego](../debugger/media/dbg_natvis_expand_synthetic.png "Współbieżność::Tablica z rozwinięciem elementu syntetycznego")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>Element HResult
 Element `HResult` umożliwia dostosowanie informacji wyświetlanych dla **HRESULT** w oknach debugera. Element `HRValue` musi zawierać wartość 32-bitową **funkcji HRESULT,** która ma zostać dostosowana. Element `HRDescription` zawiera informacje, które mają być wyświetlane w oknie debugera.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>UIWizualizer element
Element `UIVisualizer` rejestruje wtyczkę wizualizatora graficznego z debugerem. Wizualizator graficzny tworzy okno dialogowe lub inny interfejs, który pokazuje zmienną lub obiekt w sposób zgodny z jego typem danych. Wtyczka wizualizatora musi być autorstwa jako [VSPackage](../extensibility/internals/vspackages.md)i musi udostępnić usługę, która może korzystać debuger. Plik *.natvis* zawiera informacje rejestracyjne dla wtyczki, takie jak jego nazwa, identyfikator GUID usługi narażone i typy, które można wizualizować.

Oto przykład elementu UIVisualizer:

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

- `ServiceId`  -  Para `Id` atrybutów identyfikuje `UIVisualizer`plik . Jest `ServiceId` identyfikator GUID usługi visualizer pakiet udostępnia. `Id`jest unikatowym identyfikatorem, który odróżnia wizualizatory, jeśli usługa zapewnia więcej niż jeden. W poprzednim przykładzie tej samej usługi wizualizatora zapewnia dwa wizualizatory.

- Atrybut `MenuName` definiuje nazwę wizualizatora do wyświetlenia w rozwijanej obok ikony lupy w debugerze. Przykład:

  ![Menu skrótów menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menu skrótów menu UIVisualizer")

Każdy typ zdefiniowany w pliku *.natvis* musi jawnie wyświetlić wszystkie wizualizatory interfejsu użytkownika, które mogą go wyświetlać. Debuger dopasowuje odwołania wizualizatora we wpisach typu z zarejestrowanymi wizualizatorami. Na przykład następujący wpis `std::vector` typu dla `UIVisualizer` odwołań w poprzednim przykładzie.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Można zobaczyć przykład `UIVisualizer` w rozszerzeniu Image [Watch](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) używane do wyświetlania map bitowych w pamięci.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Element CustomVisualizer
 `CustomVisualizer`jest punktem rozszerzalności, który określa rozszerzenie VSIX, które można zapisać do kontrolowania wizualizacji w kodzie programu Visual Studio. Aby uzyskać więcej informacji na temat pisania rozszerzeń VSIX, zobacz [visual studio SDK](../extensibility/visual-studio-sdk.md).

Pisanie niestandardowego wizualizatora niż definicji XML Natvis jest o wiele więcej pracy, ale nie masz ograniczeń dotyczących tego, co Natvis obsługuje lub nie obsługuje. Wizualizatory niestandardowe mają dostęp do pełnego zestawu interfejsów API rozszerzalności debugera, które mogą wysyłać zapytania i modyfikować proces debugowania lub komunikować się z innymi częściami programu Visual Studio.

 `Condition`Można użyć `IncludeView`, i `ExcludeView` atrybuty na `CustomVisualizer` elementach.

 ## <a name="limitations"></a>Ograniczenia

Dostosowania Natvis działają z klasami i strukturami, ale nie typedefs.

Natvis nie obsługuje wizualizatorów dla typów `int`pierwotnych (na przykład , `bool`) lub wskaźników do typów pierwotnych. W tym scenariuszu jedną z opcji jest użycie [specyfikatora formatu](../debugger/format-specifiers-in-cpp.md) odpowiedniego dla danego przypadku użycia. Na przykład, jeśli `double* mydoublearray` używasz w kodzie, a następnie można użyć specyfikatora formatu tablicy `mydoublearray, [100]`w oknie **czujki** debugera, takich jak wyrażenie , który pokazuje pierwsze 100 elementów.

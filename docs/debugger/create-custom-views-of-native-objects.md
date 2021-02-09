---
title: Tworzenie niestandardowych widoków obiektów C++
description: Użyj struktury Natvis, aby dostosować sposób, w jaki program Visual Studio Wyświetla natywne typy w debugerze
ms.date: 03/02/2020
ms.topic: how-to
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 5a219ae5257bce2a84dc17556939a44ecb02dcce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857743"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Tworzenie niestandardowych widoków obiektów C++ w debugerze przy użyciu struktury Natvis

Struktura programu Visual Studio *Natvis* dostosowuje sposób, w jaki typy natywne są wyświetlane w oknach zmiennych debugera, takich jak **Ustawienia regionalne** i okna **czujki** , oraz w **etykietkach** danych. Wizualizacje Natvis mogą pomóc w tworzeniu typów, które można wyświetlić podczas debugowania.

Natvis zastępuje plik *autoexp. dat* we wcześniejszych wersjach programu Visual Studio z SKŁADNIĄ języka XML, lepszą diagnostyką, przechowywaniem wersji i obsługą wielu plików.

> [!NOTE]
> Dostosowania Natvis współpracują z klasami i strukturami, ale nie z typedef.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Wizualizacje Natvis

Struktura Natvis służy do tworzenia reguł wizualizacji dla tworzonych typów, dzięki czemu deweloperzy mogą łatwiej widzieć je podczas debugowania.

Na przykład na poniższej ilustracji przedstawiono zmienną typu [Windows:: UI:: XAML:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) w oknie debugera bez zastosowanych niestandardowych wizualizacji.

![Wizualizacja domyślna TextBox](../debugger/media/dbg_natvis_textbox_default.png "Wizualizacja domyślna TextBox")

Wyróżniony wiersz pokazuje `Text` Właściwość `TextBox` klasy. Złożona hierarchia klas utrudnia znalezienie tej właściwości. Debuger nie wie, jak interpretować niestandardowy typ ciągu, dlatego nie można zobaczyć ciągu przechowywanego wewnątrz pola tekstowego.

Ten sam `TextBox` wygląd jest znacznie prostszy w oknie zmiennych, gdy stosowane są reguły niestandardowego wizualizatora Natvis. Ważne elementy członkowskie klasy są wyświetlane razem, a debuger pokazuje podstawową wartość ciągu niestandardowego typu ciągu.

![Dane TextBox przy użyciu wizualizatora](../debugger/media/dbg_natvis_textbox_visualizer.png "Dane TextBox przy użyciu wizualizatora")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Korzystanie z plików. Natvis w projektach C++

Plik Natvis używa plików *. Natvis* , aby określić reguły wizualizacji. Plik *. Natvis* jest plikiem XML z rozszerzeniem *. Natvis* . Schemat Natvis został zdefiniowany w *%VSInstallDir%\Xml\Schemas\natvis.xsd*.

Podstawowa struktura pliku *. Natvis* to jeden lub więcej `Type` elementów reprezentujących wpisy wizualizacji. W pełni kwalifikowana nazwa każdego `Type` elementu jest określona w jego `Name` atrybucie.

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

Program Visual Studio udostępnia pliki *Natvis* w folderze *%VSInstallDir%\Common7\Packages\Debugger\Visualizers* . Te pliki mają reguły wizualizacji dla wielu wspólnych typów i mogą być przykładowe do pisania wizualizacji dla nowych typów.

### <a name="add-a-natvis-file-to-a-c-project"></a>Dodawanie pliku. Natvis do projektu języka C++

Plik *. Natvis* można dodać do dowolnego projektu języka C++.

**Aby dodać nowy plik *Natvis* :**

1. Wybierz węzeł projekt C++ w **Eksplorator rozwiązań** i wybierz pozycję **projekt**  >  **Dodaj nowy element** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj**  >  **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz   >    >  **plik wizualizacji debugera narzędzi Visual C++ (Natvis)**.

1. Nazwij plik, a następnie wybierz pozycję **Dodaj**.

   Nowy plik zostanie dodany do **Eksplorator rozwiązań** i otwarty w okienku dokumentu programu Visual Studio.

Debuger programu Visual Studio ładuje pliki *Natvis* w projektach języka C++ automatycznie, a domyślnie dołącza je do pliku *. pdb* podczas kompilowania projektu. W przypadku debugowania skompilowanej aplikacji debuger ładuje plik *. Natvis* z pliku *. pdb* , nawet jeśli nie ma otwartego projektu. Jeśli nie chcesz, aby plik *. Natvis* został uwzględniony w pliku *. pdb*, możesz go wykluczyć z skompilowanego plik *. pdb* .

**Aby wykluczyć plik *. Natvis* z pliku *. pdb*:**

1. Wybierz plik *. Natvis* w **Eksplorator rozwiązań** i wybierz ikonę **Właściwości** lub kliknij plik prawym przyciskiem myszy, a następnie wybierz polecenie **Właściwości**.

1. Rozwiń strzałkę obok pozycji **wykluczone z kompilacji** i wybierz opcję **tak**, a następnie wybierz przycisk **OK**.

>[!NOTE]
>W przypadku debugowania projektów wykonywalnych Użyj elementów rozwiązania, aby dodać dowolne pliki *. Natvis* , które nie znajdują się w pliku *. pdb*, ponieważ nie ma dostępnego projektu języka C++.

>[!NOTE]
>Reguły Natvis zostały załadowane z *. pdb* stosuje się tylko do typów modułów, do których odwołuje się plik. *PDB* . Na przykład jeśli *Module1. pdb* ma wpis Natvis dla typu o nazwie `Test` , ma zastosowanie tylko do `Test` klasy w *Module1.dll*. Jeśli inny moduł definiuje również klasę o nazwie `Test` , wpis *Module1. pdb* Natvis nie ma zastosowania do tego elementu.

**Aby zainstalować i zarejestrować plik *. Natvis* za pośrednictwem pakietu VSIX:**

Pakiet VSIX może instalować i rejestrować pliki *. Natvis* . Niezależnie od tego, gdzie są zainstalowane, wszystkie zarejestrowane pliki *Natvis* są automatycznie wybierane podczas debugowania.

1. Dołącz plik *. Natvis* w pakiecie VSIX. Na przykład dla następującego pliku projektu:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Zarejestruj plik *Natvis* w pliku *source. Extension. vsixmanifest* :

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a> Lokalizacje plików Natvis

Pliki *. Natvis* można dodać do katalogu użytkownika lub do katalogu systemowego, jeśli mają być stosowane do wielu projektów.

Pliki *. Natvis* są oceniane w następującej kolejności:

1. Wszystkie pliki *. Natvis* , które są osadzone w debugowanym pliku *. pdb* , chyba że plik o tej samej nazwie istnieje w załadowanym projekcie.

2. Wszystkie pliki *. Natvis* , które znajdują się w załadowanym projekcie C++ lub w rozwiązaniu najwyższego poziomu. Ta grupa zawiera wszystkie załadowane projekty języka C++, w tym biblioteki klas, ale nie projekty w innych językach.

3. Wszystkie pliki *Natvis* zainstalowane i zarejestrowane za pośrednictwem pakietu VSIX.

::: moniker range="vs-2017"

4. Katalog Natvis specyficzny dla użytkownika (na przykład *%USERPROFILE%\Documents\Visual Studio 2017 \ Wizualizatory*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Katalog Natvis specyficzny dla użytkownika (na przykład *%USERPROFILE%\Documents\Visual Studio 2019 \ Wizualizatory*).

::: moniker-end

5. Katalog Natvis całego systemu (*%VSInstallDir%\Common7\Packages\Debugger\Visualizers*). Ten katalog zawiera pliki *. Natvis* , które są instalowane z programem Visual Studio. Jeśli masz uprawnienia administratora, możesz dodać pliki do tego katalogu.

## <a name="modify-natvis-files-while-debugging"></a>Modyfikuj pliki Natvis podczas debugowania

Podczas debugowania projektu można zmodyfikować plik *. Natvis* w środowisku IDE. Otwórz plik w tym samym wystąpieniu programu Visual Studio, który jest debugowany, zmodyfikuj go i Zapisz. Gdy tylko plik zostanie zapisany, **zobaczysz** i zmienią **Ustawienia regionalne** w usłudze Windows Update, aby odzwierciedlić zmiany.

Można również dodawać lub usuwać pliki *Natvis* w debugowanym rozwiązaniu, a program Visual Studio dodaje lub usuwa odpowiednie wizualizacje.

Nie można zaktualizować plików *. Natvis* , które są osadzone w plikach *. pdb* podczas debugowania.

Jeśli zmodyfikujesz plik *. Natvis* poza programem Visual Studio, zmiany nie zaczną obowiązywać automatycznie. Aby zaktualizować okna debugera, można wykonać ponowną ocenę polecenia **. natvisreload** w oknie **bezpośrednim** . Następnie zmiany zostaną zastosowane bez ponownego uruchomienia sesji debugowania.

Należy również użyć polecenia **. natvisreload** , aby uaktualnić plik *. Natvis* do nowszej wersji. Na przykład plik *. Natvis* może zostać zaewidencjonowany do kontroli źródła i chcesz pobrać ostatnie zmiany, które ktoś inny wprowadził.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Wyrażenia i formatowanie
Wizualizacje Natvis używają wyrażeń języka C++ do określania elementów danych do wyświetlenia. Oprócz ulepszeń i ograniczeń języka C++ w debugerze, które są opisane w [operatorze kontekstu (c++)](../debugger/context-operator-cpp.md), należy pamiętać o następujących kwestiach:

- Wyrażenia Natvis są oceniane w kontekście wizualizacji obiektu, a nie od bieżącej ramki stosu. Na przykład `x` w wyrażeniu Natvis odwołuje się do pola o nazwie **x** w wizualizacji obiektu, a nie do zmiennej lokalnej o nazwie **x** w bieżącej funkcji. Nie można uzyskać dostępu do zmiennych lokalnych w wyrażeniach Natvis, chociaż można uzyskać dostęp do zmiennych globalnych.

- Wyrażenia Natvis nie umożliwiają oceny funkcji ani efektów ubocznych. Wywołania funkcji i operatory przypisania są ignorowane. Ponieważ [funkcje wewnętrzne debugera](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) są wolne od efektów ubocznych, mogą być swobodnie wywoływane z dowolnego wyrażenia Natvis, nawet jeśli inne wywołania funkcji są niedozwolone.

- Aby kontrolować sposób wyświetlania wyrażenia, można użyć dowolnego specyfikatora formatu opisanego w [specyfikatorach formatu w języku C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Specyfikatory formatu są ignorowane, gdy wpis jest używany wewnętrznie przez Natvis, takich jak `Size` wyrażenie w [rozwinięciu ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

>[!NOTE]
> Ponieważ dokument Natvis jest XML, wyrażenia nie mogą bezpośrednio korzystać z operatorów "handlowe", większe niż, ani przesunięcia. Należy zmienić te znaki zarówno w treści elementu, jak i instrukcji warunku. Na przykład:<br>
> \<Item Name="HiByte"\>Bajc (_flags \& gt; \& gt 24), x\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) == 0"\>Dawaj\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) != 0"\>Pewnego\</Item\>

## <a name="natvis-views"></a>Widoki Natvis

Można zdefiniować różne widoki Natvis do wyświetlania typów na różne sposoby. Na przykład Oto Wizualizacja `std::vector` , która definiuje uproszczony widok o nazwie `simple` . `DisplayString`Elementy i są `ArrayItems` wyświetlane w widoku domyślnym i `simple` widoku, podczas gdy `[size]` `[capacity]` elementy i nie są wyświetlane w `simple` widoku.

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

W oknie **czujki** Użyj specyfikatora formatu **widoku,** aby określić widok alternatywny. Widok prosty jest wyświetlany jako **VEC, View (Simple)**:

![okno wyrażeń kontrolnych z widokiem prostym](../debugger/media/watch-simpleview.png "okno wyrażeń kontrolnych z widokiem prostym")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Błędy Natvis

Gdy debuger napotyka błędy w wpisie wizualizacji, ignoruje je. Wyświetla typ w jego pierwotnej postaci lub wybiera inną odpowiednią wizualizację. Można użyć diagnostyki Natvis, aby zrozumieć, dlaczego debuger zignorował wpis wizualizacji i zobaczyć podstawową składnię i błędy analizy.

**Aby włączyć diagnostykę programu Natvis:**

- W obszarze **Narzędzia**  >  **Opcje** ( lub  >  **Opcje** debugowania) > **debugowanie**  >  **okno dane wyjściowe**, **Ustawianie komunikatów diagnostycznych Natvis (tylko C++)** do **błędów**, **ostrzeżeń** lub **pełnych**, a następnie wybierz przycisk **OK**.

Błędy pojawiają się w oknie **danych wyjściowych** .

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Dokumentacja składni Natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Element autowizualizatora
`AutoVisualizer`Element jest węzłem głównym pliku *. Natvis* i zawiera `xmlns:` atrybut Namespace.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

`AutoVisualizer`Element może mieć elementy podrzędne [Type](#BKMK_Type), [HRESULT](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)i [CustomVisualizer](#BKMK_CustomVisualizer) .

### <a name="type-element"></a><a name="BKMK_Type"></a> Element Type

Podstawowy `Type` wygląda podobnie do tego przykładu:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type`Element określa:

1. Typ, dla którego ma być używana Wizualizacja ( `Name` atrybut).

2. Wartość obiektu tego typu powinna wyglądać jak ( `DisplayString` element).

3. Elementy członkowskie typu powinny wyglądać podobnie, gdy użytkownik rozszerza typ w oknie zmiennych ( `Expand` węzeł).

#### <a name="templated-classes"></a>Klasy z szablonami
`Name`Atrybut `Type` elementu akceptuje gwiazdkę `*` jako symbol wieloznaczny, który może być używany dla nazw klas z szablonami.

W poniższym przykładzie jest używana ta sama Wizualizacja, niezależnie od tego, czy obiekt jest, czy `CAtlArray<int>` `CAtlArray<float>` . Jeśli istnieje konkretny wpis wizualizacji dla elementu `CAtlArray<float>` , ma pierwszeństwo przed ogólnym.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Parametry szablonu można odwoływać w wpisie wizualizacji, używając makr $T 1, $T 2 i tak dalej. Aby znaleźć przykłady tych makr, zobacz pliki *Natvis* dostarczone z programem Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Dopasowanie typu wizualizatora
Jeśli nie można zweryfikować wpisu wizualizacji, zostanie użyta Następna dostępna Wizualizacja.

#### <a name="inheritable-attribute"></a>Dziedziczony atrybut
Opcjonalny `Inheritable` atrybut określa, czy wizualizacja ma zastosowanie tylko do typu podstawowego, czy do typu podstawowego i wszystkich typów pochodnych. Wartość domyślna `Inheritable` to `true` .

W poniższym przykładzie Wizualizacja ma zastosowanie tylko do `BaseClass` typu:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priorytet — atrybut

Opcjonalny `Priority` atrybut określa kolejność, w której mają być używane definicje alternatywne, jeśli nie można przeanalizować definicji. Możliwe wartości `Priority` to:,, `Low` , `MediumLow` `Medium` `MediumHigh` i `High` . Wartość domyślna to `Medium`. Ten `Priority` atrybut odróżnia tylko między priorytetami w tym samym pliku *. Natvis* .

Poniższy przykład najpierw analizuje wpis pasujący do 2015 STL. Jeśli przeanalizowanie nie powiedzie się, używa alternatywnego wpisu dla wersji 2013 biblioteki STL:

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
Można umieścić `Optional` atrybut w dowolnym węźle. Jeśli Podwyrażenie w opcjonalnym węźle nie zostanie przeanalizowane, debuger zignoruje ten węzeł, ale stosuje pozostałe `Type` reguły. Następujący typ nie `[State]` jest opcjonalny, ale `[Exception]` jest opcjonalny.  Jeśli `MyNamespace::MyClass` ma pole o nazwie _ `M_exceptionHolder` , pojawi się zarówno `[State]` węzeł, jak i `[Exception]` węzeł, ale jeśli nie ma `_M_exceptionHolder` pola, `[State]` pojawia się tylko węzeł.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Atrybut warunku

Opcjonalny `Condition` atrybut jest dostępny dla wielu elementów wizualizacji i określa, kiedy używać reguły wizualizacji. Jeśli wyrażenie wewnątrz atrybutu warunku jest rozpoznawane jako `false` , reguła wizualizacji nie ma zastosowania. Jeśli wartość jest równa `true` lub nie ma `Condition` atrybutu, stosowana jest wizualizacja. Tego atrybutu można użyć dla logiki if-else w wpisach wizualizacji.

Na przykład następująca Wizualizacja ma dwa `DisplayString` elementy dla typu inteligentnego wskaźnika. Gdy `_Myptr` element członkowski jest pusty, warunek pierwszego `DisplayString` elementu jest rozpoznawany jako `true` , co spowoduje wyświetlenie formularza. Gdy `_Myptr` element członkowski nie jest pusty, warunek jest obliczany `false` , a drugi `DisplayString` element zostanie wyświetlony.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>IncludeView i ExcludeView — atrybuty

`IncludeView`Atrybuty i `ExcludeView` określają elementy do wyświetlania lub nie są wyświetlane w określonych widokach. Na przykład w poniższej specyfikacji Natvis programu w `std::vector` `simple` widoku nie są wyświetlane `[size]` `[capacity]` elementy i.

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

Można użyć `IncludeView` `ExcludeView` atrybutów i dla typów i poszczególnych członków.

### <a name="version-element"></a><a name="BKMK_Versioning"></a> Element wersji
`Version`Element Scopes wpis wizualizacji do określonego modułu i wersji. `Version`Element pozwala uniknąć kolizji nazw, zmniejsza nieumyślne niezgodności i umożliwia różne wizualizacje dla różnych wersji typów.

Jeśli wspólny plik nagłówka używany przez różne moduły definiuje typ, Wizualizacja wersji pojawia się tylko wtedy, gdy typ znajduje się w określonej wersji modułu.

W poniższym przykładzie Wizualizacja dotyczy tylko `DirectUI::Border` typu znalezionego w `Windows.UI.Xaml.dll` wersji od 1,0 do 1,5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Nie potrzebujesz jednocześnie `Min` i `Max` . Są to atrybuty opcjonalne. Nie są obsługiwane żadne symbole wieloznaczne.

`Name`Atrybut ma format *filename. ext*, taki jak *hello.exe* lub *some.dll*. Nazwy ścieżek nie są dozwolone.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> DisplayString, element
`DisplayString`Element określa ciąg, który ma być pokazywany jako wartość zmiennej. Akceptuje dowolne ciągi zmieszane z wyrażeniami. Wszystkie elementy wewnątrz nawiasów klamrowych są interpretowane jako wyrażenie. Na przykład następujący `DisplayString` wpis:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Oznacza, że zmienne typu `CPoint` są wyświetlane jak na poniższej ilustracji:

 ![Korzystanie z elementu DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Korzystanie z elementu DisplayString")

W `DisplayString` wyrażeniu `x` i `y` , które są elementami członkowskimi `CPoint` , znajdują się wewnątrz nawiasów klamrowych, więc ich wartości są oceniane. W przykładzie pokazano również, jak można wyjść z klamry klamrowej przy użyciu podwójnych nawiasów klamrowych ( `{{` lub `}}` ).

> [!NOTE]
> `DisplayString`Element jest jedynym elementem, który akceptuje dowolne ciągi i składnię nawiasów klamrowych. Wszystkie inne elementy wizualizacji akceptują tylko wyrażenia, które może oszacować debuger.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a> StringView, element

`StringView`Element definiuje wartość, którą debuger może wysłać do wbudowanego wizualizatora tekstu. Na przykład, mając następujące wizualizacje dla `ATL::CStringT` typu:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

`CStringT`Obiekt jest wyświetlany w oknie zmiennych, jak w tym przykładzie:

![CStringT — element klasy DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT — element klasy DisplayString")

Dodanie `StringView` elementu powoduje, że debuger może wyświetlić wartość jako wizualizację tekstu.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Podczas debugowania można wybrać ikonę lupy obok zmiennej, a następnie wybrać **wizualizator tekstu** , aby wyświetlić ciąg, do którego **m_pszData** wskazuje.

 ![CStringT danych za pomocą wizualizatora StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT danych za pomocą wizualizatora StringView")

Wyrażenie `{m_pszData,su}` zawiera specyfikator formatu języka C++, aby wyświetlić wartość jako ciąg Unicode. Aby uzyskać więcej informacji, zobacz [specyfikatory formatu w języku C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a> Rozwiń element

Opcjonalny `Expand` węzeł dostosowuje elementy podrzędne typu wizualizacji po rozwinięciu tego typu w oknie zmiennych. `Expand`Węzeł akceptuje listę węzłów podrzędnych, które definiują elementy podrzędne.

- Jeśli `Expand` węzeł nie jest określony w wpisie wizualizacji, elementy podrzędne używają domyślnych reguł rozszerzania.

- Jeśli `Expand` węzeł jest określony bez węzłów podrzędnych, nie można rozwinąć tego typu w oknach debugera.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Rozszerzenie elementu

 `Item`Element jest najbardziej podstawowym i typowym elementem w `Expand` węźle. `Item` definiuje pojedynczy element podrzędny. Na przykład `CRect` Klasa z polami,, `top` `left` `right` i `bottom` zawiera następujący wpis wizualizacji:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

W oknie debugera `CRect` Typ wygląda podobnie do tego przykładu:

![CRect z rozwinięciem elementu elementu](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect z rozwinięciem elementu elementu")

Debuger oblicza wyrażenia określone w `Width` `Height` elementach i i wyświetla wartości w kolumnie **wartość** w oknie zmiennych.

Debuger automatycznie tworzy węzeł **[RAW View]** dla każdego rozszerzenia niestandardowego. Poprzedni zrzut ekranu wyświetla rozwinięty węzeł **[widok nieprzetworzony]** , aby pokazać, jak domyślny nieprzetworzony widok obiektu różni się od wizualizacji Natvis. Domyślne rozwijanie tworzy poddrzewo dla klasy bazowej i wyświetla wszystkie elementy członkowskie danych klasy podstawowej jako elementy podrzędne.

> [!NOTE]
> Jeśli wyrażenie elementu Item wskazuje typ złożony, sam węzeł **elementu** jest rozwijany.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> Rozwinięcie ArrayItems
Użyj `ArrayItems` węzła, aby debuger programu Visual Studio interpretuje typ jako tablicę i wyświetlał jego poszczególne elementy. Wizualizacja dla programu `std::vector` jest dobrym przykładem:

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

A `std::vector` pokazuje poszczególne elementy po rozwinięciu w oknie zmiennych:

![std:: Vector przy użyciu rozszerzenia ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: Vector przy użyciu rozszerzenia ArrayItems")

`ArrayItems`Węzeł musi mieć:

- `Size`Wyrażenie (które musi oszacować do liczby całkowitej), aby debuger mógł zrozumieć długość tablicy.
- Wyrażenie wskazujące `ValuePointer` na pierwszy element (który musi być wskaźnikiem typu elementu, który nie jest `void*` ).

Wartość domyślna dolnej granicy tablicy wynosi 0. Aby zastąpić wartość, użyj `LowerBound` elementu. Pliki *. Natvis* dostarczane z programem Visual Studio zawierają przykłady.

>[!NOTE]
>Operatora można używać `[]` na przykład `vector[i]` z dowolną wizualizacją tablicową jednowymiarową używaną `ArrayItems` , nawet jeśli sam typ (na przykład `CATLArray` ) nie zezwala na ten operator.

Można również określić wielowymiarowe tablice. W takim przypadku debuger potrzebuje nieco więcej informacji, aby prawidłowo wyświetlać elementy podrzędne:

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

- `Direction` Określa, czy tablica jest w kolejności głównej wiersza czy kolumny.
- `Rank` Określa rangę tablicy.
- `Size`Element akceptuje niejawny `$i` parametr, który zastępuje indeks wymiaru, aby znaleźć długość tablicy w tym wymiarze. W poprzednim przykładzie wyrażenie `_M_extent.M_base[0]` powinno podawać długość wymiaru 0th, `_M_extent._M_base[1]` 1 i tak dalej.

Poniżej przedstawiono sposób, w jaki obiekt dwuwymiarowy `Concurrency::array` przeszukuje okno debugera:

![Dwuwymiarowa tablica z rozszerzeniem ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Dwuwymiarowa tablica z rozszerzeniem ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Rozwinięcie IndexListItems

Można użyć `ArrayItems` rozwinięcia tylko wtedy, gdy elementy tablicy są ułożone w sposób ciągły w pamięci. Debuger przechodzi do następnego elementu, po prostu zwiększając jego wskaźnik. Jeśli potrzebujesz manipulować indeksem w węźle Value, użyj `IndexListItems` węzłów. Oto Wizualizacja z `IndexListItems` węzłem:

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

Jedyną różnicą między `ArrayItems` i `IndexListItems` jest `ValueNode` , która oczekuje pełnego wyrażenia do i<sup>ty</sup> elementu z niejawnym `$i` parametrem.

>[!NOTE]
>Operatora można używać `[]` na przykład `vector[i]` z dowolną wizualizacją tablicową jednowymiarową używaną `IndexListItems` , nawet jeśli sam typ (na przykład `CATLArray` ) nie zezwala na ten operator.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Rozwinięcie LinkedListItems

Jeśli typ wizualizacji reprezentuje listę połączoną, debuger może wyświetlić jego elementy podrzędne przy użyciu `LinkedListItems` węzła. Następująca Wizualizacja dla `CAtlList` typu jest stosowana `LinkedListItems` :

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

`Size`Element odnosi się do długości listy. `HeadPointer` wskazuje na pierwszy element, `NextPointer` odnosi się do następnego elementu i `ValueNode` odwołuje się do wartości elementu.

Debuger oblicza `NextPointer` `ValueNode` wyrażenia i w kontekście `LinkedListItems` elementu węzła, a nie typu listy nadrzędnej. W poprzednim przykładzie `CAtlList` ma `CNode` klasę (znalezioną w elemencie `atlcoll.h` ), która jest węzłem listy połączonej. `m_pNext` i `m_element` są polami tej `CNode` klasy, a nie z `CAtlList` klasą.

`ValueNode` może pozostać puste lub użyć, `this` Aby odwołać się do `LinkedListItems` samego węzła.

#### <a name="customlistitems-expansion"></a>Rozwinięcie CustomListItems

`CustomListItems`Rozszerzenie umożliwia pisanie logiki niestandardowej do przechodzenia ze strukturą danych, taką jak Hashtable. Służy `CustomListItems` do wizualizacji struktur danych, które mogą używać wyrażeń języka C++ dla wszystkiego, czego potrzebujesz do oszacowania, ale nie pasują do Mold dla `ArrayItems` , `IndexListItems` , lub `LinkedListItems` .

Można użyć, `Exec` Aby wykonać kod wewnątrz `CustomListItems` rozwinięcia, przy użyciu zmiennych i obiektów zdefiniowanych w rozwinięciu. Operatory logiczne, operatory arytmetyczne i operatory przypisania można używać razem z `Exec` . Nie można użyć `Exec` do obliczenia funkcji, z wyjątkiem [funkcji wewnętrznych debugera](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) obsługiwanych przez ewaluatora wyrażeń języka C++.

Poniższy wizualizator `CAtlMap` jest doskonałym przykładem, gdzie `CustomListItems` jest odpowiedni.

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

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Rozwinięcie TreeItems
 Jeśli typ wizualizacji reprezentuje drzewo, debuger może przeprowadzić drzewo i wyświetlić jego elementy podrzędne przy użyciu `TreeItems` węzła. Oto Wizualizacja dla `std::map` typu przy użyciu `TreeItems` węzła:

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

Składnia jest podobna do `LinkedListItems` węzła. `LeftPointer`, `RightPointer` , i `ValueNode` są oceniane w kontekście klasy węzła drzewa. `ValueNode` może pozostać puste lub użyć, `this` Aby odwołać się do `TreeItems` samego węzła.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Rozwinięcie ExpandedItem
 `ExpandedItem`Element generuje Zagregowany widok podrzędny przez wyświetlanie właściwości klas podstawowych lub składowych danych, tak jakby były elementami podrzędnymi typu wizualizacji. Debuger oblicza określone wyrażenie i dołącza podrzędne węzły wyniku do podrzędnej listy wizualizacji typu.

Na przykład typ inteligentnego wskaźnika `auto_ptr<vector<int>>` zwykle jest wyświetlany jako:

 ![Auto&#95;PTR&#60;wektor&#60;int&#62;&#62; domyślne rozwinięcie](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Domyślne rozwinięcie")

 Aby wyświetlić wartości wektora, należy przejść do szczegółów dwóch poziomów w oknie zmiennych, przechodząc przez `_Myptr` element członkowski. Poprzez dodanie `ExpandedItem` elementu można wyeliminować `_Myptr` zmienną z hierarchii i bezpośrednio przeglądać elementy wektorowe:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![Funkcja Auto&#95;PTR&#60;wektor&#60;int&#62;&#62; rozwinięcie ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Rozwinięcie ExpandedItem")

Poniższy przykład pokazuje, jak agregować właściwości z klasy podstawowej w klasie pochodnej. Załóżmy, że `CPanel` Klasa pochodzi od `CFrameworkElement` . Zamiast powtarzania właściwości, które pochodzą z klasy bazowej `CFrameworkElement` , `ExpandedItem` Wizualizacja węzła dołącza te właściwości do podrzędnej listy `CPanel` klasy.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Specyfikator formatu **ND** , który wyłącza dopasowanie wizualizacji dla klasy pochodnej, jest tutaj niezbędny. W przeciwnym razie wyrażenie `*(CFrameworkElement*)this` spowodowałoby `CPanel` ponowne zastosowanie wizualizacji, ponieważ domyślne reguły dopasowywania typów wizualizacji uważają, że są one najbardziej odpowiednie. Użyj specyfikatora formatu **ND** , aby polecić debugerowi użycie wizualizacji klasy bazowej lub domyślnego rozwinięcia, jeśli klasa bazowa nie ma wizualizacji.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Rozwinięcie elementu syntetycznego
 Gdy `ExpandedItem` element zawiera Flatter widok danych, eliminując hierarchie, `Synthetic` węzeł jest odwrotny. Umożliwia tworzenie sztucznego elementu podrzędnego, który nie jest wynikiem wyrażenia. Sztuczny element może mieć własne elementy podrzędne. W poniższym przykładzie Wizualizacja dla `Concurrency::array` typu używa `Synthetic` węzła, aby pokazać użytkownikowi komunikat diagnostyczny:

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

 ![Concurrency:: Array z syntetycznym rozszerzeniem elementu](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency:: Array z syntetycznym rozszerzeniem elementu")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> HResult, element
 `HResult`Element umożliwia dostosowanie informacji pokazywanych dla **HRESULT** w oknach debugera. `HRValue`Element musi zawierać 32-bitową wartość **HRESULT** , która ma zostać dostosowana. `HRDescription`Element zawiera informacje, które mają być wyświetlane w oknie debugera.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> UIVisualizer, element
`UIVisualizer`Element rejestruje wtyczkę wizualizacji graficznej przy użyciu debugera. Wizualizator graficzny tworzy okno dialogowe lub inny interfejs, który pokazuje zmienną lub obiekt w sposób spójny z typem danych. Wtyczka wizualizatora musi zostać utworzona jako [pakietu VSPackage](../extensibility/internals/vspackages.md)i musi uwidaczniać usługę, którą może wykorzystać debuger. Plik *. Natvis* zawiera informacje o rejestracji wtyczki, takie jak nazwa, identyfikator GUID uwidocznionej usługi i typy, które mogą być wizualizowane.

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

- `ServiceId`  -  `Id` Para atrybutów identyfikuje `UIVisualizer` . `ServiceId`Jest identyfikatorem GUID usługi udostępnianej przez pakiet wizualizatora. `Id` jest unikatowym identyfikatorem odróżniającym Wizualizatory, jeśli usługa zawiera więcej niż jeden. W poprzednim przykładzie ta sama usługa wizualizatora udostępnia dwa Wizualizatory.

- `MenuName`Atrybut definiuje nazwę wizualizatora do wyświetlenia na liście rozwijanej obok ikony lupy w debugerze. Na przykład:

  ![Menu skrótów menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menu skrótów menu UIVisualizer")

Każdy typ zdefiniowany w pliku *Natvis* musi jawnie zawierać wszystkie WIZUALIZATORY interfejsu użytkownika, które mogą je wyświetlić. Debuger dopasowuje odwołania wizualizatora w wpisach typu do zarejestrowanych wizualizatorów. Na przykład następujący wpis typu w odniesieniu do `std::vector` odwołania do `UIVisualizer` powyższego przykładu.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Można zobaczyć przykład `UIVisualizer` w rozszerzeniu [Obejrzyj obraz](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) , służącym do wyświetlania map bitowych w pamięci.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>CustomVisualizer, element
 `CustomVisualizer` jest punktem rozszerzalności, który określa rozszerzenie VSIX, które można napisać, aby kontrolować wizualizacje w programie Visual Studio Code. Aby uzyskać więcej informacji na temat pisania rozszerzeń VSIX, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Jest to znacznie większa ilość pracy, która pozwala napisać wizualizację niestandardową niż definicja pliku Natvis XML, ale nie jest to ograniczenie dotyczące tego, co plik Natvis działa lub nie obsługuje. Wizualizacje niestandardowe mają dostęp do pełnego zestawu interfejsów API rozszerzalności debugera, które mogą wysyłać zapytania i modyfikować proces debugowanego obiektu lub komunikować się z innymi częściami programu Visual Studio.

 Można użyć `Condition` `IncludeView` atrybutów, i `ExcludeView` dla `CustomVisualizer` elementów.

## <a name="limitations"></a>Ograniczenia

Dostosowania Natvis współpracują z klasami i strukturami, ale nie z typedef.

Natvis nie obsługuje wizualizatorów dla typów pierwotnych (na przykład, `int` `bool` ) lub dla wskaźników do typów pierwotnych. W tym scenariuszu jedną z opcji jest użycie [specyfikatora formatu](../debugger/format-specifiers-in-cpp.md) odpowiedniego dla Twojego przypadku użycia. Na przykład jeśli używasz `double* mydoublearray` w kodzie, możesz użyć specyfikatora formatu tablicy w oknie **czujki** debugera, takiego jak wyrażenie `mydoublearray, [100]` , które pokazuje pierwsze 100 elementów.

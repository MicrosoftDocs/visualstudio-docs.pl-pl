---
title: Tworzenie niestandardowych widoków obiektów C++
description: Użyj struktury Natvis, aby dostosować sposób, w jaki program Visual Studio Wyświetla natywne typy w debugerze
ms.date: 10/31/2018
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
ms.openlocfilehash: 61a8cce68a55f6db26de7754bdfc9dda196c457a
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091786"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Tworzenie niestandardowych widoków C++ obiektów w debugerze przy użyciu struktury Natvis

Struktura programu Visual Studio *Natvis* dostosowuje sposób, w jaki typy natywne są wyświetlane w oknach zmiennych debugera, takich jak **Ustawienia regionalne** i okna **czujki** , oraz w **etykietkach**danych. Wizualizacje Natvis mogą pomóc w tworzeniu typów, które można wyświetlić podczas debugowania.

Natvis zastępuje plik *autoexp. dat* we wcześniejszych wersjach programu Visual Studio z SKŁADNIĄ języka XML, lepszą diagnostyką, przechowywaniem wersji i obsługą wielu plików.

> [!NOTE]
> Dostosowania Natvis współpracują z klasami i strukturami, ale nie z typedef.

## <a name="BKMK_Why_create_visualizations_"></a>Wizualizacje Natvis

Struktura Natvis służy do tworzenia reguł wizualizacji dla tworzonych typów, dzięki czemu deweloperzy mogą łatwiej widzieć je podczas debugowania.

Na przykład na poniższej ilustracji przedstawiono zmienną typu [Windows:: UI:: XAML:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) w oknie debugera bez zastosowanych niestandardowych wizualizacji.

![Wizualizacja domyślna TextBox](../debugger/media/dbg_natvis_textbox_default.png "Wizualizacja domyślna TextBox")

Wyróżniony wiersz zawiera właściwość `Text` klasy `TextBox`. Złożona hierarchia klas utrudnia znalezienie tej właściwości. Debuger nie wie, jak interpretować niestandardowy typ ciągu, dlatego nie można zobaczyć ciągu przechowywanego wewnątrz pola tekstowego.

Ten sam `TextBox` wygląda znacznie prostsze w oknie zmiennych, gdy stosowane są reguły niestandardowego wizualizatora Natvis. Ważne elementy członkowskie klasy są wyświetlane razem, a debuger pokazuje podstawową wartość ciągu niestandardowego typu ciągu.

![Dane TextBox przy użyciu wizualizatora](../debugger/media/dbg_natvis_textbox_visualizer.png "Dane TextBox przy użyciu wizualizatora")

## <a name="BKMK_Using_Natvis_files"></a>Korzystanie z plików. Natvis C++ w projektach

Plik Natvis używa plików *. Natvis* , aby określić reguły wizualizacji. Plik *. Natvis* jest plikiem XML z rozszerzeniem *. Natvis* . Schemat Natvis został zdefiniowany w *%VSInstallDir%\Xml\Schemas\natvis.xsd*.

Podstawowa struktura pliku *Natvis* to jeden lub więcej elementów `Type` reprezentujących wpisy wizualizacji. W pełni kwalifikowana nazwa każdego elementu `Type` jest określona w jego atrybut `Name`.

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

### <a name="add-a-natvis-file-to-a-c-project"></a>Dodawanie pliku. Natvis do C++ projektu

Plik *. Natvis* można dodać do dowolnego C++ projektu.

**Aby dodać nowy plik *Natvis* :**

1. Wybierz węzeł C++ projektu w **Eksplorator rozwiązań**i wybierz pozycję **projekt** > **Dodaj nowy element**lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz opcję **Narzędzie**  **C++ Visual** >  > **plik wizualizacji debugera (. Natvis)** .

1. Nazwij plik, a następnie wybierz pozycję **Dodaj**.

   Nowy plik zostanie dodany do **Eksplorator rozwiązań**i otwarty w okienku dokumentu programu Visual Studio.

Debuger programu Visual Studio ładuje pliki *Natvis* w C++ projektach automatycznie, a domyślnie dołącza je do pliku *. pdb* podczas kompilowania projektu. W przypadku debugowania skompilowanej aplikacji debuger ładuje plik *. Natvis* z pliku *. pdb* , nawet jeśli nie ma otwartego projektu. Jeśli nie chcesz, aby plik *. Natvis* został uwzględniony w pliku *. pdb*, możesz go wykluczyć z skompilowanego plik *. pdb* .

**Aby wykluczyć plik *. Natvis* z pliku *. pdb*:**

1. Wybierz plik *. Natvis* w **Eksplorator rozwiązań**i wybierz ikonę **Właściwości** lub kliknij plik prawym przyciskiem myszy, a następnie wybierz polecenie **Właściwości**.

1. Rozwiń strzałkę obok pozycji **wykluczone z kompilacji** i wybierz opcję **tak**, a następnie wybierz przycisk **OK**.

>[!NOTE]
>W przypadku debugowania projektów wykonywalnych Użyj elementów rozwiązania, aby dodać dowolne pliki *. Natvis* , które nie znajdują się w pliku *. pdb*, C++ ponieważ nie ma dostępnego projektu.

>[!NOTE]
>Reguły Natvis zostały załadowane z *. pdb* stosuje się tylko do typów modułów, do których odwołuje się plik. *PDB* . Na przykład jeśli *Module1. pdb* ma wpis Natvis dla typu o nazwie `Test`, dotyczy tylko klasy `Test` w *Module1. dll*. Jeśli inny moduł również definiuje klasę o nazwie `Test`, wpis Natvis *Module1. pdb* nie dotyczy tego elementu.

### <a name="BKMK_natvis_location"></a>Lokalizacje plików Natvis

Pliki *. Natvis* można dodać do katalogu użytkownika lub do katalogu systemowego, jeśli mają być stosowane do wielu projektów.

Pliki *. Natvis* są oceniane w następującej kolejności:

1. Wszystkie pliki *. Natvis* , które są osadzone w debugowanym pliku *. pdb* , chyba że plik o tej samej nazwie istnieje w załadowanym projekcie.

2. Wszystkie pliki *Natvis* , które znajdują się w C++ załadowanym projekcie lub w rozwiązaniu najwyższego poziomu. Ta grupa zawiera wszystkie załadowane C++ projekty, w tym biblioteki klas, ale nie projekty w innych językach.

::: moniker range="vs-2017"

3. Katalog Natvis specyficzny dla użytkownika (na przykład *%USERPROFILE%\Documents\Visual Studio 2017 \ Wizualizatory*).

::: moniker-end

::: moniker range=">= vs-2019"

3. Katalog Natvis specyficzny dla użytkownika (na przykład *%USERPROFILE%\Documents\Visual Studio 2019 \ Wizualizatory*).

::: moniker-end

4. Katalog Natvis całego systemu ( *%VSInstallDir%\Common7\Packages\Debugger\Visualizers*). Ten katalog zawiera pliki *. Natvis* , które są instalowane z programem Visual Studio. Jeśli masz uprawnienia administratora, możesz dodać pliki do tego katalogu.

## <a name="modify-natvis-files-while-debugging"></a>Modyfikuj pliki Natvis podczas debugowania

Podczas debugowania projektu można zmodyfikować plik *. Natvis* w środowisku IDE. Otwórz plik w tym samym wystąpieniu programu Visual Studio, który jest debugowany, zmodyfikuj go i Zapisz. Gdy tylko plik zostanie zapisany, **zobaczysz** i zmienią **Ustawienia regionalne** w usłudze Windows Update, aby odzwierciedlić zmiany.

Można również dodawać lub usuwać pliki *Natvis* w debugowanym rozwiązaniu, a program Visual Studio dodaje lub usuwa odpowiednie wizualizacje.

Nie można zaktualizować plików *. Natvis* , które są osadzone w plikach *. pdb* podczas debugowania.

Jeśli zmodyfikujesz plik *. Natvis* poza programem Visual Studio, zmiany nie zaczną obowiązywać automatycznie. Aby zaktualizować okna debugera, można wykonać ponowną ocenę polecenia **. natvisreload** w oknie **czujki** . Następnie zmiany zostaną zastosowane bez ponownego uruchomienia sesji debugowania.

Należy również użyć polecenia **. natvisreload** , aby uaktualnić plik *. Natvis* do nowszej wersji. Na przykład plik *. Natvis* może zostać zaewidencjonowany do kontroli źródła i chcesz pobrać ostatnie zmiany, które ktoś inny wprowadził.

## <a name="BKMK_Expressions_and_formatting"></a>Wyrażenia i formatowanie
Wizualizacje Natvis używają C++ wyrażeń do określania elementów danych do wyświetlenia. Oprócz ulepszeń i ograniczeń C++ wyrażeń w debugerze, które są opisane w [operatorze kontekstu (C++)](../debugger/context-operator-cpp.md), należy pamiętać o następujących kwestiach:

- Wyrażenia Natvis są oceniane w kontekście wizualizacji obiektu, a nie od bieżącej ramki stosu. Na przykład `x` w wyrażeniu Natvis odwołuje się do pola o nazwie **x** w wizualizacji obiektu, a nie do zmiennej lokalnej o nazwie **x** w bieżącej funkcji. Nie można uzyskać dostępu do zmiennych lokalnych w wyrażeniach Natvis, chociaż można uzyskać dostęp do zmiennych globalnych.

- Wyrażenia Natvis nie umożliwiają oceny funkcji ani efektów ubocznych. Wywołania funkcji i operatory przypisania są ignorowane. Ponieważ [funkcje wewnętrzne debugera](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) są wolne od efektów ubocznych, mogą być swobodnie wywoływane z dowolnego wyrażenia Natvis, nawet jeśli inne wywołania funkcji są niedozwolone.

- Aby kontrolować sposób wyświetlania wyrażenia, można użyć dowolnego specyfikatora formatu opisanego w [specyfikatorach formatu w C++ ](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Specyfikatory formatu są ignorowane, gdy wpis jest używany wewnętrznie przez Natvis, takich jak wyrażenie `Size` w [rozszerzeniu ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Widoki Natvis

Można zdefiniować różne widoki Natvis do wyświetlania typów na różne sposoby. Na przykład poniżej przedstawiono wizualizację `std::vector`, która definiuje uproszczony widok o nazwie `simple`. `DisplayString` i `ArrayItems` elementy są wyświetlane w widoku domyślnym i `simple` widoku, podczas gdy elementy `[size]` i `[capacity]` nie są wyświetlane w widoku `simple`.

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

W oknie **czujki** Użyj specyfikatora formatu **widoku,** aby określić widok alternatywny. Widok prosty jest wyświetlany jako **VEC, View (Simple)** :

![okno wyrażeń kontrolnych z widokiem prostym](../debugger/media/watch-simpleview.png "okno wyrażeń kontrolnych z widokiem prostym")

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Błędy Natvis

Gdy debuger napotyka błędy w wpisie wizualizacji, ignoruje je. Wyświetla typ w jego pierwotnej postaci lub wybiera inną odpowiednią wizualizację. Można użyć diagnostyki Natvis, aby zrozumieć, dlaczego debuger zignorował wpis wizualizacji i zobaczyć podstawową składnię i błędy analizy.

**Aby włączyć diagnostykę programu Natvis:**

- W **obszarze narzędzia** > **Opcje** ( **lub Debuguj** > **Opcje**) > **debugowanie** > **okno dane wyjściowe**, ustaw **komunikaty diagnostyczne NatvisC++ (tylko)** na **błąd**, **Ostrzeżenie**lub **pełne**, a następnie wybierz przycisk **OK**.

Błędy pojawiają się w oknie **danych wyjściowych** .

## <a name="BKMK_Syntax_reference"></a>Dokumentacja składni Natvis

### <a name="BKMK_AutoVisualizer"></a>Element autowizualizatora
Element `AutoVisualizer` jest węzłem głównym pliku *. Natvis* i zawiera `xmlns:` atrybutu Namespace.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Element `AutoVisualizer` może mieć elementy podrzędne [Type](#BKMK_Type), [HRESULT](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)i [CustomVisualizer](#BKMK_CustomVisualizer) .

### <a name="BKMK_Type"></a>Element Type

Podstawowa `Type` wygląda następująco:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Element `Type` określa:

1. Typ, dla którego ma być używana Wizualizacja (atrybut `Name`).

2. Wartość obiektu tego typu powinna wyglądać jak (`DisplayString` elementu).

3. Elementy członkowskie typu powinny wyglądać podobnie, gdy użytkownik rozszerza typ w oknie zmiennych (`Expand` węzła).

#### <a name="templated-classes"></a>Klasy z szablonami
Atrybut `Name` elementu `Type` akceptuje gwiazdki `*` jako symbol wieloznaczny, który może być używany dla nazw klas z szablonami.

W poniższym przykładzie jest używana ta sama Wizualizacja, niezależnie od tego, czy obiekt jest `CAtlArray<int>`, czy `CAtlArray<float>`. Jeśli dla `CAtlArray<float>`istnieje konkretny wpis wizualizacji, ma on pierwszeństwo przed ogólnym.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Parametry szablonu można odwoływać w wpisie wizualizacji, używając makr $T 1, $T 2 i tak dalej. Aby znaleźć przykłady tych makr, zobacz pliki *Natvis* dostarczone z programem Visual Studio.

#### <a name="BKMK_Visualizer_type_matching"></a>Dopasowanie typu wizualizatora
Jeśli nie można zweryfikować wpisu wizualizacji, zostanie użyta Następna dostępna Wizualizacja.

#### <a name="inheritable-attribute"></a>Dziedziczony atrybut
Opcjonalny atrybut `Inheritable` określa, czy wizualizacja ma zastosowanie tylko do typu podstawowego, czy do typu podstawowego i wszystkich typów pochodnych. Wartość domyślna `Inheritable` jest `true`.

W poniższym przykładzie Wizualizacja dotyczy tylko typu `BaseClass`:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priorytet — atrybut

Opcjonalny atrybut `Priority` określa kolejność, w której mają być używane definicje alternatywne, jeśli nie można przeanalizować definicji. Możliwe wartości `Priority` to: `Low`, `MediumLow`,`Medium`, `MediumHigh`i `High`. Wartość domyślna to `Medium`. Atrybut `Priority` odróżnia tylko między priorytetami w tym samym pliku *. Natvis* .

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
Atrybut `Optional` można umieścić w dowolnym węźle. Jeśli Podwyrażenie w opcjonalnym węźle nie zostanie przeanalizowane, debuger zignoruje ten węzeł, ale stosuje pozostałe reguły `Type`. W poniższym typie `[State]` nie jest opcjonalny, ale `[Exception]` jest opcjonalne.  Jeśli `MyNamespace::MyClass` ma pole o nazwie _`M_exceptionHolder`, pojawi się zarówno węzeł `[State]`, jak i węzeł `[Exception]`, ale jeśli nie ma pola `_M_exceptionHolder`, pojawi się tylko węzeł `[State]`.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="BKMK_Condition_attribute"></a>Atrybut warunku

Opcjonalny atrybut `Condition` jest dostępny dla wielu elementów wizualizacji i określa, kiedy używać reguły wizualizacji. Jeśli wyrażenie wewnątrz atrybutu warunku jest rozpoznawane jako `false`, reguła wizualizacji nie ma zastosowania. Jeśli zostanie wyznaczona wartość `true`lub nie ma atrybutu `Condition`, zostanie zastosowana Wizualizacja. Tego atrybutu można użyć dla logiki if-else w wpisach wizualizacji.

Na przykład następująca Wizualizacja ma dwa elementy `DisplayString` dla typu inteligentnego wskaźnika. Gdy element członkowski `_Myptr` jest pusty, warunek pierwszego elementu `DisplayString` jest rozpoznawany jako `true`, tak że formularz zostanie wyświetlony. Gdy członek `_Myptr` nie jest pusty, warunek szacuje się na `false`, a drugi `DisplayString` element zostanie wyświetlony.

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

Atrybuty `IncludeView` i `ExcludeView` określają elementy do wyświetlenia lub nie są wyświetlane w określonych widokach. Na przykład w poniższej specyfikacji Natvis dla `std::vector`widok `simple` nie wyświetla `[size]` i `[capacity]` elementów.

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

Atrybutów `IncludeView` i `ExcludeView` można użyć dla typów i poszczególnych członków.

### <a name="BKMK_Versioning"></a>Element wersji
Element `Version` zakresuje wpis wizualizacji do określonego modułu i wersji. Element `Version` pozwala uniknąć kolizji nazw, zmniejsza nieumyślne niezgodności i umożliwia różne wizualizacje dla różnych wersji typów.

Jeśli wspólny plik nagłówka używany przez różne moduły definiuje typ, Wizualizacja wersji pojawia się tylko wtedy, gdy typ znajduje się w określonej wersji modułu.

W poniższym przykładzie Wizualizacja dotyczy tylko typu `DirectUI::Border` znalezionego w `Windows.UI.Xaml.dll` z wersji 1,0 do 1,5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Nie potrzebujesz jednocześnie `Min` i `Max`. Są to atrybuty opcjonalne. Nie są obsługiwane żadne symbole wieloznaczne.

Atrybut `Name` ma format *filename. ext*, taki jak *Hello. exe* lub *plik. dll*. Nazwy ścieżek nie są dozwolone.

### <a name="BKMK_DisplayString"></a>DisplayString, element
Element `DisplayString` określa ciąg, który ma być wyświetlany jako wartość zmiennej. Akceptuje dowolne ciągi zmieszane z wyrażeniami. Wszystkie elementy wewnątrz nawiasów klamrowych są interpretowane jako wyrażenie. Na przykład następujący wpis `DisplayString`:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Oznacza, że zmienne typu `CPoint` wyświetlane jak na poniższej ilustracji:

 ![Korzystanie z elementu DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Korzystanie z elementu DisplayString")

W wyrażeniu `DisplayString` `x` i `y`, które są elementami członkowskimi `CPoint`, znajdują się wewnątrz nawiasów klamrowych, więc ich wartości są oceniane. W przykładzie pokazano również, jak można wyjść z klamry klamrowej przy użyciu podwójnych nawiasów klamrowych (`{{` lub `}}`).

> [!NOTE]
> Element `DisplayString` jest jedynym elementem, który akceptuje dowolne ciągi i składnię nawiasów klamrowych. Wszystkie inne elementy wizualizacji akceptują tylko wyrażenia, które może oszacować debuger.

### <a name="BKMK_StringView"></a>StringView, element

Element `StringView` definiuje wartość, którą debuger może wysłać do wbudowanego wizualizatora tekstu. Na przykład, mając następujące wizualizacje dla typu `ATL::CStringT`:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Obiekt `CStringT` jest wyświetlany w oknie zmiennych podobnym do tego przykładu:

![CStringT — element klasy DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT — element klasy DisplayString")

Dodanie elementu `StringView` informuje debuger, że może wyświetlić wartość jako wizualizację tekstu.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Podczas debugowania można wybrać ikonę lupy obok zmiennej, a następnie wybrać **wizualizator tekstu** , aby wyświetlić ciąg, do którego **m_pszData** wskazuje.

 ![CStringT danych za pomocą wizualizatora StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT danych za pomocą wizualizatora StringView")

Wyrażenie `{m_pszData,su}` zawiera specyfikator C++ formatu **Su**, aby wyświetlić wartość jako ciąg Unicode. Aby uzyskać więcej informacji, zobacz [specyfikatory formatu C++w ](../debugger/format-specifiers-in-cpp.md).

### <a name="BKMK_Expand"></a>Rozwiń element

Opcjonalny węzeł `Expand` dostosowuje elementy podrzędne typu wizualizacji po rozwinięciu tego typu w oknie zmiennych. Węzeł `Expand` akceptuje listę węzłów podrzędnych, które definiują elementy podrzędne.

- Jeśli węzeł `Expand` nie jest określony w wpisie wizualizacji, elementy podrzędne używają domyślnych reguł rozszerzania.

- Jeśli węzeł `Expand` jest określony bez węzłów podrzędnych, nie można rozwinąć tego typu w oknach debugera.

#### <a name="BKMK_Item_expansion"></a>Rozszerzenie elementu

 Element `Item` jest najbardziej podstawowym i typowym elementem w węźle `Expand`. `Item` definiuje pojedynczy element podrzędny. Na przykład Klasa `CRect` z polami `top`, `left`, `right`i `bottom` zawiera następujący wpis wizualizacji:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

W oknie debugera typ `CRect` wygląda następująco:

![CRect z rozwinięciem elementu elementu](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect z rozwinięciem elementu elementu")

Debuger oblicza wyrażenia określone w `Width` i `Height` elementów, a następnie wyświetla wartości w kolumnie **wartość** w oknie zmiennych.

Debuger automatycznie tworzy węzeł **[RAW View]** dla każdego rozszerzenia niestandardowego. Poprzedni zrzut ekranu wyświetla rozwinięty węzeł **[widok nieprzetworzony]** , aby pokazać, jak domyślny nieprzetworzony widok obiektu różni się od wizualizacji Natvis. Domyślne rozwijanie tworzy poddrzewo dla klasy bazowej i wyświetla wszystkie elementy członkowskie danych klasy podstawowej jako elementy podrzędne.

> [!NOTE]
> Jeśli wyrażenie elementu Item wskazuje typ złożony, sam węzeł **elementu** jest rozwijany.

#### <a name="BKMK_ArrayItems_expansion"></a>Rozwinięcie ArrayItems
Użyj węzła `ArrayItems`, aby debuger programu Visual Studio interpretuje typ jako tablicę i wyświetlał poszczególne elementy. Wizualizacja dla `std::vector` jest dobrym przykładem:

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

W oknie zmiennych `std::vector` są wyświetlane poszczególne elementy:

![std:: Vector przy użyciu rozszerzenia ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: Vector przy użyciu rozszerzenia ArrayItems")

Węzeł `ArrayItems` musi mieć:

- Wyrażenie `Size` (które musi zostać oszacowane jako liczba całkowita), aby debuger mógł zrozumieć długość tablicy.
- Wyrażenie `ValuePointer` wskazujące na pierwszy element (który musi być wskaźnikiem typu elementu, który nie jest `void*`).

Wartość domyślna dolnej granicy tablicy wynosi 0. Aby zastąpić wartość, użyj elementu `LowerBound`. Pliki *. Natvis* dostarczane z programem Visual Studio zawierają przykłady.

>[!NOTE]
>Można użyć operatora `[]`, na przykład `vector[i]`, z dowolną wizualizacją tablicową jednowymiarową, która używa `ArrayItems`, nawet jeśli sam typ (na przykład `CATLArray`) nie zezwala na ten operator.

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

- `Direction` określa, czy tablica jest w kolejności rzędów głównych czy kolumnowych.
- `Rank` określa rangę tablicy.
- Element `Size` akceptuje niejawny `$i` parametr, który zastępuje indeks wymiaru, aby znaleźć długość tablicy w tym wymiarze. W poprzednim przykładzie wyrażenie `_M_extent.M_base[0]` powinno dać długość wymiaru 0th, `_M_extent._M_base[1]` 1 i tak dalej.

Poniżej przedstawiono sposób, w jaki obiekt dwuwymiarowy `Concurrency::array` przeszukuje okno debugera:

![Dwuwymiarowa tablica z rozszerzeniem ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Dwuwymiarowa tablica z rozszerzeniem ArrayItems")

#### <a name="BKMK_IndexListItems_expansion"></a>Rozwinięcie IndexListItems

Można użyć rozwinięcia `ArrayItems` tylko wtedy, gdy elementy tablicy są ułożone w sposób ciągły w pamięci. Debuger przechodzi do następnego elementu, po prostu zwiększając jego wskaźnik. Jeśli potrzebujesz manipulować indeksem w węźle Value, użyj węzłów `IndexListItems`. Oto Wizualizacja z węzłem `IndexListItems`:

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

Jedyną różnicą między `ArrayItems` i `IndexListItems` jest `ValueNode`, która oczekuje pełnego wyrażenia do i<sup>ty</sup> elementu z niejawnym parametrem `$i`.

>[!NOTE]
>Można użyć operatora `[]`, na przykład `vector[i]`, z dowolną wizualizacją tablicową jednowymiarową, która używa `IndexListItems`, nawet jeśli sam typ (na przykład `CATLArray`) nie zezwala na ten operator.

#### <a name="BKMK_LinkedListItems_expansion"></a>Rozwinięcie LinkedListItems

Jeśli typ wizualizacji reprezentuje listę połączoną, debuger może wyświetlić jego elementy podrzędne przy użyciu węzła `LinkedListItems`. Następujące wizualizacje dla typu `CAtlList` używają `LinkedListItems`:

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

`Size` element odnosi się do długości listy. `HeadPointer` wskazuje na pierwszy element, `NextPointer` odnosi się do następnego elementu, a `ValueNode` odnosi się do wartości elementu.

Debuger oblicza wyrażenia `NextPointer` i `ValueNode` w kontekście `LinkedListItems` elementu węzła, a nie typu listy nadrzędnej. W poprzednim przykładzie `CAtlList` ma klasę `CNode` (znajdującą się w `atlcoll.h`), która jest węzłem listy połączonej. `m_pNext` i `m_element` są polami tej klasy `CNode`, a nie z klasą `CAtlList`.

`ValueNode` można pozostawić puste lub użyć `this`, aby odwołać się do węzła `LinkedListItems`.

#### <a name="customlistitems-expansion"></a>Rozwinięcie CustomListItems
Rozwinięcie `CustomListItems` pozwala pisać logikę niestandardową do przechodzenia ze strukturą danych, taką jak Hashtable. Użyj `CustomListItems` do wizualizacji struktur danych, które mogą C++ używać wyrażeń dla wszystkiego, czego potrzebujesz do obliczenia, ale nie pasują do mold dla `ArrayItems`, `IndexListItems`lub `LinkedListItems`.

Poniższy wizualizator dla `CAtlMap` to doskonały przykład, w którym `CustomListItems` jest odpowiedni.

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

Za pomocą `Exec` można wykonać kod wewnątrz `CustomListItems` rozwinięcia przy użyciu zmiennych i obiektów zdefiniowanych w rozwinięciu. Operatory logiczne, operatory arytmetyczne i operatory przypisania można używać z `Exec`. Nie można użyć `Exec` do szacowania funkcji.

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

#### <a name="BKMK_TreeItems_expansion"></a>Rozwinięcie TreeItems
 Jeśli typ wizualizacji reprezentuje drzewo, debuger może przeprowadzić drzewo i wyświetlić jego elementy podrzędne przy użyciu węzła `TreeItems`. Oto Wizualizacja dla typu `std::map` przy użyciu węzła `TreeItems`:

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

Składnia jest podobna do węzła `LinkedListItems`. `LeftPointer`, `RightPointer`i `ValueNode` są oceniane w kontekście klasy węzła drzewa. `ValueNode` można pozostawić puste lub użyć `this`, aby odwołać się do węzła `TreeItems`.

#### <a name="BKMK_ExpandedItem_expansion"></a>Rozwinięcie ExpandedItem
 Element `ExpandedItem` generuje Zagregowany widok podrzędny przez wyświetlanie właściwości klas bazowych lub składowych danych, tak jakby były elementami podrzędnymi typu wizualizacji. Debuger oblicza określone wyrażenie i dołącza podrzędne węzły wyniku do podrzędnej listy wizualizacji typu.

Na przykład typ inteligentnego wskaźnika `auto_ptr<vector<int>>` zwykle jest wyświetlany jako:

 ![rozwinięcie&#60;&#62; domyślnego&#60;rozmiaru&#62; wektora&#95;autoptr](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Domyślne rozwinięcie")

 Aby wyświetlić wartości wektora, należy przejść do szczegółów dwóch poziomów w oknie zmiennych, przechodząc przez składową `_Myptr`. Poprzez dodanie elementu `ExpandedItem` można wyeliminować zmienną `_Myptr` z hierarchii i bezpośrednio przeglądać elementy wektorowe:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![&#95;rozwinięcie&#60;&#62; ExpandedItem&#60;wektora&#62; autoptr](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Rozwinięcie ExpandedItem")

Poniższy przykład pokazuje, jak agregować właściwości z klasy podstawowej w klasie pochodnej. Załóżmy, że Klasa `CPanel` dziedziczy z `CFrameworkElement`. Zamiast powtarzania właściwości, które pochodzą z klasy podstawowej `CFrameworkElement`, Wizualizacja `ExpandedItem` węzła dołącza te właściwości do listy podrzędnej klasy `CPanel`.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Specyfikator formatu **ND** , który wyłącza dopasowanie wizualizacji dla klasy pochodnej, jest tutaj niezbędny. W przeciwnym razie wyrażenie `*(CFrameworkElement*)this` mogłoby spowodować ponowne zastosowanie wizualizacji `CPanel`, ponieważ domyślne reguły dopasowywania typów wizualizacji uważają, że są one najbardziej odpowiednie. Użyj specyfikatora formatu **ND** , aby polecić debugerowi użycie wizualizacji klasy bazowej lub domyślnego rozwinięcia, jeśli klasa bazowa nie ma wizualizacji.

#### <a name="BKMK_Synthetic_Item_expansion"></a>Rozwinięcie elementu syntetycznego
 Chociaż `ExpandedItem` element zawiera Flatter widok danych, eliminując hierarchie, węzeł `Synthetic` jest odwrotny. Umożliwia tworzenie sztucznego elementu podrzędnego, który nie jest wynikiem wyrażenia. Sztuczny element może mieć własne elementy podrzędne. W poniższym przykładzie Wizualizacja dla typu `Concurrency::array` używa węzła `Synthetic`, aby pokazać użytkownikowi komunikat diagnostyczny:

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

### <a name="BKMK_HResult"></a>HResult, element
 Element `HResult` umożliwia dostosowanie informacji pokazywanych dla **HRESULT** w oknach debugera. Element `HRValue` musi zawierać wartość 32-bitową **HRESULT** , która ma zostać dostosowana. Element `HRDescription` zawiera informacje, które mają być wyświetlane w oknie debugera.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="BKMK_UIVisualizer"></a>UIVisualizer, element
Element `UIVisualizer` rejestruje wtyczkę wizualizacji graficznej z debugerem. Wizualizator graficzny tworzy okno dialogowe lub inny interfejs, który pokazuje zmienną lub obiekt w sposób spójny z typem danych. Wtyczka wizualizatora musi zostać utworzona jako [pakietu VSPackage](../extensibility/internals/vspackages.md)i musi uwidaczniać usługę, którą może wykorzystać debuger. Plik *. Natvis* zawiera informacje o rejestracji wtyczki, takie jak nazwa, identyfikator GUID uwidocznionej usługi i typy, które mogą być wizualizowane.

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

- `ServiceId` - `Id` para atrybutów identyfikuje `UIVisualizer`. `ServiceId` jest identyfikatorem GUID usługi udostępnianej przez pakiet wizualizatora. `Id` jest unikatowym identyfikatorem odróżniającym Wizualizatory, jeśli usługa zawiera więcej niż jeden element. W poprzednim przykładzie ta sama usługa wizualizatora udostępnia dwa Wizualizatory.

- Atrybut `MenuName` definiuje nazwę wizualizatora do wyświetlenia na liście rozwijanej obok ikony lupy w debugerze. Na przykład:

  ![Menu skrótów menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menu skrótów menu UIVisualizer")

Każdy typ zdefiniowany w pliku *Natvis* musi jawnie zawierać wszystkie WIZUALIZATORY interfejsu użytkownika, które mogą je wyświetlić. Debuger dopasowuje odwołania wizualizatora w wpisach typu do zarejestrowanych wizualizatorów. Na przykład następujący wpis typu dla `std::vector` odwołuje się do `UIVisualizer` w poprzednim przykładzie.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Można zobaczyć przykład `UIVisualizer` w rozszerzeniu [czujki obrazu](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) używanym do wyświetlania map bitowych w pamięci.

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer, element
 `CustomVisualizer` jest punktem rozszerzalności, który określa rozszerzenie VSIX, które można napisać, aby kontrolować wizualizacje w programie Visual Studio Code. Aby uzyskać więcej informacji na temat pisania rozszerzeń VSIX, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Jest to znacznie większa ilość pracy, która pozwala napisać wizualizację niestandardową niż definicja pliku Natvis XML, ale nie jest to ograniczenie dotyczące tego, co plik Natvis działa lub nie obsługuje. Wizualizacje niestandardowe mają dostęp do pełnego zestawu interfejsów API rozszerzalności debugera, które mogą wysyłać zapytania i modyfikować proces debugowanego obiektu lub komunikować się z innymi częściami programu Visual Studio.

 Można użyć atrybutów `Condition`, `IncludeView`i `ExcludeView` dla elementów `CustomVisualizer`.

 ## <a name="limitations"></a>Ograniczenia

Dostosowania Natvis współpracują z klasami i strukturami, ale nie z typedef.

Natvis nie obsługuje wizualizatorów dla typów pierwotnych (na przykład `int`, `bool`) ani dla wskaźników do typów pierwotnych. W tym scenariuszu jedną z opcji jest użycie [specyfikatora formatu](../debugger/format-specifiers-in-cpp.md) odpowiedniego dla Twojego przypadku użycia. Na przykład jeśli używasz `double* mydoublearray` w kodzie, możesz użyć specyfikatora formatu tablicy w oknie **czujki** debugera, takiego jak wyrażenie `mydoublearray, [100]`, które pokazuje pierwsze 100 elementów.
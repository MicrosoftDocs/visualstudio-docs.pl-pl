---
title: Fragmenty kodu — informacje o schemacie
ms.date: 02/25/2019
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22f84fbe5188e74acbf24256444ad11dd9c64347
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301840"
---
# <a name="code-snippets-schema-reference"></a>Fragmenty kodu — informacje o schemacie

Urywki kodu IntelliSense są wstępnie utworami kodu, które są gotowe do wstawienia do aplikacji za pomocą programu Visual Studio. Umożliwiają one poprawę wydajności pracy, ponieważ zmniejszają ilość czasu spędzanego na wielokrotnym wpisywaniu tego samego kodu czy wyszukiwaniu przykładów. Schemat XML fragmentu kodu IntelliSense można użyć do utworzenia własnych fragmentów kodu i dodania ich do fragmentów kodu, które visual studio już zawiera.

## <a name="assembly-element"></a>Element złożenia

Określa nazwę zestawu, do którego się odwołuje fragment kodu.

Wartość tekstowa elementu **Assembly** jest przyjazną nazwą tekstową zestawu, taką jak `System.dll`, `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`lub jego silną nazwą, taką jak .

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element odniesienia](../ide/code-snippets-schema-reference.md#reference-element)|Zawiera informacje o odwołaniach do zestawów wymaganych przez fragment kodu.|

Wartość tekstowa jest wymagana. Tekst określa zestaw, do którego odwołuje się fragment kodu.

## <a name="author-element"></a>Element autora

Określa nazwę autora fragmentu kodu. **Menedżer urywków kodu** wyświetla nazwę `Author` przechowywaną w elemencie fragmentu kodu.

```xml
<Author>
   Code Snippet Author
</Author>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header-element)|Zawiera ogólne informacje o fragmencie kodu.|

Wartość tekstowa jest wymagana. Tekst określa autora fragmentu kodu.

## <a name="code-element"></a>Element Code

Stanowi kontener dla krótkich bloków kodu.

### <a name="keywords"></a>Słowa kluczowe

Dwa słowa zastrzeżone są dostępne do `Code` użycia `$end$` `$selected$`w tekście elementu: i . `$end$`oznacza lokalizację, aby umieścić kursor po wstawieniu fragmentu kodu. `$selected$`reprezentuje tekst zaznaczony w dokumencie, który ma zostać wstawiony do fragmentu kodu podczas wywoływania. Na przykład, biorąc pod uwagę fragment kodu, który zawiera:

```
$selected$ is a great color.
```

Jeśli słowo "Niebieski" jest zaznaczone, gdy użytkownik wywołuje szablon, wynik jest:

```
Blue is a great color.
```

Nie można używać `$end$` jednego `$selected$` lub więcej lub jeden raz we urywek kodu. Jeśli to zrobisz, tylko drugie wystąpienie jest rozpoznawany. Biorąc pod uwagę fragment kodu, który zawiera:

```
$selected$ is a great color. I love $selected$.
```

Jeśli wybrano słowo "Niebieski", wynik jest:

```
 is a great color. I love Blue.
```

Początkowa przestrzeń pojawia się, `$selected$` ponieważ `is`istnieje odstęp między i .

Wszystkie `$` inne słowa kluczowe są `<Literal>` dynamicznie definiowane w i `<Object>` tagi.

Poniżej przedstawiono strukturę elementu Code:

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

Wartość tekstowa jest wymagana. Ten tekst określa kod, wraz z literałami i obiektami, których można użyć, gdy ten fragment kodu zostanie wstawiony do pliku kodu.

### <a name="attributes"></a>Atrybuty

Istnieją trzy atrybuty dostępne dla Code elementu:

- **Wymagany język** - _atrybut,_ który określa język fragmentu kodu. Może to być jedna z następujących wartości:

   |Wartość|Opis|
   |-----|-----------|
   |`VB`|Identyfikuje fragment kodu języka Visual Basic.|
   |`CSharp`|Identyfikuje fragment kodu języka C#.|
   |`CPP`|Identyfikuje fragment kodu języka C++.|
   |`XML`|Identyfikuje fragment kodu języka XML.|
   |`JavaScript`|Identyfikuje fragment kodu języka JavaScript.|
   |`TypeScript`|Identyfikuje fragment kodu TypeScript.|
   |`SQL`|Identyfikuje fragment kodu języka SQL.|
   |`HTML`|Identyfikuje fragment kodu języka HTML.|

- **Rodzaj** - _Opcjonalny_ atrybut, który określa rodzaj kodu, który zawiera fragment kodu. Może to być jedna z następujących wartości:

   |Wartość|Opis|
   |-----|-----------|
   |`method body`|Określa, że fragment kodu jest treścią metody i w związku z tym należy go wstawić do deklaracji metody.|
   |`method decl`|Określa, że fragment kodu jest metodą i w związku z tym należy go wstawić do klasy lub modułu.|
   |`type decl`|Określa, że fragment kodu jest typem i w związku z tym należy go wstawić do klasy, modułu lub przestrzeni nazw.|
   |`file`|Określa, że fragment jest kompletnym plikiem kodu. Takie fragmenty kodu można wstawiać autonomicznie do pliku kodu albo do przestrzeni nazw.|
   |`any`|Określa, że fragment można wstawić w dowolnym miejscu. Ten tag jest używany we fragmentach kodu niezależnych od kontekstu, takich jak komentarze.|

- **Ogranicznik** - _Opcjonalny_ atrybut, który określa ogranicznik używany do opisywania literałów i obiektów w kodzie. Domyślnie ogranicznik `$`to .

### <a name="parent-element"></a>Element nadrzędny

|Element nadrzędny|Opis|
| - |-----------------|
|[Element urywka](../ide/code-snippets-schema-reference.md#snippet-element)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|

## <a name="codesnippet-element"></a>Element CodeSnippet

Umożliwia określenie nagłówka oraz wielu fragmentów kodu IntelliSense, które można wstawiać do plików kodu programu Visual Studio.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>
```

|Atrybut|Opis|
|---------------|-----------------|
|`Format`|Atrybut wymagany. Określa wersję schematu fragmentu kodu. Atrybut Format musi być ciągiem tekstowym o składni x.x.x, gdzie każdy znak „x” reprezentuje wartość liczbową numeru wersji. Visual Studio zignoruje fragmenty kodu z `Format` atrybutami, które nie rozumieją.|

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header-element)|Element wymagany. Zawiera ogólne informacje o fragmencie kodu. Musi istnieć dokładnie `Header` jeden element we fragmentie kodu.|
|[Element urywka](../ide/code-snippets-schema-reference.md#snippet-element)|Element wymagany. Zawiera kod, który będzie wstawiany przez program Visual Studio. Musi istnieć dokładnie `Snippet` jeden element we fragmentie kodu.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element CodeSnippets](../ide/code-snippets-schema-reference.md#codesnippets-element)|Element główny schematu XML fragmentu kodu.|

## <a name="codesnippets-element"></a>Element CodeSnippets

Grupuje elementy [codesnippet.](../ide/code-snippets-schema-reference.md#codesnippet-element) Element `CodeSnippets` jest elementem głównym schematu XML fragmentu kodu.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Element opcjonalny. Element nadrzędny dla wszystkich danych fragmentu kodu. Może istnieć zero `CodeSnippet` lub `CodeSnippets` więcej elementów w elemencie.|

## <a name="declarations-element"></a>Element Deklaracje

Określa literały i obiekty tworzące sekcje fragmentu kodu, które można edytować.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element dosłowny](../ide/code-snippets-schema-reference.md#literal-element)|Element opcjonalny. Definiuje literały fragmentu kodu, które można edytować. Może istnieć zero `Literal` lub `Declarations` więcej elementów w elemencie.|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object-element)|Element opcjonalny. Definiuje obiekty fragmentu kodu, które można edytować. Może istnieć zero `Object` lub `Declarations` więcej elementów w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element urywka](../ide/code-snippets-schema-reference.md#snippet-element)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|

## <a name="default-element"></a>Element domyślny

Określa domyślną wartość literału lub obiektu fragmentu kodu IntelliSense.

```xml
<Default>
    Default value
</Default>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element dosłowny](../ide/code-snippets-schema-reference.md#literal-element)|Definiuje pola literałów fragmentu kodu, które można edytować.|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object-element)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

Wartość tekstowa jest wymagana. Ten tekst określa domyślną wartość literału lub obiektu wypełniającego pola fragment kodu, który można edytować.

## <a name="description-element"></a>Element opisu

Określa opisowe informacje o zawartości fragmentu kodu IntelliSense.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header-element)|Zawiera ogólne informacje o fragmencie kodu.|

Wartość tekstowa jest wymagana. Ten tekst opisuje fragment kodu.

## <a name="function-element"></a>Element funkcyjny

Określa funkcję do wykonania, gdy w programie Visual Studio na literale lub obiekcie zostanie ustawiony fokus.

> [!NOTE]
> Element `Function` jest obsługiwany tylko w fragmentach kodu języka C#.

```xml
<Function>
    FunctionName
</Function>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element dosłowny](../ide/code-snippets-schema-reference.md#literal-element)|Definiuje pola literałów fragmentu kodu, które można edytować.|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object-element)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

Wartość tekstowa jest wymagana. Ten tekst określa funkcję do wykonania, gdy w programie Visual Studio na literale lub polu obiektu zostanie ustawiony fokus.

## <a name="header-element"></a>Element nagłówka

Zawiera ogólne informacje o fragmencie kodu IntelliSense.

```xml
<Header>
    <Title>... </Title>
    <Author>... </Author>
    <Description>... </Description>
    <HelpUrl>... </HelpUrl>
    <SnippetTypes>... </SnippetTypes>
    <Keywords>... </Keywords>
    <Shortcut>... </Shortcut>
</Header>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element autora](../ide/code-snippets-schema-reference.md#author-element)|Element opcjonalny. Imię i nazwisko/nazwa osoby lub firmy, która utworzyła fragment kodu. Może istnieć zero `Author` lub `Header` jeden element w elemencie.|
|[Element opisu](../ide/code-snippets-schema-reference.md#description-element)|Element opcjonalny. Opis fragmentu kodu. Może istnieć zero `Description` lub `Header` jeden element w elemencie.|
|[Element HelpUrl](../ide/code-snippets-schema-reference.md#helpurl-element)|Element opcjonalny. Adres URL strony zawierającej poszerzone informacje o fragmencie kodu. Może istnieć zero `HelpURL` lub jeden element w header elementu. **Uwaga:**  Visual Studio nie `HelpUrl` używa elementu. Element jest częścią schematu XML fragmentu kodu IntelliSense. Wszystkie fragmenty kodu zawierające element będą weryfikowane, ale wartość elementu nigdy nie jest używana.|
|[Element słowa kluczowe](../ide/code-snippets-schema-reference.md#keywords-element)|Element opcjonalny. Grupuje `Keyword` elementy. Może istnieć zero `Keywords` lub `Header` jeden element w elemencie.|
|[Element skrótu](../ide/code-snippets-schema-reference.md#shortcut-element)|Element opcjonalny. Określa tekst skrótu, który pozwala wstawić fragment kodu. Może istnieć zero `Shortcut` lub `Header` jeden element w elemencie.|
|[Element urywek](../ide/code-snippets-schema-reference.md#snippettypes-element)|Element opcjonalny. Grupuje `SnippetType` elementy. Może istnieć zero `SnippetTypes` lub `Header` jeden element w elemencie. Jeśli nie `SnippetTypes` ma żadnych elementów, fragment kodu jest zawsze prawidłowy.|
|[Element tytułu](../ide/code-snippets-schema-reference.md#title-element)|Element wymagany. Przyjazna nazwa fragmentu kodu. Musi istnieć dokładnie `Title` jeden `Header` element w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Element nadrzędny dla wszystkich danych fragmentu kodu.|

## <a name="helpurl-element"></a>Element HelpUrl

Określa adres URL strony zawierającej poszerzone informacje o fragmencie kodu.

> [!NOTE]
> Visual Studio nie `HelpUrl` używa elementu. Element jest częścią schematu XML fragmentu kodu IntelliSense. Wszystkie fragmenty kodu zawierające element będą weryfikowane, ale wartość elementu nigdy nie jest używana.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header-element)|Zawiera ogólne informacje o fragmencie kodu.|

Wartość tekstowa jest opcjonalna. Ten tekst określa adres URL strony, na której można znaleźć więcej informacji o fragmencie kodu.

## <a name="id-element"></a>Element identyfikatora

Określa unikatowy identyfikator `Literal` elementu `Object` lub elementu. Żadne dwa literały lub obiekty w tym samym fragmentie kodu mogą `ID` mieć taką samą wartość tekstową w swoich elementach. Literały i obiekty nie `ID` mogą zawierać elementu o wartości końca. Wartość `$end$` jest zarezerwowana i służy do oznaczania lokalizacji w celu umieszczenia kursora po wstawieniu fragmentu kodu.

```xml
<ID>
    Unique Identifier
</ID>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element dosłowny](../ide/code-snippets-schema-reference.md#literal-element)|Definiuje pola literałów fragmentu kodu, które można edytować.|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object-element)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

Wartość tekstowa jest wymagana. Ten tekst określa unikatowy identyfikator obiektu lub literału.

## <a name="import-element"></a>Element importu

Określa importowane przestrzenie nazw używane przez fragment kodu IntelliSense.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element obszaru nazw](../ide/code-snippets-schema-reference.md#namespace-element)|Element wymagany. Określa przestrzeń nazw używaną przez fragment kodu. Musi istnieć dokładnie `Namespace` jeden `Import` element w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element Importu](../ide/code-snippets-schema-reference.md#imports-element)|Element grupowania dla **importu** elementów.|

## <a name="imports-element"></a>Element Importu

Grupuje `Import` poszczególne elementy.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element importu](../ide/code-snippets-schema-reference.md#import-element)|Element opcjonalny. Zawiera zaimportowane przestrzenie nazw fragmentu kodu. Może być zero **Import** lub więcej `Imports` Import elementów w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element urywka](../ide/code-snippets-schema-reference.md#snippet-element)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|

## <a name="keyword-element"></a>Element słowa kluczowego

Określa niestandardowe słowo kluczowe fragmentu kodu. Słowa kluczowe fragmentu kodu są wykorzystywane przez program Visual Studio. Stanowią standardowy mechanizm, przy użyciu którego dostawcy treści internetowych mogą dodawać słowa kluczowe na potrzeby wyszukiwania lub kategoryzacji.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element słowa kluczowe](../ide/code-snippets-schema-reference.md#keywords-element)|Grupuje `Keyword` poszczególne elementy.|

Wartość tekstowa jest wymagana. Słowo kluczowe fragmentu kodu.

## <a name="keywords-element"></a>Element słowa kluczowe

Grupuje `Keyword` poszczególne elementy. Słowa kluczowe fragmentu kodu są wykorzystywane przez program Visual Studio. Stanowią standardowy mechanizm, przy użyciu którego dostawcy treści internetowych mogą dodawać słowa kluczowe na potrzeby wyszukiwania lub kategoryzacji.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element słowa kluczowego](../ide/code-snippets-schema-reference.md#keyword-element)|Element opcjonalny. Zawiera poszczególne słowa kluczowe fragmentu kodu. Może istnieć zero `Keyword` lub `Keywords` więcej elementów w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header-element)|Zawiera ogólne informacje o fragmencie kodu.|

## <a name="literal-element"></a>Element dosłowny

Definiuje literały fragmentu kodu, które można edytować. Element `Literal` jest używany do identyfikowania zastąpienia fragmentu kodu, który jest całkowicie zawarty w urywek, ale prawdopodobnie zostaną dostosowane po wstawieniu do kodu. Jako literały należy na przykład deklarować ciągi literałowe, wartości liczbowe i nazwy niektórych zmiennych.

Literały i obiekty nie mogą zawierać elementu **identyfikatora** o wartości zaznaczonej lub końcowej. Wartość `$selected$` reprezentuje tekst zaznaczony w dokumencie, który ma zostać wstawiony do fragmentu kodu podczas wywoływania. `$end$`oznacza lokalizację, aby umieścić kursor po wstawieniu fragmentu kodu.

```xml
<Literal Editable="true/false">
   <ID>... </ID>
   <ToolTip>... </ToolTip>
   <Default>... </Default>
   <Function>... </Function>
</Literal>
```

|Atrybut|Opis|
|---------------|-----------------|
|`Editable`|Opcjonalny `Boolean` atrybut. Określa, czy po wstawieniu fragmentu kodu można edytować literał. Domyślną wartością tego `true`atrybutu jest .|

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element domyślny](../ide/code-snippets-schema-reference.md#default-element)|Element wymagany. Określa domyślną wartość literału po wstawieniu fragmentu kodu. Musi istnieć dokładnie `Default` jeden `Literal` element w elemencie.|
|[Element funkcyjny](../ide/code-snippets-schema-reference.md#function-element)|Element opcjonalny. Określa funkcję do wykonania, gdy w programie Visual Studio na literale zostanie ustawiony fokus. Może istnieć zero `Function` lub `Literal` jeden element w elemencie.|
|[Element identyfikatora](../ide/code-snippets-schema-reference.md#id-element)|Element wymagany. Określa unikatowy identyfikator literału. Musi istnieć dokładnie `ID` jeden `Literal` element w elemencie.|
|[Element Etykietki narzędzia](../ide/code-snippets-schema-reference.md#tooltip-element)|Element opcjonalny. Opisuje oczekiwaną wartość i użycie literału. Może istnieć zero lub jeden `Literal` **tooltip** elementów w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element Deklaracje](../ide/code-snippets-schema-reference.md#declarations-element)|Zawiera literały i obiekty fragmentu kodu, które można edytować.|

## <a name="namespace-element"></a>Element obszaru nazw

Określa przestrzeń nazw, którą należy zaimportować, aby fragment kodu został skompilowany i działał. Obszar nazw określony `Namespace` w elemencie `using` jest `Imports` automatycznie dodawany do dyrektywy lub instrukcji na początku kodu, jeśli jeszcze nie istnieje.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element importu](../ide/code-snippets-schema-reference.md#import-element)|Importowanie określonej przestrzeni nazw.|

Wartość tekstowa jest wymagana. Ten tekst określa obszar nazw, wstawki zakłada jest importowany.

## <a name="object-element"></a>Element obiektu

Definiuje obiekty fragmentu kodu, które można edytować. Element `Object` jest używany do identyfikowania elementu, który jest wymagany przez fragment kodu, ale prawdopodobnie zostanie zdefiniowany poza samym fragmentem kodu. Na przykład formanty interfejsu Windows Forms, formanty środowiska ASP.NET, wystąpienia obiektów i wystąpienia typów powinny być deklarowane jako obiekty. Deklaracje obiektów wymagają, aby określić typ, `Type` który odbywa się z elementem.

```xml
<Object Editable="true/false">
    <ID>... </ID>
    <Type>... </Type>
    <ToolTip>... </ToolTip>
    <Default>... </Default>
    <Function>... </Function>
</Object>
```

|Atrybut|Opis|
|---------------|-----------------|
|`Editable`|Opcjonalny `Boolean` atrybut. Określa, czy po wstawieniu fragmentu kodu można edytować literał. Domyślną wartością tego `true`atrybutu jest .|

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element domyślny](../ide/code-snippets-schema-reference.md#default-element)|Element wymagany. Określa domyślną wartość literału po wstawieniu fragmentu kodu. Musi istnieć dokładnie `Default` jeden `Literal` element w elemencie.|
|[Element funkcyjny](../ide/code-snippets-schema-reference.md#function-element)|Element opcjonalny. Określa funkcję do wykonania, gdy w programie Visual Studio na literale zostanie ustawiony fokus. Może istnieć zero `Function` lub `Literal` jeden element w elemencie.|
|[Element identyfikatora](../ide/code-snippets-schema-reference.md#id-element)|Element wymagany. Określa unikatowy identyfikator literału. Musi istnieć dokładnie `ID` jeden `Literal` element w elemencie.|
|[Element Etykietki narzędzia](../ide/code-snippets-schema-reference.md#tooltip-element)|Element opcjonalny. Opisuje oczekiwaną wartość i użycie literału. Może istnieć zero lub jeden `Literal` **tooltip** elementów w elemencie.|
|[Element tekstowy](../ide/code-snippets-schema-reference.md#type-element)|Element wymagany. Określa typ obiektu. Musi istnieć dokładnie `Type` jeden `Object` element w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element Deklaracje](../ide/code-snippets-schema-reference.md#declarations-element)|Zawiera literały i obiekty fragmentu kodu, które można edytować.|

## <a name="reference-element"></a>Element odniesienia

Określa informacje o odwołaniach do zestawów wymaganych przez fragment kodu.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element złożenia](../ide/code-snippets-schema-reference.md#assembly-element)|Element wymagany. Zawiera nazwę zestawu, do którego się odwołuje fragment kodu. Musi istnieć dokładnie `Assembly` jeden `Reference` element w elemencie.|
|[Element adresu URL](../ide/code-snippets-schema-reference.md#url-element)|Element opcjonalny. Zawiera adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie. Może istnieć zero `Url` lub `Reference` jeden element w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element Odwołania](../ide/code-snippets-schema-reference.md#references-element)|Element grupowania `Reference` elementów.|

## <a name="references-element"></a>Element Odwołania

Grupuje `Reference` poszczególne elementy.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element odniesienia](../ide/code-snippets-schema-reference.md#reference-element)|Element opcjonalny. Zawiera informacje o odwołaniach do zestawów z fragmentu kodu. Może istnieć zero `Reference` lub `References` więcej elementów w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element urywka](../ide/code-snippets-schema-reference.md#snippet-element)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|

## <a name="shortcut-element"></a>Element skrótu

Określa tekst skrótu służący do wstawiania fragmentu kodu. Wartość tekstowa `Shortcut` elementu może zawierać tylko znaki alfanumeryczne i podkreślenia ( _ ).

> [!CAUTION]
> Znak podkreślenia (_) nie jest obsługiwany w skrótach fragmentu kodu języka C++.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header-element)|Zawiera ogólne informacje o fragmencie kodu.|

Wartość tekstowa jest opcjonalna. Ten tekst jest używany jako skrót do wstawiania fragmentu kodu.

## <a name="snippet-element"></a>Element urywka

Określa odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element kodu](../ide/code-snippets-schema-reference.md#code-element)|Element wymagany. Określa kod, który ma zostać wstawiony do pliku dokumentacji. Musi istnieć dokładnie `Code` jeden `Snippet` element w elemencie.|
|[Element Deklaracje](../ide/code-snippets-schema-reference.md#declarations-element)|Element opcjonalny. Określa literały i obiekty tworzące sekcje fragmentu kodu, które można edytować. Może istnieć zero `Declarations` lub `Snippet` jeden element w elemencie.|
|[Element Importu](../ide/code-snippets-schema-reference.md#imports-element)|Element opcjonalny. Grupuje `Import` poszczególne elementy. Może istnieć zero `Imports` lub `Snippet` jeden element w elemencie.|
|[Element Odwołania](../ide/code-snippets-schema-reference.md#references-element)|Element opcjonalny. Grupuje `Reference` poszczególne elementy. Może istnieć zero `References` lub `Snippet` jeden element w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Umożliwia określenie nagłówka oraz wielu fragmentów kodu IntelliSense, które można wstawiać do plików kodu programu Visual Studio.|

## <a name="snippettype-element"></a>Element urywkatyp

Określa, w jaki sposób program Visual Studio wstawia fragment kodu.

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element urywek](../ide/code-snippets-schema-reference.md#snippettypes-element)|Grupuje `SnippetType` elementy.|

Wartość tekstowa musi być jedną z następujących:

- `SurroundsWith`: umożliwia umieszczenie fragmentu kodu wokół wybranego fragmentu kodu.

- `Expansion`: umożliwia wstawienie fragmentu kodu do kursora.

- `Refactoring`: określa, że fragment kodu jest używany podczas refaktoryzacji języka C#. `Refactoring`nie można używać w niestandardowych fragmentach kodu.

## <a name="snippettypes-element"></a>Element urywek

Grupuje `SnippetType` poszczególne elementy. Jeśli `SnippetTypes` element nie jest obecny, fragment kodu można wstawić w dowolnym miejscu w kodzie.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element urywkatyp](../ide/code-snippets-schema-reference.md#snippettype-element)|Element opcjonalny. Określa, w jaki sposób program Visual Studio wstawia fragment kodu do kodu. Może istnieć zero `SnippetType` lub `SnippetTypes` więcej elementów w elemencie.|

|Element nadrzędny|Opis|
| - |-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header-element)|Określa ogólne informacje o fragmencie kodu.|

## <a name="title-element"></a>Element tytułu

Określa tytuł fragmentu kodu. Tytuł zapisany we `Title` elemencie fragmentu kodu pojawia się w **selektorze fragmentów kodu** oraz w opisie fragmentu kodu w **Menedżerze urywków kodu**.

```xml
<Title>
    Code Snippet Title
</Title>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header-element)|Określa ogólne informacje o fragmencie kodu.|

Wartość tekstowa jest wymagana. Tekst określa tytuł fragmentu kodu.

## <a name="tooltip-element"></a>Element Etykietki narzędzia

Opisuje oczekiwaną wartość i użycie literału lub obiektu we fragmencie kodu. Informacje te będą wyświetlane w programie Visual Studio w etykietce narzędzia po wstawieniu fragmentu kodu do projektu. Tekst etykietki narzędzia jest wyświetlany, gdy wskaźnik myszy znajdzie się nad literałem lub obiektem.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element dosłowny](../ide/code-snippets-schema-reference.md#literal-element)|Definiuje pola literałów fragmentu kodu, które można edytować.|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object-element)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

Wartość tekstowa jest wymagana. Ten tekst określa opis etykietki narzędzia, który zostanie skojarzony z obiektem lub literałem we fragmencie kodu.

## <a name="type-element"></a>Element tekstowy

Określa typ obiektu. Element `Object` jest używany do identyfikowania elementu, który jest wymagany przez fragment kodu, ale prawdopodobnie zostanie zdefiniowany poza samym fragmentem kodu. Na przykład formanty interfejsu Windows Forms, formanty środowiska ASP.NET, wystąpienia obiektów i wystąpienia typów powinny być deklarowane jako obiekty. Deklaracje obiektów wymagają, aby określić typ, `Type` który odbywa się z elementem.

```xml
<Type>
    Type
</Type>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object-element)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

Wartość tekstowa jest wymagana. Ten tekst określa typ obiektu. Przykład:

```xml
<Type>System.Data.SqlClient.SqlConnection</Type>
```

## <a name="url-element"></a>Element adresu URL

Określa adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie.

> [!NOTE]
> Element `Url` jest obsługiwany tylko dla projektów języka Visual Basic.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Element nadrzędny|Opis|
| - |-----------------|
|[Element odniesienia](../ide/code-snippets-schema-reference.md#reference-element)|Określa odwołania do zestawów wymagane we fragmencie kodu.|

Wartość tekstowa jest wymagana. Ten tekst określa adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie. Ten adres URL jest wyświetlany, gdy do projektu nie można dodać odwołania.

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../ide/code-snippets.md)
- [Przewodnik: tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)

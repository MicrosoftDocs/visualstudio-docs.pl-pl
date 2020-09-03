---
title: Fragmenty kodu — odwołanie do schematu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67bc1a18b4e4cbfdf69fe917c0d0fdff09832983
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545031"
---
# <a name="code-snippets-schema-reference"></a>Fragmenty kodu — Odwołanie do schematu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kodu IntelliSense to wstępnie utworzone fragmenty kodu, które są gotowe do wstawienia do aplikacji za pomocą programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Umożliwiają one poprawę wydajności pracy, ponieważ zmniejszają ilość czasu spędzanego na wielokrotnym wpisywaniu tego samego kodu czy wyszukiwaniu przykładów. Możesz użyć schematu XML fragmentu kodu IntelliSense, aby utworzyć własne fragmenty kodu i dodać je do fragmentów kodu, które [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] już obejmują.

## <a name="intellisense-code-snippets-schema-elements"></a>Elementy schematu fragmentów kodu IntelliSense

|Element|Element|Element|
|-|-|-|
|[Element Assembly](../ide/code-snippets-schema-reference.md#assembly)|[HelpUrl, element](../ide/code-snippets-schema-reference.md#helpurl)|[References — element](../ide/code-snippets-schema-reference.md#references)|
|[Author — element](../ide/code-snippets-schema-reference.md#author)|[ID — element](../ide/code-snippets-schema-reference.md#id)|[Element skrótu](../ide/code-snippets-schema-reference.md#shortcut)|
|[Element Code](../ide/code-snippets-schema-reference.md#code)|[Importuj element](../ide/code-snippets-schema-reference.md#import)|[Element fragmentu kodu](../ide/code-snippets-schema-reference.md#snippet)|
|[CodeSnippet, element](../ide/code-snippets-schema-reference.md#codesnippet)|[Imports — element](../ide/code-snippets-schema-reference.md#imports)|[Element SnippetType](../ide/code-snippets-schema-reference.md#snippettype)|
|[CodeSnippets, element](../ide/code-snippets-schema-reference.md#codesnippets)|[Element słowo kluczowe](../ide/code-snippets-schema-reference.md#keyword)|[SnippetTypes, element](../ide/code-snippets-schema-reference.md#snippettypes)|
|[Element deklaracji](../ide/code-snippets-schema-reference.md#declarations)|[Keywords — element](../ide/code-snippets-schema-reference.md#keywords)|[Title — element](../ide/code-snippets-schema-reference.md#title)|
|[Element domyślny](../ide/code-snippets-schema-reference.md#default)|[Element Literal](../ide/code-snippets-schema-reference.md#literal)|[Element ToolTip](../ide/code-snippets-schema-reference.md#tooltip)|
|[Description — element](../ide/code-snippets-schema-reference.md#description)|[Element Namespace](../ide/code-snippets-schema-reference.md#namespace)|[Element Type](../ide/code-snippets-schema-reference.md#type)|
|[Element Function](../ide/code-snippets-schema-reference.md#function)|[Element obiektu](../ide/code-snippets-schema-reference.md#object)|[Element adresu URL](../ide/code-snippets-schema-reference.md#url)|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|[Reference — element](../ide/code-snippets-schema-reference.md#reference)||

## <a name="assembly-element"></a><a name="assembly"></a> Element Assembly
 Określa nazwę zestawu, do którego się odwołuje fragment kodu.

> [!NOTE]
> `Assembly`Element jest obsługiwany tylko przez fragmenty kodu Visual Basic.

 Wartość tekstowa elementu **zestawu** jest przyjazną nazwą tekstu zestawu, taką jak `System.dll` lub jego silną nazwą, taką jak `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1` .

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Reference — element](../ide/code-snippets-schema-reference.md#reference)|Zawiera informacje o odwołaniach do zestawów wymaganych przez fragment kodu.|

 Wartość tekstowa jest wymagana. Tekst określa zestaw, do którego odwołuje się fragment kodu.

## <a name="author-element"></a><a name="author"></a> Author — element
 Określa nazwę autora fragmentu kodu. **Menedżer fragmentów kodu** wyświetla nazwę przechowywaną w `Author` elemencie fragmentu kodu.

```xml
<Author>
   Code Snippet Author
</Author>

```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|

 Wartość tekstowa jest wymagana. Tekst określa autora fragmentu kodu.

## <a name="code-element"></a><a name="code"></a> Element kodu
 Stanowi kontener dla krótkich bloków kodu.

 Dwa zastrzeżone słowa są dostępne do użycia w tekście `Code` elementu: `$end$` i `$selected$` . `$end$` oznacza lokalizację, w której ma zostać umieszczony kursor po wstawieniu fragmentu kodu. `$selected$` reprezentuje tekst zaznaczony w dokumencie, który ma zostać wstawiony do fragmentu, gdy jest wywoływany. Na przykład, w którym znajduje się fragment kodu zawierający:

```xml
$selected$ is a great color.
```

 Jeśli zostanie wybrany wyraz "Blue", gdy użytkownik wywoła szablon, wynikiem jest:

```xml
Blue is a great color.
```

 Nie można użyć `$end$` lub `$selected$` więcej niż jeden raz w fragmencie kodu. W takim przypadku tylko drugie wystąpienie zostanie rozpoznane. Podano fragment kodu obejmujący:

```
$selected$ is a great color. I love $selected$.
```

 W przypadku wybrania wyrazu "Blue" wynikiem jest:

```
is a great color. I love Blue.
```

 Początkowe miejsce jest wyświetlane ze względu na miejsce między `$selected$` i `is` .

 Wszystkie inne `$` słowa kluczowe są definiowane dynamicznie w `<Literal>` `<Object>` tagach i.

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

|Atrybut|Opis|
|---------------|-----------------|
|`Delimiter`|Atrybut opcjonalny. Określa separator używany do opisywania literałów i obiektów w kodzie. Domyślnie ogranicznik jest `$` .|
|`Kind`|Atrybut opcjonalny. Określa rodzaj kodu znajdującego się we fragmencie oraz miejsce, gdzie trzeba wstawić fragment, aby został poprawnie skompilowany. Dostępne wartości to,,, `method body` `method decl` `type decl` `file` i `any` .|
|`Language`|Atrybut wymagany. Określa język fragmentu kodu.|

|Wartość atrybutu Kind|Opis|
|--------------------------|-----------------|
|`method body`|Określa, że fragment kodu jest treścią metody i w związku z tym należy go wstawić do deklaracji metody.|
|`method decl`|Określa, że fragment kodu jest metodą i w związku z tym należy go wstawić do klasy lub modułu.|
|`type decl`|Określa, że fragment kodu jest typem i w związku z tym należy go wstawić do klasy, modułu lub przestrzeni nazw.|
|`file`|Określa, że fragment jest kompletnym plikiem kodu. Takie fragmenty kodu można wstawiać autonomicznie do pliku kodu albo do przestrzeni nazw.|
|`any`|Określa, że fragment można wstawić w dowolnym miejscu. Ten tag jest używany we fragmentach kodu niezależnych od kontekstu, takich jak komentarze.|

|Wartość atrybutu Language|Opis|
|------------------------------|-----------------|
|`VB`|Identyfikuje fragment kodu języka Visual Basic.|
|`CSharp`|Identyfikuje fragment kodu języka C#.|
|`CPP`|Identyfikuje fragment kodu języka C++.|
|`XML`|Identyfikuje fragment kodu języka XML.|
|`JavaScript`|Identyfikuje fragment kodu języka JavaScript.|
|`SQL`|Identyfikuje fragment kodu języka SQL.|
|`HTML`|Identyfikuje fragment kodu języka HTML.|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element fragmentu kodu](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|

 Wartość tekstowa jest wymagana. Tekst określa kod, łącznie z literałami i obiektami, którego można używać podczas wstawiania tego fragmentu do projektu.

## <a name="codesnippet-element"></a><a name="codesnippet"></a> CodeSnippet, element
 Umożliwia określenie nagłówka oraz wielu fragmentów kodu IntelliSense, które można wstawiać do plików kodu programu Visual Studio.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>

```

|Atrybut|Opis|
|---------------|-----------------|
|`Format`|Atrybut wymagany. Określa wersję schematu fragmentu kodu. Atrybut Format musi być ciągiem tekstowym o składni x.x.x, gdzie każdy znak „x” reprezentuje wartość liczbową numeru wersji. Program Visual Studio zignoruje fragmenty kodu z `Format` atrybutami, które nie są zrozumiałe.|

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Element wymagany. Zawiera ogólne informacje o fragmencie kodu. Fragment kodu musi zawierać dokładnie jeden `Header` element.|
|[Element fragmentu kodu](../ide/code-snippets-schema-reference.md#snippet)|Element wymagany. Zawiera kod, który będzie wstawiany przez program Visual Studio. Fragment kodu musi zawierać dokładnie jeden `Snippet` element.|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[CodeSnippets, element](../ide/code-snippets-schema-reference.md#codesnippets)|Element główny schematu XML fragmentu kodu.|

## <a name="codesnippets-element"></a><a name="codesnippets"></a> CodeSnippets, element
 Grupuje elementy [elementu CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet). `CodeSnippets`Element jest elementem głównym schematu XML fragmentu kodu.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>

```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[CodeSnippet, element](../ide/code-snippets-schema-reference.md#codesnippet)|Element opcjonalny. Element nadrzędny dla wszystkich danych fragmentu kodu. Element może mieć zero lub więcej `CodeSnippet` elementów `CodeSnippets` .|

## <a name="declarations-element"></a><a name="declarations"></a> Element deklaracji
 Określa literały i obiekty tworzące sekcje fragmentu kodu, które można edytować.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>

```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal)|Element opcjonalny. Definiuje literały fragmentu kodu, które można edytować. Element może mieć zero lub więcej `Literal` elementów `Declarations` .|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object)|Element opcjonalny. Definiuje obiekty fragmentu kodu, które można edytować. Element może mieć zero lub więcej `Object` elementów `Declarations` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element fragmentu kodu](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|

## <a name="default-element"></a><a name="default"></a> Element domyślny
 Określa domyślną wartość literału lub obiektu fragmentu kodu IntelliSense.

```xml
<Default>
    Default value
</Default>

```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

 Wartość tekstowa jest wymagana. Ten tekst określa domyślną wartość literału lub obiektu wypełniającego pola fragment kodu, który można edytować.

## <a name="description-element"></a><a name="description"></a> Description — element
 Określa opisowe informacje o zawartości fragmentu kodu IntelliSense.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|

 Wartość tekstowa jest wymagana. Ten tekst opisuje fragment kodu.

## <a name="function-element"></a><a name="function"></a> Element Function
 Określa funkcję do wykonania, gdy w programie Visual Studio na literale lub obiekcie zostanie ustawiony fokus.

> [!NOTE]
> `Function`Element jest obsługiwany tylko w fragmentach kodu języka Visual C#.

```xml
<Function>
    FunctionName
</Function>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

 Wartość tekstowa jest wymagana. Ten tekst określa funkcję do wykonania, gdy w programie Visual Studio na literale lub polu obiektu zostanie ustawiony fokus.

## <a name="header-element"></a><a name="header"></a> Element nagłówka
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
|[Author — element](../ide/code-snippets-schema-reference.md#author)|Element opcjonalny. Imię i nazwisko/nazwa osoby lub firmy, która utworzyła fragment kodu. Element nie może zawierać żadnych `Author` elementów `Header` .|
|[Description — element](../ide/code-snippets-schema-reference.md#description)|Element opcjonalny. Opis fragmentu kodu. Element nie może zawierać żadnych `Description` elementów `Header` .|
|[HelpUrl, element](../ide/code-snippets-schema-reference.md#helpurl)|Element opcjonalny. Adres URL strony zawierającej poszerzone informacje o fragmencie kodu. Element nagłówka może zawierać tylko jeden `HelpURL` element. **Uwaga:**  Program Visual Studio nie używa `HelpUrl` elementu. Element jest częścią schematu XML fragmentu kodu IntelliSense. Wszystkie fragmenty kodu zawierające element będą weryfikowane, ale wartość elementu nigdy nie jest używana.|
|[Keywords — element](../ide/code-snippets-schema-reference.md#keywords)|Element opcjonalny. Grupuje `Keyword` elementy. Element nie może zawierać żadnych `Keywords` elementów `Header` .|
|[Element skrótu](../ide/code-snippets-schema-reference.md#shortcut)|Element opcjonalny. Określa tekst skrótu, który pozwala wstawić fragment kodu. Element nie może zawierać żadnych `Shortcut` elementów `Header` .|
|[SnippetTypes, element](../ide/code-snippets-schema-reference.md#snippettypes)|Element opcjonalny. Grupuje `SnippetType` elementy. Element nie może zawierać żadnych `SnippetTypes` elementów `Header` . Jeśli nie ma żadnych `SnippetTypes` elementów, fragment kodu jest zawsze prawidłowy.|
|[Title — element](../ide/code-snippets-schema-reference.md#title)|Element wymagany. Przyjazna nazwa fragmentu kodu. W elemencie musi znajdować się tylko jeden `Title` element `Header` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[CodeSnippet, element](../ide/code-snippets-schema-reference.md#codesnippet)|Element nadrzędny dla wszystkich danych fragmentu kodu.|

## <a name="helpurl-element"></a><a name="helpurl"></a> HelpUrl, element
 Określa adres URL strony zawierającej poszerzone informacje o fragmencie kodu.

> [!NOTE]
> Program Visual Studio nie używa `HelpUrl` elementu. Element jest częścią schematu XML fragmentu kodu IntelliSense. Wszystkie fragmenty kodu zawierające element będą weryfikowane, ale wartość elementu nigdy nie jest używana.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>

```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|

 Wartość tekstowa jest opcjonalna. Ten tekst określa adres URL strony, na której można znaleźć więcej informacji o fragmencie kodu.

## <a name="id-element"></a><a name="id"></a> ID — element
 Określa unikatowy identyfikator `Literal` `Object` elementu lub. Żadne dwa literały lub obiekty w tym samym fragmencie kodu nie mogą mieć tej samej wartości tekstowej w swoich `ID` elementach. Literały i obiekty nie mogą zawierać `ID` elementu z wartością końcową. Wartość `$end$` jest zarezerwowana i jest używana do oznaczania lokalizacji kursora po wstawieniu fragmentu kodu.

```xml
<ID>
    Unique Identifier
</ID>

```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

 Wartość tekstowa jest wymagana. Ten tekst określa unikatowy identyfikator obiektu lub literału.

## <a name="import-element"></a><a name="import"></a> Importuj element
 Określa zaimportowaną przestrzeń nazw używaną przez fragment kodu IntelliSense.

> [!NOTE]
> `Import`Element jest obsługiwany tylko w projektach Visual Basic.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>

```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element Namespace](../ide/code-snippets-schema-reference.md#namespace)|Element wymagany. Określa przestrzeń nazw używaną przez fragment kodu. W elemencie musi znajdować się tylko jeden `Namespace` element `Import` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Imports — element](../ide/code-snippets-schema-reference.md#imports)|Element grupujący dla elementów **importu** .|

## <a name="imports-element"></a><a name="imports"></a> Imports — element
 Grupuje poszczególne `Import` elementy.

> [!NOTE]
> `Imports`Element jest obsługiwany tylko w projektach Visual Basic.

```xml
<Imports>
    <Import>... </Import>
<Imports>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Importuj element](../ide/code-snippets-schema-reference.md#import)|Element opcjonalny. Zawiera zaimportowane przestrzenie nazw fragmentu kodu. Element nie może zawierać żadnych elementów **importu** `Imports` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element fragmentu kodu](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|

## <a name="keyword-element"></a><a name="keyword"></a> Element słowo kluczowe
 Określa niestandardowe słowo kluczowe fragmentu kodu. Słowa kluczowe fragmentu kodu są wykorzystywane przez program Visual Studio. Stanowią standardowy mechanizm, przy użyciu którego dostawcy treści internetowych mogą dodawać słowa kluczowe na potrzeby wyszukiwania lub kategoryzacji.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Keywords — element](../ide/code-snippets-schema-reference.md#keywords)|Grupuje poszczególne `Keyword` elementy.|

 Wartość tekstowa jest wymagana. Słowo kluczowe fragmentu kodu.

## <a name="keywords-element"></a><a name="keywords"></a> Keywords — element
 Grupuje poszczególne `Keyword` elementy. Słowa kluczowe fragmentu kodu są wykorzystywane przez program Visual Studio. Stanowią standardowy mechanizm, przy użyciu którego dostawcy treści internetowych mogą dodawać słowa kluczowe na potrzeby wyszukiwania lub kategoryzacji.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
<Keywords>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element słowo kluczowe](../ide/code-snippets-schema-reference.md#keyword)|Element opcjonalny. Zawiera poszczególne słowa kluczowe fragmentu kodu. Element może mieć zero lub więcej `Keyword` elementów `Keywords` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|

## <a name="literal-element"></a><a name="literal"></a> Literal — element
 Definiuje literały fragmentu kodu, które można edytować. `Literal`Element jest używany do identyfikowania zastąpienia dla fragmentu kodu, który jest całkowicie zawarty w fragmencie, ale prawdopodobnie zostanie dostosowany po wstawieniu go do kodu. Jako literały należy na przykład deklarować ciągi literałowe, wartości liczbowe i nazwy niektórych zmiennych.

 Literały i obiekty nie mogą zawierać elementu **ID** z wartością wybraną lub końcową. Wartość `$selected$` reprezentuje tekst zaznaczony w dokumencie, który ma zostać wstawiony do fragmentu kodu, gdy jest wywoływany. `$end$` oznacza lokalizację, w której ma zostać umieszczony kursor po wstawieniu fragmentu kodu.

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
|`Editable`|Opcjonalny `Boolean` atrybut. Określa, czy po wstawieniu fragmentu kodu można edytować literał. Wartość domyślna tego atrybutu to `true` .|

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element domyślny](../ide/code-snippets-schema-reference.md#default)|Element wymagany. Określa domyślną wartość literału po wstawieniu fragmentu kodu. W elemencie musi znajdować się tylko jeden `Default` element `Literal` .|
|[Element Function](../ide/code-snippets-schema-reference.md#function)|Element opcjonalny. Określa funkcję do wykonania, gdy w programie Visual Studio na literale zostanie ustawiony fokus. Element nie może zawierać żadnych `Function` elementów `Literal` .|
|[ID — element](../ide/code-snippets-schema-reference.md#id)|Element wymagany. Określa unikatowy identyfikator literału. W elemencie musi znajdować się tylko jeden `ID` element `Literal` .|
|[Element ToolTip](../ide/code-snippets-schema-reference.md#tooltip)|Element opcjonalny. Opisuje oczekiwaną wartość i użycie literału. Element nie może zawierać żadnych elementów **etykietki narzędzia** `Literal` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element deklaracji](../ide/code-snippets-schema-reference.md#declarations)|Zawiera literały i obiekty fragmentu kodu, które można edytować.|

## <a name="namespace-element"></a><a name="namespace"></a> Element Namespace
 Określa przestrzeń nazw, którą należy zaimportować, aby fragment kodu został skompilowany i działał. Przestrzeń nazw określona w `Namespace` elemencie jest automatycznie dodawana do `Imports` instrukcji na początku kodu, jeśli jeszcze nie istnieje.

> [!NOTE]
> `Namespace`Element jest obsługiwany tylko w projektach Visual Basic.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Importuj element](../ide/code-snippets-schema-reference.md#import)|Importowanie określonej przestrzeni nazw.|

 Wartość tekstowa jest wymagana. Ten tekst określa obszar nazw, wstawki zakłada jest importowany.

## <a name="object-element"></a><a name="object"></a> Element obiektu
 Definiuje obiekty fragmentu kodu, które można edytować. `Object`Element jest używany do identyfikowania elementu, który jest wymagany przez fragment kodu, ale prawdopodobnie zostanie zdefiniowany poza fragmentem. Na przykład formanty interfejsu Windows Forms, formanty środowiska ASP.NET, wystąpienia obiektów i wystąpienia typów powinny być deklarowane jako obiekty. Deklaracje obiektów wymagają określenia typu, który jest wykonywany przy użyciu `Type` elementu.

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
|`Editable`|Opcjonalny `Boolean` atrybut. Określa, czy po wstawieniu fragmentu kodu można edytować literał. Wartość domyślna tego atrybutu to `true` .|

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element domyślny](../ide/code-snippets-schema-reference.md#default)|Element wymagany. Określa domyślną wartość literału po wstawieniu fragmentu kodu. W elemencie musi znajdować się tylko jeden `Default` element `Literal` .|
|[Element Function](../ide/code-snippets-schema-reference.md#function)|Element opcjonalny. Określa funkcję do wykonania, gdy w programie Visual Studio na literale zostanie ustawiony fokus. Element nie może zawierać żadnych `Function` elementów `Literal` .|
|[ID — element](../ide/code-snippets-schema-reference.md#id)|Element wymagany. Określa unikatowy identyfikator literału. W elemencie musi znajdować się tylko jeden `ID` element `Literal` .|
|[Element ToolTip](../ide/code-snippets-schema-reference.md#tooltip)|Element opcjonalny. Opisuje oczekiwaną wartość i użycie literału. Element nie może zawierać żadnych elementów **etykietki narzędzia** `Literal` .|
|[Element Type](../ide/code-snippets-schema-reference.md#type)|Element wymagany. Określa typ obiektu. W elemencie musi znajdować się tylko jeden `Type` element `Object` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element deklaracji](../ide/code-snippets-schema-reference.md#declarations)|Zawiera literały i obiekty fragmentu kodu, które można edytować.|

## <a name="reference-element"></a><a name="reference"></a> Reference — element
 Określa informacje o odwołaniach do zestawów wymaganych przez fragment kodu.

> [!NOTE]
> `Reference`Element jest obsługiwany tylko w projektach Visual Basic.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element Assembly](../ide/code-snippets-schema-reference.md#assembly)|Element wymagany. Zawiera nazwę zestawu, do którego się odwołuje fragment kodu. W elemencie musi znajdować się tylko jeden `Assembly` element `Reference` .|
|[Element adresu URL](../ide/code-snippets-schema-reference.md#url)|Element opcjonalny. Zawiera adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie. Element nie może zawierać żadnych `Url` elementów `Reference` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[References — element](../ide/code-snippets-schema-reference.md#references)|Element grupujący dla `Reference` elementów.|

## <a name="references-element"></a><a name="references"></a> References — element
 Grupuje poszczególne `Reference` elementy.

> [!NOTE]
> `References`Element jest obsługiwany tylko w projektach Visual Basic.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Reference — element](../ide/code-snippets-schema-reference.md#reference)|Element opcjonalny. Zawiera informacje o odwołaniach do zestawów z fragmentu kodu. Element może mieć zero lub więcej `Reference` elementów `References` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element fragmentu kodu](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|

## <a name="shortcut-element"></a><a name="shortcut"></a> Element skrótu
 Określa tekst skrótu służący do wstawiania fragmentu kodu. Wartość tekstowa `Shortcut` elementu może zawierać tylko znaki alfanumeryczne, łączniki (-) i znaki podkreślenia (_).

> [!CAUTION]
> Znaki _ i — nie są obsługiwane w skrótach do fragmentów kodu języka C++.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|

 Wartość tekstowa jest opcjonalna. Ten tekst jest używany jako skrót do wstawiania fragmentu kodu.

## <a name="snippet-element"></a><a name="snippet"></a> Element fragmentu kodu
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
|[Element Code](../ide/code-snippets-schema-reference.md#code)|Element wymagany. Określa kod, który ma zostać wstawiony do pliku dokumentacji. W elemencie musi znajdować się tylko jeden `Code` element `Snippet` .|
|[Element deklaracji](../ide/code-snippets-schema-reference.md#declarations)|Element opcjonalny. Określa literały i obiekty tworzące sekcje fragmentu kodu, które można edytować. Element nie może zawierać żadnych `Declarations` elementów `Snippet` .|
|[Imports — element](../ide/code-snippets-schema-reference.md#imports)|Element opcjonalny. Grupuje poszczególne `Import` elementy. Element nie może zawierać żadnych `Imports` elementów `Snippet` .|
||Element opcjonalny. Grupuje poszczególne `Reference` elementy. Element nie może zawierać żadnych `References` elementów `Snippet` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[CodeSnippet, element](../ide/code-snippets-schema-reference.md#codesnippet)|Umożliwia określenie nagłówka oraz wielu fragmentów kodu IntelliSense, które można wstawiać do plików kodu programu Visual Studio.|

## <a name="snippettype-element"></a><a name="snippettype"></a> Fragment kodu elementu
 Określa, w jaki sposób program Visual Studio wstawia fragment kodu.

```xml
<SnippetType>
    SurroundsWith/Expansion
<SnippetType>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[SnippetTypes, element](../ide/code-snippets-schema-reference.md#snippettypes)|Grupuje `SnippetType` elementy.|

 Wartość tekstowa musi być jedną z następujących:

- `SurroundsWith`: umożliwia umieszczenie fragmentu kodu wokół zaznaczonego fragmentu kodu.

- `Expansion`: umożliwia wstawianie fragmentu kodu do kursora.

- `Refactoring`: określa, że fragment kodu jest używany podczas refaktoryzacji Visual C#. `Refactoring` nie można używać w niestandardowych fragmentach kodu.

## <a name="snippettypes-element"></a><a name="snippettypes"></a> SnippetTypes, element
 Grupuje poszczególne `SnippetType` elementy. Jeśli `SnippetTypes` element nie jest obecny, fragment kodu można wstawić w dowolnym miejscu w kodzie.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
<SnippetTypes>
```

|Element podrzędny|Opis|
|-------------------|-----------------|
|[Element SnippetType](../ide/code-snippets-schema-reference.md#snippettype)|Element opcjonalny. Określa, w jaki sposób program Visual Studio wstawia fragment kodu do kodu. Element może mieć zero lub więcej `SnippetType` elementów `SnippetTypes` .|

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Określa ogólne informacje o fragmencie kodu.|

## <a name="title-element"></a><a name="title"></a> Title — element
 Określa tytuł fragmentu kodu. Tytuł przechowywany w `Title` elemencie fragmentu kodu pojawia się w **selektorze fragmentów kodu** i w opisie fragmentu kodu w **Menedżerze fragmentów kodu**.

```xml
<Title>
    Code Snippet Title
<Title>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Określa ogólne informacje o fragmencie kodu.|

 Wartość tekstowa jest wymagana. Tekst określa tytuł fragmentu kodu.

## <a name="tooltip-element"></a><a name="tooltip"></a> Element ToolTip
 Opisuje oczekiwaną wartość i użycie literału lub obiektu we fragmencie kodu. Informacje te będą wyświetlane w programie Visual Studio w etykietce narzędzia po wstawieniu fragmentu kodu do projektu. Tekst etykietki narzędzia jest wyświetlany, gdy wskaźnik myszy znajdzie się nad literałem lub obiektem.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

 Wartość tekstowa jest wymagana. Ten tekst określa opis etykietki narzędzia, który zostanie skojarzony z obiektem lub literałem we fragmencie kodu.

## <a name="type-element"></a><a name="type"></a> Element Type
 Określa typ obiektu. `Object`Element jest używany do identyfikowania elementu, który jest wymagany przez fragment kodu, ale prawdopodobnie zostanie zdefiniowany poza fragmentem. Na przykład formanty interfejsu Windows Forms, formanty środowiska ASP.NET, wystąpienia obiektów i wystąpienia typów powinny być deklarowane jako obiekty. Deklaracje obiektów wymagają określenia typu, który jest wykonywany przy użyciu `Type` elementu.

```xml
<Type>
    Type
</Type>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Element obiektu](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|

 Wartość tekstowa jest wymagana. Ten tekst określa typ obiektu.

## <a name="url-element"></a><a name="url"></a> Element adresu URL
 Określa adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie.

> [!NOTE]
> `Url`Element jest obsługiwany tylko w projektach Visual Basic.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Element nadrzędny|Opis|
|--------------------|-----------------|
|[Reference — element](../ide/code-snippets-schema-reference.md#reference)|Określa odwołania do zestawów wymagane we fragmencie kodu.|

 Wartość tekstowa jest wymagana. Ten tekst określa adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie. Ten adres URL jest wyświetlany, gdy do projektu nie można dodać odwołania.

## <a name="see-also"></a>Zobacz też
 Przewodnik po [fragmentach kodu](../ide/code-snippets.md) [: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)

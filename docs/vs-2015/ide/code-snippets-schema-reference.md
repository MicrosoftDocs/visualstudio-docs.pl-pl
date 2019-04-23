---
title: Odwołanie do schematu fragmentów kodu | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 994b87de61aaa0b303b0b0bf8454dad716c9978f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114512"
---
# <a name="code-snippets-schema-reference"></a>Fragmenty kodu — Odwołanie do schematu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kodu IntelliSense to wstępnie przygotowane wycinki kodu źródłowego, które są gotowe do wstawienia do aplikacji za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Umożliwiają one poprawę wydajności pracy, ponieważ zmniejszają ilość czasu spędzanego na wielokrotnym wpisywaniu tego samego kodu czy wyszukiwaniu przykładów. Można użyć schematu XML fragmentu kodu IntelliSense, aby utworzyć własne fragmenty kodu i dodaj je do fragmentów kodu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zawiera już.  
  
## <a name="intellisense-code-snippets-schema-elements"></a>Elementy schematu fragmentów kodu IntelliSense  
  
||||  
|-|-|-|  
|[Assembly — Element](../ide/code-snippets-schema-reference.md#assembly)|[Helpurl — Element](../ide/code-snippets-schema-reference.md#helpurl)|[References — Element](../ide/code-snippets-schema-reference.md#references)|  
|[AUTHOR — Element](../ide/code-snippets-schema-reference.md#author)|[ID — Element](../ide/code-snippets-schema-reference.md#id)|[Shortcut — Element](../ide/code-snippets-schema-reference.md#shortcut)|  
|[Code Element](../ide/code-snippets-schema-reference.md#code)|[Import — Element](../ide/code-snippets-schema-reference.md#import)|[Snippet — Element](../ide/code-snippets-schema-reference.md#snippet)|  
|[CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)|[Imports Element](../ide/code-snippets-schema-reference.md#imports)|[Snippettype — Element](../ide/code-snippets-schema-reference.md#snippettype)|  
|[Codesnippets — Element](../ide/code-snippets-schema-reference.md#codesnippets)|[Keyword Element](../ide/code-snippets-schema-reference.md#keyword)|[Snippettypes — Element](../ide/code-snippets-schema-reference.md#snippettypes)|  
|[Declarations — Element](../ide/code-snippets-schema-reference.md#declarations)|[Keywords Element](../ide/code-snippets-schema-reference.md#keywords)|[Title — Element](../ide/code-snippets-schema-reference.md#title)|  
|[Default — Element](../ide/code-snippets-schema-reference.md#default)|[Literal — Element](../ide/code-snippets-schema-reference.md#literal)|[ToolTip — Element](../ide/code-snippets-schema-reference.md#tooltip)|  
|[Description — Element](../ide/code-snippets-schema-reference.md#description)|[Namespace — Element](../ide/code-snippets-schema-reference.md#namespace)|[Typ elementu](../ide/code-snippets-schema-reference.md#type)|  
|[Function — Element](../ide/code-snippets-schema-reference.md#function)|[Object — Element](../ide/code-snippets-schema-reference.md#object)|[URL — Element](../ide/code-snippets-schema-reference.md#url)|  
|[Header — Element](../ide/code-snippets-schema-reference.md#header)|[Reference — Element](../ide/code-snippets-schema-reference.md#reference)||  
  
## <a name="assembly"></a> Assembly — Element  
 Określa nazwę zestawu, do którego się odwołuje fragment kodu.  
  
> [!NOTE]
>  `Assembly` Jest obsługiwany tylko przez fragmenty kodu Visual Basic.  
  
 Wartość tekstowa elementu **zestawu** element jest albo przyjazna tekstowa Nazwa zestawu, taką jak `System.dll`, lub jego silna nazwa, taka jak `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.  
  
```xml  
<Assembly>  
    AssemblyName  
</Assembly>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Reference — Element](../ide/code-snippets-schema-reference.md#reference)|Zawiera informacje o odwołaniach do zestawów wymaganych przez fragment kodu.|  
  
 Wartość tekstowa jest wymagana. Tekst określa zestaw, do którego odwołuje się fragment kodu.  
  
## <a name="author"></a> AUTHOR — Element  
 Określa nazwę autora fragmentu kodu. **Menedżera wstawek kodu** Wyświetla nazwę przechowywanego w `Author` element fragmentu kodu.  
  
```xml  
<Author>  
   Code Snippet Author  
</Author>  
  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Header — Element](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest wymagana. Tekst określa autora fragmentu kodu.  
  
## <a name="code"></a> Code Element  
 Stanowi kontener dla krótkich bloków kodu.  
  
 Dwa słowa zastrzeżone są dostępne do użycia w tekście `Code` element: `$end$` i `$selected$`. `$end$` oznacza lokalizację, aby umieść kursor po wstawieniu fragmentu kodu. `$selected$` reprezentuje tekst zaznaczony w dokumencie, który ma zostać wstawiony do fragment kodu podczas jego wywoływania. Na przykład biorąc pod uwagę fragment kodu, który zawiera:  
  
```xml  
$selected$ is a great color.  
```  
  
 Jeśli wyraz "Niebieski" jest zaznaczone, gdy użytkownik wywołuje szablon, wynik jest:  
  
```xml  
Blue is a great color.  
```  
  
 Nie możesz użyć albo `$end$` lub `$selected$` więcej niż jeden raz we fragmencie kodu. Jeśli to zrobisz, drugie wystąpienie jest rozpoznawana. Podane fragment kodu, który zawiera:  
  
```  
$selected$ is a great color. I love $selected$.  
```  
  
 Jeśli wybrano słowo "Blue", wynik jest:  
  
```  
is a great color. I love Blue.  
```  
  
 Początkowa przestrzeń pojawia się, ponieważ brakuje miejsca między `$selected$` i `is`.  
  
 Wszystkie inne `$` słowa kluczowe są definiowane dynamicznie w `<Literal>` i `<Object>` tagów.  
  
```xml  
<Code Language="Language"  
    Kind="method body/method decl/type decl/page/file/any"  
    Delimiter="Delimiter">  
    Code to insert  
</Code>  
```  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Delimiter`|Atrybut opcjonalny. Określa separator używany do opisywania literałów i obiektów w kodzie. Domyślnie ogranicznikiem jest znak `$`.|  
|`Kind`|Atrybut opcjonalny. Określa rodzaj kodu znajdującego się we fragmencie oraz miejsce, gdzie trzeba wstawić fragment, aby został poprawnie skompilowany. Dostępne wartości to `method body`, `method decl`, `type decl`, `file`, i `any`.|  
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
|[Snippet — Element](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|  
  
 Wartość tekstowa jest wymagana. Tekst określa kod, łącznie z literałami i obiektami, którego można używać podczas wstawiania tego fragmentu do projektu.  
  
## <a name="codesnippet"></a> CodeSnippet Element  
 Umożliwia określenie nagłówka oraz wielu fragmentów kodu IntelliSense, które można wstawiać do plików kodu programu Visual Studio.  
  
```xml  
<CodeSnippet Format="x.x.x">  
    <Header>... </Header>  
    <Snippet>... </Snippet>  
</CodeSnippet>  
  
```  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Format`|Atrybut wymagany. Określa wersję schematu fragmentu kodu. Atrybut Format musi być ciągiem tekstowym o składni x.x.x, gdzie każdy znak „x” reprezentuje wartość liczbową numeru wersji. Program Visual Studio będzie ignorować fragmentów kodu z `Format` atrybuty, których nie rozumie.|  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Header — Element](../ide/code-snippets-schema-reference.md#header)|Element wymagany. Zawiera ogólne informacje o fragmencie kodu. Musi zawierać dokładnie jeden `Header` element we fragmencie kodu.|  
|[Snippet — Element](../ide/code-snippets-schema-reference.md#snippet)|Element wymagany. Zawiera kod, który będzie wstawiany przez program Visual Studio. Musi zawierać dokładnie jeden `Snippet` element we fragmencie kodu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Codesnippets — Element](../ide/code-snippets-schema-reference.md#codesnippets)|Element główny schematu XML fragmentu kodu.|  
  
## <a name="codesnippets"></a> Codesnippets — Element  
 Grupy [CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)elementów. `CodeSnippets` Element jest elementem główny schematu XML fragmentu kodu.  
  
```xml  
<CodeSnippets>  
    <CodeSnippet>... </CodeSnippet>  
</CodeSnippets>  
  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)|Element opcjonalny. Element nadrzędny dla wszystkich danych fragmentu kodu. Może wynosić zero lub więcej `CodeSnippet` elementów w `CodeSnippets` elementu.|  
  
## <a name="declarations"></a> Declarations — Element  
 Określa literały i obiekty tworzące sekcje fragmentu kodu, które można edytować.  
  
```xml  
<Declarations>  
    <Literal>... </Literal>  
    <Object>... </Object>  
</Declarations>  
  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Literal — Element](../ide/code-snippets-schema-reference.md#literal)|Element opcjonalny. Definiuje literały fragmentu kodu, które można edytować. Może wynosić zero lub więcej `Literal` elementów w `Declarations` elementu.|  
|[Object — Element](../ide/code-snippets-schema-reference.md#object)|Element opcjonalny. Definiuje obiekty fragmentu kodu, które można edytować. Może wynosić zero lub więcej `Object` elementów w `Declarations` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Snippet — Element](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|  
  
## <a name="default"></a> Default — Element  
 Określa domyślną wartość literału lub obiektu fragmentu kodu IntelliSense.  
  
```xml  
<Default>  
    Default value  
</Default>  
  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Literal — Element](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|  
|[Object — Element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa domyślną wartość literału lub obiektu wypełniającego pola fragment kodu, który można edytować.  
  
## <a name="description"></a> Description — Element  
 Określa opisowe informacje o zawartości fragmentu kodu IntelliSense.  
  
```xml  
<Description>  
    Code Snippet Description  
</Description>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Header — Element](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest wymagana. Ten tekst opisuje fragment kodu.  
  
## <a name="function"></a> Function — Element  
 Określa funkcję do wykonania, gdy w programie Visual Studio na literale lub obiekcie zostanie ustawiony fokus.  
  
> [!NOTE]
>  `Function` Jest obsługiwany tylko w fragmentach kodu języka Visual C#.  
  
```xml  
<Function>  
    FunctionName  
</Function>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Literal — Element](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|  
|[Object — Element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa funkcję do wykonania, gdy w programie Visual Studio na literale lub polu obiektu zostanie ustawiony fokus.  
  
## <a name="header"></a> Header — Element  
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
|[AUTHOR — Element](../ide/code-snippets-schema-reference.md#author)|Element opcjonalny. Imię i nazwisko/nazwa osoby lub firmy, która utworzyła fragment kodu. Może mieć zero lub jeden `Author` elementów w `Header` elementu.|  
|[Description — Element](../ide/code-snippets-schema-reference.md#description)|Element opcjonalny. Opis fragmentu kodu. Może mieć zero lub jeden `Description` elementów w `Header` elementu.|  
|[Helpurl — Element](../ide/code-snippets-schema-reference.md#helpurl)|Element opcjonalny. Adres URL strony zawierającej poszerzone informacje o fragmencie kodu. Może mieć zero lub jeden `HelpURL` elementy w elemencie nagłówka. **Uwaga:**  Visual Studio nie wykorzystuje `HelpUrl` elementu. Element jest częścią schematu XML fragmentu kodu IntelliSense. Wszystkie fragmenty kodu zawierające element będą weryfikowane, ale wartość elementu nigdy nie jest używana.|  
|[Keywords Element](../ide/code-snippets-schema-reference.md#keywords)|Element opcjonalny. Grupy `Keyword` elementów. Może mieć zero lub jeden `Keywords` elementów w `Header` elementu.|  
|[Shortcut — Element](../ide/code-snippets-schema-reference.md#shortcut)|Element opcjonalny. Określa tekst skrótu, który pozwala wstawić fragment kodu. Może mieć zero lub jeden `Shortcut` elementów w `Header` elementu.|  
|[Snippettypes — Element](../ide/code-snippets-schema-reference.md#snippettypes)|Element opcjonalny. Grupy `SnippetType` elementów. Może mieć zero lub jeden `SnippetTypes` elementów w `Header` elementu. W przypadku nie `SnippetTypes` elementów, fragment kodu zawsze jest prawidłowy.|  
|[Title — Element](../ide/code-snippets-schema-reference.md#title)|Element wymagany. Przyjazna nazwa fragmentu kodu. Musi zawierać dokładnie jeden `Title` element `Header` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)|Element nadrzędny dla wszystkich danych fragmentu kodu.|  
  
## <a name="helpurl"></a> Helpurl — Element  
 Określa adres URL strony zawierającej poszerzone informacje o fragmencie kodu.  
  
> [!NOTE]
>  Visual Studio nie wykorzystuje `HelpUrl` elementu. Element jest częścią schematu XML fragmentu kodu IntelliSense. Wszystkie fragmenty kodu zawierające element będą weryfikowane, ale wartość elementu nigdy nie jest używana.  
  
```xml  
<HelpUrl>  
    www.microsoft.com  
</HelpUrl>  
  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Header — Element](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest opcjonalna. Ten tekst określa adres URL strony, na której można znaleźć więcej informacji o fragmencie kodu.  
  
## <a name="id"></a> ID — Element  
 Określa unikatowy identyfikator `Literal` lub `Object` elementu. Żadne dwa literały ani obiekty w tym samym fragmencie kodu może mieć takiej samej wartości tekstowej w swoich `ID` elementów. Literały i obiekty nie mogą zawierać `ID` element z wartością elementu end. Wartość `$end$` jest zastrzeżona i służy do oznaczania miejsca aby umieść kursor po wstawieniu fragmentu kodu.  
  
```xml  
<ID>  
    Unique Identifier  
</ID>  
  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Literal — Element](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|  
|[Object — Element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa unikatowy identyfikator obiektu lub literału.  
  
## <a name="import"></a> Import — Element  
 Określa zaimportowaną przestrzeń nazw używaną przez fragment kodu IntelliSense.  
  
> [!NOTE]
>  `Import` Element jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<Import>  
    <Namespace>... </Namespace>  
</Import>  
  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Namespace — Element](../ide/code-snippets-schema-reference.md#namespace)|Element wymagany. Określa przestrzeń nazw używaną przez fragment kodu. Musi zawierać dokładnie jeden `Namespace` element `Import` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Imports Element](../ide/code-snippets-schema-reference.md#imports)|Element grupujący **importu** elementów.|  
  
## <a name="imports"></a> Imports Element  
 Grupuje poszczególne `Import` elementów.  
  
> [!NOTE]
>  `Imports` Element jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<Imports>  
    <Import>... </Import>  
<Imports>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Import — Element](../ide/code-snippets-schema-reference.md#import)|Element opcjonalny. Zawiera zaimportowane przestrzenie nazw fragmentu kodu. Może wynosić zero lub więcej **importu** elementów w `Imports` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Snippet — Element](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|  
  
## <a name="keyword"></a> Keyword — Element  
 Określa niestandardowe słowo kluczowe fragmentu kodu. Słowa kluczowe fragmentu kodu są wykorzystywane przez program Visual Studio. Stanowią standardowy mechanizm, przy użyciu którego dostawcy treści internetowych mogą dodawać słowa kluczowe na potrzeby wyszukiwania lub kategoryzacji.  
  
```xml  
<Keyword>  
    Code Snippet Keyword  
</Keyword>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Keywords Element](../ide/code-snippets-schema-reference.md#keywords)|Grupuje poszczególne `Keyword` elementów.|  
  
 Wartość tekstowa jest wymagana. Słowo kluczowe fragmentu kodu.  
  
## <a name="keywords"></a> KEYWORDS — Element  
 Grupuje poszczególne `Keyword` elementów. Słowa kluczowe fragmentu kodu są wykorzystywane przez program Visual Studio. Stanowią standardowy mechanizm, przy użyciu którego dostawcy treści internetowych mogą dodawać słowa kluczowe na potrzeby wyszukiwania lub kategoryzacji.  
  
```xml  
<Keywords>  
    <Keyword>... </Keyword>  
    <Keyword>... </Keyword>  
<Keywords>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Keyword Element](../ide/code-snippets-schema-reference.md#keyword)|Element opcjonalny. Zawiera poszczególne słowa kluczowe fragmentu kodu. Może wynosić zero lub więcej `Keyword` elementów w `Keywords` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Header — Element](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
## <a name="literal"></a> Literal — Element  
 Definiuje literały fragmentu kodu, które można edytować. `Literal` Element jest używany do identyfikowania zamiennika fragment kodu, który zawiera się całkowicie we fragmencie, ale prawdopodobnie można dostosować, po jego wstawieniu do kodu. Jako literały należy na przykład deklarować ciągi literałowe, wartości liczbowe i nazwy niektórych zmiennych.  
  
 Literały i obiekty nie mogą zawierać **identyfikator** wybrany element o wartości ani na końcu. Wartość `$selected$` reprezentuje tekst zaznaczony w dokumencie, który ma zostać wstawiony do fragment kodu podczas jego wywoływania. `$end$` oznacza lokalizację, aby umieść kursor po wstawieniu fragmentu kodu.  
  
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
|`Editable`|Opcjonalnie `Boolean` atrybutu. Określa, czy po wstawieniu fragmentu kodu można edytować literał. Wartość domyślna tego atrybutu to `true`.|  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Default — Element](../ide/code-snippets-schema-reference.md#default)|Element wymagany. Określa domyślną wartość literału po wstawieniu fragmentu kodu. Musi zawierać dokładnie jeden `Default` element `Literal` elementu.|  
|[Function — Element](../ide/code-snippets-schema-reference.md#function)|Element opcjonalny. Określa funkcję do wykonania, gdy w programie Visual Studio na literale zostanie ustawiony fokus. Może mieć zero lub jeden `Function` elementów w `Literal` elementu.|  
|[ID — Element](../ide/code-snippets-schema-reference.md#id)|Element wymagany. Określa unikatowy identyfikator literału. Musi zawierać dokładnie jeden `ID` element `Literal` elementu.|  
|[ToolTip — Element](../ide/code-snippets-schema-reference.md#tooltip)|Element opcjonalny. Opisuje oczekiwaną wartość i użycie literału. Może mieć zero lub jeden **etykietki narzędzia** elementów w `Literal` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Declarations — Element](../ide/code-snippets-schema-reference.md#declarations)|Zawiera literały i obiekty fragmentu kodu, które można edytować.|  
  
## <a name="namespace"></a> Namespace — Element  
 Określa przestrzeń nazw, którą należy zaimportować, aby fragment kodu został skompilowany i działał. Przestrzeń nazw określona w `Namespace` element jest automatycznie dodawany do `Imports` instrukcji na początku kodu, jeśli jeszcze nie istnieje.  
  
> [!NOTE]
>  `Namespace` Element jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<Namespace>  
    Namespace  
</Namespace>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Import — Element](../ide/code-snippets-schema-reference.md#import)|Importowanie określonej przestrzeni nazw.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa obszar nazw, wstawki zakłada jest importowany.  
  
## <a name="object"></a> Object — Element  
 Definiuje obiekty fragmentu kodu, które można edytować. `Object` Element jest używany do identyfikowania elementu, który jest wymagany przez fragment kodu, ale prawdopodobnie zostanie zdefiniowany poza fragmentem. Na przykład formanty interfejsu Windows Forms, formanty środowiska ASP.NET, wystąpienia obiektów i wystąpienia typów powinny być deklarowane jako obiekty. Deklaracje obiektów wymagają określenia typu, który jest przeprowadzane za pomocą `Type` elementu.  
  
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
|`Editable`|Opcjonalnie `Boolean` atrybutu. Określa, czy po wstawieniu fragmentu kodu można edytować literał. Wartość domyślna tego atrybutu to `true`.|  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Default — Element](../ide/code-snippets-schema-reference.md#default)|Element wymagany. Określa domyślną wartość literału po wstawieniu fragmentu kodu. Musi zawierać dokładnie jeden `Default` element `Literal` elementu.|  
|[Function — Element](../ide/code-snippets-schema-reference.md#function)|Element opcjonalny. Określa funkcję do wykonania, gdy w programie Visual Studio na literale zostanie ustawiony fokus. Może mieć zero lub jeden `Function` elementów w `Literal` elementu.|  
|[ID — Element](../ide/code-snippets-schema-reference.md#id)|Element wymagany. Określa unikatowy identyfikator literału. Musi zawierać dokładnie jeden `ID` element `Literal` elementu.|  
|[ToolTip — Element](../ide/code-snippets-schema-reference.md#tooltip)|Element opcjonalny. Opisuje oczekiwaną wartość i użycie literału. Może mieć zero lub jeden **etykietki narzędzia** elementów w `Literal` elementu.|  
|[Typ elementu](../ide/code-snippets-schema-reference.md#type)|Element wymagany. Określa typ obiektu. Musi zawierać dokładnie jeden `Type` element `Object` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Declarations — Element](../ide/code-snippets-schema-reference.md#declarations)|Zawiera literały i obiekty fragmentu kodu, które można edytować.|  
  
## <a name="reference"></a> Reference — Element  
 Określa informacje o odwołaniach do zestawów wymaganych przez fragment kodu.  
  
> [!NOTE]
>  `Reference` Element jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<Reference>  
    <Assembly>... </Assembly>  
    <Url>... </Url>  
</Reference>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Assembly — Element](../ide/code-snippets-schema-reference.md#assembly)|Element wymagany. Zawiera nazwę zestawu, do którego się odwołuje fragment kodu. Musi zawierać dokładnie jeden `Assembly` element `Reference` elementu.|  
|[URL — Element](../ide/code-snippets-schema-reference.md#url)|Element opcjonalny. Zawiera adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie. Może mieć zero lub jeden `Url` elementów w `Reference` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[References — Element](../ide/code-snippets-schema-reference.md#references)|Element grupujący `Reference` elementów.|  
  
## <a name="references"></a> References — Element  
 Grupuje poszczególne `Reference` elementów.  
  
> [!NOTE]
>  `References` Element jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<References>  
    <Reference>... </Reference>  
</References>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Reference — Element](../ide/code-snippets-schema-reference.md#reference)|Element opcjonalny. Zawiera informacje o odwołaniach do zestawów z fragmentu kodu. Może wynosić zero lub więcej `Reference` elementów w `References` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Snippet — Element](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|  
  
## <a name="shortcut"></a> Shortcut — Element  
 Określa tekst skrótu służący do wstawiania fragmentu kodu. Wartość tekstowa elementu `Shortcut` element może zawierać tylko znaki alfanumeryczne, łączniki (-) i podkreślenia (_).  
  
> [!CAUTION]
>  Znaki _ i — nie są obsługiwane w skrótach do fragmentów kodu języka C++.  
  
```xml  
<Shortcut>  
    Shortcut Text  
</Shortcut>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Header — Element](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest opcjonalna. Ten tekst jest używany jako skrót do wstawiania fragmentu kodu.  
  
## <a name="snippet"></a> Snippet — Element  
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
|[Code Element](../ide/code-snippets-schema-reference.md#code)|Element wymagany. Określa kod, który ma zostać wstawiony do pliku dokumentacji. Musi zawierać dokładnie jeden `Code` element `Snippet` elementu.|  
|[Declarations — Element](../ide/code-snippets-schema-reference.md#declarations)|Element opcjonalny. Określa literały i obiekty tworzące sekcje fragmentu kodu, które można edytować. Może mieć zero lub jeden `Declarations` elementów w `Snippet` elementu.|  
|[Imports Element](../ide/code-snippets-schema-reference.md#imports)|Element opcjonalny. Grupuje poszczególne `Import` elementów. Może mieć zero lub jeden `Imports` elementów w `Snippet` elementu.|  
||Element opcjonalny. Grupuje poszczególne `Reference` elementów. Może mieć zero lub jeden `References` elementów w `Snippet` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)|Umożliwia określenie nagłówka oraz wielu fragmentów kodu IntelliSense, które można wstawiać do plików kodu programu Visual Studio.|  
  
## <a name="snippettype"></a> Snippettype — Element  
 Określa, w jaki sposób program Visual Studio wstawia fragment kodu.  
  
```xml  
<SnippetType>  
    SurroundsWith/Expansion  
<SnippetType>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Snippettypes — Element](../ide/code-snippets-schema-reference.md#snippettypes)|Grupy `SnippetType` elementów.|  
  
 Wartość tekstowa musi być jedną z następujących:  
  
- `SurroundsWith`: pozwala umieścić wokół zaznaczonej sekcji kodu fragment kodu.  
  
- `Expansion`: pozwala fragment kodu, który ma zostać wstawiony przy kursorze.  
  
- `Refactoring`: Określa, że fragment kodu jest używany podczas refaktoryzacji Visual C#. `Refactoring` Nie można używać w niestandardowych fragmentach kodu.  
  
## <a name="snippettypes"></a> Snippettypes — Element  
 Grupuje poszczególne `SnippetType` elementów. Jeśli `SnippetTypes` element nie jest obecny, fragment kodu można wstawić w dowolnym miejscu w kodzie.  
  
```xml  
<SnippetTypes>  
    <SnippetType>... </SnippetType>  
    <SnippetType>... </SnippetType>  
<SnippetTypes>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Snippettype — Element](../ide/code-snippets-schema-reference.md#snippettype)|Element opcjonalny. Określa, w jaki sposób program Visual Studio wstawia fragment kodu do kodu. Może wynosić zero lub więcej `SnippetType` elementów w `SnippetTypes` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Header — Element](../ide/code-snippets-schema-reference.md#header)|Określa ogólne informacje o fragmencie kodu.|  
  
## <a name="title"></a> Title — Element  
 Określa tytuł fragmentu kodu. Tytuł przechowywany w `Title` element wstawki kodu programu pojawia się w **selektor wstawek kodu** oraz w opisie fragmentu kodu w **Menedżera wstawek kodu**.  
  
```xml  
<Title>  
    Code Snippet Title  
<Title>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Header — Element](../ide/code-snippets-schema-reference.md#header)|Określa ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest wymagana. Tekst określa tytuł fragmentu kodu.  
  
## <a name="tooltip"></a> ToolTip — Element  
 Opisuje oczekiwaną wartość i użycie literału lub obiektu we fragmencie kodu. Informacje te będą wyświetlane w programie Visual Studio w etykietce narzędzia po wstawieniu fragmentu kodu do projektu. Tekst etykietki narzędzia jest wyświetlany, gdy wskaźnik myszy znajdzie się nad literałem lub obiektem.  
  
```xml  
<ToolTip>  
    ToolTip description  
</ToolTip>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Literal — Element](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|  
|[Object — Element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa opis etykietki narzędzia, który zostanie skojarzony z obiektem lub literałem we fragmencie kodu.  
  
## <a name="type"></a> Typ elementu  
 Określa typ obiektu. `Object` Element jest używany do identyfikowania elementu, który jest wymagany przez fragment kodu, ale prawdopodobnie zostanie zdefiniowany poza fragmentem. Na przykład formanty interfejsu Windows Forms, formanty środowiska ASP.NET, wystąpienia obiektów i wystąpienia typów powinny być deklarowane jako obiekty. Deklaracje obiektów wymagają określenia typu, który jest przeprowadzane za pomocą `Type` elementu.  
  
```xml  
<Type>  
    Type  
</Type>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Object — Element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa typ obiektu.  
  
## <a name="url"></a> URL — Element  
 Określa adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie.  
  
> [!NOTE]
>  `Url` Element jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<Url>  
    www.microsoft.com  
</Url>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Reference — Element](../ide/code-snippets-schema-reference.md#reference)|Określa odwołania do zestawów wymagane we fragmencie kodu.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie. Ten adres URL jest wyświetlany, gdy do projektu nie można dodać odwołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Fragmenty kodu](../ide/code-snippets.md)   
 [Przewodnik: Tworzenie fragmentów kodu](../ide/walkthrough-creating-a-code-snippet.md)

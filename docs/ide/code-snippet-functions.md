---
title: Funkcje wstawek kodu
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60453b6842dd321b7c85c2837e12b1208adb18f9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939518"
---
# <a name="code-snippet-functions"></a>Funkcje fragmentów kodu

Istnieją trzy funkcje dostępne do użycia za pomocą wstawek kodu C#. Funkcje są określone w [funkcja](../ide/code-snippets-schema-reference.md#function-element) element fragmentu kodu. Aby uzyskać informacje na temat tworzenia fragmenty kodu, zobacz [fragmenty kodu](../ide/code-snippets.md).

## <a name="functions"></a>Funkcje

W poniższej tabeli opisano funkcje dostępne w połączeniu z `Function` element fragmentów kodu.

|Funkcja|Opis|Język|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|Generuje instrukcję switch i zestaw instrukcji case dla elementów członkowskich wyliczenia określony przez `EnumerationLiteral` parametru. `EnumerationLiteral` Parametr musi być odwołaniem do wyliczenia literału lub typ wyliczenia.|C#|
|`ClassName()`|Zwraca nazwę klasy, która zawiera wstawiono fragment kodu.|C#|
|`SimpleTypeName(TypeName)`|Zmniejsza *TypeName* parametr najprostszej postaci w kontekście, w której wywołano fragmentu kodu.|C#|

## <a name="generateswitchcases-example"></a>Przykład GenerateSwitchCases

Poniższy przykład pokazuje, jak używać `GenerateSwitchCases` funkcji. Po wstawieniu ten fragment kodu i wyliczenia jest zawierana `$switch_on$` literału, `$cases$` generuje literał `case` poufności informacji dla każdej wartości w wyliczeniu.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="classname-example"></a>Przykład ClassName

Poniższy przykład pokazuje, jak używać `ClassName` funkcji. Podczas wstawiania tego fragmentu kodu `$classname$` literał jest zastępowana nazwą otaczającej klasy w tej lokalizacji w pliku kodu.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="simpletypename-example"></a>Przykład SimpleTypeName

W tym przykładzie pokazano, jak używać `SimpleTypeName` funkcji. Gdy ten fragment kodu jest wstawiany do pliku z kodem `$SystemConsole$` literał zostanie zastąpiony najprostsza forma <xref:System.Console> typu w kontekście, w której wywołano fragment kodu.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Zobacz także

- [Function — element](../ide/code-snippets-schema-reference.md#function-element)
- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)

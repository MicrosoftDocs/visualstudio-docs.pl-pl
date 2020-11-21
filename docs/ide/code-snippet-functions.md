---
title: Funkcje wstawek kodu
description: Dowiedz się więcej na temat funkcji GenerateSwitchCases (EnumerationLiteral), ClassName () i SimpleTypeName (TypeName) dostępnych do użycia z fragmentami kodu w języku C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6529f4f82f7a8a6862ae85adbf170d2fb6f8706
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006513"
---
# <a name="code-snippet-functions"></a>Funkcje fragmentów kodu

Dostępne są trzy funkcje do użycia z fragmentami kodu w języku C#. Funkcje są określone w elemencie [Function](../ide/code-snippets-schema-reference.md#function-element) fragmentu kodu. Aby uzyskać informacje na temat tworzenia fragmentów kodu, zobacz [fragmenty kodu](../ide/code-snippets.md).

## <a name="functions"></a>Funkcje

W poniższej tabeli opisano funkcje dostępne do użycia z `Function` elementem w fragmentach kodu.

|Funkcja|Opis|Język|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|Generuje instrukcję Switch i zestaw instrukcji case dla elementów członkowskich wyliczenia określonego przez `EnumerationLiteral` parametr. `EnumerationLiteral`Parametr musi być odwołaniem do literału wyliczenia lub typem wyliczenia.|C#|
|`ClassName()`|Zwraca nazwę klasy zawierającej wstawiony fragment kodu.|C#|
|`SimpleTypeName(TypeName)`|Zmniejsza parametr *TypeName* do najprostszej postaci w kontekście, w którym został wywołany fragment kodu.|C#|

## <a name="generateswitchcases-example"></a>Przykład GenerateSwitchCases

Poniższy przykład pokazuje, jak używać `GenerateSwitchCases` funkcji. Gdy ten fragment kodu zostanie wstawiony, a Wyliczenie jest wprowadzane do `$switch_on$` literału, `$cases$` literał generuje `case` instrukcję dla każdej wartości w wyliczeniu.

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

Poniższy przykład pokazuje, jak używać `ClassName` funkcji. Po wstawieniu tego fragmentu `$classname$` literał zostanie zastąpiony nazwą otaczającej klasy w tej lokalizacji w pliku kodu.

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

Ten przykład pokazuje, jak używać `SimpleTypeName` funkcji. Gdy ten fragment kodu zostanie wstawiony do pliku z kodem, `$SystemConsole$` literał zostanie zastąpiony najprostszą formą <xref:System.Console> typu w kontekście, w którym został wywołany fragment kodu.

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

- [Element Function](../ide/code-snippets-schema-reference.md#function-element)
- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)

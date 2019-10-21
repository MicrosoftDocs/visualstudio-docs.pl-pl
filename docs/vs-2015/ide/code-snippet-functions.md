---
title: Funkcje fragmentów kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 92533b90e6a2da9f29a67d13c6e0eee2c31dbcfe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620237"
---
# <a name="code-snippet-functions"></a>Funkcje wstawek kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dostępne są trzy funkcje do użycia z fragmentami kodu [!INCLUDE[csprcs](../includes/csprcs-md.md)]. Funkcje są określone w elemencie [Function](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) fragmentu kodu. Aby uzyskać informacje na temat tworzenia fragmentów kodu, zobacz [fragmenty kodu](../ide/code-snippets.md).

## <a name="functions"></a>Funkcje
 W poniższej tabeli opisano funkcje dostępne do użycia z elementem `Function` w fragmentach kodu.

|Funkcja|Opis|Język|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Generuje instrukcję Switch i zestaw instrukcji case dla elementów członkowskich wyliczenia określonego przez parametr `EnumerationLiteral`. Parametr `EnumerationLiteral` musi być odwołaniem do literału wyliczenia lub typem wyliczenia.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`ClassName()`|Zwraca nazwę klasy zawierającej wstawiony fragment kodu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`SimpleTypeName(` `TypeName` `)`|Zmniejsza parametr *TypeName* do najprostszej postaci w kontekście, w którym został wywołany fragment kodu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać funkcji `GenerateSwitchCases`. Gdy ten fragment kodu zostanie wstawiony, a Wyliczenie zostanie wprowadzone do literału `$switch_on$`, literał `$cases$` generuje instrukcję `case` dla każdej wartości w wyliczeniu.

```
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

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać funkcji `ClassName`. Po wstawieniu tego fragmentu kodu literał `$classname$` jest zastępowany nazwą klasy otaczającej w tej lokalizacji w pliku kodu.

```
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
            <Code Language="vjsharp" Format="CData">
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

## <a name="example"></a>Przykład
 Ten przykład pokazuje, jak używać funkcji `SimpleTypeName`. Po wstawieniu tego fragmentu kodu do pliku w postaci literału `$SystemConsole$` zostanie zastąpiony najprostszą formą typu <xref:System.Console> w kontekście, w którym został wywołany fragment kodu.

```
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

## <a name="see-also"></a>Zobacz też
 [Function — element (fragmenty kodu IntelliSense)](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) [odwołania do schematu fragmentów kodu](../ide/code-snippets-schema-reference.md)

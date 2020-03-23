---
title: Funkcje wstawek kodu
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
ms.openlocfilehash: c7df85c429794d61028d5304108d289dfe9bf496
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594243"
---
# <a name="code-snippet-functions"></a>Funkcje fragmentów kodu

Dostępne są trzy funkcje do użycia z fragmentami kodu języka C#. Funkcje są określone w [function](../ide/code-snippets-schema-reference.md#function-element) elementu fragmentu kodu. Aby uzyskać informacje na temat tworzenia fragmentów kodu, zobacz [Fragmenty kodu](../ide/code-snippets.md).

## <a name="functions"></a>Funkcje

W poniższej tabeli opisano funkcje dostępne do użycia z elementem `Function` w fragmentach kodu.

|Funkcja|Opis|Język|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|Generuje instrukcję switch i zestaw instrukcji case dla członków wyliczenia `EnumerationLiteral` określonego przez parametr. Parametr `EnumerationLiteral` musi być odwołaniem do literału wyliczenia lub typem wyliczenia.|C#|
|`ClassName()`|Zwraca nazwę klasy zawierającej wstawiony fragment kodu.|C#|
|`SimpleTypeName(TypeName)`|Zmniejsza *Parametr TypeName* do najprostszej postaci w kontekście, w którym wywoływano fragment kodu.|C#|

## <a name="generateswitchcases-example"></a>Przykład GenerateSwitchCases

W poniższym przykładzie `GenerateSwitchCases` pokazano, jak korzystać z funkcji. Po wstawieniu tego fragmentu kodu i wyliczenia `$switch_on$` jest wprowadzany do literału, `$cases$` literał generuje instrukcję `case` dla każdej wartości w wyliczeniu.

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

## <a name="classname-example"></a>Przykład classname

W poniższym przykładzie `ClassName` pokazano, jak korzystać z funkcji. Po wstawieniu tego fragmentu `$classname$` literału jest zastępowana nazwą otaczającej klasy w tej lokalizacji w pliku kodu.

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

W tym przykładzie `SimpleTypeName` pokazano, jak korzystać z funkcji. Gdy ten fragment kodu zostanie wstawiony `$SystemConsole$` do pliku kodu, literał zostanie <xref:System.Console> zastąpiony najprostszą formą typu w kontekście, w którym fragment kodu został wywołany.

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

## <a name="see-also"></a>Zobacz też

- [Element funkcyjny](../ide/code-snippets-schema-reference.md#function-element)
- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)

---
title: Flagi Command-Line VSCT | Microsoft Docs
description: Kompilator Visual Studio command table udostępnia opcje wiersza polecenia w celu zapewnienia pomyślnej kompilacji plików vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce83df56e1bcfad50fe71da31291b5c43b26c47a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898899"
---
# <a name="vsct-compiler-command-line-flags"></a>Flagi wiersza polecenia kompilatora VSCT
Kompilator Visual Studio Command Table (VSCT) udostępnia przełączniki wiersza polecenia, aby zapewnić pomyślną kompilację plików vsct.

## <a name="command-line-parameters"></a>Parametry wiersza polecenia
 Aby wyświetlić podstawową pomoc VSCT w oknie polecenia, przejdź do folderu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  *Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ i wpisz:

```
vsct /?
```

 To polecenie zwraca następującą treść:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Znaki — (kreska) i / (ukośnik) są akceptowaną notacją wskazującą parametry wiersza polecenia.

 Dopuszczalne flagi i ich znaczenie są następujące.

|Przełącznik|Opis|
|------------|-----------------|
|-D|Określ wszelkie dodatkowe zdefiniowane symbole.|
|-I|Wskaż dodatkowe ścieżki dołączania, które mają być używane podczas rozpoznawania odwołań do plików.|
|-L|Określ nazwę <xref:System.Globalization.CultureInfo> kultury, na przykład "en-US".|
|-E|Emituj obiekty języka C# w określonej przestrzeni nazw dla elementów poleceń, a następnie [C&#124;H&#124;N]:*nazwa* pliku, gdzie C = C#, H = nagłówek C++, N = przestrzeń nazw. Przestrzeń nazw jest wymagana dla języka C#.|
|-v|Pełne dane wyjściowe.|

 Przełącznik -L nakazuje kompilatorowi wybranie grupy ciągów w celu uzyskania binarnego pliku cto, który odpowiada podanej <xref:System.Globalization.CultureInfo> nazwie kultury. Nazwa określonej kultury powinna być dopasowana do atrybutu Language co najmniej jednego [elementu Strings w](../../extensibility/strings-element.md) pliku vsct. Jeśli element Strings nie ma atrybutu Language, jest dziedziczony z zawierającego [go elementu CommandTable](../../extensibility/commandtable-element.md).

 Plik .vsct może mieć wiele elementów Strings, a każdy z nich może mieć inny atrybut Language. Globalizacja jest osiągana przez wielokrotne uruchomienie kompilatora VSCT i zmianę przełącznika -L dla każdej nazwy kultury.

 Jeśli nazwa kultury nadana przez przełącznik -L nie pasuje do atrybutu Language dowolnego elementu Strings, kompilator spróbuje dopasować język, a nie region. Jeśli na przykład nie można znaleźć "en-US", kompilator spróbuje zamiast tego użyć "en". W przeciwnym razie zostanie wypróbowana bieżąca kultura systemu operacyjnego. Jeśli to się nie stanie, zostanie skompilowany pierwszy element Strings, który znajdzie.

 Przełącznik -E może służyć do emitowania pliku nagłówka w stylu C, który zawiera symbole używane przez tabelę poleceń, lub do emitowania pliku C# zawierającego obiekty symboli poleceń.

 Przełączniki -D i -I mają składnię flag preprocesora Cl.exe C, które mają taką samą nazwę. Definicje -D w formacie X =Y są używane do rozszerzania testów opartych na formacie XML \<Defined> w `Condition` atrybutach. —Ścieżki dołączania są używane do rozpoznawania \<Include> odwołań \<Extern> do plików i \<Bitmap> . Więcej informacji można znaleźć w temacie VSCT XML Schema Reference (Odwołanie do [schematu XML VSCT).](../../extensibility/vsct-xml-schema-reference.md)

 Kompilator VSCT może również dekompilować wcześniej skompilowany plik binarny. W tym celu należy podać plik binarny dla pliku \<infile> .   Jeśli plik binarny został generowany przez kompilator VSCT, będzie miał już osadzone symbole i będzie tworzyć dane wyjściowe z nazwami symbolicznymi \<Symbols> w sekcji danych wyjściowych. Jeśli plik binarny został generowany przez kompilator CTC, dane wyjściowe będą zawierać rzeczywiste identyfikatory GUID i identyfikatory. Jeśli plik *.ctsym, który jest wytwarzanych przez bieżące wersje programu Ctc.exe, znajduje się w tym samym folderze co binarny plik wejściowy, symbole zostaną załadowane z tego pliku i użyte do danych wyjściowych.

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

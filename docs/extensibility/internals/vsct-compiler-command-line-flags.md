---
title: Flagi Command-Line kompilatora VSCT | Microsoft Docs
description: Kompilator tabeli poleceń programu Visual Studio udostępnia opcje wiersza polecenia, aby zapewnić pomyślne skompilowanie plików. vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 53e50e408166eb2d2e1545549cdd6c72018c9553
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938788"
---
# <a name="vsct-compiler-command-line-flags"></a>Flagi wiersza polecenia kompilatora VSCT
Kompilator programu Visual Studio Command Table (VSCT) zapewnia przełączniki wiersza polecenia, aby zapewnić pomyślne Kompilowanie plików. vsct.

## <a name="command-line-parameters"></a>Parametry wiersza polecenia
 Aby wyświetlić podstawową pomoc VSCT z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] okna **polecenia** , przejdź do *ścieżki instalacji zestawu SDK programu Visual Studio*\VisualStudioIntegration\Tools\Bin\ folder i wpisz:

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
> Znaki-(myślnik) i/(ukośnik) są zarówno zaakceptowanymi zapisami w celu wskazania parametrów wiersza polecenia.

 Dopuszczalne flagi i ich znaczenie są następujące.

|Przełącznik|Opis|
|------------|-----------------|
|-D|Określ wszelkie dodatkowe zdefiniowane symbole.|
|-I|Wskaż dodatkowe ścieżki dołączania, które powinny być używane podczas rozpoznawania odwołań do plików.|
|-L|Określ <xref:System.Globalization.CultureInfo> nazwę kultury, na przykład "en-us".|
|-E|Emituj obiekty w języku C# w określonej przestrzeni nazw dla elementów polecenia, a następnie [C&#124;H&#124;N]:*filename* gdzie C = C#, H = nagłówek C++, N = przestrzeń nazw. Przestrzeń nazw jest wymagana dla języka C#.|
|-v|Pełne dane wyjściowe.|

 Przełącznik-L instruuje kompilator, aby wybierał grupę ciągów, aby utworzyć plik binarny. Dyrektor ds, który odnosi się do podanej <xref:System.Globalization.CultureInfo> nazwy kultury. Określona nazwa kultury powinna być zgodna z atrybutem Language jednego lub więcej [elementów String](../../extensibility/strings-element.md) w pliku. vsct. Jeśli element Strings nie ma atrybutu language, jest Dziedziczony z zawierającego [element](../../extensibility/commandtable-element.md).

 Plik. vsct może mieć wiele elementów String, a każdy z nich może mieć inny atrybut języka. Globalizacja jest osiągana przez uruchomienie kompilatora VSCT wiele razy i zmianę przełącznika-L dla każdej nazwy kultury.

 Jeśli nazwa kultury określona przez przełącznik-L nie jest zgodna z atrybutem Language dowolnego elementu String, kompilator podejmie próbę dopasowania do języka, a nie regionu. Na przykład jeśli nie można znaleźć "en-US", kompilator podejmie próbę "en" zamiast tego. Niepowodzenie, spowoduje to wypróbowanie bieżącej kultury systemu operacyjnego. Niepowodzenie, spowoduje skompilowanie pierwszych znalezionych elementów ciągów.

 Przełącznik-E może służyć do emitowania pliku nagłówkowego w stylu C, który zawiera symbole, które są używane przez tabelę poleceń, lub do emitowania pliku C#, który zawiera obiekty dla symboli poleceń.

 Przełączniki-D i-I mają składnię flag preprocesora Cl.exe C o tej samej nazwie. Definicje-D, które mają format X = Y, służą do rozszerzania testów opartych na języku XML \<Defined> w `Condition` atrybutach. -I dołączanie ścieżek służy do rozwiązywania \<Include> \<Extern> i \<Bitmap> odwoływania się do pliku. Aby uzyskać więcej informacji, zobacz [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

 Kompilator VSCT może również dekompilować wcześniej skompilowany plik binarny. W tym celu podaj plik binarny dla \<infile> .   Jeśli plik binarny został utworzony przez kompilator VSCT, będzie miał już osadzone symbole i spowoduje wygenerowanie danych wyjściowych z symbolicznymi nazwami w \<Symbols> sekcji danych wyjściowych. Jeśli plik binarny został utworzony przez kompilator CTC, dane wyjściowe będą zawierać faktyczne identyfikatory GUID i identyfikator. Jeśli plik *. CTSYM, który jest tworzony przez bieżące wersje Ctc.exe, znajduje się w tym samym folderze co plik wejściowy binarny, symbole zostaną załadowane z tego pliku i użyte do danych wyjściowych.

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

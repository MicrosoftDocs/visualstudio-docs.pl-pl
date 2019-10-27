---
title: Flagi wiersza polecenia kompilatora VSCT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71634a007019dd39e843ccc63af1c3188f778ea9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722028"
---
# <a name="vsct-compiler-command-line-flags"></a>Flagi wiersza polecenia kompilatora VSCT
Kompilator programu Visual Studio Command Table (VSCT) zapewnia przełączniki wiersza polecenia, aby zapewnić pomyślne Kompilowanie plików. vsct.

## <a name="command-line-parameters"></a>Parametry wiersza polecenia
 Aby wyświetlić podstawową pomoc VSCT z okna **polecenia** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], przejdź do *ścieżki instalacji zestawu SDK programu Visual Studio*\VisualStudioIntegration\Tools\Bin\ folder i wpisz:

```
vsct /?
```

 Spowoduje to zwrócenie:

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
|-L|Określ nazwę kultury <xref:System.Globalization.CultureInfo>, na przykład "en-US".|
|-E|Emituj C# obiekty w określonej przestrzeni nazw dla elementów polecenia, a następnie [C&#124;H&#124;N]:*filename*, gdzie C C#=, H C++ = nagłówek, N = przestrzeń nazw. Przestrzeń nazw jest wymagana dla C#programu.|
|-v|Pełne dane wyjściowe.|

 Przełącznik-L instruuje kompilator, aby wybierał grupę ciągów, aby utworzyć plik binarny. Dyrektor ds, który odnosi się do podanej nazwy kultury <xref:System.Globalization.CultureInfo>. Określona nazwa kultury powinna być zgodna z atrybutem Language jednego lub więcej [elementów String](../../extensibility/strings-element.md) w pliku. vsct. Jeśli element Strings nie ma atrybutu language, jest Dziedziczony z zawierającego [element](../../extensibility/commandtable-element.md).

 Plik. vsct może mieć wiele elementów String, a każdy z nich może mieć inny atrybut języka. Globalizacja jest osiągana przez uruchomienie kompilatora VSCT wiele razy i zmianę przełącznika-L dla każdej nazwy kultury.

 Jeśli nazwa kultury określona przez przełącznik-L nie jest zgodna z atrybutem Language dowolnego elementu String, kompilator podejmie próbę dopasowania do języka, a nie regionu. Na przykład jeśli nie można znaleźć "en-US", kompilator podejmie próbę "en" zamiast tego. Niepowodzenie, spowoduje to wypróbowanie bieżącej kultury systemu operacyjnego. Niepowodzenie, spowoduje skompilowanie pierwszych znalezionych elementów ciągów.

 Przełącznik-E może służyć do emitowania pliku nagłówkowego w stylu C, który zawiera symbole, które są używane przez tabelę poleceń, lub do emitowania C# pliku, który zawiera obiekty dla symboli poleceń.

 Przełączniki-D i-I mają składnię flag preprocesora CL. exe C, które mają taką samą nazwę. Definicje-D, które mają format X = Y, służą do rozszerzania \<zdefiniowanych przez XML > testów w `Condition` atrybutów. -I include ścieżki są używane do rozpoznawania \<Dołącz >, \<zewnętrzne > i \<Mapa bitowa > odwołania do pliku. Aby uzyskać więcej informacji, zobacz [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

 Kompilator VSCT może również dekompilować wcześniej skompilowany plik binarny. W tym celu podaj plik binarny dla > \<plików.   Jeśli plik binarny został utworzony przez kompilator VSCT, będzie miał już osadzone symbole i spowoduje wygenerowanie danych wyjściowych z symbolicznymi nazwami w \<symbole > sekcji danych wyjściowych. Jeśli plik binarny został utworzony przez kompilator CTC, dane wyjściowe będą zawierać faktyczne identyfikatory GUID i identyfikator. Jeśli plik *. CTSYM, który jest tworzony przez bieżące wersje programu CTC. exe, znajduje się w tym samym folderze co plik wejściowy binarny, symbole zostaną załadowane z tego pliku i użyte do danych wyjściowych.

## <a name="see-also"></a>Zobacz także
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
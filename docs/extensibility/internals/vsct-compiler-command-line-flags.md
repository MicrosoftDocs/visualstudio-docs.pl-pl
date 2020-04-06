---
title: Flagi wiersza polecenia kompilatora VSCT | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703967"
---
# <a name="vsct-compiler-command-line-flags"></a>Flagi wiersza polecenia kompilatora VSCT
Kompilator tabeli poleceń programu Visual Studio (VSCT) udostępnia przełączniki wiersza polecenia w celu zapewnienia pomyślnej kompilacji plików .vsct.

## <a name="command-line-parameters"></a>Parametry wiersza polecenia
 Aby wyświetlić podstawową [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pomoc programu VSCT z okna **polecenia,** przejdź do folderu i wpisz folder \VisualStudioIntegration\Tools\Bin\path w programie Visual *Studio:*

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
> Znaki - (myślnik) i / (ukośnik do przodu) są akceptowane notacji do wskazywania parametrów wiersza polecenia.

 Dopuszczalne flagi i to, co oznaczają, są następujące.

|Przełącznik|Opis|
|------------|-----------------|
|-D|Określ wszelkie dodatkowe zdefiniowane symbole.|
|-I|Wskaż dodatkowe ścieżki dołączania, które powinny być używane podczas rozpoznawania odwołań do plików.|
|-L|Określ <xref:System.Globalization.CultureInfo> nazwę kultury, na przykład "en-US".|
|-E|Emituj obiekty C# w określonym obszarze nazw dla elementów poleceń, a następnie [C&#124;H&#124;N]:*nazwa pliku,* gdzie C = C#, H = Nagłówek C++, N = obszar nazw. Obszar nazw jest wymagany dla języka C#.|
|-v|Pełne dane wyjściowe.|

 Przełącznik -L nakazuje kompilatorowi wybranie grupy ciągów do produkcji binarnego pliku <xref:System.Globalization.CultureInfo> cto, który odpowiada nazwie danej kultury. Nazwa określonej kultury powinna być zgodna z atrybutem Language jednego lub więcej [stringów w](../../extensibility/strings-element.md) pliku vsct. Jeśli element Strings nie ma atrybutu Language, jest on dziedziczony z zawierającego [elementu CommandTable](../../extensibility/commandtable-element.md).

 Plik vsct może mieć wiele ciągów elementów, a każdy może mieć inny atrybut Language. Globalizacja jest osiągana przez uruchomienie kompilatora VSCT wiele razy i zmiana przełącznika -L dla każdej nazwy kultury.

 Jeśli nazwa kultury podana przez przełącznik -L nie pasuje do atrybutu Language dowolnego elementu Strings, kompilator spróbuje dopasować język, a nie region. Na przykład jeśli nie można odnaleźć "en-US", kompilator spróbuje zamiast tego "en". W przeciwnym razie spróbuje bieżącej kultury systemu operacyjnego. W przeciwnym razie skompiluje pierwszy strings element znajdzie.

 Przełącznik -E może służyć do emitowania pliku nagłówka w stylu C, który zawiera symbole, które są używane przez tabelę poleceń, lub do emitowania pliku C#, który zawiera obiekty dla symboli poleceń.

 Przełączniki -D i -I mają składnię flag preprocesora Cl.exe C, które mają taką samą nazwę. -D definicje, które mają format X = Y są \<używane do rozszerzania `Condition` testów zdefiniowanych> opartych na języku XML w atrybutach. -I obejmują ścieżki są \<używane do rozwiązywania Include>, \< \<Extern> i Bitmap> odwołania do plików. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

 Kompilator VSCT może również dekompilować wcześniej zbudowany plik binarny. Aby to zrobić, podaj \<plik binarny dla pliku infile>.   Jeśli plik binarny został wyprodukowany przez kompilator VSCT, będzie miał już osadzone \<symbole i będzie produkować dane wyjściowe z nazwami symbolicznymi w sekcji Symbole> danych wyjściowych. Jeśli plik binarny został wyprodukowany przez kompilator CTC, dane wyjściowe będą zawierać rzeczywiste identyfikatory GUID i identyfikatory. Jeśli plik *.ctsym, który jest produkowany przez bieżące wersje ctc.exe znajduje się w tym samym folderze co binarny plik wejściowy, symbole zostaną załadowane z tego pliku i używane do wyjścia.

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

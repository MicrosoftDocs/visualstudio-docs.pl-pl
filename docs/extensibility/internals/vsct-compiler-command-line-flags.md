---
title: Flagi wiersza polecenia kompilatora VSCT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cdf74d0c6c77a2c7c22829c8aaa3e238e65703a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744885"
---
# <a name="vsct-compiler-command-line-flags"></a>Flagi wiersza polecenia kompilatora VSCT
Kompilator programu Visual Studio polecenie tabeli (VSCT) udostępnia przełączniki wiersza polecenia w celu zapewnienia pomyślnej kompilacji .vsct — pliki.  
  
## <a name="command-line-parameters"></a>Parametry wiersza polecenia  
 Aby wyświetlić podstawowe pomocy VSCT [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **polecenia** okna, przejdź do *ścieżka instalacji programu Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ folder i wpisz:  
  
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
>  Znaki — (kreska) i / (ukośnik) są oba akceptowane notacji wskazujący parametry wiersza polecenia.  
  
 Dopuszczalne flag i ich znaczenie są.  
  
|Przełącznik|Opis|  
|------------|-----------------|  
|-D|Określ wszystkie dodatkowe zdefiniowane symbole.|  
|-I|Wskazują, że dodatkowe ścieżki dołączanych plików, które powinny być używane podczas rozpoznawania odwołań do pliku.|  
|-L|Określ <xref:System.Globalization.CultureInfo> nazwy kultury, na przykład "en US".|  
|-E|Emituj C# obiekty w określonej przestrzeni nazw dla elementów polecenia, a następnie [C&#124;H&#124;N]:*filename*gdzie C = C#, H = nagłówka C++, N = przestrzeni nazw. Przestrzeń nazw jest wymagany dla języka C#.|  
|-v|Pełne dane wyjściowe.|  
  
 Przełącznik -L informuje kompilator, aby wybrać grupę ciągów, aby wygenerować plik binarny .cto, który odpowiada danym <xref:System.Globalization.CultureInfo> nazwa kultury. Określona nazwa kultury powinien być zgodny w atrybucie Language elementu co najmniej jeden [Strings, Element](../../extensibility/strings-element.md) w pliku vsct. Jeśli Strings, element nie ma języka atrybutu, zostało ono odziedziczone zawierający [CommandTable, Element](../../extensibility/commandtable-element.md).  
  
 Pliku vsct może mieć wielu elementów ciągi, a każdy może mieć inny atrybut Language. Globalizacja odbywa się uruchamianie kompilatora VSCT wiele razy, a następnie zmieniając przełącznika -L dla każdej nazwy kultury.  
  
 Nazwa kultury, biorąc pod uwagę przez przełącznik -L niezgodny atrybut Language Strings, jeśli element kompilator podejmie próbę dopasowania języka, bez regionu. Na przykład, jeśli nie można odnaleźć "en US", kompilator będzie "en" zamiast tego spróbuj wykonać. Jeśli nie spróbuje bieżącej kultury systemu operacyjnego. Jeśli nie jego zostanie skompilowany pierwszy element ciągów, które znajdzie.  
  
 -E przełącznika może służyć do emitowania pliku nagłówka stylu C, który zawiera symbole, które są używane przez tabeli poleceń lub do wysyłania plik C#, który zawiera obiekty symboli polecenia.  
  
 -D i - przełączniki mieć składni flagi preprocesora Cl.exe C, które mają taką samą nazwę. -D definicje, które mają format X = Y służą do rozszerzenia oparte na języku XML \<zdefiniowane > testów w `Condition` atrybutów. -I ścieżek dołączania są używane do rozpoznawania \<Include >, \<Extern > i \<mapy bitowej > pliku odwołania. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Kompilatora VSCT można również dekompilować wcześniej skompilowany plik binarny. Aby to zrobić, należy dostarczyć plik binarny dla \<infile >.   Plik binarny został utworzony za pomocą kompilatora VSCT, będzie miał jego symbole już osadzone i generuje danych wyjściowych za pomocą nazw symbolicznych w \<symbole > części danych wyjściowych. Plik binarny został utworzony przez kompilator CTC, wynik będzie zawierać rzeczywiste identyfikatory GUID i identyfikatory. Jeśli *.ctsym pliku, który jest wytwarzany przez bieżące wersje Ctc.exe znajduje się w tym samym folderze co plik binarny danych wejściowych, symbole zostanie załadowany z tego pliku i używane dla danych wyjściowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabeli poleceń programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Odwołanie do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)   
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
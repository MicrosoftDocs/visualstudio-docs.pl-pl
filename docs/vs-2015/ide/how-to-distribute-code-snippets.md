---
title: 'Instrukcje: Dystrybuowanie fragmentów kodu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d1878fd1ce91842e8d03b6e78de244380df8eb2b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054563"
---
# <a name="how-to-distribute-code-snippets"></a>Instrukcje: Dystrybuowanie fragmentów kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz po prostu udostępnić swoje fragmenty kodu programu znajomym i je zainstalowali na swoich komputerach za pomocą Menedżera fragmentów kodu. Jednakże jeśli masz kilka fragmentów do dystrybucji lub chcesz przekazać je szerzej, dołączyć plik fragmentu do pliku w rozszerzeniu Visual Studio, które użytkownicy programu Visual Studio mogą instalować.  
  
 Visual Studio SDK należy zainstalować, aby można było utworzyć rozszerzenia programu Visual Studio. Znajdź wersję VSSDK, która jest zgodna z instalacją programu Visual Studio na [pobieranie Visual Studio 2015](http://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs.aspx).  
  
## <a name="setting-up-the-extension"></a>Definiowanie rozszerzenia  
 W tej procedurze użyto tego samego fragmentu kodu Hello World utworzonego w [instruktażu: Creating a Code Snippet](../ide/walkthrough-creating-a-code-snippet.md). Firma Microsoft będzie dostarczać tekst .snippet, dzięki czemu nie trzeba wrócić i zmienić jedną.  
  
1. Utwórz nowy projekt VSIX, o nazwie **TestSnippet**. (**Plik / nowy / Project / Visual C# (lub Visual Basic / rozszerzalności**)  
  
2. W **TestSnippet** projektu, Dodaj nowy plik XML i wywołać go **VBCodeSnippet.snippet**. Zastąp zawartość następujących czynności:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <CodeSnippets  
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
      <CodeSnippet Format="1.0.0">  
        <Header>  
          <Title>Hello World VB</Title>  
          <Shortcut>HelloWorld</Shortcut>  
          <Description>Inserts code</Description>  
          <Author>MSIT</Author>  
          <SnippetTypes>  
            <SnippetType>Expansion</SnippetType>  
            <SnippetType>SurroundsWith</SnippetType>  
          </SnippetTypes>  
        </Header>  
        <Snippet>  
          <Code Language="VB">  
            <![CDATA[Console.WriteLine("Hello, World!")]]>  
          </Code>  
        </Snippet>  
      </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
#### <a name="setting-up-the-directory-structure"></a>Konfigurowanie struktury katalogów  
  
1. W Eksploratorze rozwiązań wybierz węzeł projektu i Dodaj folder, który ma nazwę, która ma fragment kodu w Menedżerze fragmentów kodu. W takim przypadku należy **HelloWorldVB**.  
  
2. Przenieść plik .snippet **HelloWorldVB** folderu.  
  
3. Wybierz plik .snippet w Eksploratorze rozwiązań, a w **właściwości** okna, upewnij się, że **Build Action** jest ustawiona na **zawartości**, **skopiuj dane wyjściowe Katalog** jest ustawiona na **zawsze Kopiuj**, i **Include w VSIX** ustawiono **true**.  
  
#### <a name="adding-the-pkgdef-file"></a>Dodawanie pliku pkgdef  
  
1. Dodaj z pliku tekstowego **HelloWorldVB** folder i nadaj mu nazwę **HelloWorldVB.pkgdef**. Ten plik jest używany do dodania określonych kluczy rejestru. W tym przypadku dodaje nowy klucz  
  
     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic**.  
  
2. Dodaj następujące wiersze do pliku.  
  
    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  
  
     Gdy przyjrzysz się tego klucza, widać sposób określania różnych językach.  
  
3. Wybierz plik .pkgdef, w Eksploratorze rozwiązań, a w **właściwości** okna, upewnij się, że **Build Action** jest ustawiona na **zawartości**, **Kopiuj do katalogu wyjściowego**  ustawiono **zawsze Kopiuj**, i **Include w VSIX** ustawiono **true**.  
  
4. Dodaj plik .pkgdef jako zasób w manifestu VSIX. W pliku source.extension.vsixmanifest, przejdź do **zasoby** kartę, a następnie kliknij przycisk **New**.  
  
5. W **Dodaj nowy zasób** okno dialogowe, zestaw **typu** do **Microsoft.VisualStudio.VsPackage**, **typu** do **plików na System plików**i **ścieżki** do **HelloWorldVB.pkgdef** (który powinna zostać wyświetlona na liście rozwijanej).  
  
### <a name="testing-the-snippet"></a>Testowanie fragmentu kodu  
  
1. Teraz możesz upewnić się, że fragment kodu działa w doświadczalnym wystąpieniu programu Visual Studio. Eksperymentalne wystąpienie jest drugą kopię programu Visual Studio, który jest oddzielony od tego, który używa się do pisania kodu. Umożliwia on pracować nad rozszerzeniem bez wywierania wpływu na środowiska deweloperskiego.  
  
2. Skompiluj projekt, a następnie rozpocząć debugowanie. Drugie wystąpienie programu Visual Studio powinny być wyświetlane.  
  
3. W doświadczalnym wystąpieniu, przejdź do **narzędzia / kodu Menedżera wstawek** i ustaw **języka** do **podstawowe**. Powinien zostać wyświetlony HelloWorldVB jako jeden z folderów i powinno być możliwe rozwinąć folder, aby wyświetlić fragment HelloWorldVB.  
  
4. Przetestuj fragmentu kodu. W doświadczalnym wystąpieniu Otwórz projekt języka Visual Basic, a następnie otwórz jeden z plików kodu. Umieść kursor w miejscu gdzieś w kodzie, kliknij prawym przyciskiem myszy, a na stronie wybierz menu kontekstowe **Wstaw fragment kodu**.  
  
5. HelloWorldVB powinna być widoczna jako jeden z folderów. Kliknij go dwukrotnie. Powinny zostać wyświetlone okno podręczne **Wstaw fragment kodu: HellowWorldVB >** zawierający listę rozwijaną **HelloWorldVB**. Kliknij listę rozwijaną HelloWorldVB. Powinien zostać wyświetlony następujący wiersz, które są dodawane do pliku:  
  
    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Fragmenty kodu](../ide/code-snippets.md)

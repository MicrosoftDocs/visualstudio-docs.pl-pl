---
title: 'Instrukcje: dystrybuowanie fragmentów kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1a692ee29ea9d43e1a0a4fbed5c52934d69256d
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476987"
---
# <a name="how-to-distribute-code-snippets"></a>Porady: rozprowadzanie wstawek kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po prostu możesz nadać swoim znajomym fragmenty kodu i zainstalować je na swoich komputerach za pomocą Menedżera fragmentów kodu. Jeśli jednak masz kilka fragmentów do dystrybucji lub chcesz ich szerzej rozpowszechniać, Dołącz plik fragmentu do rozszerzenia programu Visual Studio, które użytkownicy programu Visual Studio mogą instalować.

 Aby utworzyć rozszerzenia programu Visual Studio, należy zainstalować zestaw SDK programu Visual Studio. Znajdź wersję VSSDK zgodną z instalacją programu Visual Studio na stronie [pobierania programu Visual studio 2015](https://visualstudio.microsoft.com/vs/older-downloads/).

## <a name="setting-up-the-extension"></a>Konfigurowanie rozszerzenia
 W ramach tej procedury będziemy używać tego samego fragmentu kodu Hello world utworzonego w [przewodniku: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md). Dostarczymy tekst fragmentu, więc nie trzeba go wycofać i utworzyć.

1. Utwórz nowy projekt VSIX o nazwie **TestSnippet**. (**Plik/nowy/projekt/Wizualizacja C# (lub Visual Basic/rozszerzalność**)

2. W projekcie **TestSnippet** Dodaj nowy plik XML i Wywołaj go **VBCodeSnippet. fragment kodu**. Zastąp zawartość następującym:

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

1. W Eksplorator rozwiązań wybierz węzeł projektu, a następnie Dodaj folder, który ma nazwę, którą ma mieć fragment w Menedżerze fragmentów kodu. W takim przypadku należy **HelloWorldVB**.

2. Przenieś plik fragmentu kodu do folderu **HelloWorldVB** .

3. Wybierz plik fragmentu kodu w Eksplorator rozwiązań, a w oknie **Właściwości** upewnij się, że **Akcja kompilacja** jest ustawiona na **zawartość**, w polu **Kopiuj do katalogu wyjściowego** jest ustawiona wartość **Kopiuj zawsze**, a dla opcji Dołącz do pliku **VSIX** wybierz pozycję **prawda**.

#### <a name="adding-the-pkgdef-file"></a>Dodawanie pliku. pkgdef

1. Dodaj plik tekstowy do folderu **HelloWorldVB** i nadaj mu nazwę **HelloWorldVB. pkgdef**. Ten plik jest używany do dodawania niektórych kluczy do rejestru. W takim przypadku dodaje nowy klucz do

     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic**.

2. Dodaj następujące wiersze do pliku.

    ```
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

     Po sprawdzeniu tego klucza można zobaczyć, jak określić różne języki.

3. Wybierz plik. pkgdef w Eksplorator rozwiązań, a w oknie **Właściwości** upewnij się, że **Akcja kompilacja** jest ustawiona na **zawartość**, w polu **Kopiuj do katalogu wyjściowego** jest ustawiona wartość **Kopiuj zawsze**, a dla opcji Dołącz do pliku **VSIX** wybierz pozycję **prawda**.

4. Dodaj plik. pkgdef jako element zawartości w manifeście VSIX. W pliku source. Extension. vsixmanifest przejdź do karty **zasoby** , a następnie kliknij przycisk **Nowy**.

5. W oknie dialogowym **Dodawanie nowego elementu zawartości** Ustaw **typ** na **Microsoft. VisualStudio. pakietu VSPackage**, **Typ** do **pliku w systemie plików**i **ścieżkę** do **HelloWorldVB. pkgdef** (który powinien pojawić się na liście rozwijanej).

### <a name="testing-the-snippet"></a>Testowanie fragmentu kodu

1. Teraz można upewnić się, że fragment kodu działa w eksperymentalnym wystąpieniu programu Visual Studio. Eksperymentalne wystąpienie to druga kopia programu Visual Studio, która jest oddzielona od użytego do pisania kodu. Umożliwia pracę nad rozszerzeniem bez wpływu na środowisko deweloperskie.

2. Skompiluj projekt, a następnie rozpocząć debugowanie. Powinno zostać wyświetlone drugie wystąpienie programu Visual Studio.

3. W eksperymentalnym wystąpieniu przejdź do pozycji **Tools/Code wstaweks Manager** i ustaw **Język** na **Basic**. Powinien być widoczny HelloWorldVB jako jeden z folderów i można rozwinąć folder, aby wyświetlić fragment kodu HelloWorldVB.

4. Przetestuj fragment kodu. W eksperymentalnym wystąpieniu Otwórz projekt Visual Basic i otwórz jeden z plików kodu. Umieść kursor w dowolnym miejscu w kodzie, kliknij prawym przyciskiem myszy, a następnie w menu kontekstowym wybierz **Wstaw fragment**kodu.

5. Należy zobaczyć HelloWorldVB jako jeden z folderów. Kliknij go dwukrotnie. Powinien pojawić się podręczny **Wstaw fragment kodu: HellowWorldVB >** , który ma **HelloWorldVB**listy rozwijanej. Kliknij listę rozwijaną HelloWorldVB. Do pliku powinien zostać dodany następujący wiersz:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Zobacz też
 [Fragmenty kodu](../ide/code-snippets.md)

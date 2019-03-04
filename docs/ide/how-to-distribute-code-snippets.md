---
title: 'Instrukcje: Dystrybuowanie fragmentów kodu'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2dde020192e4b301083c69963720f6222639f7b1
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323056"
---
# <a name="how-to-distribute-code-snippets"></a>Instrukcje: Dystrybuowanie fragmentów kodu

Możesz udostępnić swoje fragmenty kodu programu znajomym i je zainstalowali na swoich komputerach przy użyciu **Menedżera wstawek kodu**. Jednak jeśli masz kilka fragmentów do dystrybucji lub chcesz przekazać je szerzej, dodasz plik fragmentu do pliku w rozszerzeniem programu Visual Studio. Visual Studio użytkownicy mogą następnie zainstalować rozszerzenie.

Visual Studio SDK należy zainstalować, aby można było utworzyć rozszerzenia programu Visual Studio. Znajdź wersję VSSDK, która jest zgodna z instalacją programu Visual Studio na [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017).

## <a name="set-up-the-extension"></a>Skonfiguruj rozszerzenia

W tej procedurze użyto tym samym fragmencie kodu Hello World, który jest tworzony w [instruktażu: Utwórz fragment kodu](../ide/walkthrough-creating-a-code-snippet.md). Firma Microsoft będzie dostarczać *.snippet* tekstu, dzięki czemu nie trzeba wrócić i zmienić jedną.

1. Utwórz nowy projekt VSIX, o nazwie **TestSnippet**. (**Pliku** > **nowe** > **projektu** > **Visual C# (lub Visual Basic)**  >  **Rozszerzalności**.)

2. W **TestSnippet** projektu, Dodaj nowy plik XML i wywołać go *VBCodeSnippet.snippet*. Zastąp zawartość następujący kod XML:

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

### <a name="set-up-the-directory-structure"></a>Konfigurowanie struktury katalogów

1. W **Eksploratora rozwiązań**, wybierz węzeł projektu i dodawanie folderu, który ma nazwę, która ma fragment kodu w **Menedżera wstawek kodu**. W tym przypadku powinien być **HelloWorldVB**.

2. Przenieś *.snippet* plik *HelloWorldVB* folderu.

3. Wybierz *.snippet* w pliku **Eksploratora rozwiązań**, a następnie w **właściwości** okna, upewnij się, **Akcja kompilacji** jest ustawiona na **Zawartości**, **Kopiuj do katalogu wyjściowego** ustawiono **zawsze Kopiuj**, i **Include w VSIX** ustawiono **true**.

### <a name="add-the-pkgdef-file"></a>Dodaj plik .pkgdef

::: moniker range="vs-2017"

1. Dodaj z pliku tekstowego *HelloWorldVB* folder i nadaj mu nazwę *HelloWorldVB.pkgdef*. Ten plik jest używany do dodania określonych kluczy rejestru. W tym przypadku dodaje nowy podklucz do **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic** klucza.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dodaj z pliku tekstowego *HelloWorldVB* folder i nadaj mu nazwę *HelloWorldVB.pkgdef*. Ten plik jest używany do dodania określonych kluczy rejestru. W tym przypadku dodaje nowy podklucz do **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic** klucza.

::: moniker-end

2. Dodaj następujące wiersze do pliku.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Gdy przyjrzysz się tego klucza, widać sposób określania różnych językach.

3. Wybierz *.pkgdef* w pliku **Eksploratora rozwiązań**, a następnie w **właściwości** okna, upewnij się, że:

   - **Akcja kompilacji** ustawiono **zawartości**
   - **Kopiuj do katalogu wyjściowego** ustawiono **zawsze Kopiuj**
   - **Uwzględnione w VSIX** ustawiono **true**

4. Dodaj *.pkgdef* plików jako zasób w manifestu VSIX. W *source.extension.vsixmanifest* pliku, przejdź do **zasoby** kartę, a następnie kliknij przycisk **New**.

5. W **Dodaj nowy zasób** okno dialogowe, zestaw **typu** do **Microsoft.VisualStudio.VsPackage**, **źródła** do **plików na System plików**i **ścieżki** do **HelloWorldVB.pkgdef** (który powinna zostać wyświetlona na liście rozwijanej).

### <a name="test-the-snippet"></a>Fragment kodu testu

1. Teraz możesz upewnić się, że fragment kodu działa w doświadczalnym wystąpieniu programu Visual Studio. Eksperymentalne wystąpienie jest drugą kopię programu Visual Studio, który jest oddzielony od tego, który używa się do pisania kodu. Umożliwia on pracować nad rozszerzeniem bez wywierania wpływu na środowiska deweloperskiego.

2. Skompiluj projekt, a następnie rozpocząć debugowanie.

   Zostanie wyświetlone drugie wystąpienie programu Visual Studio.

3. W doświadczalnym wystąpieniu, przejdź do **narzędzia** > **Menedżera wstawek kodu** i ustaw **języka** do **podstawowe**. Powinien zostać wyświetlony *HelloWorldVB* zgodnie z jednym z folderów, a powinien być można rozwinąć folder, aby wyświetlić *HelloWorldVB* fragmentu kodu.

4. Przetestuj fragmentu kodu. W doświadczalnym wystąpieniu Otwórz projekt języka Visual Basic, a następnie otwórz jeden z plików kodu. Umieść kursor w miejscu gdzieś w kodzie, kliknij prawym przyciskiem myszy, a na stronie wybierz menu kontekstowe **Wstaw fragment kodu**.

5. Powinien zostać wyświetlony *HelloWorldVB* jako jeden z folderów. Kliknij go dwukrotnie. Powinny zostać wyświetlone okno podręczne **Wstaw fragment kodu: HelloWorldVB >** zawierający listę rozwijaną **HelloWorldVB**. Kliknij przycisk **HelloWorldVB** listy rozwijanej. Powinien zostać wyświetlony następujący wiersz, które są dodawane do pliku:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../ide/code-snippets.md)
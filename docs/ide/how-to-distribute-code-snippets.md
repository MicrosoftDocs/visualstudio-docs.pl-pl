---
title: Dystrybuowanie fragmentów kodu jako rozszerzenie
ms.date: 03/21/2019
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
ms.openlocfilehash: 0f0b3211352dc16e51b64196e13f7378bf2a423c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429552"
---
# <a name="how-to-distribute-code-snippets"></a>Instrukcje: Dystrybuowanie fragmentów kodu

Możesz udostępnić swoje fragmenty kodu programu znajomym i je zainstalowali na swoich komputerach przy użyciu **Menedżera wstawek kodu**. Jednak jeśli masz kilka fragmentów do dystrybucji lub chcesz przekazać je szerzej, może zawierać pliki fragmentu kodu w rozszerzeniu Visual Studio. Użytkowników usługi Visual Studio można zainstalować rozszerzenia Aby uzyskać fragmenty kodu.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj **programowanie rozszerzeń programu Visual Studio** obciążenie w celu uzyskania dostępu do **projekt VSIX** szablony projektów.

![Obciążenie programowanie rozszerzenia programu Visual Studio](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Skonfiguruj rozszerzenia

W tej procedurze, używane będzie tym samym fragmencie kodu Hello World, który jest tworzony w [instruktażu: Utwórz fragment kodu](../ide/walkthrough-creating-a-code-snippet.md). Ten artykuł zawiera fragment kodu XML, aby nie musieli przejść wstecz i utwórz fragment kodu.

1. Utwórz nowy projekt z **pusty projekt VSIX** szablonu i nazwy projektu **TestSnippet**.

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

5. Powinien zostać wyświetlony *HelloWorldVB* jako jeden z folderów. Kliknij go dwukrotnie. Powinny zostać wyświetlone okno podręczne **Wstaw fragment kodu: HelloWorldVB >** zawierający listę rozwijaną **HelloWorldVB**. Kliknij przycisk **HelloWorldVB** listy rozwijanej.

   Następujący wiersz jest dodawana do pliku kodu:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../ide/code-snippets.md)
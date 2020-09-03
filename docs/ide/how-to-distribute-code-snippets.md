---
title: Rozpowszechnianie fragmentów kodu jako rozszerzenia
ms.date: 03/21/2019
ms.topic: how-to
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: c283d5ca29b67e772df2a0bb2e25dee70cd63fd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284376"
---
# <a name="how-to-distribute-code-snippets"></a>Instrukcje: dystrybuowanie fragmentów kodu

Możesz nadać swoim znajomym fragmenty kodu i zainstalować je na swoich komputerach za pomocą **Menedżera fragmentów kodu**. Jeśli jednak masz kilka fragmentów do dystrybucji lub chcesz ich szerzej rozpowszechniać, możesz uwzględnić pliki fragmentów kodu w rozszerzeniu programu Visual Studio. Użytkownicy programu Visual Studio mogą następnie zainstalować rozszerzenie w celu uzyskania fragmentów kodu.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj obciążenie **programowanie rozszerzenia programu Visual Studio** , aby uzyskać dostęp do szablonów projektu **VSIX** .

![Obciążenie programowanie rozszerzeń programu Visual Studio](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Skonfiguruj rozszerzenie

Ta procedura spowoduje użycie tego samego fragmentu kodu Hello world, który został utworzony w [przewodniku: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md). Ten artykuł zawiera kod XML fragmentu kodu, dzięki czemu nie musisz wrócić i utworzyć fragmentu kodu.

1. Utwórz nowy projekt na podstawie **pustego szablonu projektu VSIX** i Nadaj projektowi nazwę **TestSnippet**.

2. W projekcie **TestSnippet** Dodaj nowy plik XML i Wywołaj go *VBCodeSnippet. fragment kodu*. Zastąp zawartość następującym kodem XML:

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

1. W **Eksplorator rozwiązań**wybierz węzeł projektu, a następnie Dodaj folder, który ma nazwę, której fragment ma mieć w programie **fragmentów kodu**. W takim przypadku powinna być **HelloWorldVB**.

2. Przenieś plik *fragmentu kodu* do folderu *HelloWorldVB* .

3. Wybierz plik *fragmentu kodu* w **Eksplorator rozwiązań**, a w oknie **Właściwości** upewnij się, **że akcja kompilacji** jest ustawiona na **zawartość**, w polu **Kopiuj do katalogu wyjściowego** jest ustawiona wartość **Kopiuj zawsze**, a **w polu VSIX** wybierz pozycję **prawda**.

### <a name="add-the-pkgdef-file"></a>Dodaj plik. pkgdef

::: moniker range="vs-2017"

1. Dodaj plik tekstowy do folderu *HelloWorldVB* i nadaj mu nazwę *HelloWorldVB. pkgdef*. Ten plik jest używany do dodawania niektórych kluczy do rejestru. W takim przypadku dodaje nowy podklucz do **HKEY_CURRENT_USER klucza \software\microsoft\visualstudio\15.0\languages\codeexpansions\basic** .

::: moniker-end

::: moniker range=">=vs-2019"

1. Dodaj plik tekstowy do folderu *HelloWorldVB* i nadaj mu nazwę *HelloWorldVB. pkgdef*. Ten plik jest używany do dodawania niektórych kluczy do rejestru. W takim przypadku dodaje nowy podklucz do **HKEY_CURRENT_USER klucza \software\microsoft\visualstudio\16.0\languages\codeexpansions\basic** .

::: moniker-end

2. Dodaj następujące wiersze do pliku.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Po sprawdzeniu tego klucza można zobaczyć, jak określić różne języki.

3. Wybierz plik *. pkgdef* w **Eksplorator rozwiązań**, a w oknie **Właściwości** upewnij się, że:

   - **Akcja kompilacji** jest ustawiona na **zawartość**
   - Wartość **Kopiuj do katalogu wyjściowego** jest ustawiona na **zawsze Kopiuj**
   - **Dołączanie w VSIX** jest ustawione na **wartość true**

4. Dodaj plik *. pkgdef* jako element zawartości w manifeście VSIX. W pliku *source. Extension. vsixmanifest* przejdź do karty **zasoby** , a następnie kliknij przycisk **Nowy**.

5. W oknie **dialogowym Dodawanie nowego elementu zawartości** Ustaw dla **opcji Typ** **Microsoft. VisualStudio. pakietu VSPackage**, **Źródło** do **pliku w systemie plików**oraz **ścieżkę** do **HelloWorldVB. pkgdef** (która powinna pojawić się na liście rozwijanej).

### <a name="test-the-snippet"></a>Testowanie fragmentu kodu

1. Teraz można upewnić się, że fragment kodu działa w eksperymentalnym wystąpieniu programu Visual Studio. Eksperymentalne wystąpienie to druga kopia programu Visual Studio, która jest oddzielona od użytego do pisania kodu. Umożliwia pracę nad rozszerzeniem bez wpływu na środowisko deweloperskie.

2. Skompiluj projekt i Rozpocznij debugowanie.

   Zostanie wyświetlone drugie wystąpienie programu Visual Studio.

3. W eksperymentalnym wystąpieniu Przejdź kolejno do pozycji **Narzędzia**  >  **Wstaw fragmenty kodu Menedżer** i ustaw **Język** na **podstawowy**. Powinien być widoczny *HelloWorldVB* jako jeden z folderów i można rozwinąć folder, aby wyświetlić fragment kodu *HelloWorldVB* .

4. Przetestuj fragment kodu. W eksperymentalnym wystąpieniu Otwórz projekt Visual Basic i otwórz jeden z plików kodu. Umieść kursor w dowolnym miejscu w kodzie, kliknij prawym przyciskiem myszy, a następnie w menu kontekstowym wybierz **Wstaw fragment**kodu.

5. Należy zobaczyć *HelloWorldVB* jako jeden z folderów. Kliknij go dwukrotnie. Powinien pojawić się podręczny **Wstaw fragment kodu: HelloWorldVB >** , który ma **HelloWorldVB**listy rozwijanej. Kliknij listę rozwijaną **HelloWorldVB** .

   Do pliku kodu zostanie dodany następujący wiersz:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../ide/code-snippets.md)

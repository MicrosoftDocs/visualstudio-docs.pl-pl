---
title: Rozpowszechnianie fragmentów kodu jako rozszerzenia
ms.date: 03/21/2019
ms.topic: conceptual
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
ms.openlocfilehash: 23e77658b2b09f643af18a3f136f5428828cfb5c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591063"
---
# <a name="how-to-distribute-code-snippets"></a>Jak: Rozpowszechnianie fragmentów kodu

Możesz przekazać urywki kodu znajomym i złożyć im urywki na własnych komputerach za pomocą **Menedżera fragmentów kodu**. Jednak jeśli masz kilka fragmentów do dystrybucji lub chcesz rozpowszechniać je szerzej, można dołączyć pliki urywka w rozszerzeniu programu Visual Studio. Użytkownicy programu Visual Studio mogą następnie zainstalować rozszerzenie, aby uzyskać fragmenty kodu.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj obciążenie **deweloperskie rozszerzenia programu Visual Studio,** aby uzyskać dostęp do szablonów projektu **projektu VSIX.**

![Obciążenie programem Visual Studio dotyczące tworzenia rozszerzeń](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Konfigurowanie rozszerzenia

W tej procedurze użyjesz tego samego fragmentu kodu Hello World, który jest tworzony w [przewodniku: Utwórz fragment kodu](../ide/walkthrough-creating-a-code-snippet.md). Ten artykuł zawiera urywek XML, więc nie trzeba wracać i tworzyć fragment kodu.

1. Utwórz nowy projekt z **szablonu Pusty projekt VSIX** i nazwij projekt **TestSnippet**.

2. W projekcie **TestSnippet** dodaj nowy plik XML i nazwij go *VBCodeSnippet.snippet*. Zastąp zawartość następującym kodem XML:

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

1. W **Eksploratorze rozwiązań**wybierz węzeł projektu i dodaj folder o nazwie, którą ma mieć fragment kodu w **Menedżerze urywków kodu**. W takim przypadku powinno być **HelloWorldVB**.

2. Przenieś plik *.urywek* do folderu *HelloWorldVB.*

3. Zaznacz plik *.urywek* w **Eksploratorze rozwiązań,** a w oknie Właściwości upewnij się, że **akcja kompilacji** jest **ustawiona**na Zawartość , **Kopiowanie do katalogu wyjściowego** jest ustawione na **Kopiowanie zawsze**, a włączenie **do VSIX** jest ustawiona na **true**. **Properties**

### <a name="add-the-pkgdef-file"></a>Dodawanie pliku pkgdef

::: moniker range="vs-2017"

1. Dodaj plik tekstowy do folderu *HelloWorldVB* i nazwij go *HelloWorldVB.pkgdef*. Ten plik służy do dodawania niektórych kluczy do rejestru. W takim przypadku dodaje nowy podklucz do **klucza HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Dodaj plik tekstowy do folderu *HelloWorldVB* i nazwij go *HelloWorldVB.pkgdef*. Ten plik służy do dodawania niektórych kluczy do rejestru. W takim przypadku dodaje nowy podklucz do **klucza HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic.**

::: moniker-end

2. Dodaj następujące wiersze do pliku.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Jeśli zbadasz ten klucz, możesz zobaczyć, jak określić różne języki.

3. Wybierz plik *pkgdef* w **Eksploratorze rozwiązań**i w oknie **Właściwości** upewnij się, że:

   - **Akcja kompilacji** jest **ustawiona** na Zawartość
   - **Kopiowanie do katalogu wyjściowego** jest zawsze ustawione na **Kopiowanie**
   - **Uwzględnij w VSIX** jest **ustawiona** na true

4. Dodaj plik *pkgdef* jako zasób w manifeście VSIX. W pliku *source.extension.vsixmanifest* przejdź do karty **Zasoby** i kliknij pozycję **Nowy**.

5. W oknie dialogowym **Dodaj nowy zasób** ustaw **typ** na **Microsoft.VisualStudio.VsPackage**, **Źródło** do **pliku w systemie plików**i **Ścieżka** do **HelloWorldVB.pkgdef** (które powinny pojawić się w rozwijaniu).

### <a name="test-the-snippet"></a>Przetestuj fragment kodu

1. Teraz można upewnić się, że fragment kodu działa w eksperymentalnym wystąpieniu programu Visual Studio. Eksperymentalne wystąpienie jest drugą kopią programu Visual Studio, która jest oddzielona od tej, której używasz do pisania kodu. Umożliwia pracę nad rozszerzeniem bez wpływu na środowisko programistyczne.

2. Skompiluj projekt i rozpocznij debugowanie.

   Pojawi się drugie wystąpienie programu Visual Studio.

3. W przypadku wystąpienia eksperymentalnego przejdź do**Menedżera urywków kodu** **narzędzi** > i ustaw **język** na **Podstawowy**. Powinieneś zobaczyć *HelloWorldVB* jako jeden z folderów i powinieneś być w stanie rozwinąć folder, aby zobaczyć fragment *HelloWorldVB.*

4. Przetestuj fragment kodu. W wystąpieniu eksperymentalnym otwórz projekt języka Visual Basic i otwórz jeden z plików kodu. Umieść kursor gdzieś w kodzie, kliknij prawym przyciskiem myszy, a w menu kontekstowym wybierz polecenie **Wstaw fragment kodu**.

5. Powinieneś zobaczyć *HelloWorldVB* jako jeden z folderów. Kliknij go dwukrotnie. Powinieneś zobaczyć wyskakujące **fragmenty wstawiania: HelloWorldVB >,** który ma rozwijaną **HelloWorldVB**. Kliknij przycisk listy rozwijanej **HelloWorldVB.**

   Do pliku kodu jest dodawany następujący wiersz:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../ide/code-snippets.md)

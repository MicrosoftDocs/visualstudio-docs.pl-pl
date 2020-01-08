---
title: Samouczek rozszerzenia Hello world | Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0345d67a4202b8b267d213e0c288847e2774f722
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404138"
---
# <a name="create-your-first-extension-hello-world"></a>Utwórz swoje pierwsze rozszerzenie: Hello world

Ten Hello world przykład przeprowadzi Cię przez proces tworzenia pierwszego rozszerzenia dla programu Visual Studio. W tym samouczku pokazano, jak dodać nowe polecenie do programu Visual Studio.

W procesie dowiesz się, jak:

* **[Tworzenie projektu rozszerzalności](#create-an-extensibility-project)**
* **[Dodaj polecenie niestandardowe](#add-a-custom-command)**
* **[Modyfikowanie kodu źródłowego](#modify-the-source-code)**
* **[Uruchom](#run-it)**

W tym przykładzie użyjesz wizualizacji C# , aby dodać niestandardowy przycisk menu o nazwie "Powiedz Hello World!" Wygląda to następująco:

![Polecenie Hello world](media/hello-world-say-hello-world.png)

> [!NOTE]
> Ten artykuł ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Przewodnik rozszerzalności w programie Visual Studio dla komputerów Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem upewnij się, że zainstalowano obciążenie **programowanie rozszerzenia programu Visual Studio** , które obejmuje wymagany szablon VSIX i przykładowy kod.

> [!NOTE]
> Aby utworzyć projekt rozszerzalności programu Visual Studio, można użyć dowolnej wersji programu Visual Studio (Community, Professional lub Enterprise).

## <a name="create-an-extensibility-project"></a>Tworzenie projektu rozszerzalności

::: moniker range="vs-2017"

Krok 1. Z **pliku** menu, wybierz opcję **New** > **projektu**.

Krok 2. W polu wyszukiwania w prawym górnym rogu wpisz "VSIX" i wybierz C# **projekt Visual VSIX**. Wprowadź ciąg "HelloWorld" jako **nazwę** w dolnej części okna dialogowego i wybierz **przycisk OK**.

![Nowy projekt](media/hello-world-new-project.png)

Powinna zostać wyświetlona strona Wprowadzenie i kilka przykładowych zasobów.

Jeśli musisz opuścić ten samouczek i wrócić do niego, możesz znaleźć nowy projekt HelloWorld na **stronie startowej** w sekcji **ostatnie** .

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. Z **pliku** menu, wybierz opcję **New** > **projektu**. Wyszukaj ciąg "VSIX" i wybierz projekt Visual C# **VSIX** , a następnie kliknij przycisk **dalej**.

Krok 2. Wprowadź ciąg "HelloWorld" dla **nazwy projektu** i wybierz pozycję **Utwórz**.

![Nowy projekt](media/hello-world-new-project-2019.png)

Powinieneś teraz zobaczyć projekt HelloWorld w **Eksplorator rozwiązań**.

::: moniker-end

## <a name="add-a-custom-command"></a>Dodaj polecenie niestandardowe

Krok 1. W przypadku wybrania pliku manifestu *. vsixmanifest* można zobaczyć, jakie opcje są zmieniane, takie jak opis, autor i wersja.

Krok 2. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie). W menu kontekstowym wybierz pozycję **Dodaj**, a następnie pozycję **nowy element**.

Krok 3. Wybierz sekcję **rozszerzalność** , a następnie wybierz **polecenie**.

Krok 4. W polu **Nazwa** u dołu wprowadź nazwę pliku, na przykład *Command.cs*.

![polecenie niestandardowe](media/hello-world-vsix-command.png)

Nowy plik poleceń jest widoczny w **Eksplorator rozwiązań**. W węźle **zasoby** znajdziesz inne pliki powiązane z poleceniem. Na przykład jeśli chcesz zmodyfikować obraz, plik PNG jest tutaj.

## <a name="modify-the-source-code"></a>Modyfikowanie kodu źródłowego

W tym momencie tekst polecenia i przycisku są generowane automatycznie i nie jest bardzo interesujący. Jeśli chcesz wprowadzić zmiany, możesz zmodyfikować plik VSCT i plik CS.

* Plik VSCT jest miejscem, w którym można zmieniać nazwy poleceń, a także definiować, gdzie są one w systemie poleceń programu Visual Studio. Podczas eksplorowania pliku VSCT zobaczysz komentarze objaśniające, co Każda sekcja kontrolek kodu VSCT.

* Plik CS jest miejscem, w którym można definiować akcje, takie jak obsługa kliknięcia.

::: moniker range="vs-2017"

Krok 1. W **Eksplorator rozwiązań**Znajdź plik vsct dla nowego polecenia. W takim przypadku zostanie on wywołany *CommandPackage. vsct*.

![Pakiet poleceń vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. W **Eksplorator rozwiązań**Znajdź plik vsct dla rozszerzenia programu vs. W takim przypadku zostanie on wywołany *HelloWorldPackage. vsct*.

::: moniker-end

Krok 2. Zmień parametr `ButtonText`, aby `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Krok 3. Wróć do **Eksplorator rozwiązań** i znajdź plik *Command.cs* . W metodzie `Execute` Zmień ciąg `message` z `string.Format(..)` na `Hello World!`.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Upewnij się, że Zapisano zmiany w każdym pliku.

## <a name="run-it"></a>Uruchom skrypt

Teraz można uruchomić kod źródłowy w eksperymentalnym wystąpieniu programu Visual Studio.

Krok 1. Naciśnij klawisz **F5** , aby uruchomić polecenie **Rozpocznij debugowanie** . To polecenie kompiluje projekt i uruchamia debuger, uruchamiając nowe wystąpienie programu Visual Studio o nazwie **wystąpienie eksperymentalne**.

::: moniker range="vs-2017"

Na pasku tytułu programu Visual Studio zobaczysz **wystąpienie eksperymentalne** .

![eksperymentalny pasek tytułu wystąpienia](media/hello-world-exp-instance.png)

::: moniker-end

Krok 2. W menu **Narzędzia** **wystąpienia eksperymentalnego**kliknij polecenie **powiedz Hello World!** .

![wynik końcowy](media/hello-world-final-result.png)

Powinny zostać wyświetlone dane wyjściowe z nowego polecenia niestandardowego, w tym przypadku okno dialogowe na środku ekranu, który zapewnia **Hello World!** .

## <a name="next-steps"></a>Następne kroki

Teraz, gdy znasz podstawowe informacje dotyczące pracy z rozszerzalnością programu Visual Studio, tutaj możesz dowiedzieć się więcej:

* [Zacznij tworzyć rozszerzenia programu Visual Studio](starting-to-develop-visual-studio-extensions.md) — przykłady i samouczki. i publikowanie rozszerzenia
* [Co nowego w programie Visual studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) — nowe funkcje rozszerzalności w programie visual Studio 2017
* [Co nowego w programie Visual studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) — nowe funkcje rozszerzalności w programie visual Studio 2019
* W [zestawie SDK programu Visual Studio](internals/inside-the-visual-studio-sdk.md) — Poznaj szczegóły rozszerzalności programu Visual Studio

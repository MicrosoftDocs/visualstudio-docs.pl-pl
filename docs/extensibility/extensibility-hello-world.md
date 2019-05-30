---
title: Witaj świecie rozszerzenie samouczka | Dokumentacja firmy Microsoft
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c3bbafcf138c60b65940bcee73c74f56cf6e2fd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342861"
---
# <a name="create-your-first-extension-hello-world"></a>Tworzenie pierwszego rozszerzenia: Witaj Świecie

W tym przykładzie Hello World przeprowadzi Cię przez tworzenie pierwszego rozszerzenia dla programu Visual Studio. Ten samouczek pokazuje, jak dodać nowe polecenie do programu Visual Studio.

W procesie, dowiesz się jak:

* **[Utwórz projekt rozszerzenia](#create-an-extensibility-project)**
* **[Dodaj polecenie niestandardowe](#add-a-custom-command)**
* **[Modyfikowanie kodu źródłowego](#modify-the-source-code)**
* **[Uruchom go](#run-it)**

W tym przykładzie użyjemy Visual C# można dodać niestandardowe menu przycisku o nazwie "Powiedz Hello World!" który wygląda następująco:

![Witaj świecie polecenia](media/hello-world-say-hello-world.png)

> [!NOTE]
> Ten artykuł dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [wskazówki rozszerzalności programu Visual Studio dla komputerów Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem upewnij się, że zainstalowano **programowanie rozszerzeń programu Visual Studio** obciążenia, który zawiera szablon VSIX, będzie konieczne i przykładowy kod.

> [!NOTE]
> Możesz użyć dowolnej wersji programu Visual Studio (Community, Professional lub Enterprise), aby utworzyć projekt rozszerzalności programu Visual Studio.

## <a name="create-an-extensibility-project"></a>Utwórz projekt rozszerzenia

::: moniker range="vs-2017"

Krok 1. Z **pliku** menu, wybierz opcję **New** > **projektu**.

Krok 2. W polu wyszukiwania w prawym górnym rogu, wpisz "vsix", a następnie wybierz wizualizację C# **projekt VSIX**. Wprowadź "nazwę HelloWorld" **nazwa** u dołu okna dialogowego, a następnie wybierz pozycję **OK**.

![Nowy projekt](media/hello-world-new-project.png)

Powinna zostać wyświetlona na stronie wprowadzenie i kilka przykładowych zasobów.

Jeśli potrzebujesz opuścić ten samouczek i wrócić do niego, można znaleźć nowego projektu HelloWorld na **strona startowa** w **ostatnie** sekcji.

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. Z **pliku** menu, wybierz opcję **New** > **projektu**. Wyszukaj frazę "vsix" i wybierz wizualizację C# **projekt VSIX** i następnie **dalej**.

Krok 2. Wprowadź "nazwę HelloWorld" **Nazwa projektu** i wybierz **Utwórz**.

![Nowy projekt](media/hello-world-new-project-2019.png)

Powinien zostać wyświetlony projektu HelloWorld w **Eksploratora rozwiązań**.

::: moniker-end

## <a name="add-a-custom-command"></a>Dodaj polecenie niestandardowe

Krok 1. Jeśli wybierzesz *.vsixmanifest* plik manifestu, można zobaczyć, jakie opcje są zmieniane, takich jak opis, autora i wersji.

Krok 2. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie). W menu kontekstowym wybierz **Dodaj**, a następnie **nowy element**.

Krok 3. Wybierz **rozszerzalności** sekcji, a następnie wybierz **polecenia niestandardowego**.

Krok 4. W **nazwa** u dołu ekranu, wprowadź nazwę pliku, taką jak *Command.cs*.

![polecenie niestandardowe](media/hello-world-custom-command.png)

Nowy plik poleceń jest widoczna w **Eksploratora rozwiązań**. W obszarze **zasobów** węzła, znajdziesz innych plików związanych z polecenia. Na przykład jeśli chcesz zmodyfikować obraz, plik PNG Krewny.

## <a name="modify-the-source-code"></a>Modyfikowanie kodu źródłowego

W tym momencie polecenia i tekst przycisku są wygenerowany automatycznie i nie bardzo interesujące. Jeśli chcesz wprowadzić zmiany, można zmodyfikować pliku VSCT i pliku CS.

* Plik VSCT jest, gdzie możesz można zmienić nazwy poleceń, a także określić, gdzie go w systemie polecenia programu Visual Studio. Gdy eksplorujesz pliku VSCT zauważysz komentarze objaśniające, jakie każdej sekcji VSCT formanty kodu.

* Plik CS jest, gdzie można zdefiniować akcji, takich jak program obsługi kliknięcie.

::: moniker range="vs-2017"

Krok 1. W **Eksploratora rozwiązań**, znaleźć pliku VSCT nowe polecenie. W takich przypadkach zostanie wywołany *CommandPackage.vsct*.

![polecenie pakietu vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. W **Eksploratora rozwiązań**, znaleźć pliku VSCT pakiet rozszerzenia programu VS. W takich przypadkach zostanie wywołany *HelloWorldPackage.vsct*.

::: moniker-end

Krok 2. Zmiana `ButtonText` parametr `Say Hello World!`.

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

Krok 3. Wróć do **Eksploratora rozwiązań** i Znajdź *Command.cs* pliku. W `Execute` metodę, Zmień parametry `message` z `string.Format(..)` do `Hello World!`.

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

Upewnij się zapisać zmiany do każdego pliku.

## <a name="run-it"></a>Uruchom go

Teraz możesz uruchomić kod źródłowy w wystąpienie eksperymentalne programu Visual Studio.

Krok 1. Naciśnij klawisz **F5** do uruchomienia **Rozpocznij debugowanie** polecenia. To polecenie kompiluje projekt i uruchamia debuger uruchamianie nowego wystąpienia programu Visual Studio o nazwie **wystąpienie doświadczalne**.

::: moniker range="vs-2017"

Zostanie wyświetlone zostaną słowa **wystąpienie doświadczalne** na pasku tytułu programu Visual Studio.

![pasek tytułu w doświadczalnym wystąpieniu](media/hello-world-exp-instance.png)

::: moniker-end

Krok 2. Na **narzędzia** menu **wystąpienie doświadczalne**, kliknij przycisk **Say Hello World!** .

![wynik końcowy](media/hello-world-final-result.png)

Należy wyświetlić dane wyjściowe z nowe polecenie niestandardowe, w tym przypadku okno na środku ekranu, która zapewnia **Witaj, świecie!** Komunikat.

## <a name="next-steps"></a>Następne kroki

Skoro znasz już podstawy pracy z Visual Studio Extensibility, poniżej przedstawiono, gdzie można dowiedzieć się więcej:

* [Do tworzenia rozszerzenia programu Visual Studio](starting-to-develop-visual-studio-extensions.md) — przykłady i samouczki. i publikowania rozszerzenia
* [What's new in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) — nowe funkcje rozszerzalności programu Visual Studio 2017
* [What's new in Visual Studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) — nowe funkcje rozszerzalności programu Visual Studio 2019 r.
* [Wewnątrz zestawu Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) — Dowiedz się, szczegółowe informacje o możliwościach rozszerzania programu Visual Studio
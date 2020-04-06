---
title: Hello World rozszerzenie tutorial | Dokumenty firmy Microsoft
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711664"
---
# <a name="create-your-first-extension-hello-world"></a>Stwórz swoje pierwsze rozszerzenie: Hello World

W tym przykładzie Hello World przeprowadzi Cię przez tworzenie pierwszego rozszerzenia dla programu Visual Studio. W tym samouczku pokazano, jak dodać nowe polecenie do programu Visual Studio.

W procesie tym dowiesz się, jak:

* **[Tworzenie projektu rozszerzalności](#create-an-extensibility-project)**
* **[Dodawanie polecenia niestandardowego](#add-a-custom-command)**
* **[Modyfikowanie kodu źródłowego](#modify-the-source-code)**
* **[Uruchom skrypt](#run-it)**

W tym przykładzie użyjesz języka Visual C#, aby dodać niestandardowy przycisk menu o nazwie "Say Hello World!" który wygląda tak:

![Polecenie Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Ten artykuł dotyczy programu Visual Studio w systemie Windows. W programie Visual Studio dla komputerów Mac zobacz [Przewodnik rozszerzalności w programie Visual Studio dla komputerów Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem upewnij się, że zainstalowano obciążenie **deweloperskie rozszerzenia programu Visual Studio,** które zawiera szablon VSIX, którego potrzebujesz i przykładowy kod.

> [!NOTE]
> Do utworzenia projektu rozszerzalności programu Visual Studio można użyć dowolnej wersji programu Visual Studio (Community, Professional lub Enterprise).

## <a name="create-an-extensibility-project"></a>Tworzenie projektu rozszerzalności

::: moniker range="vs-2017"

Krok 1. Z menu **Plik** wybierz polecenie **Nowy** > **projekt**.

Krok 2. W polu wyszukiwania w prawym górnym rogu wpisz "vsix" i wybierz projekt Visual C# **VSIX**. Wpisz "HelloWorld" dla **nazwy** w dolnej części okna dialogowego i wybierz **OK**.

![nowy projekt](media/hello-world-new-project.png)

Teraz powinna zostać wyświetlona strona Wprowadzenie i niektóre przykładowe zasoby.

Jeśli chcesz opuścić ten samouczek i wrócić do niego, możesz znaleźć swój nowy projekt HelloWorld na **stronie startowej** w sekcji **Ostatnie.**

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. Z menu **Plik** wybierz polecenie **Nowy** > **projekt**. Wyszukaj "vsix" i wybierz projekt Visual C# **VSIX,** a następnie **dalej**.

Krok 2. Wprowadź "HelloWorld" dla **nazwy projektu** i wybierz **pozycję Utwórz**.

![nowy projekt](media/hello-world-new-project-2019.png)

Projekt HelloWorld powinien zostać wyświetlony w **Eksploratorze rozwiązań**.

::: moniker-end

## <a name="add-a-custom-command"></a>Dodawanie polecenia niestandardowego

Krok 1. Jeśli wybierzesz plik manifestu *vsixmanifest,* możesz zobaczyć, jakie opcje można zmieniać, na przykład opis, autor i wersja.

Krok 2. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie). W menu kontekstowym wybierz polecenie **Dodaj**, a następnie **pozycję Nowy element**.

Krok 3. Wybierz sekcję **Rozszerzalność,** a następnie wybierz polecenie **Polecenie**.

Krok 4. W polu **Nazwa** u dołu wprowadź nazwę pliku, taką jak *Command.cs*.

![polecenie niestandardowe](media/hello-world-vsix-command.png)

Nowy plik poleceń jest widoczny w **Eksploratorze rozwiązań**. W węźle **Zasoby** znajdziesz inne pliki związane z twoim poleceniem. Na przykład, jeśli chcesz zmodyfikować obraz, plik PNG jest tutaj.

## <a name="modify-the-source-code"></a>Modyfikowanie kodu źródłowego

W tym momencie polecenie i button tekst są generowane automatycznie i nie bardzo interesujące. Jeśli chcesz wprowadzić zmiany, można zmodyfikować plik VSCT i plik CS.

* Plik VSCT jest, gdzie można zmienić nazwy poleceń, a także określić, gdzie idą w systemie poleceń programu Visual Studio. Podczas eksplorowania pliku VSCT można zauważyć komentarze, które wyjaśniają, co każda sekcja formanty kodu VSCT.

* Plik CS to miejsce, w którym można zdefiniować akcje, takie jak program obsługi kliknięć.

::: moniker range="vs-2017"

Krok 1. W **Eksploratorze rozwiązań**znajdź plik VSCT dla nowego polecenia. W takim przypadku będzie on nosił nazwę *CommandPackage.vsct*.

![vsct pakietu poleceń](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. W **Eksploratorze rozwiązań**znajdź plik VSCT dla pakietu rozszerzenia VS. W takim przypadku będzie się *nazywać HelloWorldPackage.vsct*.

::: moniker-end

Krok 2. Zmień `ButtonText` parametr `Say Hello World!`na .

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

Krok 3. Wróć do **Eksploratora rozwiązań** i znajdź plik *Command.cs.* W `Execute` metodzie zmień `message` ciąg `string.Format(..)` `Hello World!`z na .

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

Pamiętaj, aby zapisać zmiany w każdym pliku.

## <a name="run-it"></a>Uruchom skrypt

Teraz można uruchomić kod źródłowy w wystąpieniu eksperymentalnym programu Visual Studio.

Krok 1. Naciśnij **klawisz F5,** aby uruchomić polecenie **Rozpocznij debugowanie.** To polecenie tworzy projekt i uruchamia debuger, uruchamiając nowe wystąpienie programu Visual Studio o nazwie **Wystąpienie eksperymentalne.**

::: moniker range="vs-2017"

Zostaną wyświetlene słowa **Wystąpienie eksperymentalne** na pasku tytułu programu Visual Studio.

![pasek tytułu wystąpienia eksperymentalnego](media/hello-world-exp-instance.png)

::: moniker-end

Krok 2. W menu **Narzędzia** **wystąpienia eksperymentalnego**kliknij przycisk **Powiedz witaj światu!**.

![wynik końcowy](media/hello-world-final-result.png)

Powinieneś zobaczyć dane wyjściowe z nowego polecenia niestandardowego, w tym przypadku okno dialogowe na środku ekranu, które daje **Hello World!** .

## <a name="next-steps"></a>Następne kroki

Teraz, gdy znasz podstawy pracy z programem Visual Studio Extensibility, tutaj możesz dowiedzieć się więcej:

* [Rozpocznij tworzenie rozszerzeń programu Visual Studio](starting-to-develop-visual-studio-extensions.md) — przykłady, samouczki. i publikowanie rozszerzenia
* [Co nowego w SDK programu Visual Studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) — nowe funkcje rozszerzalności w programie Visual Studio 2017
* [Co nowego w SDK programu Visual Studio 2019](whats-new-visual-studio-2019-sdk.md) — nowe funkcje rozszerzalności w programie Visual Studio 2019
* [Wewnątrz visual studio SDK](internals/inside-the-visual-studio-sdk.md) — dowiedz się szczegóły programu Visual Studio rozszerzalność

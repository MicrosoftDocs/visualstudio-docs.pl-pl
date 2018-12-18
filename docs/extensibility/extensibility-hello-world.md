---
title: Witaj świecie rozszerzenie samouczka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2122a98778372690990a75269be2f3087653678
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349468"
---
# <a name="create-your-first-extension-hello-world"></a>Tworzenie pierwszego rozszerzenia: Hello World

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

Krok 1. Z **pliku** menu, kliknij przycisk **nowy projekt**. W dolnej części ekranu Podaj nazwę projektu.

Krok 2. Z **szablony** menu, kliknij przycisk **Visual C#**, kliknij przycisk **rozszerzalności**, a następnie kliknij przycisk **projekt VSIX**.

![Nowy projekt](media/hello-world-new-project.png)

Powinna zostać wyświetlona na stronie wprowadzenie i kilka przykładowych zasobów.

Jeśli potrzebujesz opuścić ten samouczek i wrócić do niego, można znaleźć nowego projektu HelloWorld na **strona startowa** w **ostatnie** sekcji.

## <a name="add-a-custom-command"></a>Dodaj polecenie niestandardowe

Krok 1. Jeśli wybierzesz manifestu, zostanie wyświetlony, jakie są opcje mogły być zmieniane dla wystąpienia, metadane, opis i wersji.

Krok 2. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie). W menu kontekstowym kliknij **Dodaj**, a następnie kliknij przycisk **nowy element**.

Krok 3. Wybierz **rozszerzalności** sekcji, a następnie kliknij przycisk **polecenia niestandardowego**.

Krok 4. W **nazwa** u dołu ekranu, nadaj jej nazwę, na przykład *Command.cs*.

![polecenie niestandardowe](media/hello-world-custom-command.png)

Nowe polecenie znajduje się w **Eksploratora rozwiązań** w obszarze **zasobów** gałęzi. Jest to również, gdzie znajdziesz innych plików związanych z polecenia, takich jak pliki PNG i ICO, jeśli chcesz zmodyfikować obraz.

## <a name="modify-the-source-code"></a>Modyfikowanie kodu źródłowego

W tym momencie przycisk dodawania jest dość ogólny. Należy zmodyfikować pliku VSCT i pliku CS, jeśli chcesz wprowadzić zmiany.

* Plik VSCT jest, gdzie możesz można zmienić nazwy poleceń, a także określić, gdzie go w systemie polecenia programu Visual Studio. Gdy eksplorujesz pliku VSCT można zauważyć wiele skomentowanej kod, który wyjaśnia, jakie każdej sekcji Formanty kodu.

* Plik CS jest, gdzie można zdefiniować akcji, takich jak program obsługi kliknięcie.

Krok 1. W **Eksploratora rozwiązań**, znaleźć pliku VSCT nowe polecenie. W takich przypadkach zostanie wywołany *CommandPackage.vsct*.

![polecenie pakietu vsct](media/hello-world-command-package-vsct.png)

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

Krok 3. Wróć do **Eksploratora rozwiązań** i Znajdź *Command.cs* pliku. Zmień ciąg `message` polecenia `string.Format(..)` do `Hello World!`.

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

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

Krok 1. Kliknij przycisk **Start** na pasku narzędzi. To kompiluje projekt i uruchamia debuger uruchamianie nowego wystąpienia programu Visual Studio o nazwie **wystąpienie doświadczalne**.

Zostanie wyświetlone zostaną słowa **wystąpienie doświadczalne** na pasku tytułu programu Visual Studio.

![pasek tytułu w doświadczalnym wystąpieniu](media/hello-world-exp-instance.png)

Krok 2. Na **narzędzia** menu **wystąpienie doświadczalne**, kliknij przycisk **Say Hello World!**.

![wynik końcowy](media/hello-world-final-result.png)

Należy wyświetlić dane wyjściowe z nowe polecenie niestandardowe, w tym przypadku okno na środku ekranu, która zapewnia **Witaj, świecie!** Komunikat.

## <a name="next-steps"></a>Następne kroki

Skoro znasz już podstawy pracy z Visual Studio Extensibility, poniżej przedstawiono, gdzie można dowiedzieć się więcej:

* [Do tworzenia rozszerzenia programu Visual Studio](starting-to-develop-visual-studio-extensions.md) — przykłady i samouczki. i publikowania rozszerzenia
* [What's new in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) — nowe funkcje rozszerzalności programu Visual Studio 2017
* [Wewnątrz zestawu Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) — Dowiedz się, szczegółowe informacje o możliwościach rozszerzania programu Visual Studio
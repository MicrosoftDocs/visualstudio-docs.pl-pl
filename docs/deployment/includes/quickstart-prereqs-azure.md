---
ms.openlocfilehash: 3ffab1767817189c8bf27c699713354979425d21
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101751045"
---
## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

* [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) został zainstalowany z odpowiednimi obciążeniami dla wybranego języka:
  * ASP.NET: **ASP.NET i programowanie dla sieci Web**
  * Node.js: **tworzenieNode.js**
::: moniker-end
::: moniker range="vs-2017"
* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) został zainstalowany z odpowiednimi obciążeniami dla wybranego języka:
  * ASP.NET: **ASP.NET i programowanie dla sieci Web**
  * Node.js: **tworzenieNode.js**
::: moniker-end

* Subskrypcja platformy Azure. Jeśli nie masz jeszcze subskrypcji, [zarejestruj się bezpłatnie](https://azure.microsoft.com/free/dotnet/), co obejmuje $200 USD za 30 dni i 12 miesięcy za popularne bezpłatne usługi.

* Projekt ASP.NET, ASP.NET Core, .NET Core lub Node.js. Jeśli nie masz jeszcze projektu, wybierz opcję poniżej:
  * ASP.NET Core: Postępuj zgodnie z [przewodnikiem Szybki Start: Użyj programu Visual Studio do utworzenia pierwszej aplikacji internetowej ASP.NET Core](../../ide/quickstart-aspnet-core.md)lub wykonaj następujące czynności:
    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wybierz pozycję **Utwórz nowy projekt** w oknie uruchamiania. Jeśli okno startowe nie jest otwarte, wybierz pozycję **plik**  >  **startowy**. W polu wyszukiwania wpisz ciąg **aplikacja sieci Web** , wybierz pozycję **C#** jako język, a następnie wybierz pozycję **ASP.NET Core aplikacji sieci Web (Model-View-Controller)**, a następnie wybierz przycisk **dalej**. Na następnym ekranie Nazwij projekt **MyASPApp**, a następnie wybierz przycisk **dalej**.

    Wybierz zalecaną platformę docelową (.NET Core 3,1) lub .NET 5, a następnie wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz pozycję **plik**  >  **Nowy projekt**, wybierz pozycję **Visual C#**  >  **.NET Core**, a następnie wybierz pozycję **ASP.NET Core aplikacji sieci Web**. Po wyświetleniu monitu wybierz szablon **aplikacja sieci Web (Model-View-Controller)** , upewnij się, że **nie** wybrano opcji uwierzytelnianie, a następnie wybierz przycisk **OK**.
    ::: moniker-end
  * Node.js: Postępuj zgodnie z [przewodnikiem Szybki Start: Użyj programu Visual Studio do utworzenia pierwszej aplikacji Node.js](../../ide/quickstart-nodejs.md)lub użyj opcji **plik**  >  **Nowy projekt**, wybierz pozycję **JavaScript**, a następnie wybierz pozycję **puste Node.js aplikacji sieci Web**.

* Przed wykonaniem kroków wdrażania należy się upewnić, że projekt został skompilowany przy użyciu polecenia **kompiluj > Kompiluj rozwiązanie** .
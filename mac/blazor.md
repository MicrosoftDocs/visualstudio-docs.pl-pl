---
title: Tworzenie Blazor aplikacji sieci Web
description: Zawiera informacje na temat Blazor pomocy technicznej w aplikacjach ASP.NET Core w Visual Studio dla komputerów Mac.
author: jongalloway
ms.author: jogallow
ms.date: 08/31/2020
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 0dcc254366e0d652ab7a8442a4d0c526fd72c403
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402544"
---
# <a name="create-no-locblazor-web-apps"></a>Tworzenie Blazor aplikacji sieci Web

Ten przewodnik zawiera wprowadzenie do tworzenia pierwszej Blazor aplikacji sieci Web. Aby uzyskać bardziej szczegółowe wskazówki, zobacz [wprowadzenie do ASP.NET Core Blazor ](/aspnet/core/blazor/index).

ASP.NET Core Blazor obsługuje dwie różne opcje hostingu: Blazor WebAssembly (WASM) lub Blazor serwer. Visual Studio dla komputerów Mac obsługuje oba modele hostingu. Visual Studio dla komputerów Mac 8.4 + obsługuje Blazor serwer i Visual Studio dla komputerów Mac 8.6 +. Aby uzyskać więcej informacji na temat Blazor modeli hostingu, zobacz [ASP.NET Core Blazor modele hostingu ](https://docs.microsoft.com/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1). Obsługa debugowania Blazor WebAssembly projektów w Visual Studio dla komputerów Mac jest dostępna w wersji zapoznawczej programu v 8.8 (dostępnej za pośrednictwem kanału aktualizacji w wersji zapoznawczej w programie **Visual Studio > Sprawdź dostępność aktualizacji...** menu).

Co to jest Blazor ? Blazor to platforma służąca do tworzenia interakcyjnego interfejsu użytkownika sieci Web po stronie klienta w programie .NET, który oferuje następujące korzyści dla deweloperów sieci Web:

* Napisz kod w języku C# zamiast języka JavaScript.
* Skorzystaj z istniejącego ekosystemu .NET bibliotek platformy .NET.
* Udostępnianie logiki aplikacji między serwerem i klientem.
* Skorzystaj z programu. Wydajność, niezawodność i bezpieczeństwo sieci.
* Bądź na bieżąco z programem Visual Studio na komputerach PC, Linux i macOS.
* Twórz w oparciu o wspólny zestaw języków, struktur i narzędzi, które są stabilne, bogate w funkcje i łatwe w użyciu.

## <a name="create-a-new-no-locblazor-webassembly-project"></a>Utwórz nowy Blazor WebAssembly projekt
1. W **oknie uruchamiania**wybierz pozycję **Nowy** , aby utworzyć nowy projekt:

   ![Visual Studio dla komputerów Mac okno uruchamiania z wyróżnionym nowym wyborem](media/blazor-new-project.png)

1. W oknie dialogowym **Nowy projekt** wybierz pozycję Aplikacja **platformy .NET Core** > **App** > ** Blazor WebAssembly ** i wybierz pozycję **dalej**: ![ Wybierz szablon okna dialogowego nowego projektu z::: No-Loc (Blazor)::: serwer — wybrany szablon aplikacji](media/blazor-wasm-project-template.png)

1. Wybierz pozycję .NET Core 3,1 jako platformę docelową, a następnie wybierz pozycję **dalej**. 
   ![Skonfiguruj nowy plik::: No-Loc (Blazor webassembly)::: App okno dialogowe z wybraną platformą docelową dla platformy .NET Core 3,1](media/blazor-wasm-select-target-framework.png)

1. Wybierz nazwę projektu i w razie potrzeby Dodaj obsługę usługi git. Wybierz polecenie **Create** (Utwórz), aby utworzyć projekt.
    ![Skonfiguruj nowe::: No-Loc (Blazor webassembly)::: App okno dialogowe wyświetlane podczas wprowadzania nazwy projektu](media/blazor-wasm-name-project.png)

   Visual Studio dla komputerów Mac otwiera projekt w oknie układu kodu.

1. Wybierz pozycję **Uruchom**  >  **Uruchom bez debugowania** , aby uruchomić aplikację.

   Program Visual Studio uruchamia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), otwiera przeglądarkę do `https://localhost:5001` i wyświetla Blazor aplikację sieci Web.

   ![::: No-Loc (Blazor)::: aplikacja sieci Web w przeglądarce Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="creating-a-new-no-locblazor-server-project"></a>Tworzenie nowego Blazor projektu serwera

1. W **oknie uruchamiania**wybierz pozycję **Nowy** , aby utworzyć nowy projekt:

   ![Visual Studio dla komputerów Mac okno uruchamiania z wyróżnionym nowym wyborem](media/blazor-new-project.png)
1. W oknie dialogowym **Nowy projekt** wybierz pozycję Aplikacja **.NET Core** > **App** > ** Blazor Server** , a następnie wybierz pozycję **dalej**: ![ Wybierz szablon okna dialogowego nowego projektu z::: No-Loc (Blazor)::: serwer — wybrany szablon aplikacji](media/blazor-project-template.png)

1. Wybierz pozycję .NET Core 3,1 jako platformę docelową, a następnie wybierz pozycję **dalej**. 
   ![Skonfiguruj nową aplikację::: No-Loc (Blazor)::: serwer okno dialogowe wyświetlane z platformą docelową wybraną dla platformy .NET Core 3,1](media/blazor-select-target-framework.png)

1. Wybierz nazwę projektu i w razie potrzeby Dodaj obsługę usługi git. Wybierz polecenie **Create** (Utwórz), aby utworzyć projekt.
   ![Skonfiguruj nową aplikację::: No-Loc (Blazor)::: serwer okno dialogowe wyświetlaną podczas wprowadzania nazwy projektu](media/blazor-name-project.png)

   Visual Studio dla komputerów Mac otwiera projekt w oknie układu kodu.
1. Wybierz pozycję **Uruchom**  >  **Uruchom bez debugowania** , aby uruchomić aplikację.

   Program Visual Studio uruchamia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), otwiera przeglądarkę do `https://localhost:5001` i wyświetla Blazor aplikację sieci Web.

   ![::: No-Loc (Blazor)::: aplikacja sieci Web w przeglądarce Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="no-locblazor-support-in-visual-studio-for-mac"></a>Blazor Obsługa w Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac (począwszy od wersji 8,4) zawiera nowe funkcje, które ułatwiają tworzenie nowych Blazor projektów serwera. Zapewnia również pomoc techniczną standardową, która powinna być taka, jak kompilowanie, uruchamianie i debugowanie Blazor projektów. W Visual Studio dla komputerów Mac 8,6 obsługa tworzenia, kompilowania i uruchamiania Blazor WebAssembly projektów została dodana.

W powyższym instruktażu przedstawiono sposób, w jaki Blazor szablon projektu aplikacji serwera pomaga utworzyć nową Blazor aplikację serwera lub Blazor WebAssembly projekt aplikacji. Przyjrzyjmy się kilku dodatkowym funkcjom w Visual Studio dla komputerów Mac, aby obsługiwać Blazor projektowanie projektu.

### <a name="editor-support-for-razor-files"></a>Obsługa edytora dla plików *. Razor*
Visual Studio dla komputerów Mac obejmuje obsługę edytowania plików Razor — większość plików, które będą używane podczas tworzenia Blazor aplikacji. Visual Studio dla komputerów Mac zapewnia pełną obsługę kolorowania i uzupełniania dla plików Razor, w tym uzupełniania dla składników Razor zadeklarowanych w projekcie.

![Okno edytora Visual Studio dla komputerów Mac, w którym jest wyświetlana funkcja IntelliSense dla::: No-Loc (Blazor)::](media/blazor-intellisense.png)

### <a name="publishing-no-locblazor-applications-to-azure-app-service"></a>Publikowanie Blazor aplikacji w Azure App Service
Możesz również publikować Blazor aplikacje bezpośrednio do Azure App Service. Jeśli nie masz konta platformy Azure, aby uruchomić Blazor aplikację na platformie Azure, możesz zawsze [utworzyć bezpłatne](https://azure.microsoft.com/free) konto, które obejmuje 12 miesięcy bezpłatnych usług, $200 bezpłatnych środków na korzystanie z platformy Azure i ponad 25 zawsze bezpłatnych usług.

![Visual Studio dla komputerów Mac przedstawiające środowisko publikowania platformy Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomia projektu

Blazor aplikacje sieci Web domyślnie zawierają kilka katalogów i plików. Po rozpoczęciu pracy poniżej znajdują się główne te, z którymi należy się zapoznać:

### <a name="pages-folder"></a>Folder stron

Ten folder zawiera strony sieci Web projektu, które używają rozszerzenia pliku *Razor* .

### <a name="shared-folder"></a>Folder udostępniony

Ten folder zawiera składniki udostępnione, również przy użyciu rozszerzenia *Razor* . Zobaczysz, że obejmuje to *MainLayout. Razor*, który jest używany do definiowania wspólnego układu w aplikacji. Zawiera również współużytkowany składnik *NavMenu. Razor* , który jest używany na wszystkich stronach. Jeśli tworzysz składniki wielokrotnego użytku, zostaną one umieszczone w folderze **udostępnionym** .

### <a name="app-settings"></a>Ustawienia aplikacji

*appSettings.jsw* pliku zawiera dane konfiguracyjne, takie jak parametry połączenia.

Aby uzyskać więcej informacji na temat konfiguracji, zobacz [Konfiguracja w przewodniku ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>folder wwwroot

Ten folder zawiera pliki statyczne, takie jak pliki HTML, JavaScript i CSS. Aby uzyskać więcej informacji, zobacz [pliki statyczne w ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Ten plik zawiera punkt wejścia dla programu. Aby uzyskać więcej informacji, zobacz [ASP.NET Core hosta sieci Web](/aspnet/core/fundamentals/host/web-host).

### <a name="no-locblazor-server-app-specific-files"></a>Blazor Pliki specyficzne dla aplikacji serwera
#### <a name="app-settings"></a>Ustawienia aplikacji

*appSettings.jsw* pliku zawiera dane konfiguracyjne, takie jak parametry połączenia.

Aby uzyskać więcej informacji na temat konfiguracji, zobacz [Konfiguracja w przewodniku ASP.NET](/aspnet/core/fundamentals/configuration/index).

#### <a name="startupcs"></a>Startup.cs

Ten plik zawiera kod konfigurujący zachowanie aplikacji, na przykład czy aplikacja wymaga zgody na pliki cookie. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji w ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Podsumowanie
W tym samouczku pokazano, jak utworzyć nową Blazor aplikację lub aplikację serwera Blazor WebAssembly w Visual Studio dla komputerów Mac i poznać niektóre funkcje, które Visual Studio dla komputerów Mac oferty ułatwiające tworzenie Blazor aplikacji.

## <a name="see-also"></a>Zobacz też

Aby uzyskać bardziej obszerny przewodnik tworzenia Blazor aplikacji sieci Web, zobacz [wprowadzenie do Blazor ASP.NET Core ](/aspnet/core/blazor/index).

---
title: Tworzenie aplikacji sieci Web Blazor
description: Zawiera informacje na temat obsługi Blazor w aplikacjach ASP.NET Core w Visual Studio dla komputerów Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.topic: how-to
ms.openlocfilehash: ac7fcd9044aa6367f140ac4aa96e6aaf4a9f5885
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939147"
---
# <a name="create-blazor-web-apps"></a>Tworzenie aplikacji sieci Web Blazor

Ten przewodnik zawiera wprowadzenie do tworzenia pierwszej aplikacji sieci Web Blazor. Aby uzyskać bardziej szczegółowe wskazówki, zobacz [wprowadzenie do ASP.NET Core Blazor](/aspnet/core/blazor/index).

ASP.NET Core Blazor obsługuje dwie różne opcje hostingu; Blazor Server i Blazor webassembly. Visual Studio dla komputerów Mac obsługuje oba modele hostingu. Visual Studio dla komputerów Mac 8.4 + obsługuje serwer Blazor i Visual Studio dla komputerów Mac 8.6 + obsługuje oba te elementy. Aby uzyskać więcej informacji na temat modeli hostingu Blazor, zobacz [ASP.NET Core Blazor hosting modeli ](https://docs.microsoft.com/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1). Obsługa debugowania projektów Blazor webassembly w programie Visual Studio dla komputerów Mac będzie dostępna w wersji po 8,6.

Co to jest Blazor? Blazor to struktura służąca do kompilowania interakcyjnego interfejsu użytkownika sieci Web po stronie klienta przy użyciu platformy .NET, który oferuje następujące korzyści dla deweloperów sieci Web:

* Napisz kod w języku C# zamiast języka JavaScript.
* Skorzystaj z istniejącego ekosystemu .NET bibliotek platformy .NET.
* Udostępnianie logiki aplikacji między serwerem i klientem.
* Skorzystaj z programu. Wydajność, niezawodność i bezpieczeństwo sieci.
* Bądź na bieżąco z programem Visual Studio na komputerach PC, Linux i macOS.
* Twórz w oparciu o wspólny zestaw języków, struktur i narzędzi, które są stabilne, bogate w funkcje i łatwe w użyciu.

## <a name="creating-a-new-blazor-server-project"></a>Tworzenie nowego projektu serwera Blazor

1. W **oknie uruchamiania**wybierz pozycję **Nowy** , aby utworzyć nowy projekt:

   ![Visual Studio dla komputerów Mac okno uruchamiania z wyróżnionym nowym wyborem](media/blazor-new-project.png)
1. W oknie dialogowym **Nowy projekt** wybierz pozycję Aplikacja **.NET Core** > **App** > **Blazor Server App** i wybierz pozycję **Next (dalej**): ![ Wybierz szablon okna dialogowego Nowy projekt z wybranym szablonem aplikacji Blazor Server](media/blazor-project-template.png)

1. Wybierz pozycję .NET Core 3,1 jako platformę docelową, a następnie wybierz pozycję **dalej**. 
   ![Skonfiguruj nowe okno dialogowe aplikacji serwera Blazor z wybranym platformą docelową do platformy .NET Core 3,1](media/blazor-select-target-framework.png)

1. Wybierz nazwę projektu i w razie potrzeby Dodaj obsługę usługi git. Wybierz polecenie **Create** (Utwórz), aby utworzyć projekt.
   ![BConfigure nowe okno dialogowe aplikacji serwera Blazor wyświetlane podczas wprowadzania nazwy projektu](media/blazor-name-project.png)

   Visual Studio dla komputerów Mac otwiera projekt w oknie układu kodu.
1. Wybierz pozycję **Uruchom**  >  **Uruchom bez debugowania** , aby uruchomić aplikację.

   Program Visual Studio uruchamia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), otwiera przeglądarkę do `https://localhost:5001` i wyświetla aplikację sieci Web Blazor.

   ![Aplikacja internetowa Blazor w przeglądarce Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Obsługa Blazor w Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac (począwszy od wersji 8,4) zawiera nowe funkcje, które ułatwiają tworzenie nowych projektów serwera Blazor. Zapewnia również pomoc techniczną standardową, która powinna być taka, jak kompilowanie, uruchamianie i Debugowanie projektów Blazor. W Visual Studio dla komputerów Mac 8,6 obsługa tworzenia, kompilowania i uruchamiania projektów Blazor webassembly.

W powyższym instruktażu przedstawiono sposób, w jaki szablon projektu aplikacji serwera Blazor ułatwia tworzenie nowego projektu aplikacji Blazor Server. Zapoznaj się z kilkoma dodatkowymi funkcjami w Visual Studio dla komputerów Mac, aby obsłużyć programowanie projektów Blazor.

### <a name="editor-support-for-razor-files"></a>Obsługa edytora dla plików *. Razor*
Visual Studio dla komputerów Mac obejmuje obsługę edytowania plików Razor — większość plików, które będą używane podczas tworzenia aplikacji Blazor. Wersja systemu Windows i Mac środowiska IDE współużytkują ten sam edytor dla plików. Razor. Zobaczysz pełny kolor i pomoc techniczną dla plików Razor, włącznie z uzupełnianiem dla składników Razor zadeklarowanych w projekcie.

![Okno edytora Visual Studio dla komputerów Mac z technologią IntelliSense dla Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Publikowanie aplikacji Blazor do Azure App Service
Możesz również opublikować aplikacje Blazor bezpośrednio w Azure App Service. Jeśli nie masz konta platformy Azure, aby uruchomić aplikację Blazor na platformie Azure, możesz zawsze [utworzyć bezpłatne](https://azure.microsoft.com/free) konto, które obejmuje 12 miesięcy bezpłatnych usług, $200 bezpłatnych kredytów na korzystanie z platformy Azure i ponad 25 bezpłatnych usług.

![Visual Studio dla komputerów Mac przedstawiające środowisko publikowania platformy Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomia projektu

Aplikacje sieci Web Blazor domyślnie zawierają kilka katalogów i plików. Po rozpoczęciu pracy poniżej znajdują się główne te, z którymi należy się zapoznać:

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

### <a name="startupcs"></a>Startup.cs

Ten plik zawiera kod konfigurujący zachowanie aplikacji, na przykład czy aplikacja wymaga zgody na pliki cookie. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji w ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Podsumowanie
W tym samouczku pokazano, jak utworzyć nową aplikację serwera Blazor w Visual Studio dla komputerów Mac i poznać niektóre funkcje, które Visual Studio dla komputerów Mac oferty ułatwiające tworzenie aplikacji Blazor.

## <a name="see-also"></a>Zobacz też

Aby uzyskać bardziej obszerny przewodnik tworzenia Blazor Web Apps, zobacz [wprowadzenie do ASP.NET Core Blazor](/aspnet/core/blazor/index).

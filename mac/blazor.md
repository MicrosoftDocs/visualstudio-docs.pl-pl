---
title: Tworzenie aplikacji internetowych Blazor
description: Zawiera informacje o pomocy technicznej blazor w ASP.NET podstawowych aplikacji w programie Visual Studio dla komputerów Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75737587"
---
# <a name="create-blazor-web-apps"></a>Tworzenie aplikacji internetowych Blazor

Ten przewodnik zawiera wprowadzenie do tworzenia pierwszej aplikacji internetowej Blazor. Aby uzyskać bardziej szczegółowe wskazówki, zobacz [Wprowadzenie do ASP.NET Core Blazor](/aspnet/core/blazor/index).

Visual Studio dla komputerów Mac (począwszy od wersji 8.4) obejmuje obsługę tworzenia i publikowania ASP.NET core blazor server aplikacji. Blazor to struktura do tworzenia interaktywnego interfejsu użytkownika sieci web po stronie klienta za pomocą platformy .NET, która oferuje następujące korzyści deweloperom stron internetowych:

* Napisz kod w języku C# zamiast JavaScript.
* Wykorzystaj istniejący ekosystem platformy .NET bibliotek .NET.
* Udostępnianie logiki aplikacji na serwerze i kliencie.
* Korzystaj z . Wydajność, niezawodność i bezpieczeństwo sieci NET.
* Zachowaj produktywność dzięki programowi Visual Studio na komputerach PC, Linux i macOS.
* Korzystaj ze wspólnego zestawu języków, struktur i narzędzi, które są stabilne, bogate w funkcje i łatwe w użyciu.

## <a name="creating-a-new-blazor-project"></a>Tworzenie nowego projektu Blazor

1. W **oknie startowym**wybierz pozycję **Nowy,** aby utworzyć nowy projekt:

   ![Okno startowe programu Visual Studio dla komputerów Mac z wyróżnionym nowym zaznaczeniem](media/blazor-new-project.png)
1. W oknie dialogowym **Nowy projekt** wybierz pozycję **.NET Core** > ![ **App** > **Blazor Server App** i wybierz pozycję **Dalej**: Wybierz szablon dla nowego okna dialogowego projektu z wybranym szablonem aplikacji Blazor Server](media/blazor-project-template.png)

1. Wybierz .NET Core 3.1 jako platformę docelową, a następnie wybierz **przycisk Dalej**. 
   ![Skonfiguruj nowe okno dialogowe aplikacji Blazor Server z wybraną ramą docelową na .NET Core 3.1](media/blazor-select-target-framework.png)

1. Wybierz nazwę projektu i w razie potrzeby dodaj obsługę Git. Wybierz polecenie **Create** (Utwórz), aby utworzyć projekt.
   ![BKonfigurowanie nowego okna dialogowego aplikacji Blazor Server wyświetlane podczas wprowadzania nazwy projektu](media/blazor-name-project.png)

   Program Visual Studio dla komputerów Mac otwiera projekt w oknie układu Kod.
1. Wybierz **uruchom** > **start bez debugowania,** aby uruchomić aplikację.

   Visual Studio uruchamia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), `https://localhost:5001`otwiera przeglądarkę do , i wyświetla aplikację internetową Blazor.

   ![Aplikacja internetowa Blazor w przeglądarce Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Pomoc techniczna blazora w programie Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac (począwszy od wersji 8.4) zawiera nowe funkcje ułatwiające tworzenie nowych projektów serwera Blazor. Jak również zapewnia standardowe wsparcie, których można oczekiwać, takich jak tworzenie, uruchamianie i debugowanie projektów Blazor. 

W powyższym przewodniku zobaczyliśmy, jak szablon projektu aplikacji Blazor Server pomaga utworzyć nowy projekt aplikacji Blazor Server. Przyjrzyjmy się niektórym dodatkowym funkcjom programu Visual Studio dla komputerów Mac do obsługi tworzenia projektu serwera Blazor.

### <a name="editor-support-for-razor-files"></a>Obsługa edytora plików *.brzytwa*
Program Visual Studio dla komputerów Mac obsługuje edytowanie plików .brzytwa — większość plików, których będziesz używać podczas tworzenia aplikacji Blazor. Wersja IDE dla systemów Windows i Mac ma ten sam edytor dla plików .brzytwa. Zobaczysz pełną obsługę koloryzacji i uzupełniania plików .brzytwa, w tym uzupełnienia składników Razor zadeklarowanych w projekcie.

![Okno edytora programu Visual Studio dla komputerów Mac z poleceniem Intellisense dla blazora](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Publikowanie aplikacji Blazor w usłudze Azure App Service
Można również publikować aplikacje Blazor bezpośrednio w usłudze Azure App Service. Jeśli nie masz konta platformy Azure do uruchamiania aplikacji Blazor na platformie Azure, zawsze możesz [zarejestrować się w bezpłatnej aplikacji,](https://azure.microsoft.com/free) która również ma 12 miesięcy bezpłatnych popularnych usług, 200 usd bezpłatnych kredytów platformy Azure i ponad 25 zawsze bezpłatnych usług.

![Visual Studio dla komputerów Mac z wyświetlaniem publikowania na platformie Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomia projektu

Aplikacje internetowe Blazor zawierają domyślnie kilka katalogów i plików. Jak zaczynasz, oto główne z nich, które musisz znać:

### <a name="pages-folder"></a>Folder Strony

Ten folder zawiera strony internetowe projektu, które używają rozszerzenia pliku *.brzytwa.*

### <a name="shared-folder"></a>Folder udostępniony

Ten folder zawiera składniki udostępnione, również przy użyciu rozszerzenia *.brzytwa.* Zobaczysz, że obejmuje to *MainLayout.brzytwa*, który jest używany do definiowania wspólnego układu w całej aplikacji. Zawiera również udostępniony komponent *NavMenu.brzytwa,* który jest używany na wszystkich stronach. Jeśli tworzysz składniki wielokrotnego porodu, trafią one do folderu **Udostępnione.**

### <a name="app-settings"></a>Ustawienia aplikacji

Plik *appSettings.json* zawiera dane konfiguracyjne, takie jak parametry połączenia.

Aby uzyskać więcej informacji na temat konfiguracji, zobacz [przewodnik Konfiguracja w ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>folder wwwroot

Ten folder zawiera pliki statyczne, takie jak pliki HTML, JavaScript i CSS. Aby uzyskać więcej informacji, zobacz [Pliki statyczne w ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Ten plik zawiera punkt wejścia dla programu. Aby uzyskać więcej informacji, zobacz [ASP.NET Core Web Host](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Ten plik zawiera kod, który konfiguruje zachowanie aplikacji, na przykład czy aplikacja wymaga zgody na pliki cookie. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji w ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Podsumowanie
W tym samouczku opisano, jak utworzyć nową aplikację Blazor Server w programie Visual Studio dla komputerów Mac i dowiedzieć się więcej o niektórych funkcjach, które program Visual Studio dla komputerów Mac oferuje, aby ułatwić tworzenie aplikacji Blazor.

## <a name="see-also"></a>Zobacz też

Aby uzyskać bardziej kompleksowy przewodnik po tworzeniu aplikacji internetowych Blazor, zobacz [Wprowadzenie do ASP.NET Core Blazor](/aspnet/core/blazor/index).

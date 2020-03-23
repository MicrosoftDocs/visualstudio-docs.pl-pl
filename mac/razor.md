---
title: Tworzenie aplikacji internetowych Razor
description: Zawiera informacje o obsłudze brzytwy w aplikacjach ASP.NET Core w programie Visual Studio dla komputerów Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715874"
---
# <a name="create-razor-web-apps"></a>Tworzenie aplikacji internetowych Razor

Ten przewodnik zawiera wprowadzenie do tworzenia pierwszej aplikacji internetowej Razor. Aby uzyskać bardziej szczegółowe wskazówki, zobacz [Wprowadzenie do stron razor w ASP.NET Core](/aspnet/core/razor-pages/index).

Program Visual Studio dla komputerów Mac zapewnia obsługę edycji razor, w tym IntelliSense i wyróżniania składni w plikach *cshtml.* Nowością w programie Visual Studio 2019 dla komputerów Mac 8.3+ jest możliwość zapoznania się z kontekstem IntelliSense w pliku Razor, dzięki czemu otrzymujesz intellisense, który pasuje do języka, który aktualnie edytujesz w dokumencie.

![Edycja maszynki do golenia w programie Visual Studio dla komputerów Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Tworzenie nowego projektu Razor

1. Na ekranie powitalnym wybierz pozycję **Nowy,** aby utworzyć nowy projekt:

   ![Nowy projekt programu Visual Studio dla komputerów Mac](media/razor-new.png)
1. W oknie dialogowym **Nowy projekt** przejdź do aplikacji**sieci Web** **.NET Core** > **App** > i wybierz pozycję **Dalej:**

   ![Szablon projektu Razor](media/razor-new-project1.png)
1. Wybierz platformę docelową .NET Core (zalecamy wersję 2.2 lub nowszą), a następnie wybierz pozycję **Dalej**. Wybierz nazwę projektu i w razie potrzeby dodaj obsługę Git. Wybierz polecenie **Create** (Utwórz), aby utworzyć projekt.

   ![Nazwa projektu Razor](media/razor-new-project2.png)

   Program Visual Studio dla komputerów Mac otwiera projekt w oknie układu Kod.
1. Uruchom projekt bez debugowania za pomocą **polecenia+option+F5**.

   Program Visual Studio uruchamia [Kestrel](/aspnet/core/fundamentals/servers/kestrel) `https://localhost:5001`, otwiera przeglądarkę do , i wyświetla pierwszą aplikację internetową Razor.

   ![Aplikacja internetowa Razor w przeglądarce Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomia projektu

Aplikacje internetowe Razor zawierają następujące składniki.

### <a name="pages-folder"></a>Folder Strony

Ten folder zawiera strony internetowe projektu wraz z kodem dla każdego z nich:
   - Plik * \*cshtml* dla znaczników HTML i składni Razor.
   - Plik * \*.cshtml.cs* dla kodu C# dla obsługi zdarzeń strony.

Pliki pomocnicze mają nazwy, które zaczynają się od podkreślenia. Na przykład plik _Layout.cshtml konfiguruje elementy interfejsu użytkownika wspólne dla wszystkich stron. Ten plik konfiguruje menu nawigacyjne w górnej części strony i informacje o prawach autorskich na dole. Aby uzyskać więcej informacji, zobacz [Układ w ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Ustawienia uruchamiania

Plik *launchSettings.json* zawiera ustawienia usług IIS, adres URL aplikacji i inne powiązane ustawienia.

### <a name="app-settings"></a>Ustawienia aplikacji

Plik *appSettings.json* zawiera dane konfiguracyjne, takie jak parametry połączenia.

Aby uzyskać więcej informacji na temat konfiguracji, zobacz [przewodnik Konfiguracja w ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>folder wwwroot

Ten folder zawiera pliki statyczne, takie jak pliki HTML, JavaScript i CSS. Aby uzyskać więcej informacji, zobacz [Pliki statyczne w ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Ten plik zawiera punkt wejścia dla programu. Aby uzyskać więcej informacji, zobacz [ASP.NET Core Web Host](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Ten plik zawiera kod, który konfiguruje zachowanie aplikacji, na przykład czy aplikacja wymaga zgody na pliki cookie. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji w ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Zobacz też

Aby uzyskać bardziej kompleksowy przewodnik po tworzeniu aplikacji internetowych Razor, zobacz [Wprowadzenie do stron Razor w ASP.NET Core](/aspnet/core/razor-pages/index).

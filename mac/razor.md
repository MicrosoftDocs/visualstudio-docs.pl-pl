---
title: Tworzenie aplikacji sieci Web Razor
description: Zawiera informacje na temat obsługi Razor w aplikacjach ASP.NET Core w Visual Studio dla komputerów Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715874"
---
# <a name="create-razor-web-apps"></a>Tworzenie aplikacji sieci Web Razor

Ten przewodnik zawiera wprowadzenie do tworzenia pierwszej aplikacji sieci Web Razor. Aby uzyskać bardziej szczegółowe wskazówki, zobacz [wprowadzenie do Razor Pages w ASP.NET Core](/aspnet/core/razor-pages/index).

Visual Studio dla komputerów Mac zapewnia obsługę edytowania Razor, w tym funkcji IntelliSense i wyróżniania składni w plikach *. cshtml* . Nowość w programie Visual Studio 2019 for Mac 8.3 + to możliwość posiadania funkcji IntelliSense obsługującej kontekst w pliku Razor, dzięki czemu otrzymujesz funkcję IntelliSense zgodną z językiem aktualnie edytowanym w dokumencie.

![Edytowanie Razor w Visual Studio dla komputerów Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Tworzenie nowego projektu Razor

1. Na ekranie powitalnym wybierz pozycję **Nowy** , aby utworzyć nowy projekt:

   ![Visual Studio dla komputerów Mac nowy projekt](media/razor-new.png)
1. W oknie dialogowym **Nowy projekt** przejdź do pozycji **.NET Core** > **App** > **aplikacji sieci Web** i wybierz pozycję **dalej**:

   ![Szablon projektu Razor](media/razor-new-project1.png)
1. Wybierz platformę docelową platformy .NET Core (zalecamy wersję 2,2 lub nowszą), a następnie wybierz pozycję **dalej**. Wybierz nazwę projektu i w razie potrzeby Dodaj obsługę usługi git. Wybierz pozycję **Utwórz** , aby utworzyć projekt.

   ![Nazwa projektu Razor](media/razor-new-project2.png)

   Visual Studio dla komputerów Mac otwiera projekt w oknie układu kodu.
1. Uruchom projekt bez debugowania przy użyciu **polecenia + Option + F5**.

   Program Visual Studio uruchamia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), otwiera przeglądarkę w celu `https://localhost:5001`i wyświetla pierwszą aplikację sieci Web Razor.

   ![Aplikacja sieci Web Razor w przeglądarce Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomia projektu

Aplikacje sieci Web Razor zawierają następujące składniki.

### <a name="pages-folder"></a>Folder stron

Ten folder zawiera strony sieci Web projektu wraz z kodem związanym z każdym z nich:
   - Plik *\*. cshtml* dla znaczników HTML i składnia Razor.
   - Plik *\*. cshtml.cs* dla C# kodu związany z obsługą zdarzeń na stronach.

Pliki pomocnicze mają nazwy zaczynające się od znaku podkreślenia. Na przykład plik _Layout. cshtml służy do konfigurowania elementów interfejsu użytkownika wspólnych dla wszystkich stron. Ten plik konfiguruje menu nawigacji w górnej części strony i informacje o prawach autorskich u dołu. Aby uzyskać więcej informacji, zobacz [Układ w ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Ustawienia uruchamiania

Plik *profilu launchsettings. JSON* zawiera ustawienia usług IIS, adres URL aplikacji i inne powiązane ustawienia.

### <a name="app-settings"></a>Ustawienia aplikacji

Plik *appSettings. JSON* zawiera dane konfiguracyjne, takie jak parametry połączenia.

Aby uzyskać więcej informacji na temat konfiguracji, zobacz [Konfiguracja w przewodniku ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>folder wwwroot

Ten folder zawiera pliki statyczne, takie jak pliki HTML, JavaScript i CSS. Aby uzyskać więcej informacji, zobacz [pliki statyczne w ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Ten plik zawiera punkt wejścia dla programu. Aby uzyskać więcej informacji, zobacz [ASP.NET Core hosta sieci Web](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Ten plik zawiera kod konfigurujący zachowanie aplikacji, na przykład czy aplikacja wymaga zgody na pliki cookie. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji w ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Zobacz także

Aby uzyskać bardziej obszerny przewodnik tworzenia aplikacji sieci Web Razor, zobacz [wprowadzenie do Razor Pages w ASP.NET Core](/aspnet/core/razor-pages/index).

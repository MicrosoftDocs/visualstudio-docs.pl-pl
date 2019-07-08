---
title: Razor
description: Informacje na temat obsługi razor w aplikacji asp.net core w programie Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: 181059ae2985f570ad1dc0749045e39ed4ec1e7e
ms.sourcegitcommit: 3cc73e74921a9ceb622542e0e263abeebc455c00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/08/2019
ms.locfileid: "67624517"
---
# <a name="razor"></a>Razor

Program Visual Studio for Mac zapewnia obsługę Razor do edycji, w tym funkcji IntelliSense i wyróżniania składni w *.cshtml* plików.

![Razor do edycji w programie Visual Studio dla komputerów Mac](media/razor-editor.png)

Ten przewodnik zawiera wprowadzenie do tworzenia pierwszej aplikacji sieci web Razor. Bardziej szczegółowe wskazówki można znaleźć na stronie [stron Razor w dokumentacji platformy .NET Core](/aspnet/core/razor-pages/index).

## <a name="creating-a-new-razor-project"></a>Tworzenie nowego projektu Razor

* Na ekranie powitalnym wybierz **New** do utworzenia nowego projektu:

![Program Visual Studio for Mac nowy projekt](media/razor-new.png)

* W oknie dialogowym Nowy projekt, przejdź do **platformy .NET Core** > **aplikacji** > **aplikacji sieci Web** i wybierz **dalej**przycisku:

![Szablon projektu razor](media/razor-new-project1.png)

* Wybierz swoje platformy .NET Core Target Framework wymagane (zalecane 2.2 lub nowszej) i wybierz **dalej**.  Wybierz nazwę projektu i dodać obsługę usługi git, jeśli jest to wymagane. Wybierz **Utwórz** do tworzenia projektu.

![Nazwa projektu razor](media/razor-new-project2.png)

Program Visual Studio for Mac zostanie Otwórz swój projekt w układzie kodu.

* Uruchom projekt bez debugowania za pomocą **Cmd-Opt — F5**

Program Visual Studio będzie uruchomić [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) i uruchomi przeglądarkę, aby `https://localhost:5001` i wyświetlić pierwszej aplikacji sieci web Razor:

![Aplikacja sieci web razor w przeglądarce Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Struktura projektu

Aplikacje sieci web razor składają się z następujących składników:

### <a name="pages-folder"></a>Folder stron

Folder stron w projekcie jest, gdzie można znaleźć na stronach sieci web, wraz z kodem dla każdego:
*    A * *.cshtml* w pliku kodu znaczników HTML i składni Razor.
*    A * *. cshtml.cs* plików dla Twojego C# związanym z kodem obsługi zdarzenia strony.

Pliki obsługi mają nazwy rozpoczynające się od znaku podkreślenia. Na przykład pliku _Layout.cshtml konfiguruje elementy interfejsu użytkownika dla wszystkich stron. Ten plik konfiguruje menu nawigacji w górnej części strony i informacje o prawach autorskich w dolnej części strony. Aby uzyskać więcej informacji, zobacz [układu w programie ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Ustawienia uruchamiania

*LaunchSettings.json* plik zawiera ustawienia programu IIS, adres URL aplikacji i inne powiązane ustawienia.

### <a name="app-settings"></a>Ustawienia aplikacji

*AppSettings, json* plik zawiera dane konfiguracyjne, takie jak parametry połączenia.

Aby uzyskać więcej informacji o konfiguracji zobacz [konfiguracji w przewodniku ASP.NET](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Wwwroot folder

Zawiera pliki statyczne, takie jak pliki HTML, plików JavaScript i plików CSS. Aby uzyskać więcej informacji, zobacz [pliki statyczne z platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Zawiera punkt wejścia programu. Aby uzyskać więcej informacji, zobacz [hosta sieci Web programu ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Zawiera kod, który konfiguruje zachowania aplikacji, na przykład tego, czy wymaga zgody na pliki cookie. Aby uzyskać więcej informacji, zobacz [uruchamiania aplikacji w programie ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-aso"></a>Zobacz programy oraz

Aby uzyskać bardziej szczegółowe wskazówki na temat tworzenia aplikacji sieci web Razor zobacz [wprowadzenie do stron Razor programu ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).

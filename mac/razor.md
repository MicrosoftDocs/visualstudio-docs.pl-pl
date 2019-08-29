---
title: Razor
description: Informacje na temat obsługi Razor w aplikacjach asp.net Core w Visual Studio dla komputerów Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: a66a31d2c63fcb0e2adc4554c49a76c727f9a288
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107938"
---
# <a name="razor"></a>Razor

Visual Studio dla komputerów Mac zapewnia obsługę edytowania Razor, w tym funkcji IntelliSense i wyróżniania składni w plikach *. cshtml* .

![Edytowanie Razor w Visual Studio dla komputerów Mac](media/razor-editor.png)

Ten przewodnik zawiera wprowadzenie do tworzenia pierwszej aplikacji sieci Web Razor. Dokładniejszy przewodnik można Razor Pages znaleźć w [dokumentacji programu .NET Core](/aspnet/core/razor-pages/index).

## <a name="creating-a-new-razor-project"></a>Tworzenie nowego projektu Razor

* Na ekranie powitalnym wybierz pozycję **Nowy** , aby utworzyć nowy projekt:

![Visual Studio dla komputerów Mac nowy projekt](media/razor-new.png)

* W oknie dialogowym Nowy projekt przejdź do**aplikacji sieci Web** aplikacji >  **.NET Core** > i wybierz przycisk **dalej** :

![Szablon projektu Razor](media/razor-new-project1.png)

* Wybierz platformę docelową platformy .NET Core (zalecana 2,2 lub nowsza), a następnie wybierz przycisk **dalej**.  Wybierz nazwę projektu i w razie potrzeby Dodaj obsługę usługi git. Wybierz pozycję **Utwórz** , aby utworzyć projekt.

![Nazwa projektu Razor](media/razor-new-project2.png)

Visual Studio dla komputerów Mac otworzy projekt w układzie kodu.

* Uruchom projekt bez debugowania przy użyciu **polecenia CMD-OPT-F5**

Program Visual Studio uruchomi [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) i uruchomi przeglądarkę w celu `https://localhost:5001` wyświetlenia pierwszej aplikacji sieci Web Razor:

![Aplikacja sieci Web Razor w przeglądarce Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomia projektu

Aplikacje sieci Web Razor składają się z następujących składników:

### <a name="pages-folder"></a>Folder stron

Folder strony w projekcie to miejsce, w którym można znaleźć strony sieci Web, wraz z kodem związanym z każdym z nich:
* Plik * *. cshtml* dla znaczników HTML i składnia Razor.
* Plik * *. cshtml.cs* dla kodu związany C# z obsługą zdarzeń na stronach.

Pliki pomocnicze mają nazwy zaczynające się od znaku podkreślenia. Na przykład plik _Layout. cshtml służy do konfigurowania elementów interfejsu użytkownika wspólnych dla wszystkich stron. Ten plik konfiguruje menu nawigacji w górnej części strony i informacje o prawach autorskich w dolnej części strony. Aby uzyskać więcej informacji, zobacz [Układ w ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Ustawienia uruchamiania

Plik *profilu launchsettings. JSON* zawiera ustawienia usług IIS, adres URL aplikacji i inne powiązane ustawienia.

### <a name="app-settings"></a>Ustawienia aplikacji

Plik *AppSettings* w formacie JSON zawiera dane konfiguracyjne, takie jak parametry połączenia.

Aby uzyskać więcej informacji na temat konfiguracji, zobacz [Konfiguracja w przewodniku ASP.NET](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>folder wwwroot

Zawiera pliki statyczne, takie jak pliki HTML, pliki JavaScript i pliki CSS. Aby uzyskać więcej informacji, zobacz [pliki statyczne w ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Zawiera punkt wejścia dla programu. Aby uzyskać więcej informacji, zobacz [ASP.NET Core hosta sieci Web](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Zawiera kod, który konfiguruje zachowanie aplikacji, na przykład czy wymaga zgody na pliki cookie. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji w ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-aso"></a>Zobacz ASO

Aby uzyskać bardziej obszerny przewodnik dotyczący tworzenia aplikacji sieci Web Razor [, zobacz Wprowadzenie do Razor Pages w ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).

---
title: Aplikacja internetowa ASP.NET Core za pomocą platformy Entity Framework i Visual Studio 2019 r.
titleSuffix: ''
description: W pierwszym kroku przed utworzeniem aplikacji internetowej ASP.NET Core Dowiedz się, jak zainstalować program Visual Studio 2019 r z tym Samouczek wideo i instrukcje krok po kroku.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 6668648668ab71e033d1341d71ecf5c7c2a47554
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261726"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Samouczek: Utwórz swoją pierwszą aplikację ASP.NET Core przy użyciu platformy Entity Framework za pomocą programu Visual Studio 2019 r.

W tym samouczku będziesz tworzenie aplikacji internetowej ASP.NET Core, która korzysta z danych i wdrożyć ją na platformie Azure. W tym samouczku składa się z następujących czynności:

- [Krok 1. Install Visual Studio 2019](#step-1-install-visual-studio-2019)
- [Krok 2. Tworzenie pierwszej aplikacji sieci web platformy ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)
- [Krok 3. Praca z danymi przy użyciu platformy Entity Framework](tutorial-aspnet-core-ef-step-03.md)
- [Krok 4. Udostępnianie internetowego interfejsu API z poziomu aplikacji ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)
- [Krok 5. Wdrażanie aplikacji platformy ASP.NET Core na platformie Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Krok 1. Install Visual Studio 2019

Dowiedz się, jak zainstalować program Visual Studio 2019 r z tym Samouczek wideo i instrukcje krok po kroku. Jeśli zainstalowano już program Visual Studio, przejdź do sekcji [krok 2: Tworzenie pierwszej aplikacji sieci web platformy ASP.NET Core](tutorial-aspnet-core-ef-step-02.md).

_Obejrzyj ten film wideo i postępuj zgodnie z integracją programów, aby zainstalować program Visual Studio i Utwórz swoją pierwszą aplikację ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Pobierz Instalatora

Przejdź do [visualstudio.com](https://visualstudio.com) odnaleźć Instalatora. Znajdź łącza 2019 usługi Visual Studio i kliknij go, aby rozpocząć pobieranie. Bezpłatna wersja programu Visual Studio wybierz program Visual Studio Community.

## <a name="start-the-installer"></a>Uruchamianie Instalatora

Po zakończeniu pobierania kliknij **Uruchom** można uruchomić Instalatora.

![Visual Studio 2019 Installer](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Wybieranie obciążenia

Program Visual Studio może służyć do tworzenia różnego rodzaju i obciążeń ułatwiają do pobrania wszystko, co jest potrzebne do rodzaju aplikacje, które chcesz skompilować. Wybierz **ASP.NET i aplikacji sieci Web** i **programowanie dla wielu platform .NET Core** obciążeń teraz. Można zawsze ponownie uruchomić Instalatora później w celu zainstalowania dodatkowych obciążeń i składników.

![Visual Studio 2019 Choose Workloads](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Zainstaluj

Kliknij przycisk **zainstalować** i pozwól Instalatora, Pobierz i zainstaluj program Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>Uruchom program Visual Studio po raz pierwszy

Program Visual Studio powinien być uruchamiany automatycznie po zakończeniu Instalatora. Monit może zostać do logowania, która zawiera niektóre funkcje nieuprzywilejowany skojarzone z nią, ale w przypadku, teraz możesz to zrobić później. Następnie możesz wybrać ustawienia motywu i rozwoju. Po dokonaniu te opcje można rozpocząć swój pierwszy projekt. Kliknij przycisk **Utwórz nowy projekt** , a następnie wybierz **aplikacji sieci Web programu ASP.NET Core**.

![2019 usługi Visual Studio Utwórz nowy projekt aplikacji sieci Web platformy ASP.NET Core](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Poznaj typy projektów ASP.NET Core

Możesz wybierz lokalizację i nazwę projektu, a następnie wybierz **Utwórz**. Teraz można wybrać szablon, który na potrzeby aplikacji platformy ASP.NET Core. Można wybrać następujące opcje:

- Pusty. Szablon pusty projekt, który można zacząć od podstaw.
- API. Najlepsze dla interfejsów API sieci web.
- Aplikacja sieci Web. Standardowa aplikacji internetowej ASP.NET Core utworzona za pomocą stron Razor.
- Aplikacja internetowa (Model-View-Controller). Standardowa aplikacji internetowej ASP.NET Core przy użyciu wzorca Model-View-Controller.
- Platformy angular.
- React.js.
- React.js / Redux.
- Biblioteki klas razor. Umożliwia udostępnianie zasobów Razor między projektami.

Należy pamiętać, że dla większości szablonów projektu możesz również włączyć obsługę platformy Docker, zaznaczając pole. Możesz również dodać obsługę uwierzytelniania, klikając pozycję Zmień uwierzytelnianie przycisku. W tym miejscu można wybrać jeden z:

- Bez uwierzytelniania.
- Indywidualne konta użytkowników. Są one przechowywane w bazie danych lokalnych lub opartych na platformie Azure.
- Kont służbowych lub szkolnych. Ta opcja używa usługi Active Directory, Azure AD lub Office 365 do uwierzytelniania.
- Uwierzytelnianie Windows. Odpowiedni dla aplikacji intranetowych.

Wybierz standardowego szablonu aplikacji sieci Web bez uwierzytelniania, a następnie kliknij przycisk **OK**.

![Visual Studio 2019 Choose ASP.NET Core Project Options](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Następne kroki

W następnym filmie wideo dowiesz się więcej na temat swój pierwszy projekt platformy ASP.NET Core.

[Samouczek: Tworzenie pierwszej aplikacji sieci Web platformy ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Zobacz także

- [Samouczek: Rozpoczynanie pracy z usługą C# i ASP.NET Core](tutorial-aspnet-core.md) bardziej szczegółowy samouczek bez przewodnik wideo

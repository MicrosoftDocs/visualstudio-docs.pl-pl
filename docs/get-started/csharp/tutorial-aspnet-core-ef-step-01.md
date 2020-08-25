---
title: ASP.NET Core aplikację sieci Web z Entity Framework & Visual Studio 2019
titleSuffix: ''
description: Pierwszy krok przed utworzeniem ASP.NET Core aplikacji sieci Web, Dowiedz się, jak zainstalować program Visual Studio 2019 z tym samouczkiem wideo oraz instrukcje krok po kroku.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f6d069bfa462b8aa75fc9247c08b3662c4a445fd
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801805"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Samouczek: Tworzenie pierwszej aplikacji ASP.NET Core przy użyciu Entity Framework z programem Visual Studio 2019

W tym samouczku utworzysz aplikację sieci Web ASP.NET Core, która używa danych, i Wdróż ją na platformie Azure. Ten samouczek składa się z następujących kroków:

- [Krok 1. Instalowanie programu Visual Studio 2019](#step-1-install-visual-studio-2019)
- [Krok 2. Tworzenie pierwszej aplikacji sieci Web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)
- [Krok 3. Współpraca z danymi przy użyciu Entity Framework](tutorial-aspnet-core-ef-step-03.md)
- [Krok 4. Uwidacznianie internetowego interfejsu API w aplikacji ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)
- [Krok 5. wdrażanie aplikacji ASP.NET Core na platformie Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Krok 1. Instalowanie programu Visual Studio 2019

Dowiedz się, jak zainstalować program Visual Studio 2019 z tym samouczkiem wideo oraz instrukcje krok po kroku. Jeśli masz już zainstalowany program Visual Studio, przejdź do [kroku 2: Tworzenie pierwszej aplikacji sieci web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md).

_Obejrzyj ten film wideo i postępuj zgodnie z instrukcjami, aby zainstalować program Visual Studio i utworzyć swoją pierwszą aplikację ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Pobierz instalatora

Przejdź do [VisualStudio.com](https://visualstudio.com) , aby znaleźć Instalatora. Znajdź link programu Visual Studio 2019 i kliknij go, aby rozpocząć pobieranie. W przypadku bezpłatnej wersji programu Visual Studio wybierz pozycję Visual Studio Community.

## <a name="start-the-installer"></a>Uruchom Instalatora

Po zakończeniu pobierania kliknij przycisk **Uruchom** , aby uruchomić Instalatora.

![Instalator programu Visual Studio 2019](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Wybieranie obciążeń

Program Visual Studio może być używany w wielu różnych rodzajach programowania, a obciążenia ułatwiają pobieranie wszystkiego, czego potrzebujesz, dla rodzaju aplikacji, które chcesz skompilować. W tej chwili wybierz pozycję **ASP.NET i programowanie** dla **wielu platform platformy .NET Core** . Później możesz ponownie uruchomić Instalatora, aby zainstalować dodatkowe obciążenia i składniki.

![Visual Studio 2019 Wybieranie obciążeń](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Instalowanie

Kliknij przycisk **Zainstaluj** , aby Instalator mógł pobrać i zainstalować program Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>Uruchom program Visual Studio po raz pierwszy

Program Visual Studio powinien być uruchamiany automatycznie po zakończeniu działania Instalatora. Może zostać wyświetlony monit o zalogowanie się, z którym są skojarzone pewne funkcje, ale teraz można wybrać tę opcję później. Następnie możesz wybrać ustawienia motywu i programowania. Po dokonaniu tych wyborów będziesz gotowy rozpocząć swój pierwszy projekt. Kliknij przycisk **Utwórz nowy projekt** , a następnie wybierz **ASP.NET Core aplikacji sieci Web**.

![Visual Studio 2019 Utwórz nowy projekt aplikacji sieci Web ASP.NET Core](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Eksploruj ASP.NET Core typy projektów

Możesz wybrać nazwę i lokalizację projektu, a następnie wybrać pozycję **Utwórz**. Teraz wybierz szablon, który ma być używany dla aplikacji ASP.NET Core. Możesz wybrać z następujących opcji:

- Ciągiem. Pusty szablon projektu, który umożliwia rozpoczęcie od podstaw.
- Interfejsu API. Najlepsze dla interfejsów API sieci Web.
- Aplikacja sieci Web. Standardowa aplikacja sieci Web ASP.NET Core skompilowana z Razor Pages.
- Aplikacja sieci Web (Model-View-Controller). Standardowa aplikacja sieci Web ASP.NET Core przy użyciu wzorca Model-View-Controller.
- Kątow.
- React.js.
- React.js/Redux.
- Biblioteka klas Razor. Służy do udostępniania zasobów Razor między projektami.

Należy pamiętać, że w przypadku większości szablonów projektu można także wybrać opcję włączenia obsługi platformy Docker, zaznaczając pole. Możesz również dodać obsługę uwierzytelniania, klikając przycisk Zmień uwierzytelnianie. Z tego miejsca możesz wybrać jedną z opcji:

- Brak uwierzytelniania.
- Indywidualne konta użytkowników. Są one przechowywane w bazie danych lokalnych lub opartych na platformie Azure.
- Konta służbowe. Ta opcja używa Active Directory, Azure AD lub Microsoft 365 do uwierzytelniania.
- Uwierzytelnianie systemu Windows. Odpowiednie dla aplikacji intranetowych.

Wybierz szablon standardowej aplikacji sieci Web bez uwierzytelniania i kliknij przycisk **Utwórz**.

![Visual Studio 2019 wybierz opcje projektu ASP.NET Core](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Następne kroki

W następnym filmie wideo dowiesz się więcej na temat pierwszego projektu ASP.NET Core.

[Samouczek: Tworzenie pierwszej aplikacji sieci Web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Zobacz też

- [Samouczek: wprowadzenie do języka C# i ASP.NET Core](tutorial-aspnet-core.md) Bardziej szczegółowy samouczek bez instruktażu wideo

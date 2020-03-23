---
title: ASP.NET podstawowa aplikacja internetowa z programem Entity Framework & visual studio 2019
titleSuffix: ''
description: Jako pierwszy krok przed utworzeniem aplikacji sieci web ASP.NET Core, dowiedz się, jak zainstalować program Visual Studio 2019 za pomocą tego samouczka wideo i instrukcje krok po kroku.
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
ms.openlocfilehash: d900c0f51b14450f38caf06738739daef2549235
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580092"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Samouczek: Tworzenie pierwszej aplikacji core ASP.NET przy użyciu programu Entity Framework w programie Visual Studio 2019

W tym samouczku utworzysz ASP.NET podstawową aplikację sieci web, która używa danych, i wdrożysz ją na platformie Azure. Ten samouczek składa się z następujących kroków:

- [Krok 1: Instalowanie programu Visual Studio 2019](#step-1-install-visual-studio-2019)
- [Krok 2: Tworzenie pierwszej aplikacji sieci web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)
- [Krok 3: Praca z danymi przy użyciu entity framework](tutorial-aspnet-core-ef-step-03.md)
- [Krok 4: Uwidacznianie internetowego interfejsu API z aplikacji ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)
- [Krok 5: Wdrażanie aplikacji ASP.NET Core na platformie Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Krok 1: Instalowanie programu Visual Studio 2019

Dowiedz się, jak zainstalować program Visual Studio 2019 za pomocą tego samouczka wideo i instrukcji krok po kroku. Jeśli program Visual Studio został już zainstalowany, przejdź do [kroku 2: Utwórz pierwszą ASP.NET podstawową aplikację sieci Web](tutorial-aspnet-core-ef-step-02.md).

_Obejrzyj ten klip wideo i postępuj zgodnie z tym, aby zainstalować program Visual Studio i utworzyć pierwszą aplikację ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Pobierz Instalatora

Przejdź do [visualstudio.com,](https://visualstudio.com) aby znaleźć instalatora. Znajdź łącze programu Visual Studio 2019 i kliknij je, aby rozpocząć pobieranie. Aby uzyskać bezpłatną wersję programu Visual Studio, wybierz pozycję Visual Studio Community.

## <a name="start-the-installer"></a>Uruchamianie Instalatora

Po zakończeniu pobierania kliknij przycisk **Uruchom,** aby uruchomić instalator.

![Instalator programu Visual Studio 2019](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Wybieranie obciążeń

Visual Studio może służyć do wielu różnych rodzajów programowania, a obciążenia ułatwiają pobieranie wszystkiego, czego potrzebujesz dla rodzaju aplikacji, które chcesz utworzyć. Na razie **wybierz ASP.NET i web development** oraz **.NET Core — wieloplatformowe** obciążenia programistyczne. Zawsze można ponownie zainstalować instalator później, aby zainstalować dodatkowe obciążenia i składniki.

![Visual Studio 2019 Wybieranie obciążeń](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Instalowanie

Kliknij **pozycję Zainstaluj** i pozwól instalatorowi pobrać i zainstalować program Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>Uruchamianie programu Visual Studio po raz pierwszy

Visual Studio należy uruchomić automatycznie po zakończeniu instalatora. Może zostanie wyświetlony monit o zalogowanie się, co wiąże się z kilkoma ładnymi funkcjami, ale na razie możesz to zrobić później. Następnie możesz wybrać ustawienia motywu i rozwoju. Po dokonaniu tych wyborów będziesz gotowy do rozpoczęcia pierwszego projektu. Kliknij **pozycję Utwórz nowy projekt,** a następnie wybierz pozycję **ASP.NET Podstawowa aplikacja sieci Web**.

![Visual Studio 2019 Tworzenie nowego projektu aplikacji sieci Web ASP.NET Core](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Eksploruj ASP.NET podstawowe typy projektów

Możesz wybrać nazwę i lokalizację projektu, a następnie wybrać pozycję **Utwórz**. Teraz wybierz szablon, którego chcesz użyć dla aplikacji ASP.NET Core. Możesz wybrać z następujących opcji:

- Pusty. Pusty szablon projektu, który pozwala rozpocząć od zera.
- Api. Najlepsze dla internetowych interfejsów API.
- Aplikacja sieci Web. Standardowa aplikacja internetowa ASP.NET Core zbudowana ze strony Razor Pages.
- aplikacji sieci Web (model-view-controller). Standardowa aplikacja sieci web ASP.NET Core przy użyciu wzorca model-kontroler widoku.
- Kątowe.
- React.js.
- React.js / Redux.
- Biblioteka klas razor. Służy do udostępniania zasobów Razor między projektami.

Należy zauważyć, że w przypadku większości szablonów projektu można również włączyć obsługę platformy Docker, zaznaczając pole wyboru. Można również dodać obsługę uwierzytelniania, klikając przycisk zmień uwierzytelnianie. Stamtąd możesz wybrać:

- Brak uwierzytelniania.
- Indywidualne konta użytkowników. Są one przechowywane w lokalnej lub opartej na platformie Azure bazie danych.
- Konta służbowe lub szkolne. Ta opcja używa usługi Active Directory, usługi Azure AD lub Office 365 do uwierzytelniania.
- Uwierzytelnianie systemu Windows. Nadaje się do zastosowań intranetowych.

Wybierz standardowy szablon aplikacji sieci Web bez uwierzytelniania i kliknij przycisk **Utwórz**.

![Visual Studio 2019 Wybierz ASP.NET podstawowe opcje projektu](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Następne kroki

W następnym filmie dowiesz się więcej o pierwszym projekcie ASP.NET Core.

[Samouczek: Tworzenie pierwszej ASP.NET core aplikacji sieci Web](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Zobacz też

- [Samouczek: Wprowadzenie do języka C# i ASP.NET Core](tutorial-aspnet-core.md) Bardziej szczegółowy samouczek bez przewodnika wideo

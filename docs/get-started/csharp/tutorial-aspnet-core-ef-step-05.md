---
title: Krok 5. wdrażanie aplikacji ASP.NET Core na platformie Azure
description: Wdróż aplikację sieci Web ASP.NET Core na platformie Azure za pomocą tego samouczka wideo i instrukcji krok po kroku.
ms.custom: get-started
ms.date: 08/14/2020
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
ms.openlocfilehash: fc0729eccc6f1392561959dcdac0cf13dfc8e04a
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189761"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Krok 5. wdrażanie aplikacji ASP.NET Core na platformie Azure

Wykonaj następujące kroki, aby wdrożyć aplikację ASP.NET Core i jej bazę danych na platformie Azure.

_Obejrzyj ten film wideo i postępuj zgodnie z instrukcjami, aby wdrożyć swoją pierwszą aplikację ASP.NET Core na platformie Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Otwórz projekt

Otwórz aplikację ASP.NET Core w programie Visual Studio 2019. Aplikacja powinna już korzystać z konfiguracji z EF Core i działającego internetowego interfejsu API, zgodnie z konfiguracją w [kroku 4 tej serii samouczków](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

1. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **Publikuj**. W kreatorze **publikowania** wybierz **platformę Azure** jako element docelowy.

   ![Zrzut ekranu przedstawiający Azure App Service 1](media/vs-2019/app-service-screen-1.png)

1. Dla konkretnego obiektu docelowego wybierz **Azure App Service (Windows)**.

   ![Zrzut ekranu przedstawiający Azure App Service 2](media/vs-2019/app-service-screen-2.png)

1. Wybierz pozycję **Utwórz nowy Azure App Service**. Jeśli nie masz jeszcze konta platformy Azure, kliknij przycisk **Utwórz bezpłatne konto platformy Azure** i Ukończ proces rejestracji.

   ![Zrzut ekranu przedstawiający Azure App Service 3](media/vs-2019/app-service-screen-3.png)

1. Określ nazwę i grupę zasobów lub zaakceptuj wartości domyślne, a następnie wybierz pozycję **Utwórz**. Grupa zasobów jest tylko sposobem organizowania powiązanych zasobów na platformie Azure, takich jak usługi, które współpracują z kontami magazynu, magazynami kluczy i bazami danych.

   ![Zrzut ekranu przedstawiający Azure App Service 4](media/vs-2019/app-service-screen-4.png)

1. Wybierz pozycję **Zakończ**. Zasoby są tworzone na platformie Azure, aplikacja zostanie wdrożona, a karta **Publikowanie** zostanie wypełniona informacjami o właśnie utworzonych elementach. Karta **Publikowanie** zawiera przycisk umożliwiający opublikowanie jednego kliknięcia z taką samą konfiguracją, wyświetlenie szczegółów konfiguracji lub dodanie usług, takich jak baza danych.

Teraz Dodaj bazę danych usługi Azure SQL Server.

1. Na karcie **Publikowanie** w obszarze **zależności usługi** obok pozycji **SQL Server baza danych** wybierz pozycję **Konfiguruj**.

1. Na następnym ekranie wybierz **Azure SQL Database**.

   ![Zrzut ekranu przedstawiający ekran Azure SQL Database](media/vs-2019/app-service-azure-sql-db.png)

1. Na ekranie **konfigurowanie SQL Database** wybierz pozycję **Utwórz SQL Database**.

   ![Zrzut ekranu przedstawiający ekran Konfigurowanie SQL Database](media/vs-2019/app-service-azure-sql-db-2.png)

1. Na **Azure SQL Database: Utwórz nowy** ekran Utwórz nowy serwer bazy danych.

   ![Zrzut ekranu Azure SQL Database: Utwórz nowy](media/vs-2019/app-service-azure-sql-db-3.png)

1. Na **SQL Server: Utwórz nowy** ekran, wybierz nazwę i lokalizację, a następnie określ nazwa użytkownika i hasło administratora.

   ![Tworzenie SQL Server platformy Azure w programie Visual Studio 2019](media/vs-2019/app-service-azure-sql-db-overlayed.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Eksplorowanie Azure Portal i hostowanej aplikacji

Po utworzeniu usługi App Service witryna zostanie uruchomiona w przeglądarce. Podczas ładowania można również znaleźć App Service w Azure Portal. Eksplorowanie dostępnych opcji usługi App Service znajdziesz w sekcji **Omówienie** , w której można uruchomić i zatrzymać aplikację.

![Opcje Azure App Service](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Skalowalność

Możesz sprawdzić, czy są dostępne opcje skalowania aplikacji. Skalowanie w górę dotyczy zwiększenia zasobów przyznanych każdemu wystąpieniu, które obsługuje aplikację. Skalowanie w górę dotyczy zwiększenia liczby wystąpień obsługujących aplikację. Możesz skonfigurować Skalowanie automatyczne dla swojej aplikacji, która automatycznie zwiększy liczbę wystąpień używanych do hostowania aplikacji w odpowiedzi na załadowanie, a następnie obniży je po zmniejszeniu obciążenia.

### <a name="security-and-compliance"></a>Zabezpieczenia i zgodność

Kolejną zaletą hostingu aplikacji przy użyciu platformy Azure jest bezpieczeństwo i zgodność. Azure App Service zapewnia zgodność ze standardami ISO, SOC i PCI. Możemy zdecydować się na uwierzytelnianie użytkowników przy użyciu Azure Active Directory lub takich logowań, jak Twitter, Facebook, Google lub Microsoft. Możemy tworzyć ograniczenia adresów IP, zarządzać tożsamościami usług, dodawać domeny niestandardowe i obsługiwać protokół SSL dla aplikacji, a także konfigurować kopie zapasowe za pomocą dostępnych archiwum kopii zawartości, konfiguracji i bazy danych aplikacji. Te funkcje są dostępne w opcjach uwierzytelnianie/autoryzacja, tożsamość, kopie zapasowe i ustawienia protokołu SSL.

### <a name="deployment-slots"></a>Miejsca wdrożenia

Często podczas wdrażania aplikacji istnieje niewielki okres przestoju podczas ponownego uruchamiania aplikacji. Miejsca wdrożenia uniknięcie tego problemu można wdrożyć w osobnym wystąpieniu przejściowym lub w zestawie wystąpień i rozgrzać przed zainstalowaniem ich w środowisku produkcyjnym. Wymiana jest tylko natychmiastowym i bezproblemowym przekierowaniem ruchu. W przypadku wystąpienia problemów w środowisku produkcyjnym po wymianie można zawsze wrócić do ostatniego znanego dobrego stanu produkcji.

## <a name="update-connection-string"></a>Zaktualizuj parametry połączenia

Domyślnie platforma Azure oczekuje połączenia nowej aplikacji z nową bazą danych SQL Server, aby używać parametrów połączenia o nazwie `DefaultConnection` . Obecnie aplikacja utworzona wcześniej w tej serii samouczków używa parametrów połączenia o nazwie `AppDbContext` . Musimy zmienić tę wartość w *appsettings.jsna* i *Startup.cs* , a następnie ponownie wdrożyć aplikację.

## <a name="test-the-app-running-in-azure"></a>Testowanie aplikacji działającej na platformie Azure

Przejdź do ścieżki */Games* , aby móc dodać nową grę i zobaczyć ją na liście. Następnie przejdź do ścieżki */Swagger* i z tego miejsca powinna być możliwe użycie punktów końcowych internetowego interfejsu API, aby upewnić się, że interfejs API aplikacji również działa.

Gratulacje! Ta seria filmów wideo została ukończona.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o tym, jak architektować ASP.NET Core aplikacje za pomocą tych bezpłatnych zasobów.

[Architektura aplikacji ASP.NET Core](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Zobacz też

- [Publikowanie aplikacji ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2&preserve-view=true)
---
title: Krok 5. wdrażanie aplikacji ASP.NET Core na platformie Azure
description: Wdróż aplikację sieci Web ASP.NET Core na platformie Azure za pomocą tego samouczka wideo i instrukcji krok po kroku.
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
ms.openlocfilehash: dc13dbdadb0c9bca25a816b15c5a99039bff454c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77580031"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Krok 5. wdrażanie aplikacji ASP.NET Core na platformie Azure

Wykonaj następujące kroki, aby wdrożyć aplikację ASP.NET Core i jej bazę danych na platformie Azure.

_Obejrzyj ten film wideo i postępuj zgodnie z instrukcjami, aby wdrożyć swoją pierwszą aplikację ASP.NET Core na platformie Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Otwórz projekt

Otwórz aplikację ASP.NET Core w programie Visual Studio 2019. Aplikacja powinna już korzystać z konfiguracji z EF Core i działającego internetowego interfejsu API, zgodnie z konfiguracją w [kroku 4 tej serii samouczków](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **Publikuj**. Pozostaw ustawienia domyślne **App Service** i **Utwórz nowe** , a następnie kliknij przycisk **Publikuj** . Jeśli nie masz jeszcze konta platformy Azure, kliknij przycisk **Utwórz bezpłatne konto platformy Azure** i Ukończ proces rejestracji.

Dodaj SQL Server. Określ nazwę użytkownika i hasło administratora.

![Tworzenie SQL Server platformy Azure w programie Visual Studio 2019](media/vs-2019/vs2019-azure-sql-server.png)

Dodaj Application Insights.

Kliknij przycisk **Utwórz** , aby kontynuować.

![Visual Studio 2019 Utwórz nowy Azure App Service](media/vs-2019/vs2019-azure-create-new-app-service.png)

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

Domyślnie platforma Azure oczekuje połączenia nowej aplikacji z nową bazą danych SQL Server, aby użyć parametrów połączenia o nazwie `DefaultConnection`. Obecnie aplikacja utworzona wcześniej w tej serii samouczków korzysta z parametrów połączenia o nazwie `AppDbContext`. Musimy zmienić ten plik w pliku *appSettings. JSON* i *Startup.cs* , a następnie ponownie wdrożyć aplikację.

## <a name="test-the-app-running-in-azure"></a>Testowanie aplikacji działającej na platformie Azure

Przejdź do ścieżki */Games* , aby móc dodać nową grę i zobaczyć ją na liście. Następnie przejdź do ścieżki */Swagger* i z tego miejsca powinna być możliwe użycie punktów końcowych internetowego interfejsu API, aby upewnić się, że interfejs API aplikacji również działa.

Gratulacje! Ta seria filmów wideo została ukończona.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o tym, jak architektować ASP.NET Core aplikacje za pomocą tych bezpłatnych zasobów.

[Architektura aplikacji ASP.NET Core](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Zobacz też

- [Publikowanie aplikacji ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)
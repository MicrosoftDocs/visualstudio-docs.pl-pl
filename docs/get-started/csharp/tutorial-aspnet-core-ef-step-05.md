---
title: Krok 5. Wdrażanie aplikacji platformy ASP.NET Core na platformie Azure
description: Wdrażanie aplikacji sieci Web platformy ASP.NET Core na platformie Azure za pomocą tego samouczka wideo, a instrukcje krok po kroku.
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
ms.openlocfilehash: 50f9fec9168c2a7aacfcca8d96501997e6db936d
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58859152"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Krok 5. Wdrażanie aplikacji platformy ASP.NET Core na platformie Azure

Wykonaj następujące kroki, aby wdrożyć aplikację ASP.NET Core i jego bazy danych na platformie Azure.

_Obejrzyj ten film wideo i kontynuować pracę, aby wdrożyć swoją pierwszą aplikację ASP.NET Core na platformie Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Otwórz projekt

Otwórz aplikację platformy ASP.NET Core w programie Visual Studio 2019 r. Aplikacja powinna już być przy użyciu zestawu przy użyciu programu EF Core i pracy internetowego interfejsu API, zgodnie z konfiguracją w [krok 4 z tej serii samouczków](tutorial-aspnet-core-ef-step-04.md)

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **Publikuj**. Pozostaw domyślne ustawienie opcji **usługi App Service** i **Utwórz nowy** i kliknij przycisk **Publikuj** przycisku. Jeśli nie masz jeszcze konta platformy Azure, kliknij przycisk **Utwórz bezpłatne konto Azure** i ukończyć proces rejestracji krótki.

Dodaj serwer SQL. Określ nazwę użytkownika administratora i hasło.

![Visual Studio 2019 Tworzenie serwera usługi Azure SQL](media/vs-2019/vs2019-azure-sql-server.png)

Dodaj usługę Application Insights.

Kliknij przycisk **Utwórz** przycisk, aby kontynuować.

![2019 usługi Visual Studio Utwórz nową usługę Azure App Service](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Eksplorowanie witryny Azure portal i hostowanej aplikacji

Po utworzeniu usługi app service witryny zostanie uruchomiony w przeglądarce. Podczas wczytywania można również znaleźć usługi App Service w witrynie Azure portal. Eksplorowanie dostępne opcje usługi app Service znajdziesz **Przegląd** sekcji, w którym można uruchomić i zatrzymać aplikacji.

![Opcje usługi Azure App Service](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Skalowalność

Można sprawdzić opcje również jako się skalować aplikację. Skalowanie w górę odnosi się do zwiększenia zasobów do każdego wystąpienia hostującego twoją aplikację. Skalowanie w poziomie odnosi się do zwiększenia liczby wystąpień hostującego twoją aplikację. Skalowanie automatyczne można skonfigurować dla aplikacji, która automatycznie zwiększać liczbę wystąpień używanych do hostowania tej aplikacji w taki sposób, w odpowiedzi na obciążenia, a następnie zmniejszyć, gdy zmniejszyło się obciążenie.

### <a name="security-and-compliance"></a>Zabezpieczenia i zgodność

Inną zaletą hostowania naszej aplikacji korzystających z platformy Azure jest zabezpieczeń i zgodności. Usługa Azure App Service zapewnia zgodności ISO, SOC i PCI. Firma Microsoft możliwość uwierzytelniania użytkowników za pomocą usługi Azure Active Directory lub społecznościowych nazw logowania, takich jak Twitter, Facebook, Google i Microsoft. Firma Microsoft można utworzyć ograniczenia adresów IP, Zarządzaj tożsamościami usługi, dodawać domeny niestandardowe i obsługi protokołu SSL dla aplikacji, a także skonfigurować kopie zapasowe przy użyciu przywrócenia archiwizowane kopie zawartości aplikacji, konfiguracji i bazy danych. Te funkcje są dostępne w przypadku uwierzytelniania / autoryzacji, tożsamość, kopie zapasowe i ustawienia protokołu SSL opcji menu.

### <a name="deployment-slots"></a>Miejsca wdrożenia

Często podczas wdrażania aplikacji, ma mały okres przestoju podczas ponownym uruchomieniu aplikacji. Miejsca wdrożenia uniknąć tego problemu, umożliwiając wdrażanie do oddzielnego wystąpienia przejściowego lub zestaw wystąpień i przećwiczeniu podstawowych zadań je przed ich wymianą produkcji. Wymiany jest po prostu przekierowywanie ruchu błyskawiczne i bezproblemowe. Jeśli występują problemy w środowisku produkcyjnym po zakończeniu wymiany, zawsze można wymienić usługi ostatni stan znane dobre produkcji.

## <a name="update-connection-string"></a>Aktualizowanie parametrów połączenia

Domyślnie platforma Azure oczekuje połączenia nowej aplikacji do jego nowej bazy danych programu SQL Server, aby użyć parametrów połączenia o nazwie `DefaultConnection`. Obecnie aplikacja utworzonego wcześniej w tej serii samouczków używa parametrów połączenia o nazwie `AppDbContext`. Trzeba zmienić ją na *appsettings.json* i *Startup.cs* i następnie ponownie wdrożyć aplikację.

## <a name="test-the-app-running-in-azure"></a>Testowanie aplikacji działających na platformie Azure

Przejdź do */gry* ścieżki i powinno być możliwe dodawanie nowych gier i jest widoczny na liście. Następnie przejdź do */swagger* ścieżki i powinien móc Użyj punkty końcowe interfejsu API sieci web w tym miejscu, aby potwierdzić, działa także aplikacji interfejsu API.

Gratulacje! Ukończono tę serię samouczków wideo!

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej na temat architektury aplikacji platformy ASP.NET Core przy użyciu tych bezpłatnych zasobów.

[Architektury aplikacji platformy ASP.NET Core](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Zobacz także

- [Publikowanie aplikacji platformy ASP.NET Core na platformie Azure z programem Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)
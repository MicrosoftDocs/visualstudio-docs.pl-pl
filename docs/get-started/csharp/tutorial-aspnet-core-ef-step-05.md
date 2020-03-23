---
title: 'Krok 5: Wdrażanie aplikacji ASP.NET Core na platformie Azure'
description: Wdrażanie ASP.NET core aplikacji sieci Web na platformie Azure za pomocą tego samouczka wideo i instrukcji krok po kroku.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580031"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Krok 5: Wdrażanie aplikacji ASP.NET Core na platformie Azure

Wykonaj następujące kroki, aby wdrożyć aplikację ASP.NET Core i jej bazę danych na platformie Azure.

_Obejrzyj ten klip wideo i postępuj zgodnie z tym, aby wdrożyć pierwszą aplikację ASP.NET Core na platformie Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Otwórz swój projekt

Otwórz aplikację ASP.NET Core w programie Visual Studio 2019. Aplikacja powinna już używać konfiguracji z EF Core i działającym interfejsem API sieci web, zgodnie z konfiguracją w [kroku 4 tej serii samouczków](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz pozycję **Publikuj**. Pozostaw domyślne ustawienia **usługi App Service** i **Utwórz nowy** i kliknij przycisk **Publikuj.** Jeśli nie masz jeszcze konta platformy Azure, kliknij **pozycję Utwórz bezpłatne konto platformy Azure** i zakończ krótki proces rejestracji.

Dodaj program SQL Server. Określ nazwę użytkownika i hasło administratora.

![Program Visual Studio 2019 tworzenie programu Azure SQL Server](media/vs-2019/vs2019-azure-sql-server.png)

Dodaj wgląd w aplikacje.

Kliknij przycisk **Utwórz,** aby kontynuować.

![Visual Studio 2019 Tworzenie nowej usługi aplikacji platformy Azure](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Eksplorowanie portalu Platformy Azure i hostowanych aplikacji

Po utworzeniu usługi aplikacji witryna zostanie uruchomiona w przeglądarce. Podczas ładowania można również znaleźć usługę app service w witrynie Azure portal. Eksplorując dostępne opcje usługi aplikacji, znajdziesz sekcję **Przegląd,** w której możesz uruchomić i zatrzymać aplikację.

![Opcje usługi azure app service](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Skalowalność

Można zbadać opcje skalowania aplikacji w górę, jak również na zewnątrz. Skalowanie w górę odnosi się do zwiększenia zasobów podanych do każdego wystąpienia hosting aplikacji. Skalowanie w poziomie odnosi się do zwiększenia liczby wystąpień hostujących aplikację. Można skonfigurować skalowanie automatyczne dla aplikacji, co automatycznie zwiększy liczbę wystąpień używanych do hosta aplikacji w odpowiedzi na obciążenie, a następnie zmniejszyć je po zmniejszeniu obciążenia.

### <a name="security-and-compliance"></a>Bezpieczeństwo i zgodność

Kolejną zaletą hostowania naszej aplikacji przy użyciu platformy Azure jest bezpieczeństwo i zgodność. Usługa Azure App Service zapewnia zgodność z zasadami ISO, SOC i PCI. Możemy wybrać uwierzytelnienie użytkowników za pomocą usługi Azure Active Directory lub loginów społecznościowych, takich jak Twitter, Facebook, Google lub Microsoft. Możemy tworzyć ograniczenia adresów IP, zarządzać tożsamościami usług, dodawać domeny niestandardowe i obsługiwać protokół SSL dla aplikacji, a także konfigurować kopie zapasowe za pomocą kopii archiwalnych, które można przywrócić, że zawartość, konfiguracja i baza danych aplikacji można je przywrócić. Te funkcje są dostępne w opcjach menu Uwierzytelnianie / Autoryzacja, Tożsamość, kopie zapasowe i Ustawienia SSL.

### <a name="deployment-slots"></a>Miejsca wdrożenia

Często podczas wdrażania aplikacji, istnieje niewielki okres przestojów podczas ponownego uruchamiania aplikacji. Gniazda wdrażania uniknąć tego problemu, umożliwiając wdrożenie do oddzielnego wystąpienia przemieszczania lub zestaw wystąpień i ogrzać je przed zamianą ich do środowiska produkcyjnego. Zamiana jest tylko natychmiastowe i bezproblemowe przekierowanie ruchu. Jeśli istnieją jakiekolwiek problemy w produkcji po zamianie, zawsze można zamienić z powrotem do ostatniego znanego stanu produkcji dobrego.

## <a name="update-connection-string"></a>Aktualizowanie ciągu połączenia

Domyślnie platforma Azure oczekuje, że połączenie nowej aplikacji z nową bazą danych programu SQL Server będzie używać ciągu połączenia o nazwie `DefaultConnection`. Obecnie aplikacja, którą utworzyliśmy wcześniej w tej `AppDbContext`serii samouczków używa ciągu połączenia o nazwie . Musimy to zmienić w *appsettings.json* i *Startup.cs* a następnie ponownie wdrożyć aplikację.

## <a name="test-the-app-running-in-azure"></a>Testowanie aplikacji uruchomionej na platformie Azure

Przejdź do ścieżki */Games* i powinieneś być w stanie dodać nową grę i zobaczyć ją na liście. Następnie przejdź do *ścieżki /swagger* i powinieneś być w stanie użyć punktów końcowych interfejsu API sieci web stamtąd, aby potwierdzić, że interfejs API aplikacji działa również.

Gratulacje! Ukończyłeś tę serię samouczków wideo!

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o tym, jak projektować ASP.NET aplikacje Core za pomocą tych bezpłatnych zasobów.

[ASP.NET architektura aplikacji podstawowych](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Zobacz też

- [Publikowanie aplikacji ASP.NET Core na platformie Azure za pomocą programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)
---
title: Jak migrować i publikowanie aplikacji sieci Web w usłudze w chmurze platformy Azure
description: Dowiedz się, jak migrować i publikowanie aplikacji sieci web w usłudze w chmurze platformy Azure przy użyciu programu Visual Studio
author: ghogen
manager: jillfra
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: b889c6bd8b23dd49b5fd550a69b2678d6c9b09db
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967305"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Instrukcje: Migrowanie i publikowanie aplikacji internetowej w usłudze w chmurze platformy Azure z poziomu programu Visual Studio

Aby móc korzystać z usług hostingu i możliwości skalowania platformy Azure, możesz chcieć migrację i wdrażanie aplikacji sieci web w usłudze w chmurze platformy Azure. Wymagane są tylko minimalne zmiany. W tym artykule opisano wdrażanie usług w chmurze. usługi App Service, zobacz [wdrażanie aplikacji sieci web w usłudze Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Ta migracja jest obsługiwana tylko w przypadku określonych projektów programu ASP.NET, Silverlight, WCF i przepływu pracy WCF. Nie jest obsługiwana dla projektów ASP.NET Core. Zobacz [obsługiwane szablony projektów](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migracja projektu z usługami w chmurze

1. Kliknij prawym przyciskiem myszy projekt aplikacji sieci web, a następnie wybierz pozycję **przekonwertować > Konwertuj na projekt usługi w chmurze Microsoft Azure**. (Zwróć uwagę, że to polecenie nie jest wyświetlane, jeśli masz już projektu roli sieć web w rozwiązaniu).
1. Visual Studio tworzy projekt usługi w chmurze w rozwiązaniu, które zawiera rolę sieci web. Nazwa tego projektu jest taka sama jak projektu aplikacji na platformie oraz sufiks `.Azure`.
1. Program Visual Studio ustawia również **Kopiuj lokalnie** właściwości na wartość true dla wszystkich zestawów, które są wymagane dla MVC 2 MVC 3, MVC 4 i aplikacji biznesowych Silverlight. Właściwość ta dodaje te zestawy do pakietu usług, która jest używana do wdrażania.

   > [!Important]
   > Jeśli masz inne zespoły lub pliki, które są wymagane dla tej aplikacji sieci web, należy ręcznie ustawić właściwości dla tych plików. Aby uzyskać informacje o sposobie ustawiania tych właściwości, zobacz [uwzględnianie plików w pakiecie usługi](#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Błędy i ostrzeżenia

Wszelkie ostrzeżenia lub błędy, które występują wskazują na problemy, aby naprawić przed przystąpieniem do wdrażania na platformie Azure, takie jak brak zestawy.

Tworzenie aplikacji, uruchomić go lokalnie za pomocą emulatora obliczeń lub opublikować go na platformie Azure może zostać wyświetlony błąd: "Określoną ścieżkę i/lub nazwa pliku jest zbyt długa." Ten błąd wskazuje, że długość nazwy FQDN projekt platformy Azure przekracza 146 znaków. Aby rozwiązać ten problem, należy przenieść swoje rozwiązanie do innego folderu o krótszej ścieżce.

Aby uzyskać więcej informacji na temat Traktuj ostrzeżenia jako błędy, zobacz [Konfigurowanie projektu usługi w chmurze platformy Azure przy użyciu programu Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Testowania migracji lokalnie

1. W programie Visual Studio **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt usługi w chmurze dodano i wybierz **Ustaw jako projekt startowy**.
1. Wybierz **Debuguj > Rozpocznij debugowanie** (F5), można uruchomić debugowania środowiska platformy Azure. To środowisko zawiera specjalnie emulacji różne usługi platformy Azure.

### <a name="use-an-azure-sql-database-for-your-application"></a>Użyj usługi Azure SQL Database dla aplikacji

Jeśli masz parametry połączenia dla aplikacji sieci web, która korzysta z lokalnej bazy danych programu SQL Server, należy zamiast tego migracja bazy danych do usługi Azure SQL Database i aktualizowanie parametrów połączenia. Wskazówki dotyczące tego procesu można znaleźć w następujących tematach:

- [Migracja bazy danych programu SQL Server do bazy danych SQL w chmurze](/azure/sql-database/sql-database-cloud-migrate)
- [.NET (C#) za pomocą programu Visual Studio do nawiązywania połączeń i zapytań i bazy danych Azure SQL](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Publikowanie aplikacji w usłudze w chmurze platformy Azure

1. Tworzenie chmury niezbędnych kont magazynu i usługi w subskrypcji platformy Azure, zgodnie z opisem na [przygotować się do publikowania lub wdrażania aplikacji platformy Azure z programu Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. W programie Visual Studio, kliknij prawym przyciskiem myszy projekt aplikacji, a następnie wybierz **publikowanie w usłudze Microsoft Azure...**  (jest to różni się od polecenie "Publikuj...".).
1. W **publikowanie aplikacji platformy Azure** wyświetlany, zaloguj się przy użyciu konta z subskrypcją platformy Azure, a następnie wybierz pozycję **Dalej >**.
1. W **Ustawienia > typowe ustawienia** , a następnie wybierz docelową usługę w chmurze z **usługi w chmurze** listy rozwijanej, wraz z konfiguracjami oraz wybranego środowiska.
1. W **Ustawienia > Ustawienia zaawansowane**, wybierz konto magazynu do użycia, a następnie wybierz **Dalej >**.
1. W **diagnostyki**, określ, czy chcesz wysłać informacje do usługi Application Insights.
1. Wybierz **Dalej >** można wyświetlić podsumowanie, następnie wybierz pozycję **Publikuj** rozpocząć wdrażanie.
1. Program Visual Studio zostanie otwarte okno Dziennik aktywności, gdzie możesz śledzić postęp:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (Opcjonalnie) Aby anulować proces wdrażania, kliknij prawym przyciskiem myszy pozycji w dzienniku aktywności, a następnie wybierz **Anuluj i Usuń**. To polecenie powoduje zatrzymanie procesu wdrażania i usuwa środowisko wdrażania na platformie Azure. Uwaga: Aby usunąć to środowisko wdrażania po jej wdrożeniu, należy użyć [witryny Azure portal](https://portal.azure.com).
1. (Opcjonalnie) Po rozpoczęciu mają wystąpień roli, Visual Studio automatycznie wyświetla środowisko wdrażania w **Eksplorator serwera > usługi w chmurze** węzła. W tym miejscu możesz wyświetlić stan poszczególne wystąpienia ról.
1. Uzyskiwanie dostępu do aplikacji po wdrożeniu, wybierz strzałkę znajdującą się obok danego wdrożenia, gdy stan **Ukończono** pojawia się w **dziennik aktywności platformy Azure** wraz z adresu URL. Zobacz poniższą tabelę, aby uzyskać szczegółowe informacje o tym, jak uruchomić określonego typu aplikacji sieci web na platformie Azure.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Przy użyciu emulatora obliczeń i uruchamiania aplikacji na platformie Azure

Wszystkie typy aplikacji, które można uruchomić w przeglądarce, na połączenie debugera programu Visual Studio przez wybranie **Debuguj > Rozpocznij debugowanie** (F5). Z projektem pusta aplikacja sieci Web platformy ASP.NET, należy najpierw dodać `.aspx` strony w aplikacji, a następnie ustawić ją jako stronę początkową dla projektu sieci web.

Poniższa tabela zawiera szczegółowe informacje dotyczące uruchamiania aplikacji na platformie Azure:

   | Typ aplikacji sieci Web | Uruchamianie na platformie Azure |
   | --- | --- | --- |
   | Aplikacja internetowa platformy ASP.NET<br/>(w tym MVC 2 MVC 3, MVC 4) | Wybierz adres URL w **wdrożenia** karta **dziennik aktywności platformy Azure**. |
   | ASP.NET pusta aplikacja sieci Web | Jeśli masz domyślny `.aspx` strony w aplikacji, wybierz adres URL w **wdrożenia** karta **dziennik aktywności platformy Azure**. Aby przejść do innej strony, wprowadź następujący adres URL w przeglądarce: `<deployment_url>/<page_name>.aspx` |
   | Aplikacja Silverlight<br/>Aplikacji biznesowych Silverlight<br/>Aplikacja nawigacji Silverlight | Przejdź do określonej strony aplikacji przy użyciu następującej postaci adresu URL: `<deployment_url>/<page_name>.aspx` |
    Aplikacja usługi WCF<br/>Aplikacja usługi przepływu pracy WCF | Ustaw `.svc` pliku jako stronę startową w projekcie usługi WCF. Następnie przejdź do `<deployment_url>/<service_file>.svc` |
   | ASP.NET Dynamic jednostek<br/>ASP.NET Dynamic Data Linq do SQL | Zaktualizuj parametry połączenia, zgodnie z opisem w następnej sekcji. Następnie przejdź do `<deployment_url>/<page_name>.aspx`. Dla programu Linq to SQL należy użyć usługi Azure SQL database. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Zaktualizuj parametry połączenia dla jednostek dynamiczne ASP.NET

1. Utwórz bazę danych SQL Azure dla aplikacji sieci web ASP.NET dynamicznej jednostki, zgodnie z opisem we wcześniejszej części (#use-an-azuresql-database-for-your-application).
1. Dodawanie tabel i pól, które są potrzebne dla tej bazy danych w witrynie Azure portal.
1. Określ parametry połączenia w `web.config` pliku w następującym formacie, a następnie zapisz plik:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    Aktualizacja *connectionString* wartość przy użyciu parametrów połączenia ADO.NET dla bazy danych SQL Azure w następujący sposób:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Szablony projektów obsługiwane

Aplikacje, które mogą być migrowane i opublikowane do usług w chmurze, należy użyć jednego z szablonów w poniższej tabeli. Platforma ASP.NET Core nie jest obsługiwane.

| Grupa szablonów | Szablon projektu |
| --- | --- |
| sieć Web | Aplikacja sieci Web platformy ASP.NET (.NET Framework) |
| sieć Web | Aplikacja sieci Web platformy ASP.NET MVC 2 |
| sieć Web | Aplikacja sieci Web platformy ASP.NET MVC 3 |
| sieć Web | Aplikacja sieci Web ASP.NET MVC4 |
| sieć Web | ASP.NET pusta aplikacja sieci Web (lub witryny) |
| sieć Web | Aplikacja pusty sieci Web platformy ASP.NET MVC 2 |
| sieć Web | Aplikacja sieci Web ASP.NET Dynamic Data Entities |
| sieć Web | ASP.NET Dynamic Data Linq do aplikacji sieci Web SQL |
| Silverlight | Aplikacja Silverlight |
| Silverlight | Aplikacji biznesowych Silverlight |
| Silverlight | Aplikacja nawigacji Silverlight |
| WCF | Aplikacja usługi WCF |
| WCF | Aplikacja usługi przepływu pracy WCF |
| Przepływ pracy | Aplikacja usługi przepływu pracy WCF |

## <a name="next-steps"></a>Następne kroki

- [Przygotowanie do publikowania lub wdrażania aplikacji platformy Azure z programu Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Konfigurowanie o nazwie poświadczenia uwierzytelniania](vs-azure-tools-setting-up-named-authentication-credentials.md).

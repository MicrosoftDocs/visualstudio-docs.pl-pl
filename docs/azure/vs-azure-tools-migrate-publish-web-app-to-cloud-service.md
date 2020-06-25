---
title: Migrowanie & publikowanie aplikacji sieci Web w usłudze w chmurze platformy Azure
description: Dowiedz się, jak przeprowadzić migrację i publikowanie aplikacji sieci Web w usłudze w chmurze platformy Azure przy użyciu programu Visual Studio
author: ghogen
manager: jillfra
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c95c96815872c259cab761d8b4af36141f866dbd
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280560"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Instrukcje: Migrowanie i publikowanie aplikacji sieci Web w usłudze w chmurze platformy Azure z poziomu programu Visual Studio

Aby skorzystać z usług hostingowych i możliwości skalowania platformy Azure, możesz chcieć migrować i wdrożyć aplikację sieci Web w usłudze w chmurze platformy Azure. Tylko minimalne zmiany są wymagane. W tym artykule opisano wdrażanie tylko w usługach Cloud Services. Aby uzyskać App Service, zobacz [wdrażanie aplikacji sieci Web w programie Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Ta migracja jest obsługiwana tylko dla określonych projektów przepływu pracy w programie ASP.NET, WCF i WCF. Nie jest ona obsługiwana w projektach ASP.NET Core. Zobacz [obsługiwane szablony projektów](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migrowanie projektu do usług w chmurze

1. Kliknij prawym przyciskiem myszy węzeł rozwiązanie i wybierz polecenie **dodaj > nowy projekt...** i Dodaj nowy projekt **usługi Azure Cloud Service (klasyczny)** do istniejącego rozwiązania.
1. W oknie dialogowym **nowy Microsoft Azure usługa w chmurze (klasyczna)** kliknij przycisk OK bez dodawania ról do projektu.
1. Kliknij prawym przyciskiem myszy węzeł role w nowo dodanym projekcie Cloud Services i wybierz polecenie **Dodaj projekt roli sieci Web w rozwiązaniu...**.
1. W oknie dialogowym **kojarzenie z rolą projektu** wybierz projekt, który chcesz skojarzyć jako rolę sieci Web.

   > [!Important]
   > Jeśli masz inne zestawy lub pliki, które są wymagane dla tej aplikacji sieci Web, musisz ręcznie ustawić właściwości tych plików. Aby uzyskać informacje na temat sposobu ustawiania tych właściwości, zobacz [Dołączanie plików w pakiecie usługi](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Błędy i ostrzeżenia

Wszelkie ostrzeżenia lub błędy wskazujące problemy, które należy rozwiązać przed wdrożeniem na platformie Azure, takie jak brakujące zestawy.

Jeśli tworzysz aplikację, uruchom ją lokalnie przy użyciu emulatora obliczeń lub opublikuj ją na platformie Azure, ale może zostać wyświetlony następujący błąd: "określona ścieżka, nazwa pliku lub obie są zbyt długie". Ten błąd wskazuje, że długość w pełni kwalifikowanej nazwy projektu platformy Azure przekracza 146 znaków. Aby rozwiązać ten problem, Przenieś rozwiązanie do innego folderu o krótszej ścieżce.

Aby uzyskać więcej informacji o sposobie traktowania ostrzeżeń jako błędów, zobacz [Konfigurowanie projektu usługi w chmurze platformy Azure za pomocą programu Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Testowanie migracji lokalnie

1. W programie Visual Studio **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy dodany projekt usługi w chmurze i wybierz pozycję **Ustaw jako projekt startowy**.
1. Wybierz pozycję **debuguj > Rozpocznij debugowanie** (F5), aby uruchomić środowisko debugowania platformy Azure. Środowisko to zapewnia emulację różnych usług platformy Azure.

### <a name="use-an-azure-sql-database-for-your-application"></a>Użyj Azure SQL Database aplikacji

Jeśli masz parametry połączenia dla aplikacji sieci Web, która używa lokalnej bazy danych SQL Server, musisz przeprowadzić migrację bazy danych do Azure SQL Database zamiast tego i zaktualizować parametry połączenia. Aby uzyskać wskazówki dotyczące tego procesu, zapoznaj się z następującymi tematami:

- [Migracja bazy danych programu SQL Server do usługi SQL Database w chmurze](/azure/sql-database/sql-database-cloud-migrate)
- [Użyj platformy .NET (C#) z programem Visual Studio, aby nawiązać połączenie i wykonywać zapytania i usługi Azure SQL Database](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Publikowanie aplikacji w usłudze w chmurze platformy Azure

1. Utwórz niezbędne konta usług w chmurze i magazynu w ramach subskrypcji platformy Azure zgodnie z opisem w artykule [Przygotowywanie do opublikowania lub wdrożenia aplikacji platformy Azure z poziomu programu Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. W programie Visual Studio kliknij prawym przyciskiem myszy projekt aplikacji i wybierz polecenie **Publikuj do Microsoft Azure...** (co różni się od "publikowanie..." polecenie.).
1. W wyświetlonym obszarze **publikowanie aplikacji platformy Azure** Zaloguj się przy użyciu konta z subskrypcją platformy Azure i wybierz pozycję **dalej >**.
1. Na karcie **ustawienia > wspólne ustawienia** wybierz docelową usługę w chmurze z listy rozwijanej **Usługa w chmurze** wraz z wybranym środowiskiem i konfiguracjami.
1. W obszarze **ustawienia > ustawienia zaawansowane**wybierz konto magazynu, które ma być używane, a następnie wybierz pozycję **dalej >**.
1. W obszarze **Diagnostyka**wybierz, czy chcesz wysyłać informacje do Application Insights.
1. Wybierz pozycję **dalej >** , aby wyświetlić podsumowanie, a następnie wybierz pozycję **Publikuj** , aby rozpocząć wdrażanie.
1. Program Visual Studio otwiera okno dziennika aktywności, w którym można śledzić postęp:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. Obowiązkowe Aby anulować proces wdrażania, kliknij prawym przyciskiem myszy element wiersza w dzienniku aktywności, a następnie wybierz polecenie **Anuluj i Usuń**. To polecenie powoduje zatrzymanie procesu wdrażania i usunięcie środowiska wdrażania z platformy Azure. Uwaga: Aby usunąć to środowisko wdrażania po jego wdrożeniu, należy użyć [Azure Portal](https://portal.azure.com).
1. Obowiązkowe Po rozpoczęciu wystąpień roli program Visual Studio automatycznie wyświetli środowisko wdrożenia w węźle **Eksplorator serwera > Cloud Services** . W tym miejscu można wyświetlić stan poszczególnych wystąpień ról.
1. Aby uzyskać dostęp do aplikacji po wdrożeniu, wybierz strzałkę obok swojego wdrożenia, gdy w **dzienniku aktywności platformy Azure** zostanie wyświetlony stan **ukończono** wraz z adresem URL. Zapoznaj się z poniższą tabelą, aby uzyskać szczegółowe informacje na temat uruchamiania określonego typu aplikacji sieci Web z platformy Azure.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Korzystanie z emulatora obliczeń i uruchamiania aplikacji na platformie Azure

Wszystkie typy aplikacji można uruchomić w przeglądarce połączonej z debugerem programu Visual Studio, wybierając pozycję **debuguj > Rozpocznij debugowanie** (F5). Mając ASP.NET pusty projekt aplikacji sieci Web, musisz najpierw dodać `.aspx` stronę do aplikacji i ustawić ją jako stronę początkową dla projektu sieci Web.

Poniższa tabela zawiera szczegółowe informacje na temat uruchamiania aplikacji na platformie Azure:

| Typ aplikacji sieci Web | Uruchamianie na platformie Azure |
| --- | --- |
| Aplikacja sieci Web ASP.NET<br/>(w tym MVC 2, MVC 3, MVC 4) | Wybierz adres URL na karcie **wdrożenie** dla **dziennika aktywności platformy Azure**. |
| ASP.NET pustą aplikację sieci Web | Jeśli w aplikacji znajduje się `.aspx` strona domyślna, wybierz adres URL na karcie **wdrożenie** dla **dziennika aktywności platformy Azure**. Aby przejść do innej strony, wprowadź w przeglądarce adres URL następującej postaci:`<deployment_url>/<page_name>.aspx` |
| Aplikacja usługi WCF<br/>Aplikacja usługi przepływu pracy WCF | Ustaw `.svc` plik jako stronę początkową dla projektu usługi WCF. Następnie przejdź do`<deployment_url>/<service_file>.svc` |
| Jednostki dynamiczne ASP.NET<br/>ASP.NET dynamiczne dane LINQ do SQL | Zaktualizuj parametry połączenia zgodnie z opisem w następnej sekcji. Następnie przejdź do `<deployment_url>/<page_name>.aspx` . W przypadku składnika LINQ to SQL należy użyć bazy danych SQL Azure. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Aktualizowanie parametrów połączenia dla obiektów dynamicznych ASP.NET

1. Utwórz bazę danych SQL Azure dla aplikacji sieci Web ASP.NET jednostki dynamiczne zgodnie z wcześniejszym opisem w temacie (#use-a-azuresql-Database-for-Application
1. Dodaj tabele i pola, które są potrzebne dla tej bazy danych, z Azure Portal.
1. Określ parametry połączenia w `web.config` pliku o następującym formacie i Zapisz plik:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    Zaktualizuj wartość *ConnectionString* przy użyciu parametrów połączenia ADO.NET dla bazy danych SQL Azure w następujący sposób:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Obsługiwane szablony projektów

Aplikacje, które mogą zostać zmigrowane i opublikowane w usługach w chmurze, muszą używać jednego z szablonów w poniższej tabeli. ASP.NET Core nie jest obsługiwana.

| Grupa szablonów | Szablon projektu |
| --- | --- |
| Sieć Web | Aplikacja sieci Web ASP.NET (.NET Framework) |
| Sieć Web | ASP.NET aplikacji sieci Web MVC 2 |
| Sieć Web | Aplikacja sieci Web ASP.NET MVC 3 |
| Sieć Web | Aplikacja sieci Web ASP.NET MVC4 |
| Sieć Web | ASP.NET pustą aplikację sieci Web (lub lokację) |
| Sieć Web | ASP.NETą pustą aplikację sieci Web MVC 2 |
| Sieć Web | Aplikacja sieci Web ASP.NET dynamiczne jednostki danych |
| Sieć Web | ASP.NET dynamiczne dane LINQ do aplikacji sieci Web SQL |
| WCF | Aplikacja usługi WCF |
| WCF | Aplikacja usługi przepływu pracy WCF |
| Przepływ pracy | Aplikacja usługi przepływu pracy WCF |

## <a name="next-steps"></a>Następne kroki

- [Przygotowanie do opublikowania lub wdrożenia aplikacji platformy Azure z poziomu programu Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Konfigurowanie poświadczeń uwierzytelniania nazwanego](vs-azure-tools-setting-up-named-authentication-credentials.md).

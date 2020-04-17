---
title: Migrowanie & publikowania aplikacji sieci web do usługi Azure Cloud Service
description: Dowiedz się, jak migrować i publikować aplikację sieci web do usługi w chmurze platformy Azure przy użyciu programu Visual Studio
author: ghogen
manager: jillfra
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: a5f918cac9d2b9e97c047e8823d7702768134336
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489678"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Jak: Migrowanie i publikowanie aplikacji sieci Web do usługi Azure Cloud Service z programu Visual Studio

Aby skorzystać z usług hostingu i możliwości skalowania platformy Azure, można przeprowadzić migrację i wdrożyć aplikację sieci web do usługi w chmurze platformy Azure. Wymagane są tylko minimalne zmiany. W tym artykule opisano wdrażanie tylko w usługach w chmurze; dla usługi App Service, zobacz [Wdrażanie aplikacji sieci web w usłudze Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Ta migracja jest obsługiwana tylko dla określonych projektów przepływu pracy ASP.NET, Silverlight, WCF i WCF. Nie jest obsługiwany dla projektów ASP.NET Core. Zobacz [Obsługiwane szablony projektów](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migrowanie projektu do usług w chmurze

1. Kliknij prawym przyciskiem myszy projekt aplikacji sieci Web i wybierz **polecenie Konwertuj > przekonwertuj na usługę w chmurze platformy Microsoft Azure .** (Należy zauważyć, że to polecenie nie jest wyświetlane, jeśli masz już projekt roli sieci web w rozwiązaniu.)
1. Visual Studio tworzy projekt usługi w chmurze w rozwiązaniu, który zawiera wymaganą rolę sieci web. Nazwa tego projektu jest taka sama jak projekt aplikacji `.Azure`z plus sufiks .
1. Visual Studio ustawia również **copy local** właściwość true dla wszystkich zestawów, które są wymagane dla MVC 2, MVC 3, MVC 4 i Silverlight aplikacji biznesowych. Ta właściwość dodaje te zestawy do pakietu usługi, który jest używany do wdrożenia.

   > [!Important]
   > Jeśli masz inne zestawy lub pliki, które są wymagane dla tej aplikacji sieci web, należy ręcznie ustawić właściwości dla tych plików. Aby uzyskać informacje dotyczące sposobu ustawiania tych właściwości, zobacz [Dołączanie plików do pakietu usług](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Błędy i ostrzeżenia

Wszelkie ostrzeżenia lub błędy, które występują wskazują problemy do naprawienia przed wdrożeniem na platformie Azure, takie jak brakujące zestawy.

Jeśli tworzysz aplikację, uruchom ją lokalnie przy użyciu emulatora obliczeniowego lub opublikuj ją na platformie Azure, może zostać wyświetlony błąd: "Określona ścieżka, nazwa pliku lub oba są zbyt długie". Ten błąd wskazuje, że długość w pełni kwalifikowanej nazwy projektu platformy Azure przekracza 146 znaków. Aby rozwiązać ten problem, przenieś rozwiązanie do innego folderu z krótszą ścieżką.

Aby uzyskać więcej informacji na temat traktowania wszystkich ostrzeżeń jako błędów, zobacz [Konfigurowanie projektu usługi Azure Cloud Service w programie Visual Studio.](vs-azure-tools-configuring-an-azure-project.md)

### <a name="test-the-migration-locally"></a>Testowanie migracji lokalnie

1. W **Eksploratorze rozwiązań**programu Visual Studio kliknij prawym przyciskiem myszy dodany projekt usługi w chmurze i wybierz polecenie **Ustaw jako projekt uruchamiania**.
1. Wybierz **debugowanie > Rozpocznij debugowanie** (F5), aby uruchomić środowisko debugowania platformy Azure. To środowisko w szczególności zapewnia emulację różnych usług platformy Azure.

### <a name="use-an-azure-sql-database-for-your-application"></a>Korzystanie z bazy danych SQL azure dla aplikacji

Jeśli masz parametry połączenia dla aplikacji sieci web, która używa lokalnej bazy danych programu SQL Server, należy przeprowadzić migrację bazy danych do usługi Azure SQL Database i zaktualizować parametry połączenia. Aby uzyskać wskazówki dotyczące tego procesu, zapoznaj się z następującymi tematami:

- [Migracja bazy danych programu SQL Server do usługi SQL Database w chmurze](/azure/sql-database/sql-database-cloud-migrate)
- [Użyj platformy .NET (C#) z programem Visual Studio do łączenia się i wykonywania zapytań oraz bazy danych SQL platformy Azure.](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio)

## <a name="publish-the-application-to-azure-cloud-service"></a>Publikowanie aplikacji w usłudze Azure Cloud Service

1. Utwórz niezbędne konta usługi w chmurze i magazynu w ramach subskrypcji platformy Azure, zgodnie z opisem w [programie Prepare, aby opublikować lub wdrożyć aplikację platformy Azure z programu Visual Studio.](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
1. W programie Visual Studio kliknij prawym przyciskiem myszy projekt aplikacji i wybierz polecenie **Publikuj na platformie Microsoft Azure...** (która różni się od "Publikuj..." komenda.).
1. W **wyświetleniu aplikacji platformy Azure publikowania** zaloguj się przy użyciu konta za pomocą subskrypcji platformy Azure i wybierz pozycję **Następna >**.
1. Na karcie **Ustawienia > ustawienia wspólne** wybierz docelową usługę w chmurze z listy rozwijanej Usługi w **chmurze** wraz z wybranym środowiskiem i konfiguracjami.
1. W **obszarze Ustawienia > ustawienia zaawansowane**wybierz konto magazynu, którego chcesz użyć, a następnie wybierz pozycję Następny **>**.
1. W **diagnostyce**wybierz, czy mają być wysyłane informacje do usługi Application Insights.
1. Wybierz **pozycję >,** aby wyświetlić podsumowanie, a następnie wybierz pozycję **Publikuj,** aby rozpocząć wdrażanie.
1. Visual Studio otwiera okno dziennika aktywności, w którym można śledzić postęp:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (Opcjonalnie) Aby anulować proces wdrażania, kliknij prawym przyciskiem myszy element zamówienia w dzienniku aktywności, a następnie wybierz pozycję **Anuluj i usuń**. To polecenie zatrzymuje proces wdrażania i usuwa środowisko wdrażania z platformy Azure. Uwaga: aby usunąć to środowisko wdrażania po jego wdrożeniu, należy użyć [witryny Azure Portal](https://portal.azure.com).
1. (Opcjonalnie) Po uruchomieniu wystąpień roli program Visual Studio automatycznie wyświetla środowisko wdrażania w węźle **Eksplorator serwera > usługi w chmurze.** W tym miejscu można wyświetlić stan poszczególnych wystąpień roli.
1. Aby uzyskać dostęp do aplikacji po wdrożeniu, wybierz strzałkę obok wdrożenia, gdy stan **Zakończone** pojawia się w **dzienniku aktywności platformy Azure** wraz z adresem URL. Zobacz poniższą tabelę, aby uzyskać szczegółowe informacje na temat uruchamiania określonego typu aplikacji sieci web z platformy Azure.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Korzystanie z emulatora obliczeń i uruchamianie aplikacji na platformie Azure

Wszystkie typy aplikacji można uruchomić w przeglądarce połączonej z debugerem programu Visual Studio, wybierając **debugowanie > rozpocznij debugowanie** (F5). W projekcie ASP.NET pustej aplikacji sieci Web należy `.aspx` najpierw dodać stronę w aplikacji i ustawić ją jako stronę początkową dla projektu sieci web.

Poniższa tabela zawiera szczegółowe informacje na temat uruchamiania aplikacji na platformie Azure:

| Typ aplikacji sieci Web | Uruchamianie na platformie Azure |
| --- | --- |
| ASP.NET aplikacji sieci Web<br/>(w tym MVC 2, MVC 3, MVC 4) | Wybierz adres URL na karcie **Wdrażanie** **dziennika aktywności platformy Azure**. |
| ASP.NET pusta aplikacja sieci Web | Jeśli masz domyślną `.aspx` stronę w aplikacji, wybierz adres URL na karcie **Wdrażanie** dziennika aktywności platformy **Azure**. Aby przejść do innej strony, wprowadź adres URL następującego formularza w przeglądarce:`<deployment_url>/<page_name>.aspx` |
| Aplikacja Silverlight<br/>Aplikacja Silverlight Business<br/>Aplikacja nawigacyjna Silverlight | Przejdź do określonej strony aplikacji przy użyciu następującego formularza adresu URL:`<deployment_url>/<page_name>.aspx` |
| Aplikacja usługi WCF<br/>Aplikacja usługi przepływu pracy WCF | Ustaw `.svc` plik jako stronę początkową dla projektu usługi WCF. Następnie przejdź do`<deployment_url>/<service_file>.svc` |
| ASP.NET dynamiczne jednostki<br/>ASP.NET dynamiczne dane Linq do SQL | Zaktualizuj parametry połączenia zgodnie z opisem w następnej sekcji. Następnie przejdź `<deployment_url>/<page_name>.aspx`do pliku . Dla Linq do SQL, należy użyć bazy danych SQL platformy Azure. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Aktualizowanie ciągu połączenia dla ASP.NET elementów dynamicznych

1. Utwórz bazę danych SQL Azure dla aplikacji sieci web ASP.NET jednostek dynamicznych, jak opisano wcześniej w (#use-an-azuresql-database-for-your-application).
1. Dodaj tabele i pola potrzebne dla tej bazy danych z witryny Azure portal.
1. Określ ciąg połączenia `web.config` w pliku w następującym formacie i zapisz plik:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    Zaktualizuj wartość *connectionString* za pomocą ciągu połączenia ADO.NET dla bazy danych SQL Azure w następujący sposób:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Obsługiwane szablony projektów

Aplikacje, które mogą być migrowane i publikowane do usług w chmurze, muszą używać jednego z szablonów w poniższej tabeli. ASP.NET Core nie jest obsługiwany.

| Grupa szablonów | Szablon projektu |
| --- | --- |
| Sieć Web | ASP.NET aplikacji sieci Web (.NET Framework) |
| Sieć Web | ASP.NET aplikacji sieci Web MVC 2 |
| Sieć Web | ASP.NET aplikacji sieci Web MVC 3 |
| Sieć Web | ASP.NET aplikacji sieci Web MVC4 |
| Sieć Web | ASP.NET pusta aplikacja sieci Web (lub witryna) |
| Sieć Web | ASP.NET MVC 2 Pusta aplikacja sieci Web |
| Sieć Web | ASP.NET aplikacji sieci Web dynamicznych jednostek danych |
| Sieć Web | ASP.NET dynamiczne dane Linq do aplikacji sieci Web SQL |
| Silverlight | Aplikacja Silverlight |
| Silverlight | Aplikacja Silverlight Business |
| Silverlight | Aplikacja nawigacyjna Silverlight |
| WCF | Aplikacja usługi WCF |
| WCF | Aplikacja usługi przepływu pracy WCF |
| Przepływ pracy | Aplikacja usługi przepływu pracy WCF |

## <a name="next-steps"></a>Następne kroki

- [Przygotowanie do publikowania lub wdrażania aplikacji platformy Azure z programu Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Konfigurowanie poświadczeń uwierzytelniania nazwanego](vs-azure-tools-setting-up-named-authentication-credentials.md).

---
title: Funkcje zaawansowane
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f65ce2b986114dc553b87db846262c931d74b4c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78235202"
---
# <a name="features-of-visual-studio"></a>Funkcje programu Visual Studio

Artykuł [o pojucie środowiska visual studio](../get-started/visual-studio-ide.md) zawiera podstawowe wprowadzenie do programu Visual Studio. W tym artykule opisano funkcje, które mogą być bardziej odpowiednie dla doświadczonych deweloperów lub tych deweloperów, którzy są już zaznajomieni z programem Visual Studio.

## <a name="modular-installation"></a>Instalacja modułowa

Modułowy instalator programu Visual Studio umożliwia wybór i *zainstalowanie obciążeń.* Obciążenia to grupy funkcji potrzebnych dla preferowanego języka programowania lub platformy. Ta strategia pomaga zachować rozmiar instalacji programu Visual Studio mniejsze, co oznacza, że instaluje i aktualizuje szybciej zbyt.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

Aby dowiedzieć się więcej o konfigurowaniu programu Visual Studio w systemie, zobacz [Instalowanie programu Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Tworzenie aplikacji z obsługą chmury na platformie Azure

Program Visual Studio oferuje zestaw narzędzi, które umożliwiają łatwe tworzenie aplikacji obsługujących chmurę z pomocą platformy Microsoft Azure. Można skonfigurować, tworzyć, debugować, pakować i wdrażać aplikacje i usługi na platformie Microsoft Azure bezpośrednio z IDE. Aby uzyskać narzędzia platformy Azure i szablony projektów, wybierz obciążenie **deweloperskie platformy Azure** podczas instalowania programu Visual Studio.

![Obciążenie programistyczne platformy Azure](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Po zainstalowaniu obciążenia **dewelopera platformy Azure** następujące szablony **chmury** dla języka C# są dostępne w oknie dialogowym **Nowy projekt:**

![Szablony projektów w chmurze dla programu Visual Studio](media/cloud-project-templates.png)

::: moniker-end

Visual Studio [Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) umożliwia wyświetlanie zasobów chmurowych opartych na platformie Azure i zarządzanie nimi w programie Visual Studio. Zasoby te mogą obejmować maszyny wirtualne, tabele, bazy danych SQL i inne. **Cloud Explorer** pokazuje zasoby platformy Azure na wszystkich kontach zarządzanych w ramach subskrypcji platformy Azure, do której jesteś zalogowany. A jeśli określona operacja wymaga witryny Azure portal, **Cloud Explorer** zawiera łącza, które można zabrać do miejsca w portalu, gdzie należy udać.

![Eksplorator chmury w programie Visual Studio](media/cloud-explorer.png)

Możesz korzystać z usług platformy Azure dla aplikacji przy użyciu **usług połączonych,** takich jak:

- [Usługa połączona z usługą Active Directory,](/azure/active-directory/develop/vs-active-directory-add-connected-service) dzięki której użytkownicy mogą korzystać z kont z [usługi Azure Active Directory](/azure/active-directory/active-directory-whatis) do łączenia się z aplikacjami sieci Web
- [Usługa połączona z usługą Azure Storage](/azure/vs-azure-tools-connected-services-storage) dla magazynu obiektów blob, kolejek i tabel
- [Usługa połączona z usługą Key Vault](/azure/key-vault/vs-key-vault-add-connected-service) do zarządzania wpisami tajnymi dla aplikacji sieci Web

Dostępne **usługi połączone** zależą od typu projektu. Dodaj usługę, klikając prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierając **pozycję Dodaj** > **połączoną usługę**.

![Połączone usługi programu Visual Studio](media/connected-services.png)

Aby uzyskać więcej informacji, zobacz [Przenoszenie do chmury za pomocą programu Visual Studio i platformy Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Tworzenie aplikacji dla sieci Web

Sieć web napędza nasz nowoczesny świat, a program Visual Studio może pomóc w pisaniu aplikacji dla niego. Aplikacje internetowe można tworzyć przy użyciu ASP.NET, Node.js, Python, JavaScript i TypeScript. Visual Studio rozumie struktur sieci web, takich jak Angular, jQuery, Express i więcej. ASP.NET Core i .NET Core działają w systemach operacyjnych Windows, Mac i Linux. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) jest główną aktualizacją MVC, WebAPI i SignalR i działa na windows, Mac i Linux.  ASP.NET Core został zaprojektowany od podstaw, aby zapewnić Ci chudego i komponowalny stos .NET do tworzenia nowoczesnych aplikacji i usług internetowych opartych na chmurze.

Aby uzyskać więcej informacji, zobacz [Nowoczesne narzędzia internetowe](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Tworzenie aplikacji i gier między platformami

Za pomocą programu Visual Studio można tworzyć aplikacje i gry dla systemów macOS, Linux i Windows, a także dla systemów Android, iOS i innych [urządzeń przenośnych.](https://visualstudio.microsoft.com/vs/mobile-app-development/)

- Twórz aplikacje [.NET Core,](/dotnet/core/) które działają w systemach Windows, macOS i Linux.

- Tworzenie aplikacji mobilnych dla systemów iOS, Android i Windows w językach C# i F# przy użyciu platformy [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Użyj standardowych&mdash;technologii internetowych HTML, CSS i JavaScript&mdash;do tworzenia aplikacji mobilnych dla systemów iOS, Android i Windows przy użyciu [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/).

- Tworzenie gier 2D i 3D w języku C# przy użyciu [narzędzi visual studio dla unity](../cross-platform/visual-studio-tools-for-unity.md).

- Twórz natywne aplikacje Języka C++ dla urządzeń z systemami iOS, Android i Windows. Udostępnianie wspólnego kodu w bibliotekach utworzonych dla systemów iOS, Android i Windows przy użyciu [języka C++ do tworzenia między platformami](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development).

- Wdrażanie, testowanie i debugowanie aplikacji na Androida za pomocą [emulatora systemu Android](../cross-platform/visual-studio-emulator-for-android.md).

## <a name="connect-to-databases"></a>Łączenie się z bazami danych

**Eksplorator serwera** ułatwia przeglądanie wystąpień i zasobów programu SQL Server i zarządzanie nimi lokalnie, zdalnie oraz na platformie Azure, Salesforce.com, usłudze Office 365 i witrynach sieci Web. Aby otworzyć **program Server Explorer**w menu głównym, wybierz polecenie **Wyświetl** > **Eksploratora serwera**. Aby uzyskać więcej informacji na temat korzystania z Eksploratora serwera, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) to zaawansowane środowisko programistyczne dla programu SQL Server, bazy danych SQL Azure i usługi Azure SQL Data Warehouse. Umożliwia tworzenie, debugowanie, obsługa i refaktoryzowania baz danych. Można pracować z projektem bazy danych lub bezpośrednio z wystąpieniem połączonej bazy danych w siedzibie lub poza nim.

**Eksplorator obiektów programu SQL Server** w programie Visual Studio udostępnia widok obiektów bazy danych podobnych do programu SQL Server Management Studio. SQL Server Object Explorer umożliwia wykonywanie lekkich zadań administracyjnych i projektowych bazy danych. Przykłady pracy obejmują edytowanie danych tabeli, porównywanie schematów, wykonywanie zapytań przy użyciu menu kontekstowych bezpośrednio z Eksploratora obiektów programu SQL Server i innych.

![Eksplorator obiektów SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Debugowanie, testowanie i ulepszanie kodu

Podczas pisania kodu, należy go uruchomić i przetestować go pod kątem błędów i wydajności. Nowatorski system debugowania programu Visual Studio umożliwia debugowanie kodu uruchomionego w projekcie lokalnym, na urządzeniu zdalnym lub [emulatorze urządzenia.](../cross-platform/visual-studio-emulator-for-android.md) Możesz przejść przez kod jedną instrukcję naraz i sprawdzić zmienne w trakcie podróży. Można ustawić punkty przerwania, które są trafione tylko wtedy, gdy określony warunek jest spełniony. Opcje debugowania można zarządzać w samym edytorze kodu, dzięki czemu nie trzeba opuszczać kodu. Aby uzyskać więcej informacji na temat debugowania w programie Visual Studio, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

Aby dowiedzieć się więcej na temat poprawy wydajności aplikacji, wyewidencjonuj funkcję [profilowania](../profiling/profiling-feature-tour.md) programu Visual Studio.

Do [testowania](../test/improve-code-quality.md)program Visual Studio oferuje testowanie jednostkowe, testowanie jednostek na żywo, test intellitest, testowanie obciążenia i wydajności i inne. Visual Studio ma również zaawansowane możliwości [analizy kodu,](../code-quality/code-analysis-for-managed-code-overview.md) aby wychwyć projekt, zabezpieczenia i inne typy wad.

## <a name="deploy-your-finished-application"></a>Wdrażanie gotowego zgłoszenia

Gdy aplikacja jest gotowa do wdrożenia dla użytkowników lub klientów, Visual Studio udostępnia narzędzia, aby to zrobić. Opcje wdrażania obejmują sklep Microsoft Store, witrynę programu SharePoint lub technologie InstallShield lub Windows Installer. Wszystko jest dostępne za pośrednictwem IDE. Aby uzyskać więcej informacji, zobacz [Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Zarządzanie kodem źródłowym i współpraca z innymi osobami

Możesz zarządzać kodem źródłowym w repozytoriach Git obsługiwanych przez dowolnego dostawcę, w tym GitHub. Możesz też użyć [usługi Azure DevOps](/azure/devops/index) do zarządzania kodem obok błędów i elementów roboczych dla całego projektu. Zobacz [Wprowadzenie do funkcji Git i Reppos platformy Azure,](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) aby dowiedzieć się więcej o zarządzaniu repozytoriami Git w programie Visual Studio przy użyciu Eksploratora zespołu. Visual Studio ma również inne wbudowane funkcje kontroli źródła. Aby dowiedzieć się więcej o nich, zobacz [Nowe funkcje Git w programie Visual Studio (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Usługi Azure DevOps to usługi oparte na chmurze do planowania, hostowanie, automatyzacja i wdrażanie oprogramowania oraz umożliwienie współpracy w zespołach. Usługi Azure DevOps obsługują zarówno repozytoria Git (rozproszona kontrola wersji), jak i kontrolę wersji Team Foundation (scentralizowana kontrola wersji). Obsługują potoki ciągłej kompilacji i zwalniania (CI/CD) kodu przechowywanego w systemach kontroli wersji. Usługi Azure DevOps obsługują również metody programowania Scrum, CMMI i Agile.

Team Foundation Server (TFS) to centrum zarządzania cyklem życia aplikacji dla programu Visual Studio. Umożliwia wszystkim zaangażowanym w proces tworzenia udział przy użyciu jednego rozwiązania. TFS jest również przydatny do zarządzania heterogenicznymi zespołami i projektami.

Jeśli masz w sieci organizację Azure DevOps lub serwer Team Foundation Server, możesz połączyć się z nią za pośrednictwem okna **Eksploratora zespołu** w programie Visual Studio. W tym oknie można zaewidencjonować kod do lub poza kontrolą źródła, zarządzać elementami roboczymi, uruchamiać kompilacje i uzyskiwać dostęp do pomieszczeń zespołu i obszarów roboczych. **Eksploratora zespołu** można otworzyć w polu wyszukiwania lub w menu głównym w **widoku** > **Eksploratora zespołu** lub w oknie Zarządzanie **zespołami** > **Manage Connections**.

Na poniższej ilustracji przedstawiono okno **Eksploratora zespołu** dla rozwiązania hostowanego w usługach Azure DevOps.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

Można również zautomatyzować proces kompilacji do tworzenia kodu, który deweloperzy w zespole zaewidencjonowali do kontroli wersji. Można na przykład skompilować jeden lub więcej projektów w nocy lub za każdym razem, kiedy kod jest zaewidencjonowany. Aby uzyskać więcej informacji, zobacz [Potoki platformy Azure](/azure/devops/pipelines/index?view=vsts).

## <a name="extend-visual-studio"></a>Rozszerzanie funkcjonalności programu Visual Studio

Jeśli program Visual Studio nie ma dokładnie potrzebnej funkcji, możesz ją dodać! Ide można spersonalizować na podstawie przepływu pracy i stylu, dodać obsługę narzędzi zewnętrznych, które nie zostały jeszcze zintegrowane z programem Visual Studio i zmodyfikować istniejące funkcje, aby zwiększyć produktywność. Aby znaleźć najnowszą wersję narzędzi rozszerzalności programu Visual Studio (VS SDK), zobacz [Zestaw SDK programu Visual Studio](../extensibility/visual-studio-sdk.md).

Za pomocą platformy kompilatora .NET ("Roslyn") można napisać własne analizatory kodu i generatory kodu. Znajdź wszystko, czego potrzebujesz w [Roslyn](https://github.com/dotnet/Roslyn).

Znajdź [istniejące rozszerzenia](https://marketplace.visualstudio.com/vs) programu Visual Studio utworzone przez deweloperów firmy Microsoft, a także naszą społeczność programistów.

Aby dowiedzieć się więcej na temat rozszerzania programu Visual Studio, zobacz [Rozszerzanie środowiska IDE programu Visual Studio](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Zobacz też

- [Omówienie ide programu Visual Studio](../get-started/visual-studio-ide.md)
- [Co nowego w programie Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [Co nowego w programie Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)

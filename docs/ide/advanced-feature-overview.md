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
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235202"
---
# <a name="features-of-visual-studio"></a>Funkcje programu Visual Studio

Artykuł [Omówienie programu Visual Studio IDE](../get-started/visual-studio-ide.md) zawiera podstawowe wprowadzenie do programu Visual Studio. W tym artykule opisano funkcje, które mogą być bardziej odpowiednie dla doświadczonych deweloperów lub tych deweloperów, którzy już znają się w programie Visual Studio.

## <a name="modular-installation"></a>Modularna instalacja

Modułowy Instalator programu Visual Studio umożliwia wybranie i zainstalowanie *obciążeń*. Obciążenia są grupami funkcji wymaganych przez preferowany język programowania lub platformę. Taka strategia pomaga zachować śladu mniejsze, instalacja programu Visual Studio, co oznacza, jej instalowanie i aktualizowanie szybciej za.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

Aby dowiedzieć się więcej o konfigurowaniu programu Visual Studio w systemie, zobacz [Instalowanie programu Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Tworzenie aplikacji z obsługą chmury dla platformy Azure

Program Visual Studio udostępnia zestaw narzędzi, które umożliwiają proste tworzenie aplikacji z obsługą chmury obsługiwane przez Microsoft Azure. Można skonfigurować, tworzenie, debugowanie, pakowanie i wdrażanie aplikacji i usług Microsoft Azure bezpośrednio z poziomu środowiska IDE. Aby uzyskać narzędzia i szablony projektów platformy Azure, wybierz obciążenie **Programowanie na platformie Azure** podczas instalowania programu Visual Studio.

![Obciążenie programistyczne platformy Azure](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Po zainstalowaniu obciążeń **programistycznych platformy Azure** następujące szablony w **chmurze** dla programu C# są dostępne w oknie dialogowym **Nowy projekt** :

![Szablony projektów chmury dla programu Visual Studio](media/cloud-project-templates.png)

::: moniker-end

[Eksplorator chmur](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) programu Visual Studio umożliwia wyświetlanie zasobów w chmurze opartych na platformie Azure i zarządzanie nimi w programie Visual Studio. Te zasoby mogą obejmować maszyn wirtualnych, tabel, baz danych SQL i inne. W **programie Cloud Explorer** widoczne są zasoby platformy Azure we wszystkich kontach zarządzanych w ramach subskrypcji platformy Azure, do której się zalogowano. A jeśli określona operacja wymaga Azure Portal, w programie **Cloud Explorer** znajdują się linki umożliwiające przejście do miejsca w portalu, w którym należy się zapoznać.

![Eksplorator chmury w programie Visual Studio](media/cloud-explorer.png)

Możesz korzystać z usług platformy Azure dla aplikacji przy użyciu **usług połączonych** , takich jak:

- [Active Directory podłączona usługa](/azure/active-directory/develop/vs-active-directory-add-connected-service) , dzięki czemu użytkownicy mogą używać swoich kont w usłudze [Azure Active Directory](/azure/active-directory/active-directory-whatis) do nawiązywania połączeń z aplikacjami sieci Web
- [Usługa połączona usługi Azure Storage](/azure/vs-azure-tools-connected-services-storage) dla magazynu obiektów blob, kolejek i tabel
- [Key Vault podłączona usługa](/azure/key-vault/vs-key-vault-add-connected-service) do zarządzania wpisami tajnymi dla aplikacji sieci Web

Dostępne **usługi połączone** są zależne od typu projektu. Aby dodać usługę, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **połączonej usługi**.

![Usług połączonych programu Visual Studio](media/connected-services.png)

Aby uzyskać więcej informacji, zobacz [przenoszenie do chmury za pomocą programu Visual Studio i platformy Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Tworzenie aplikacji sieci Web

Sieć web dyski w nowoczesnym świecie, a Visual Studio może pomóc, dzięki czemu można tworzyć aplikacje dla niego. Można tworzyć aplikacje internetowe przy użyciu platformy ASP.NET, Node.js, Python, JavaScript i TypeScript. Program Visual Studio rozumie, środowisk sieci web, takich jak Angular, jQuery, Express i nie tylko. Platforma ASP.NET Core i .NET Core, działających w systemach operacyjnych Windows, Mac i Linux. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) to główna Aktualizacja dla MVC, WebAPI i sygnalizująca, która działa w systemach Windows, Mac i Linux.  Platformy ASP.NET Core został zaprojektowany od podstaw w górę aby zapewnić Ci .NET odchudzona i konfigurowalna stosu do tworzenia nowoczesnej sieci web, które są oparte na chmurze aplikacje i usługi.

Aby uzyskać więcej informacji, zobacz [nowoczesne narzędzia sieci Web](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Twórz Międzyplatformowe aplikacje i gry

Możesz użyć programu Visual Studio do tworzenia aplikacji i gier dla systemów macOS, Linux i Windows, a także dla urządzeń z systemami Android, iOS i innymi [urządzeniami przenośnymi](https://visualstudio.microsoft.com/vs/mobile-app-development/).

- Twórz aplikacje [platformy .NET Core](/dotnet/core/) działające w systemach Windows, MacOS i Linux.

- Twórz aplikacje mobilne dla systemów iOS, Android i Windows w C# systemach F# i przy użyciu platformy [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Używaj standardowych technologii sieci Web&mdash;językach HTML, CSS i&mdash;JavaScript, aby tworzyć aplikacje mobilne dla systemów iOS, Android i Windows przy użyciu [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/).

- Twórz gry 2D i 3W w C# programie przy użyciu [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md).

- Twórz aplikacje C++ natywne dla urządzeń z systemem iOS, Android i Windows. Udostępniaj wspólny kod w bibliotekach skompilowanych dla systemów iOS, Android i Windows za pomocą [ C++ programu do tworzenia aplikacji dla wielu platform](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development).

- Wdrażaj, Testuj i Debuguj aplikacje dla systemu Android za pomocą [emulatora systemu Android](../cross-platform/visual-studio-emulator-for-android.md).

## <a name="connect-to-databases"></a>Łączenie z bazami danych

**Eksplorator serwera** ułatwia przeglądanie SQL Server wystąpień i zasobów oraz zarządzanie nimi lokalnie, zdalnie i na platformie Azure, Salesforce.com, Office 365 i witrynach sieci Web. Aby otworzyć **Eksplorator serwera**, w menu głównym wybierz polecenie **Wyświetl** > **Eksplorator serwera**. Aby uzyskać więcej informacji na temat korzystania z Eksplorator serwera, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) to zaawansowane środowisko programistyczne dla SQL Server, Azure SQL Database i Azure SQL Data Warehouse. Umożliwia kompilowanie, debugowanie, obsługa i Refaktoryzuj baz danych. Możesz pracować z projektem bazy danych lub bezpośrednio z bazy danych połączone wystąpienie na — lub poza siedzibą firmy.

**Eksplorator obiektów SQL Server** w programie Visual Studio udostępnia widok obiektów bazy danych podobny do SQL Server Management Studio. Eksplorator obiektów SQL Server umożliwia wykonywanie zadań związanych z administracją i projektowaniem bazy danych z lekkimi opłatami. Przykłady pracy obejmują edytowanie danych tabeli, porównywanie schematów, wykonywanie zapytań za pomocą menu kontekstowych bezpośrednio z Eksplorator obiektów SQL Server i innych.

![Eksplorator obiektów SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Debugowanie, testowanie i ulepszaj swój kod

Podczas pisania kodu, musisz go uruchomić i przetestować go dla błędów i wydajności. System debugowania programu Visual Studio umożliwia debugowanie kodu działającego w projekcie lokalnym, na urządzeniu zdalnym lub w [emulatorze urządzenia](../cross-platform/visual-studio-emulator-for-android.md). Można przejść przez kod w jednej instrukcji w danym momencie i sprawdzanie zmiennych, zgodnie z rzeczywistym. Możesz ustawić punkty przerwania, które są osiągane tylko wtedy, gdy określony warunek ma wartość true. Opcjami debugowania można zarządzać w edytorze kodu, dzięki czemu nie trzeba opuszczać kodu. Aby uzyskać więcej informacji na temat debugowania w programie Visual Studio, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

Aby dowiedzieć się więcej o ulepszaniu wydajności aplikacji, Wyewidencjonuj funkcję [profilowania](../profiling/profiling-feature-tour.md) programu Visual Studio.

W przypadku [testowania](../test/improve-code-quality.md)program Visual Studio oferuje testy jednostkowe, Live Unit Testing, IntelliTest, testy obciążenia i wydajności itp. Program Visual Studio oferuje także zaawansowane funkcje [analizy kodu](../code-quality/code-analysis-for-managed-code-overview.md) umożliwiające przechwycenie projektu, zabezpieczeń i innych typów wad.

## <a name="deploy-your-finished-application"></a>Wdrażanie gotowych aplikacji

Gdy aplikacja jest gotowa do wdrożenia użytkownikom lub klientom, program Visual Studio udostępnia narzędzia do wykonania tej czynności. Opcje wdrożenia obejmują Microsoft Store, do witryny programu SharePoint lub z technologiami InstallShield lub Instalator Windows. Jest ona dostępna za pośrednictwem środowiska IDE. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Zarządzaj kodem źródłowym i współpracować z innymi

Możesz zarządzać kodem źródłowym w repozytoriach Git hostowanych przez dowolnego dostawcę, w tym witrynę GitHub. Można też używać [Azure DevOps Services](/azure/devops/index) do zarządzania kodem wraz z błędami i elementami roboczymi dla całego projektu. Zobacz Rozpoczynanie [pracy z usługą git i Azure Repos](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) , aby dowiedzieć się więcej o zarządzaniu repozytoriami Git w programie Visual Studio przy użyciu Team Explorer. Visual Studio ma również innych funkcji kontroli źródła wbudowanych. Aby dowiedzieć się więcej na ten temat, zobacz [nowe funkcje usługi Git w programie Visual Studio (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Services to usługi oparte na chmurze, które umożliwiają planowanie, hostowanie, Automatyzowanie i wdrażanie oprogramowania oraz włączanie współpracy w zespołach. Azure DevOps Services obsługiwać zarówno repozytoria Git (rozproszonej kontroli wersji), jak i Kontrola wersji serwera Team Foundation (scentralizowany system kontroli wersji). Obsługują one potoki do ciągłego kompilowania i wydawania (CI/CD) kodu przechowywanego w systemach kontroli wersji. Usługom DevOps platformy Azure obsługują również Scrum i CMMI Agile metodologii programowania.

Team Foundation Server (TFS), to Centrum zarządzania cyklem życia aplikacji dla programu Visual Studio. Dzięki temu wszyscy pracownicy z procesem rozwoju uczestnictwa, używając jednego rozwiązania. TFS jest przydatne w celu zarządzania heterogenicznych zespołów i projektów, zbyt.

Jeśli masz organizację usługi Azure DevOps lub Team Foundation Server w sieci, możesz połączyć się z nią za pomocą okna **Team Explorer** w programie Visual Studio. Z tego okna można sprawdzić kod do lub z kontroli źródła, zarządzania elementami roboczymi, kompilacji i rozpoczęcia pokoje zespołów dostępu oraz obszarów roboczych. **Team Explorer** można otworzyć w polu wyszukiwania lub w menu głównym z **widoku** > **Team Explorer** lub z **zespołu** > **Zarządzanie połączeniami**.

Na poniższej ilustracji przedstawiono okno **Team Explorer** dla rozwiązania, które jest hostowane w Azure DevOps Services.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

Możesz też zautomatyzować proces kompilacji, aby skompilować kod, który deweloperzy w zespole sprawdzeniu w kontroli wersji. Można na przykład skompilować jeden lub więcej projektów w nocy lub za każdym razem, kiedy kod jest zaewidencjonowany. Aby uzyskać więcej informacji, zobacz [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="extend-visual-studio"></a>Rozszerzanie funkcjonalności programu Visual Studio

Jeśli program Visual Studio nie ma dokładnie funkcji, czego potrzebujesz, możesz dodać go! Można personalizować środowisko IDE na podstawie przepływu pracy i stylu, dodanie obsługi narzędzi zewnętrznych, które nie są jeszcze zintegrowane z programem Visual Studio i modyfikować istniejące funkcje do zwiększenia produktywności. Aby znaleźć najnowszą wersję Visual Studio Extensibility Tools (VS SDK), zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Platforma kompilatora .NET ("Roslyn") służy do pisania własnego kodu analizatory i generatorów kodu. Znajdź wszystko, czego potrzebujesz, w witrynie [Roslyn](https://github.com/dotnet/Roslyn).

Znajdź [istniejące rozszerzenia](https://marketplace.visualstudio.com/vs) dla programu Visual Studio utworzone przez deweloperów firmy Microsoft, a także naszą społeczność deweloperów.

Aby dowiedzieć się więcej na temat rozszerzania programu Visual Studio, zobacz [rozszerzanie środowiska IDE programu Visual Studio](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Zobacz też

- [Środowisko IDE programu Visual Studio — omówienie](../get-started/visual-studio-ide.md)
- [Co nowego w programie Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [Co nowego w programie Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)

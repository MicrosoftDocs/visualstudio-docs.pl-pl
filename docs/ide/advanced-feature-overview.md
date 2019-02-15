---
title: Zaawansowane funkcje programu Visual Studio 2017
titleSuffix: ''
ms.date: 06/01/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da502b2f527f811f20bbce299107cac20517048a
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317838"
---
# <a name="features-of-visual-studio-2017"></a>Funkcje programu Visual Studio 2017

[Omówienie środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md) artykuł zawiera podstawowe wprowadzenie do programu Visual Studio. W tym artykule opisano funkcje, które mogą być bardziej odpowiednie dla doświadczonych deweloperów lub tych deweloperów, którzy są już zaznajomieni z programu Visual Studio.

## <a name="modular-installation"></a>Modularna instalacja

Moduły Instalatora programu Visual Studio umożliwia wybierz i zainstaluj *obciążeń*. Obciążenia są grupami funkcje potrzebne do programowania języka lub platformy, na której użytkownik sobie tego życzy. Taka strategia pomaga zachować śladu mniejsze, instalacja programu Visual Studio, co oznacza, jej instalowanie i aktualizowanie szybciej za.

Jeśli jeszcze nie zainstalowano programu Visual Studio 2017, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

Aby dowiedzieć się więcej o konfigurowaniu programu Visual Studio w systemie, zobacz [Install Visual Studio 2017](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Tworzenie aplikacji z obsługą chmury dla platformy Azure

Program Visual Studio udostępnia zestaw narzędzi, które umożliwiają proste tworzenie aplikacji z obsługą chmury obsługiwane przez Microsoft Azure. Można skonfigurować, tworzenie, debugowanie, pakowanie i wdrażanie aplikacji i usług Microsoft Azure bezpośrednio z poziomu środowiska IDE. Aby uzyskać szablony projektów i narzędzi platformy Azure, wybierz **programowanie na platformie Azure** obciążenia podczas instalowania programu Visual Studio.

![Obciążenie programistyczne platformy Azure](../data-tools/media/azure-development-workload.png)

Po zainstalowaniu **programowanie na platformie Azure** obciążenie, następujące **chmury** szablony dla języka C# są dostępne w **nowy projekt** okno dialogowe:

![Szablony projektów chmury dla programu Visual Studio](media/cloud-project-templates.png)

Visual Studio [programu Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) umożliwia wyświetlanie i zarządzanie zasobami w chmurze oparte na platformie Azure w programie Visual Studio. Te zasoby mogą obejmować maszyn wirtualnych, tabel, baz danych SQL i inne. **Eksplorator chmury** pokazuje zasobów platformy Azure w ramach kont zarządzanych logujesz się do subskrypcji platformy Azure. I jeśli określoną operacją wymaga witryny Azure portal **programu Cloud Explorer** łącza, które przeniosą Cię w portalu w miejscu, w którym musisz przejść.

![Eksplorator chmury w programie Visual Studio](media/cloud-explorer.png)

Można korzystać z usług platformy Azure dla aplikacji przy użyciu **podłączone usługi** takich jak:

- [Usługa połączona w usłudze Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) , dzięki czemu użytkownicy mogą używać swoich kont w [usługi Azure Active Directory](/azure/active-directory/active-directory-whatis) połączyć się z aplikacji sieci web
- [Usługa połączona usługa Azure Storage](/azure/vs-azure-tools-connected-services-storage) dla magazynu obiektów blob, kolejki i tabele
- [Usługa połączona Key Vault](/azure/key-vault/vs-key-vault-add-connected-service) do zarządzania wpisami tajnymi aplikacji sieci web

Dostępne **podłączone usługi** są zależne od typu projektu. Dodaj usługę, klikając prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierając pozycję **Dodaj** > **podłączoną usługę**.

![Usług połączonych programu Visual Studio](media/connected-services.png)

Aby uzyskać więcej informacji, zobacz [przeniesienie do chmury za pomocą programu Visual Studio i platformy Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Tworzenie aplikacji sieci Web

Sieć web dyski w nowoczesnym świecie, a Visual Studio może pomóc, dzięki czemu można tworzyć aplikacje dla niego. Można tworzyć aplikacje internetowe przy użyciu platformy ASP.NET, Node.js, Python, JavaScript i TypeScript. Program Visual Studio rozumie, środowisk sieci web, takich jak Angular, jQuery, Express i nie tylko. Platforma ASP.NET Core i .NET Core, działających w systemach operacyjnych Windows, Mac i Linux. [Platforma ASP.NET Core](http://www.asp.net/core/overview) jest ważna aktualizacja MVC, WebAPI i SignalR i działa na Windows, Mac i Linux.  Platformy ASP.NET Core został zaprojektowany od podstaw w górę aby zapewnić Ci .NET odchudzona i konfigurowalna stosu do tworzenia nowoczesnej sieci web, które są oparte na chmurze aplikacje i usługi.

Aby uzyskać więcej informacji, zobacz [nowoczesne narzędzia sieci web](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Twórz Międzyplatformowe aplikacje i gry

Używasz programu Visual Studio do tworzenia aplikacji i gier dla systemu macOS, Linux i Windows, a także dla systemów Android, iOS i innych [urządzeń przenośnych](https://visualstudio.microsoft.com/vs/mobile-app-development/).

- Tworzenie [platformy .NET Core](/dotnet/core/) aplikacji działających w Windows, macOS i Linux.

- Twórz aplikacje mobilne dla systemów iOS, Android i Windows w C# i F# przy użyciu [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Użyj standardowych technologii sieci web&mdash;HTML, CSS i JavaScript&mdash;do tworzenia aplikacji mobilnych dla systemów iOS, Android i Windows przy użyciu [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/).

- Tworzenie gier 2D i 3D w języku C# za pomocą [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md).

- Tworzenie natywnych aplikacji C++ dla systemów iOS, Android i Windows urządzenia. Udostępnić wspólny kod w bibliotekach skompilowanych dla systemu iOS, Android i Windows, przy użyciu [C++ dla wieloplatformowego opracowywania aplikacji](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md).

- Wdrażaj, Testuj i Debuguj aplikacje dla systemu Android za pomocą [emulatora systemu Android](../cross-platform/visual-studio-emulator-for-android.md).

## <a name="connect-to-databases"></a>Łączenie z bazami danych

**Eksplorator serwera** pomaga przeglądać i Zarządzanie wystąpieniami programu SQL Server i zasobami lokalnie, zdalnie i na platformy Azure, Salesforce.com, Office 365 i witryn sieci Web. Aby otworzyć **Eksploratora serwera**, w menu głównym wybierz **widoku** > **Eksploratora serwera**. Aby uzyskać więcej informacji o korzystaniu z Eksploratora serwera, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) jest zaawansowane środowisko programistyczne dla programu SQL Server, usługi Azure SQL Database i Azure SQL Data Warehouse. Umożliwia kompilowanie, debugowanie, obsługa i Refaktoryzuj baz danych. Możesz pracować z projektem bazy danych lub bezpośrednio z bazy danych połączone wystąpienie na — lub poza siedzibą firmy.

**Eksplorator obiektów SQL Server** w programie Visual Studio udostępnia widok obiektów bazy danych podobny do programu SQL Server Management Studio. Eksplorator obiektów SQL Server umożliwia wykonywanie pracy administracji i projektowania lekkich bazy danych. Praca przykładami edycji danych w tabeli, porównywanie schematów, wykonywanie zapytań za pomocą menu kontekstowych bezpośrednio w Eksploratorze obiektów SQL Server i nie tylko.

![Eksplorator obiektów SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Debugowanie, testowanie i ulepszaj swój kod

Podczas pisania kodu, musisz go uruchomić i przetestować go dla błędów i wydajności. Najnowocześniejsze system debugowania programu Visual Studio pozwala debugować możesz kod działający w projekcie lokalnym, na zdalnym urządzeniu lub na [emulator urządzenia](../cross-platform/visual-studio-emulator-for-android.md). Można przejść przez kod w jednej instrukcji w danym momencie i sprawdzanie zmiennych, zgodnie z rzeczywistym. Możesz ustawić punkty przerwania, które są osiągane tylko wtedy, gdy określony warunek ma wartość true. Debugowanie opcjami można zarządzać w edytorze kodu, dzięki czemu nie trzeba pozostawić swój kod. Aby uzyskać więcej informacji o debugowaniu w programie Visual Studio, zobacz [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md).

Aby dowiedzieć się więcej na temat zwiększania wydajności aplikacji, wyewidencjonowania się programu Visual Studio [profilowania](../profiling/profiling-feature-tour.md) funkcji.

Aby uzyskać [testowania](../test/improve-code-quality.md), program Visual Studio oferuje testy jednostkowe, Live Unit Testing, IntelliTest, obciążenia i testy wydajności i inne. Program Visual Studio również udostępnia zaawansowane [analiza kodu](../code-quality/code-analysis-for-managed-code-overview.md) możliwości, aby przechwycić projektowania, zabezpieczeń i innych typów wad.

## <a name="deploy-your-finished-application"></a>Wdrażanie gotowych aplikacji

Gdy aplikacja jest gotowa do wdrożenia użytkownicy lub klienci, program Visual Studio udostępnia narzędzia, aby to zrobić. Opcje wdrażania obejmują do Microsoft Store do witryny programu SharePoint lub przy użyciu technologii InstallShield lub Instalatora Windows. Jest ona dostępna za pośrednictwem środowiska IDE. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Zarządzaj kodem źródłowym i współpracować z innymi

Możesz zarządzać kodem źródłowym w repozytoriach Git hostowanych przez dowolnego dostawcę, w tym witrynę GitHub. Lub użyj [usługom DevOps platformy Azure](/azure/devops/index) do zarządzania kodem, usterkami i elementami roboczymi dla całego projektu. Zobacz [Rozpoczynanie pracy z usługą Git i repozytoriów platformy Azure](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) Aby dowiedzieć się więcej na temat zarządzania repozytoriami Git w programie Visual Studio za pomocą programu Team Explorer. Visual Studio ma również innych funkcji kontroli źródła wbudowanych. Aby dowiedzieć się więcej o nich, zobacz [Git nowe funkcje w programie Visual Studio 2017 (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Usługom DevOps platformy Azure są usługami w chmurze do planu, obsługi, automatyczne i wdrażanie oprogramowania i umożliwianie współpracy w zespołach. Usługom DevOps platformy Azure obsługuje zarówno repozytoria Git (rozproszonej kontroli wersji), jak i Team Foundation Version Control (scentralizowany system kontroli wersji). Obsługiwane są też potoki ciągłej kompilacji i wersji (CI/CD) przechowywane w systemach kontroli wersji kodu. Usługom DevOps platformy Azure obsługują również Scrum i CMMI Agile metodologii programowania.

Team Foundation Server (TFS), to Centrum zarządzania cyklem życia aplikacji dla programu Visual Studio. Dzięki temu wszyscy pracownicy z procesem rozwoju uczestnictwa, używając jednego rozwiązania. TFS jest przydatne w celu zarządzania heterogenicznych zespołów i projektów, zbyt.

Jeśli masz w sieci organizacji DevOps platformy Azure lub programu Team Foundation Server, nawiążesz z nim za pośrednictwem **Team Explorer** okna w programie Visual Studio. Z tego okna można sprawdzić kod do lub z kontroli źródła, zarządzania elementami roboczymi, kompilacji i rozpoczęcia pokoje zespołów dostępu oraz obszarów roboczych. Możesz otworzyć **Team Explorer** z **Szybkie uruchamianie** pole, lub w menu głównym z **widoku** > **Team Explorer** lub **Zespołu** > **Zarządzanie połączeniami**.

Na poniższej ilustracji przedstawiono **Team Explorer** okna dla rozwiązania, które jest hostowane w usługach infrastruktury DevOps platformy Azure.

![Program Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

Możesz też zautomatyzować proces kompilacji, aby skompilować kod, który deweloperzy w zespole sprawdzeniu w kontroli wersji. Można na przykład skompilować jeden lub więcej projektów w nocy lub za każdym razem, kiedy kod jest zaewidencjonowany. Aby uzyskać więcej informacji, zobacz [potoki Azure](/azure/devops/pipelines/index?view=vsts).

## <a name="extend-visual-studio"></a>Rozszerzanie funkcjonalności programu Visual Studio

Jeśli program Visual Studio nie ma dokładnie funkcji, czego potrzebujesz, możesz dodać go! Można personalizować środowisko IDE na podstawie przepływu pracy i stylu, dodanie obsługi narzędzi zewnętrznych, które nie są jeszcze zintegrowane z programem Visual Studio i modyfikować istniejące funkcje do zwiększenia produktywności. Aby uzyskać najnowszą wersję narzędzia programu Visual Studio Extensibility (zestaw SDK programu VS), zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Platforma kompilatora .NET ("Roslyn") służy do pisania własnego kodu analizatory i generatorów kodu. Znajdź wszystko, czego potrzebujesz w [Roslyn](https://github.com/dotnet/Roslyn).

Znajdź [istniejące rozszerzenia](https://marketplace.visualstudio.com/vs) dla programu Visual Studio, tworzone przez deweloperów firmy Microsoft, a także naszej społeczności deweloperów.

Aby dowiedzieć się więcej na temat rozszerzania programu Visual Studio, zobacz [rozszerzenia programu Visual Studio IDE](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Zobacz także

- [Visual Studio IDE — omówienie](../get-started/visual-studio-ide.md)
- [Co nowego w programie Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [What's new in Visual Studio Preview 2019 r](../ide/whats-new-visual-studio-2019.md)

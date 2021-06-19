---
title: Funkcje zaawansowane
description: Dowiedz się więcej o zaawansowanych funkcjach, które mogą być bardziej odpowiednie dla doświadczonych deweloperów lub tych, którzy już znają Visual Studio.
ms.custom: vs-acquisition
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6cc6604816921b054b0c909177c8e641493920a8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386199"
---
# <a name="features-of-visual-studio"></a>Funkcje Visual Studio

Artykuł [Visual Studio IDE zawiera](../get-started/visual-studio-ide.md) podstawowe wprowadzenie do Visual Studio. W tym artykule opisano funkcje, które mogą być bardziej odpowiednie dla doświadczonych deweloperów lub tych, którzy już znają Visual Studio.

## <a name="modular-installation"></a>Instalacja modułowa

Visual Studio modularny instalator firmy Visual Studio umożliwia wybieranie i *instalowanie obciążeń.* Obciążenia to grupy funkcji wymaganych dla preferowanego języka programowania lub platformy. Ta strategia pomaga zmniejszyć rozmiary Visual Studio, co oznacza, że instalacja i aktualizacje są również szybsze.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

Aby dowiedzieć się więcej na temat konfigurowania Visual Studio w systemie, zobacz [Instalowanie Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Tworzenie aplikacji z obsługą chmury dla platformy Azure

Visual Studio oferuje zestaw narzędzi, które umożliwiają łatwe tworzenie aplikacji z obsługą chmury obsługiwanych przez Microsoft Azure. Aplikacje i usługi można konfigurować, kompilować, debugować, pakować i wdrażać Microsoft Azure bezpośrednio ze środowiska IDE. Aby uzyskać narzędzia i szablony projektów platformy Azure, wybierz obciążenie Tworzenie aplikacji na platformie **Azure** podczas instalowania Visual Studio.

![Obciążenie dla developmentu na platformie Azure](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Po zainstalowaniu pakietu **roboczego Tworzenie** aplikacji na platformie Azure **następujące** szablony chmury dla języka C# są dostępne w **oknie dialogowym Nowy** projekt:

![Szablony projektów w chmurze dla Visual Studio](media/cloud-project-templates.png)

::: moniker-end

Visual Studio Cloud [Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) umożliwia wyświetlanie zasobów w chmurze opartych na platformie Azure i zarządzanie nimi w Visual Studio. Te zasoby mogą obejmować maszyny wirtualne, tabele, bazy danych SQL i nie tylko. **Eksplorator chmury** pokazuje zasoby platformy Azure na wszystkich kontach zarządzanych w ramach subskrypcji platformy Azure, do których się zalogowano. Jeśli natomiast określonej operacji wymaga **Azure Portal,** Eksplorator chmury udostępnia linki, które zapewniają dostęp do miejsca w portalu, w którym należy przejść.

![Eksplorator chmury w usłudze Visual Studio](media/cloud-explorer.png)

Możesz korzystać z usług platformy Azure dla swoich aplikacji przy użyciu **usług połączonych,** takich jak:

- [Połączona usługa Active Directory,](/azure/active-directory/develop/vs-active-directory-add-connected-service) dzięki czemu użytkownicy mogą używać swoich kont [z](/azure/active-directory/active-directory-whatis) Azure Active Directory do łączenia się z aplikacjami internetowymi
- [Połączona usługa Azure Storage dla](/azure/vs-azure-tools-connected-services-storage) magazynu obiektów blob, kolejek i tabel
- [Key Vault do zarządzania wpisami](/azure/key-vault/vs-key-vault-add-connected-service) tajnymi dla aplikacji internetowych

Dostępne usługi **połączone zależą** od typu projektu. Dodaj usługę, klikając prawym przyciskiem myszy projekt w **usłudze Eksplorator rozwiązań** a następnie wybierając **polecenie Dodaj**  >  **usługę połączeniową.**

![Visual Studio połączone usługi](media/connected-services.png)

Aby uzyskać więcej informacji, zobacz Move to the cloud With Visual Studio and Azure (Przechodzenie do chmury [przy Visual Studio Azure).](https://visualstudio.microsoft.com/vs/azure-tools/)

## <a name="create-apps-for-the-web"></a>Tworzenie aplikacji dla Internetu

Sieć Web napędza nasz nowoczesny świat, a Visual Studio może pomóc w pisanych dla niego aplikacjach. Aplikacje internetowe można tworzyć przy użyciu języków ASP.NET, Node.js, Python, JavaScript i TypeScript. Visual Studio takie jak Angular, jQuery, Express i inne. ASP.NET Core i .NET Core działają w systemach operacyjnych Windows, Mac i Linux. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) to główna aktualizacja MVC, WebAPI i SignalR, która działa w systemach Windows, Mac i Linux.  ASP.NET Core został zaprojektowany od podstaw w celu zapewnienia zuchętnego i owalnego stosu platformy .NET do tworzenia nowoczesnych aplikacji i usług internetowych opartych na chmurze.

Aby uzyskać więcej informacji, zobacz [Modern web tooling (Nowoczesne narzędzia internetowe).](https://visualstudio.microsoft.com/vs/modern-web-tooling/)

## <a name="build-cross-platform-apps-and-games"></a>Tworzenie aplikacji i gier międzyplatformowych

Za pomocą usługi Visual Studio można tworzyć aplikacje i gry dla systemów macOS, Linux i Windows, a także dla systemów Android, iOS i [innych urządzeń przenośnych.](https://visualstudio.microsoft.com/vs/mobile-app-development/)

- Twórz [aplikacje .NET Core,](/dotnet/core/) które działają w systemach Windows, macOS i Linux.

- Twórz aplikacje mobilne dla systemów iOS, Android i Windows w języku C# i F# przy użyciu [platformy Xamarin.](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)

- Twórz gry 2D i 3D w języku C# przy użyciu [Visual Studio Tools for Unity](/gamedev/unity/get-started/visual-studio-tools-for-unity.md).

- Twórz natywne aplikacje języka C++ dla urządzeń z systemami iOS, Android i Windows. Udostępniaj wspólny kod w bibliotekach dla systemów iOS, Android i Windows, używając języka C++ do tworzenia aplikacji [międzyplatformowych.](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)

## <a name="connect-to-databases"></a>Nawiązywanie połączenia z bazami danych

**Eksplorator serwera** ułatwia przeglądanie i zarządzanie SQL Server i zasobami lokalnie, zdalnie oraz na platformie Azure, Salesforce.com, Microsoft 365 i witrynach internetowych. Aby otworzyć **Eksplorator serwera**, w menu głównym wybierz pozycję **Wyświetl**  >  **Eksplorator serwera**. Aby uzyskać więcej informacji na temat używania Eksplorator serwera, [zobacz Dodawanie nowych połączeń.](../data-tools/add-new-connections.md)

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) to zaawansowane środowisko deweloperskie dla SQL Server, Azure SQL Database i Azure SQL Data Warehouse. Umożliwia tworzenie, debugowanie, konserwację i refaktoryzować bazy danych. Możesz pracować z projektem bazy danych lub bezpośrednio z połączonym wystąpieniem bazy danych lokalnie lub lokalnie.

**Eksplorator obiektów SQL Server** w Visual Studio udostępnia widok obiektów bazy danych podobny do SQL Server Management Studio. Eksplorator obiektów SQL Server umożliwia administrowanie bazami danych i ich projektowanie. Przykłady pracy obejmują edytowanie danych tabeli, porównywanie schematów, wykonywanie zapytań przy użyciu menu kontekstowych bezpośrednio Eksplorator obiektów SQL Server i nie tylko.

![Eksplorator obiektów SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Debugowanie, testowanie i ulepszanie kodu

Gdy piszesz kod, musisz go uruchomić i przetestować pod względu na błędy i wydajność. Visual Studio najnowocześniejszego systemu debugowania umożliwia debugowanie kodu uruchomionego w projekcie lokalnym, na urządzeniu zdalnym lub w [emulatorze urządzenia.](../cross-platform/visual-studio-emulator-for-android.md) Możesz przechodzić przez kod po jednej instrukcji na raz i sprawdzać zmienne w czasie rzeczywistym. Można ustawić punkty przerwania, które są trafione tylko wtedy, gdy określony warunek ma wartość true. Opcjami debugowania można zarządzać w edytorze kodu, dzięki czemu nie trzeba pozostawiać kodu. Aby uzyskać więcej informacji na temat debugowania w Visual Studio, [zobacz Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

Aby dowiedzieć się więcej o poprawianiu wydajności aplikacji, wyewidencjonowaj Visual Studio [profilowania aplikacji.](../profiling/profiling-feature-tour.md)

Do [testowania](../test/improve-code-quality.md)Visual Studio testy jednostkowe, Live Unit Testing, IntelliTest, testy obciążeniowe i wydajnościowe i nie tylko. Visual Studio zaawansowane funkcje [analizy](../code-quality/code-analysis-for-managed-code-overview.md) kodu, które mogą przechwytować błędy projektu, zabezpieczeń i inne typy wad.

## <a name="deploy-your-finished-application"></a>Wdrażanie ukończonej aplikacji

Gdy aplikacja jest gotowa do wdrożenia dla użytkowników lub klientów, Visual Studio udostępnia narzędzia do tego celu. Opcje wdrażania obejmują Microsoft Store, witrynę programu SharePoint, program InstallShield lub Instalator Windows technologii. Wszystkie te informacje są dostępne za pośrednictwem środowiska IDE. Aby uzyskać więcej informacji, zobacz [Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Zarządzanie kodem źródłowym i współpraca z innymi osobami

Kodem źródłowym można zarządzać w repozytoriach Git hostowanych przez dowolnego dostawcę, w tym usługę GitHub. Możesz też [Azure DevOps Services](/azure/devops/index) zarządzać kodem obok usterek i elementów roboczych w całym projekcie. Zobacz [Wprowadzenie do usługi Git i Azure Repos,](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) aby dowiedzieć się więcej na temat zarządzania repozytoriami Git w usłudze Visual Studio użyciu Team Explorer. Visual Studio ma również inne wbudowane funkcje kontroli źródła. Aby dowiedzieć się więcej na ich temat, zobacz [Nowe funkcje usługi Git Visual Studio (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Services to usługi oparte na chmurze umożliwiające planowanie, hostowanie, automatyzowanie i wdrażanie oprogramowania oraz współpracę w zespołach. Azure DevOps Services obsługują zarówno repozytoria Git (rozproszoną kontrolę wersji), jak i Kontrola wersji serwera Team Foundation (scentralizowaną kontrolę wersji). Obsługują one potoki ciągłej kompilacji i wydania (CI/CD) kodu przechowywanego w systemach kontroli wersji. Azure DevOps Services obsługuje również metodologie testowania Scrum, CMMI i Agile.

Team Foundation Server (TFS) to centrum zarządzania cyklem życia aplikacji dla Visual Studio. Dzięki temu wszyscy uczestnicy procesu tworzenia oprogramowania mogą uczestniczyć w jednym rozwiązaniu. Program TFS jest również przydatny do zarządzania heterogenicznymi zespołami i projektami.

Jeśli masz organizację Azure DevOps lub Team Foundation Server w sieci, możesz nawiązać z nią połączenie za pośrednictwem **Team Explorer** okna Visual Studio. W tym oknie można sprawdzać kod w kontroli kodu lub poza kontrolą źródła, zarządzać elementami roboczymi, rozpoczynać kompilacje oraz uzyskać dostęp do pomieszczeń zespołu i obszarów roboczych. Możesz otworzyć **Team Explorer** polu wyszukiwania lub w menu głównym z menu Wyświetl Team Explorer  >   lub z połączenia **team**  >  **manage**.

Na poniższej ilustracji **przedstawiono okno Team Explorer** rozwiązania hostowane w Azure DevOps Services.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

Możesz również zautomatyzować proces kompilacji, aby skompilować kod, który deweloperzy w Twoim zespole zaewidencjonowali do kontroli wersji. Można na przykład skompilować jeden lub więcej projektów w nocy lub za każdym razem, kiedy kod jest zaewidencjonowany. Aby uzyskać więcej informacji, zobacz [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="extend-visual-studio"></a>Rozszerzanie funkcjonalności programu Visual Studio

Jeśli Visual Studio nie ma dokładnie potrzebnej funkcjonalności, możesz ją dodać. Możesz spersonalizować ideę na podstawie przepływu pracy i stylu, dodać obsługę narzędzi zewnętrznych, które nie są jeszcze zintegrowane z usługą Visual Studio, i zmodyfikować istniejące funkcje, aby zwiększyć produktywność. Aby znaleźć najnowszą wersję zestawu VISUAL STUDIO EXTENSIBILITY TOOLS (VS SDK), zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Możesz użyć narzędzia .NET Compiler Platform ("Roslyn"), aby napisać własne analizatory kodu i generatory kodu. Znajdź wszystko, czego potrzebujesz, na [stronie Roslyn](https://github.com/dotnet/Roslyn).

Znajdź [istniejące rozszerzenia dla](https://marketplace.visualstudio.com/vs) Visual Studio utworzonych przez deweloperów firmy Microsoft, a także naszą społeczność deweloperów.

Aby dowiedzieć się więcej na temat rozszerzania Visual Studio, zobacz [Rozszerzanie Visual Studio IDE.](https://visualstudio.microsoft.com/vs/extend/)

## <a name="see-also"></a>Zobacz też

- [omówienie Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Co nowego w programie Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [Co nowego w programie Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)

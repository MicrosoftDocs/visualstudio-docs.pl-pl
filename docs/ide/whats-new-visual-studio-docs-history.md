---
title: 'Dokumentacja programu Visual Studio: historia nowości '
titleSuffix: ''
description: Historia nowości w dokumentacji programu Visual Studio
ms.date: 09/30/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 750fcb907350d3bd135bc86e5d1bc1ed211c4a7b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400144"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Historia nowości w dokumentacji programu Visual Studio

Witamy w historii nowości w dokumentacji programu Visual Studio. Ten temat zawiera istotne zmiany w dokumentach sprzed 2020 września (od lipca 2020). Aby uzyskać najnowsze informacje o nowościach, zobacz [Visual Studio docs: co nowego w](whats-new-visual-studio-docs.md)dokumentacji.

## <a name="august-2020"></a>Sierpień 2020 r.
### <a name="azure"></a>Azure

**Nowe artykuły**

- [Dodawanie Application Insights platformy Azure przy użyciu usług połączonych programu Visual Studio](../azure/azure-app-insights-add-connected-service.md) — usługi połączone dla programu VS 2019 16,7
- [Dodawanie pamięci podręcznej platformy Azure dla Redis przy użyciu usług połączonych programu Visual Studio](../azure/azure-cache-for-redis-add-connected-service.md) — usługi połączone dla programu VS 2019 16,7
- [Dodawanie Azure Cosmos DB do aplikacji przy użyciu usług połączonych programu Visual Studio](../azure/azure-cosmosdb-add-connected-service.md) — połączone usługi dla programu VS 2019 16,7
- [Dodaj usługę Azure sygnalizacji przy użyciu usług połączonych programu Visual Studio](../azure/azure-signalr-add-connected-service.md) — połączone usługi dla programu VS 2019 16,7
- [Dodaj połączenie z](../azure/azure-sql-database-add-connected-service.md) usługami połączonymi Azure SQL Database dla programu VS 2019 16,7

**Zaktualizowane artykuły**

- [Dodawanie usługi Azure Storage przy użyciu usług połączonych programu Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Usługi połączone dla programu VS 2019 16,7
  - Artykuł usługi połączone z usługą Azure Storage: obsługiwane typy interfejsu użytkownika i projektu

### <a name="code-quality"></a>Jakość kodu

**Nowe artykuły**

- [CA1310: Określ StringComparison do poprawnego](/dotnet/fundamentals/code-analysis/quality-rules/ca1310) — Dodaj dokumentację dla CA1310 i dokumentację aktualizacji dla CA1307
- [CA1837: Użyj środowiska Environment. ProcessId zamiast procesu. GetCurrentProcess (). ID](/dotnet/fundamentals/code-analysis/quality-rules/ca1837) -docs dla CA1837
- [CA1838: Unikaj `StringBuilder` parametrów dla P/Invoke](/dotnet/fundamentals/code-analysis/quality-rules/ca1838) -Dodaj dokumentację dla CA1838
- [CA2008: nie twórz zadań bez przekazywania TaskScheduler](/dotnet/fundamentals/code-analysis/quality-rules/ca2008) — Dodawanie dokumentacji dla CA2008
- [CA2249: Rozważ użycie ciągu. Contains zamiast String. IndexOf](/dotnet/fundamentals/code-analysis/quality-rules/ca2249) -docs dla CA2249
- [CA2361: Upewnij się, że automatycznie wygenerowana Klasa zawierająca zestaw danych. ReadXml () nie jest używana z niezaufanymi danymi](/dotnet/fundamentals/code-analysis/quality-rules/ca2361) — więcej reguł zestawu danych/obiektów DataTable
- [CA2362: niebezpieczny zestaw danych lub DataTable w wygenerowanym automatycznie typie możliwym do serializacji może być narażony na ataki zdalnego wykonywania kodu](/dotnet/fundamentals/code-analysis/quality-rules/ca2362) — więcej reguł zestawu danych/obiektów DataTable
- [IL3000: Unikaj używania dostępu do ścieżki pliku zestawu podczas publikowania jako jednoplikowej](/dotnet/fundamentals/code-analysis/quality-rules/il3000) dokumentacji do IL3000
- [IL3001: Unikaj uzyskiwania dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczy plik](/dotnet/fundamentals/code-analysis/quality-rules/il3001) — Dodaj dokumenty dla IL3001

**Aktualny**

- [CA1002: nie ujawniaj list ogólnych](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) — Dodaj określając — sekcja powierzchni interfejsu API
- [CA1046: nie należy przeciążać operatora Equals w typach referencyjnych](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) — Dodaj określając — sekcja powierzchni
- [CA1307: Określ StringComparison dla przejrzystości](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) — Dodaj dokumentację dla CA1310 i dokumentację aktualizacji dla CA1307
- [CA1700: nie należy określać wartości wyliczeniowych &#39;zastrzeżony&#39;](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) — Dodaj określając — sekcja powierzchni
- [CA1707: identyfikatory nie powinny zawierać podkreśleń](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) — Dodawanie określającej sekcji powierzchni interfejsu API
- [CA1822: Oznacz elementy członkowskie jako](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) częściowe Dodawanie określając-interfejsu API
- [CA2351: Upewnij się, że dane wejściowe DataSet. ReadXml () są](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) regułami zaufania-więcej zestawów danych/obiektów DataTable
- [Zainstaluj analizatory innych firm](../code-quality/install-roslyn-analyzers.md) — Zmieniono strukturę i tytuły dla dokumentacji analizy kodu

### <a name="containers"></a>Kontenery

**Zaktualizowane artykuły**

- [Wdrażanie kontenera ASP.NET w rejestrze kontenerów za pomocą programu Visual Studio](../containers/hosting-web-apps-in-docker.md) — aktualizacje narzędzi do kontenerów dla programu visual Studio 16,7 — interfejs użytkownika publikacji
- [Wprowadzenie do narzędzi Visual Studio Kubernetes Tools](../containers/bridge-to-kubernetes.md) — samouczek Kubernetes: Dodawanie kroków do usunięcia

### <a name="deployment"></a>Wdrożenie

**Nowe artykuły**

- [Instalator programu Visual Studio rozszerzenia projektów i .NET Core 3,1](../deployment/installer-projects-net-core.md) — Tworzenie nowej strony pomocy dla funkcji projekty Instalatora platformy .net Core 3,1

**Zaktualizowane artykuły**

- [Wdrażanie aplikacji w folderze, usługach IIS, na platformie Azure lub w innych](../deployment/deploying-applications-services-and-components-resources.md) aktualizacjach wdrożenia docelowego
- [Wdrożenie w programie Visual Studio](../deployment/index.yml) — aktualizacje wdrożenia

### <a name="extensibility"></a>Rozszerzalność

**Zaktualizowane artykuły**
- [Podtypy projektu](../extensibility/internals/project-subtypes.md) — wcięcie elementów listy poprawek
- [Odwołanie do wartości koloru dla programu Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) -AB # 1759333 poprawka braku nagłówków kolumn

### <a name="get-started"></a>Rozpoczęcie pracy

**Zaktualizowane artykuły**

- [Krok 5. wdrażanie aplikacji ASP.NET Core na platformie Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) — aktualizacje samouczka wideo dla nowego interfejsu użytkownika połączonych usług

### <a name="ide"></a>IDE

**Nowe artykuły**

- [Zmień klawisz pomocy F1 w programie Visual Studio](./not-in-toc/change-f1-help-key.md) — domyślna strona pomocy F1
- [F1 Pomoc dla edytora tekstu](./not-in-toc/default-f1-text-editor.md) — Strona pomocy dla domyślnego klawisza F1
- [Konwersja `typeof` na `nameof` ](./reference/convert-typeof-to-nameof.md) -Convert typeof do nameof refaktoryzacji
- [Uprość wyrażenie LINQ](./reference/simplify-linq-expression.md) — Uprość refaktoryzację wyrażeń LINQ

**Zaktualizowane artykuły**

- [Dostosowywanie układów okien w programie Visual Studio](./customizing-window-layouts-in-visual-studio.md) — Dodawanie monikerów z zakładkami dokumentu pionowych aby dostosować układ okna tematu
- [Jak zgłosić problem z programem Visual Studio lub Instalator programu Visual Studio](./how-to-report-a-problem-with-visual-studio.md)
  - Dodano więcej informacji do NMI
  - Redid cały raport na stronie problemu
- [F1](./not-in-toc/default.md) — domyślna strona pomocy dla F1
- [Autoodzyskiwanie, środowisko, opcje](./reference/autorecover-environment-options-dialog-box.md) — okno dialogowe — Dodawanie informacji o zaktualizowanych lokalizacjach plików zapisywania automatycznego
- [Opcje, Edytor tekstu, podstawowa (Visual Basic), zaawansowana](./reference/options-text-editor-basic-visual-basic.md) dokumentacja podstawowa dla wskazówek dotyczących nazw parametrów wbudowanych
- [Opcje, Edytor tekstu, C#, zaawansowane](./reference/options-text-editor-csharp-advanced.md) — Dodano dokumentację podstawową dla wskazówek dotyczących nazw parametrów wbudowanych
- [Porady i wskazówki dotyczące wydajności programu Visual Studio](./visual-studio-performance-tips-and-tricks.md) — Dodaj informacje "Wyłącz tryb mapowania" i "Wyłącz zawijanie wyrazów"
- [Co nowego w programie Visual studio 2019](./whats-new-visual-studio-2019.md) — aktualizowanie nowości w programie visual Studio 2019 z 16,7 ga

### <a name="rtvs"></a>RTVS

**Zaktualizowane artykuły**

- Pracuj z tabelami poprawionymi [SQL Server i R](../rtvs/integrating-sql-server-with-r.md) , aby uwzględnić nagłówki kolumn

## <a name="july-2020"></a>Lipiec 2020 r.
### <a name="code-quality"></a>Jakość kodu

**Nowe artykuły**

- [CA1417: nie używaj `OutAttribute` w parametrach ciągu dla P/Invoke](/dotnet/fundamentals/code-analysis/quality-rules/ca1417) -Dodaj dokumentację dla CA1417
- [CA1805: nie należy inicjować niepotrzebnie.](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) -Dodaj dokumenty dla CA1805
- [CA1836: Preferuj IsEmpty w liczbie, gdy jest dostępna](/dotnet/fundamentals/code-analysis/quality-rules/ca1836) — Dodaj dokumentację dla CA1836 (Preferuj IsEmpty w liczbie)
- [CA2016: Przekaż parametr CancellationToken do metod, które pobierają jeden](/dotnet/fundamentals/code-analysis/quality-rules/ca2016) -dokument CA2016-przekazuj parametr CancellationToken do metod, które przyjmują jeden
- [CA2350: Upewnij się, że dane wejściowe elementu DataTable. ReadXml () są zaufane](/dotnet/fundamentals/code-analysis/quality-rules/ca2350) -początkowe reguły deserializacji zestawu danych/DataTable
- [CA2351: Upewnij się, że dane wejściowe DataSet. ReadXml () są zaufane](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) -początkowe reguły deserializacji zestawu danych/DataTable
- [CA2352: niebezpieczny zestaw danych lub DataTable w typie możliwym do serializacji może być narażony na ataki zdalnego wykonywania kodu](/dotnet/fundamentals/code-analysis/quality-rules/ca2352) — wstępna reguła deserializacji zestawu danych/elementu DataTable
- [CA2353: niebezpieczny zestaw danych lub DataTable w obszarze możliwy do serializacji typ](/dotnet/fundamentals/code-analysis/quality-rules/ca2353) początkowy zestaw danych lub deserializacji elementu DataTable
- [CA2354: niebezpieczny zestaw danych lub element DataTable w odszeregowanym grafie obiektów może być narażony na ataki zdalnego wykonywania kodu](/dotnet/fundamentals/code-analysis/quality-rules/ca2354) — początkowy zestaw danych/reguły deserializacji elementu DataTable
- [CA2355: niebezpieczny zestaw danych lub tabela DataTable w odszeregowanym grafie obiektów](/dotnet/fundamentals/code-analysis/quality-rules/ca2355) — wstępne reguły deserializacji zestawu danych/DataTable
- [CA2356: niebezpieczny zestaw danych lub typ DataTable w grafie serializowanych obiektów sieci Web](/dotnet/fundamentals/code-analysis/quality-rules/ca2356) — wstępne reguły deserializacji zestawu danych/elementu DataTable

### <a name="containers"></a>Kontenery

**Nowe artykuły**

- [Konfigurowanie procesu lokalnego przy użyciu procesu Kubernetes](../containers/configure-bridge-to-kubernetes.md) -Local przy użyciu konfiguracji Kubernetes: YAML
- [Korzystanie z procesu lokalnego z Kubernetes (wersja zapoznawcza)](../containers/bridge-to-kubernetes.md) — migracja miejsc deweloperskich
- [Jak działa proces lokalny z usługą Kubernetes](../containers/overview-bridge-to-kubernetes.md)
  - Proces lokalny dla Kubernetes: Dodaj sekcję routingu
  - Migracja miejsc deweloperskich

### <a name="cross-platform"></a>Wiele platform

**Zaktualizowane artykuły**

- [Dziennik zmian (Visual Studio Tools for Unity, Windows)](/gamedev/unity/change-log-visual-studio-tools-for-unity.md) — nierówności rozszerzenia VSTU dziennika zmian 4.7.1.0
- [Dziennik zmian (Visual Studio Tools for Unity, Mac)](/gamedev/unity/change-log-visual-studio-tools-for-unity-mac.md) — nierówności VSTUM dziennika zmian 2.7.1.0

### <a name="get-started"></a>Rozpoczęcie pracy

**Nowe artykuły**

- [Samouczek: zwiększanie prostej aplikacji konsolowej w języku C#](../get-started/csharp/tutorial-console-part-2.md) — wersja Sidewalk — samouczek w pierwszej wersji

### <a name="ide"></a>IDE

**Nowe artykuły**

- [Wytyczne społeczności deweloperów](./developer-community-guidelines.md) — dodano wskazówki dotyczące DevCom
- [Uzupełnianie IntelliSense dla nieimportowanych typów i metod rozszerzających](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Zainstaluj

**Nowe artykuły**

- [Aktualizowanie programu Visual Studio przy użyciu minimalnego układu w trybie offline](../install/update-minimal-layout.md) — funkcja minimalnej układu dokumentu
- [Przewodnik po programie Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) — Przewodnik dla przedsiębiorstw

### <a name="javascript"></a>JavaScript

**Nowe artykuły**

- [Kompiluj kod TypeScript (Node.js)](../javascript/compile-typescript-code-npm.md) — Kompiluj i skompiluj TypeScript
- [Kompiluj kod TypeScript (ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) — Kompiluj i skompiluj TypeScript

### <a name="msbuild"></a>MSBuild

**Nowe artykuły**

- [Typowe metadane elementu MSBuild](../msbuild/common-msbuild-item-metadata.md) — MSBuild: Dodawanie tabeli dla opcjonalnych metadanych przy użyciu linku i bazy łączy
- [Filtry rozwiązań w programie MSBuild](../msbuild/solution-filters.md) — filtry rozwiązań MSBuild

### <a name="test"></a>Testowanie

**Nowe artykuły**

- [Debugowanie i analizowanie testów jednostkowych za pomocą Eksploratora testów](../test/debug-unit-tests-with-test-explorer.md) — wydajność programu Test Explorer

**Zaktualizowane artykuły**

- [Konfigurowanie testów jednostkowych przy użyciu pliku *. runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Aktualizacje dotyczące konfigurowania testów jednostkowych przy użyciu pliku runsettings
  - Opis opcji polecenia Blame został zmieniony i dodano przykład.
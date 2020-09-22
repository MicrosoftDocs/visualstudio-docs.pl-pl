---
title: 'Dokumentacja programu Visual Studio: co nowego w sierpniu 2020 '
titleSuffix: ''
description: Co nowego w dokumentacji programu Visual Studio dla sierpnia 2020.
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 2411299fbab6dfba8ced0f689bd33825b62614af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808984"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Dokumentacja programu Visual Studio: co nowego w sierpniu 2020

Witamy w nowościach w dokumentacji programu Visual Studio dla sierpnia 2020. W tym artykule wymieniono niektóre istotne zmiany w dokumentach w tym okresie. Aby uzyskać informacje na temat Nowości w poprzednich miesiącach, zobacz temat [co to jest historia](whats-new-visual-studio-docs-history.md) nowości.

## <a name="azure"></a>Azure

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

## <a name="code-quality"></a>Jakość kodu

**Nowe artykuły**

- [CA1310: Określ StringComparison do poprawnego](../code-quality/ca1310.md) — Dodaj dokumentację dla CA1310 i dokumentację aktualizacji dla CA1307
- [CA1837: Użyj środowiska Environment. ProcessId zamiast procesu. GetCurrentProcess (). ID](../code-quality/ca1837.md) -docs dla CA1837
- [CA1838: Unikaj `StringBuilder` parametrów dla P/Invoke](../code-quality/ca1838.md) -Dodaj dokumentację dla CA1838
- [CA2008: nie twórz zadań bez przekazywania TaskScheduler](../code-quality/ca2008.md) — Dodawanie dokumentacji dla CA2008
- [CA2249: Rozważ użycie ciągu. Contains zamiast String. IndexOf](../code-quality/ca2249.md) -docs dla CA2249
- [CA2361: Upewnij się, że automatycznie wygenerowana Klasa zawierająca zestaw danych. ReadXml () nie jest używana z niezaufanymi danymi](../code-quality/ca2361.md) — więcej reguł zestawu danych/obiektów DataTable
- [CA2362: niebezpieczny zestaw danych lub DataTable w wygenerowanym automatycznie typie możliwym do serializacji może być narażony na ataki zdalnego wykonywania kodu](../code-quality/ca2362.md) — więcej reguł zestawu danych/obiektów DataTable
- [IL3000: Unikaj używania dostępu do ścieżki pliku zestawu podczas publikowania jako jednoplikowej](../code-quality/il3000.md) dokumentacji do IL3000
- [IL3001: Unikaj uzyskiwania dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczy plik](../code-quality/il3001.md) — Dodaj dokumenty dla IL3001

**Aktualny**

- [CA1002: nie ujawniaj list ogólnych](../code-quality/ca1002.md) — Dodaj określając — sekcja powierzchni interfejsu API
- [CA1046: nie należy przeciążać operatora Equals w typach referencyjnych](../code-quality/ca1046.md) — Dodaj określając — sekcja powierzchni
- [CA1307: Określ StringComparison dla przejrzystości](../code-quality/ca1307.md) — Dodaj dokumentację dla CA1310 i dokumentację aktualizacji dla CA1307
- [CA1700: nie należy określać wartości wyliczeniowych &#39;zastrzeżony&#39;](../code-quality/ca1700.md) — Dodaj określając — sekcja powierzchni
- [CA1707: identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707.md) — Dodawanie określającej sekcji powierzchni interfejsu API
- [CA1822: Oznacz elementy członkowskie jako](../code-quality/ca1822.md) częściowe Dodawanie określając-interfejsu API
- [CA2351: Upewnij się, że dane wejściowe DataSet. ReadXml () są](../code-quality/ca2351.md) regułami zaufania-więcej zestawów danych/obiektów DataTable
- [Zainstaluj analizatory innych firm](../code-quality/install-roslyn-analyzers.md) — Zmieniono strukturę i tytuły dla dokumentacji analizy kodu

## <a name="containers"></a>Kontenery

**Zaktualizowane artykuły**

- [Wdrażanie kontenera ASP.NET w rejestrze kontenerów za pomocą programu Visual Studio](../containers/hosting-web-apps-in-docker.md) — aktualizacje narzędzi do kontenerów dla programu visual Studio 16,7 — interfejs użytkownika publikacji
- [Wprowadzenie do narzędzi Visual Studio Kubernetes Tools](../containers/tutorial-kubernetes-tools.md) — samouczek Kubernetes: Dodawanie kroków do usunięcia

## <a name="deployment"></a>Wdrożenie

**Nowe artykuły**

- [Instalator programu Visual Studio rozszerzenia projektów i .NET Core 3,1](../deployment/installer-projects-net-core.md) — Tworzenie nowej strony pomocy dla funkcji projekty Instalatora platformy .net Core 3,1

**Zaktualizowane artykuły**

- [Wdrażanie aplikacji w folderze, usługach IIS, na platformie Azure lub w innych](../deployment/deploying-applications-services-and-components-resources.md) aktualizacjach wdrożenia docelowego
- [Wdrożenie w programie Visual Studio](../deployment/index.yml) — aktualizacje wdrożenia

## <a name="extensibility"></a>Rozszerzalność

**Zaktualizowane artykuły**
- [Podtypy projektu](../extensibility/internals/project-subtypes.md) — wcięcie elementów listy poprawek
- [Odwołanie do wartości koloru dla programu Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) -AB # 1759333 poprawka braku nagłówków kolumn

## <a name="get-started"></a>Rozpoczęcie pracy

**Zaktualizowane artykuły**

- [Krok 5. wdrażanie aplikacji ASP.NET Core na platformie Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) — aktualizacje samouczka wideo dla nowego interfejsu użytkownika połączonych usług

## <a name="ide"></a>IDE

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

## <a name="rtvs"></a>RTVS

**Zaktualizowane artykuły**

- Pracuj z tabelami poprawionymi [SQL Server i R](../rtvs/integrating-sql-server-with-r.md) , aby uwzględnić nagłówki kolumn

## <a name="community-contributors"></a>Współautorzy społeczności

Następujące osoby współczyniły się do dokumentacji programu Visual Studio w tym okresie. Dziękujemy! Dowiedz się, jak współtworzyć dokumentację programu Visual Studio, postępując zgodnie ze wskazówkami w [przewodniku współautora](/contribute/).

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG) -Alex Black (11)
- [Youssef1313](https://github.com/Youssef1313) -Youssef Victor (8)
- [hyoshioka0128](https://github.com/hyoshioka0128) -Hiroshi Yoshioka (3)
- [AstroChoco](https://github.com/AstroChoco) -Qian lu (czekolada) (1)
- [athyunnath](https://github.com/athyunnath) -athyunnath Eleti (1)
- [Caro-Oviedo](https://github.com/caro-oviedo) -Caro Oviedo (1)
- [Evangelink](https://github.com/Evangelink) -Amaury levé (1)
- [jethas-bennettjones](https://github.com/jethas-bennettjones) -Shafiq Jetha (1)
- [nebuk89](https://github.com/nebuk89) -Ben de St paer-Gotch (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov) -Petr Kulikov (1)
- [riQQ](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger) -Timor Cornelius Metzger (1)
- [weitzhandler](https://github.com/weitzhandler) -Shimmy (1)
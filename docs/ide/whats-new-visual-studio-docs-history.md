---
title: 'Dokumentacja programu Visual Studio: historia nowości '
titleSuffix: ''
description: Historia nowości w dokumentacji programu Visual Studio
ms.date: 09/01/2020
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
ms.openlocfilehash: 8505f98163c57fe276bcf4c76195fe843300394f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809469"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Historia nowości w dokumentacji programu Visual Studio

Witamy w historii nowości w dokumentacji programu Visual Studio. Ten temat zawiera istotne zmiany w dokumentach przed 2020 sierpnia (od lipca 2020). Aby uzyskać najnowsze informacje o nowościach, zobacz [Visual Studio docs: co nowego w](whats-new-visual-studio-docs.md)dokumentacji.

## <a name="july-2020"></a>Lipiec 2020 r.
### <a name="code-quality"></a>Jakość kodu

**Nowe artykuły**

- [CA1417: nie używaj `OutAttribute` w parametrach ciągu dla P/Invoke](../code-quality/ca1417.md) -Dodaj dokumentację dla CA1417
- [CA1805: nie należy inicjować niepotrzebnie.](../code-quality/ca1805.md) -Dodaj dokumenty dla CA1805
- [CA1836: Preferuj IsEmpty w liczbie, gdy jest dostępna](../code-quality/ca1836.md) — Dodaj dokumentację dla CA1836 (Preferuj IsEmpty w liczbie)
- [CA2016: Przekaż parametr CancellationToken do metod, które pobierają jeden](../code-quality/ca2016.md) -dokument CA2016-przekazuj parametr CancellationToken do metod, które przyjmują jeden
- [CA2350: Upewnij się, że dane wejściowe elementu DataTable. ReadXml () są zaufane](../code-quality/ca2350.md) -początkowe reguły deserializacji zestawu danych/DataTable
- [CA2351: Upewnij się, że dane wejściowe DataSet. ReadXml () są zaufane](../code-quality/ca2351.md) -początkowe reguły deserializacji zestawu danych/DataTable
- [CA2352: niebezpieczny zestaw danych lub DataTable w typie możliwym do serializacji może być narażony na ataki zdalnego wykonywania kodu](../code-quality/ca2352.md) — wstępna reguła deserializacji zestawu danych/elementu DataTable
- [CA2353: niebezpieczny zestaw danych lub DataTable w obszarze możliwy do serializacji typ](../code-quality/ca2353.md) początkowy zestaw danych lub deserializacji elementu DataTable
- [CA2354: niebezpieczny zestaw danych lub element DataTable w odszeregowanym grafie obiektów może być narażony na ataki zdalnego wykonywania kodu](../code-quality/ca2354.md) — początkowy zestaw danych/reguły deserializacji elementu DataTable
- [CA2355: niebezpieczny zestaw danych lub tabela DataTable w odszeregowanym grafie obiektów](../code-quality/ca2355.md) — wstępne reguły deserializacji zestawu danych/DataTable
- [CA2356: niebezpieczny zestaw danych lub typ DataTable w grafie serializowanych obiektów sieci Web](../code-quality/ca2356.md) — wstępne reguły deserializacji zestawu danych/elementu DataTable

### <a name="containers"></a>Containers

**Nowe artykuły**

- [Konfigurowanie procesu lokalnego przy użyciu procesu Kubernetes](../containers/configure-local-process-with-kubernetes.md) -Local przy użyciu konfiguracji Kubernetes: YAML
- [Korzystanie z procesu lokalnego z Kubernetes (wersja zapoznawcza)](../containers/local-process-kubernetes.md) — migracja miejsc deweloperskich
- [Jak działa proces lokalny z usługą Kubernetes](../containers/overview-local-process-kubernetes.md)
  - Proces lokalny dla Kubernetes: Dodaj sekcję routingu
  - Migracja miejsc deweloperskich

### <a name="cross-platform"></a>Wiele platform

**Zaktualizowane artykuły**

- [Dziennik zmian (Visual Studio Tools for Unity, Windows)](../cross-platform/change-log-visual-studio-tools-for-unity.md) — nierówności rozszerzenia VSTU dziennika zmian 4.7.1.0
- [Dziennik zmian (Visual Studio Tools for Unity, Mac)](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) — nierówności VSTUM dziennika zmian 2.7.1.0

### <a name="get-started"></a>Wprowadzenie

**Nowe artykuły**

- [Samouczek: zwiększanie prostej aplikacji konsolowej w języku C#](../get-started/csharp/tutorial-console-part-2.md) — wersja Sidewalk — samouczek w pierwszej wersji

### <a name="ide"></a>IDE

**Nowe artykuły**

- [Wytyczne społeczności deweloperów](./developer-community-guidelines.md) — dodano wskazówki dotyczące DevCom
- [Uzupełnianie IntelliSense dla nieimportowanych typów i metod rozszerzających](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Instalowanie

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
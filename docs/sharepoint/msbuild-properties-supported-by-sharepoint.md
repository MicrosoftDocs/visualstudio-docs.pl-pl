---
title: Właściwości MSBuild obsługiwane przez program SharePoint | Microsoft Docs
description: Odczytaj listę nazw i opisów właściwości programu MSBuild, które są obsługiwane przez program i są specyficzne dla programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 20458cc7047e913e13f4594380d4b4946b44ec17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938515"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Właściwości MsBuild obsługiwane przez program SharePoint
  Wszystkie [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości zdefiniowane w pliku Microsoft. VisualStudio. SharePoint. targets, pliku projektu lub pliku użytkownika projektu mogą być używane w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektach programu SharePoint. Oprócz wspólnych [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Właściwości dostarczonych przez projekt, program SharePoint definiuje dodatkowe właściwości, które są specyficzne dla projektów programu SharePoint.

 Aby zapoznać się z listą typowych [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości, zobacz [typowe właściwości projektu MSBuild](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Aby zapoznać się z pełną listą właściwości obsługiwanych przez język programowania, należy zapoznać się z plikiem *. targets* , plikiem projektu (*. csproj* lub *. vbproj*) lub plikiem użytkownika projektu (*csproj. User* lub *. vbproj. User*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>Właściwości MsBuild specyficzne dla programu SharePoint
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości, które są stosowane w odniesieniu do projektów programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Istnieją inne właściwości, ale są one używane do użytku wewnętrznego.

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|SharePointSiteUrl|Ciąg, który reprezentuje [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] witrynę programu SharePoint.|
|SandboxedSolution|Wartość logiczna wskazująca, czy rozwiązanie jest rozwiązaniem w trybie piaskownicy.|
|ActiveDeploymentConfiguration|Konfiguracja aktywnego wdrożenia.|
|IncludeAssemblyInPackage|Wartość logiczna wskazująca, czy zestaw jest zawarty w pliku pakietu.|
|PreDeploymentCommand|Wartość ciągu, która reprezentuje polecenie, które ma zostać wykonane w kroku polecenia przed wdrożeniem.|
|PostDeploymentCommand|Wartość ciągu, która reprezentuje polecenie, które ma zostać wykonane w kroku polecenia po wdrożeniu.|
|CustomBeforeSharePointTargets|Ciąg, który reprezentuje ścieżkę [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] pliku targets. Jeśli plik targets istnieje i jest zdefiniowany, zostanie zaimportowany przed dowolnymi danymi obiektów docelowych programu SharePoint. Ta właściwość umożliwia dostosowanie procesu pakietu przez zdefiniowanie właściwości związanych z opakowaniem bez modyfikowania wysłanego pliku obiektów docelowych programu SharePoint, ale plik docelowy nadal dotyczy wszystkich projektów programu SharePoint.|
|CustomAfterSharePointTargets|Ciąg, który reprezentuje ścieżkę [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] pliku targets. Jeśli plik targets istnieje i jest zdefiniowany, zostaje zaimportowany po wszystkich danych programu SharePoint targets. Ta właściwość umożliwia dostosowanie procesu pakietu przez Zastępowanie właściwości i obiektów docelowych związanych z pakietem bez konieczności modyfikowania wysłanego pliku SharePoint targets, ale plik targets nadal stosuje się do wszystkich projektów programu SharePoint.|
|Element layoutPath|Ciąg, który reprezentuje katalog główny, w którym każdy z plików przeznaczonych do spakowania jest tymczasowo umieszczony przed dodaniem go do pliku *. wsp* . Ta ścieżka może być przydatna, gdy przesłonisz cele BeforeLayout i AfterLayout w celu dodania, usunięcia lub zmodyfikowania plików do spakowania, ponieważ można jej użyć do zmiany zawartości pliku *. wsp* .|
|BasePackagePath|Ciąg, który reprezentuje folder, w którym znajduje się pakiet. Ta wartość używa katalogu wyjściowego projektu, takiego jak Bin\Debug.|
|PackageExtension|Ciąg, który reprezentuje rozszerzenie nazwy pliku do dołączenia do pakietu. Wartość domyślna to wsp.|
|AssemblyDeploymentTarget|Ciąg reprezentujący lokalizację, w której zestaw projektu jest wdrożony na serwerze programu SharePoint. Jej wartość jest GlobalAssemblyCache (domyślnie) lub aplikacja WebApplication. Tę właściwość można również ustawić w okno Właściwości.|
|PackageWithValidation|Wartość logiczna określająca, czy Walidacja jest wykonywana przed opakowaniem. Ta właściwość umożliwia ignorowanie błędów walidacji podczas kompilowania pakietów.|
|ValidatePackageDependsOn|Ciąg, który definiuje dodatkowe elementy docelowe do wykonania przed elementem docelowym ValidatePackage.|
|TokenReplacementFileExensions|Ciąg definiujący pliki, których tokeny zostały zastąpione podczas tworzenia pakietów.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Korzystanie z właściwości programu MsBuild na stronie właściwości
 Aby zapewnić elastyczność, zamiast korzystać z zakodowanych ciągów w **wierszach poleceń przed wdrożeniem** i **po wdrożeniu** na stronie właściwości programu SharePoint, można użyć właściwości programu SharePoint jako argumentów. Na przykład zamiast określania określonego [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] ciągu dla witryny programu SharePoint, zamiast tego można użyć `$(SharePointSiteUrl)` .

> [!NOTE]
> [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]Aby określić właściwość, można użyć składni zmiennej `$(` *PropertyName* `)` lub zmiennej środowiskowej `%` *PropertyName* `%` .

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
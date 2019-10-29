---
title: Właściwości MSBuild obsługiwane przez program SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5470160c6b0af1af39238a14319ad497e1541a43
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985165"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Właściwości MsBuild obsługiwane przez program SharePoint
  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektach programu SharePoint można używać dowolnej właściwości [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] zdefiniowanej w pliku Microsoft. VisualStudio. SharePoint. targets, pliku projektu lub pliku użytkownika projektu. Oprócz wspólnych właściwości [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] dostarczonych przez projekt program SharePoint definiuje dodatkowe właściwości, które są specyficzne dla projektów programu SharePoint.

 Aby uzyskać listę typowych właściwości [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)], zobacz [typowe właściwości projektu MSBuild](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Aby zapoznać się z pełną listą właściwości obsługiwanych przez język programowania, należy zapoznać się z plikiem *. targets* , plikiem projektu ( *. csproj* lub *. vbproj*) lub plikiem użytkownika projektu (*csproj. User* lub *. vbproj. User*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>Właściwości MsBuild specyficzne dla programu SharePoint
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości, które są stosowane w odniesieniu do projektów programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Istnieją inne właściwości, ale są one używane do użytku wewnętrznego.

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|SharePointSiteUrl|Ciąg, który reprezentuje [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] do witryny programu SharePoint.|
|SandboxedSolution|Wartość logiczna wskazująca, czy rozwiązanie jest rozwiązaniem w trybie piaskownicy.|
|ActiveDeploymentConfiguration|Konfiguracja aktywnego wdrożenia.|
|IncludeAssemblyInPackage|Wartość logiczna wskazująca, czy zestaw jest zawarty w pliku pakietu.|
|PreDeploymentCommand|Wartość ciągu, która reprezentuje polecenie, które ma zostać wykonane w kroku polecenia przed wdrożeniem.|
|PostDeploymentCommand|Wartość ciągu, która reprezentuje polecenie, które ma zostać wykonane w kroku polecenia po wdrożeniu.|
|CustomBeforeSharePointTargets|Ciąg, który reprezentuje ścieżkę pliku obiektów docelowych [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]. Jeśli plik targets istnieje i jest zdefiniowany, zostanie zaimportowany przed dowolnymi danymi obiektów docelowych programu SharePoint. Ta właściwość umożliwia dostosowanie procesu pakietu przez zdefiniowanie właściwości związanych z opakowaniem bez modyfikowania wysłanego pliku obiektów docelowych programu SharePoint, ale plik docelowy nadal dotyczy wszystkich projektów programu SharePoint.|
|CustomAfterSharePointTargets|Ciąg, który reprezentuje ścieżkę pliku obiektów docelowych [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]. Jeśli plik targets istnieje i jest zdefiniowany, zostaje zaimportowany po wszystkich danych programu SharePoint targets. Ta właściwość umożliwia dostosowanie procesu pakietu przez Zastępowanie właściwości i obiektów docelowych związanych z pakietem bez konieczności modyfikowania wysłanego pliku SharePoint targets, ale plik targets nadal stosuje się do wszystkich projektów programu SharePoint.|
|Element layoutPath|Ciąg, który reprezentuje katalog główny, w którym każdy z plików przeznaczonych do spakowania jest tymczasowo umieszczony przed dodaniem go do pliku *. wsp* . Ta ścieżka może być przydatna, gdy przesłonisz cele BeforeLayout i AfterLayout w celu dodania, usunięcia lub zmodyfikowania plików do spakowania, ponieważ można jej użyć do zmiany zawartości pliku *. wsp* .|
|BasePackagePath|Ciąg, który reprezentuje folder, w którym znajduje się pakiet. Ta wartość używa katalogu wyjściowego projektu, takiego jak Bin\Debug.|
|PackageExtension|Ciąg, który reprezentuje rozszerzenie nazwy pliku do dołączenia do pakietu. Wartość domyślna to wsp.|
|AssemblyDeploymentTarget|Ciąg reprezentujący lokalizację, w której zestaw projektu jest wdrożony na serwerze programu SharePoint. Jej wartość jest GlobalAssemblyCache (domyślnie) lub aplikacja WebApplication. Tę właściwość można również ustawić w okno Właściwości.|
|PackageWithValidation|Wartość logiczna określająca, czy Walidacja jest wykonywana przed opakowaniem. Ta właściwość umożliwia ignorowanie błędów walidacji podczas kompilowania pakietów.|
|ValidatePackageDependsOn|Ciąg, który definiuje dodatkowe elementy docelowe do wykonania przed elementem docelowym ValidatePackage.|
|TokenReplacementFileExensions|Ciąg definiujący pliki, których tokeny zostały zastąpione podczas tworzenia pakietów.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Korzystanie z właściwości programu MsBuild na stronie właściwości
 Aby zapewnić elastyczność, zamiast korzystać z zakodowanych ciągów w **wierszach poleceń przed wdrożeniem** i **po wdrożeniu** na stronie właściwości programu SharePoint, można użyć właściwości programu SharePoint jako argumentów. Na przykład zamiast określania określonego ciągu [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] dla witryny programu SharePoint, zamiast tego można użyć `$(SharePointSiteUrl)`.

> [!NOTE]
> Można użyć składni [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] zmiennej `$(`*propertyname*`)` lub składni zmiennej środowiskowej `%`*PropertyName*`%`, aby określić właściwość.

## <a name="see-also"></a>Zobacz także

- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
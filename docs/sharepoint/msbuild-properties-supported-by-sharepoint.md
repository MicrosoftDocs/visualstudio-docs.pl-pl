---
title: Właściwości MSBuild obsługiwane przez program SharePoint | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 242412c5cf29a39294c7f223d5ebf34b56b6ea82
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866756"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Właściwości MsBuild obsługiwane przez program SharePoint
  Wszelkie [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości zdefiniowane w pliku, plik projektu lub pliku użytkownika projektu Microsoft.VisualStudio.SharePoint.targets mogą być używane w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów programu SharePoint. Oprócz typowe [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości dostarczonych przez projekt programu SharePoint definiuje dodatkowe właściwości, które są specyficzne dla projektów programu SharePoint.  
  
 Aby uzyskać listę typowych [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości, zobacz [wspólne właściwości projektów MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687). Aby uzyskać pełną listę właściwości obsługiwanych przez język programowania, Szukaj w *.targets* pliku, plik projektu (*.csproj* lub *.vbproj*), lub użytkownik projektu pliku ( *csproj.user* lub *. vbproj.user*).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>Właściwości programu MsBuild specyficzne dla programu SharePoint
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości, które mają zastosowanie do projektów programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Istnieją inne właściwości, ale są one do użytku wewnętrznego.  
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|SharePointSiteUrl|Ciąg, który reprezentuje [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] do witryny programu SharePoint.|  
|SandboxedSolution|Wartość logiczna wskazująca, czy rozwiązanie jest rozwiązanie w trybie piaskownicy.|  
|ActiveDeploymentConfiguration|Konfiguracja aktywnego wdrożenia.|  
|IncludeAssemblyInPackage|Wartość logiczna wskazująca, czy zestaw znajduje się w pliku pakietu.|  
|PreDeploymentCommand|Wartość ciągu, który reprezentuje polecenie do wykonania w kroku polecenia przed wdrożeniem.|  
|PostDeploymentCommand|Wartość ciągu, który reprezentuje polecenie do wykonania w kroku polecenia po wdrożeniu.|  
|CustomBeforeSharePointTargets|Ciąg, który reprezentuje ścieżkę [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] plik docelowy. Jeśli plik elementów docelowych istnieje i jest zdefiniowany, wartość są importowane przed wszystkie dane obiektów docelowych programu SharePoint. Ta właściwość umożliwia dostosowanie procesu pakietu za pomocą wstępnego definiowania właściwości związane z pakietem, bez konieczności modyfikacji dostarczany plik elementów docelowych programu SharePoint, ale plik elementów docelowych nadal ma zastosowanie do wszystkich projektów programu SharePoint.|  
|CustomAfterSharePointTargets|Ciąg, który reprezentuje ścieżkę [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] plik docelowy. Jeśli plik elementów docelowych istnieje i jest zdefiniowana, to po wszystkich importowanych danych obiektów docelowych programu SharePoint. Ta właściwość umożliwia dostosowanie procesu pakietu przez zastąpienie cele i właściwości związane z pakietem bez konieczności modyfikowania dostarczany plik elementów docelowych programu SharePoint, ale plik elementów docelowych nadal ma zastosowanie do wszystkich projektów programu SharePoint.|  
|Element LayoutPath|Ciąg, który reprezentuje katalog główny, w którym każdy z plików do umieszczenia w pakiecie są tymczasowo umieszczone zanim zostaną one dodane do *.wsp* pliku. Ta ścieżka może być użyteczne informacje, kiedy zastępują cele BeforeLayout i AfterLayout, aby dodać, usunąć lub zmodyfikować pliki do umieszczenia w pakiecie, ponieważ służy do zmiany zawartości *.wsp* pliku.|  
|BasePackagePath|Ciąg, który reprezentuje folder, w którym znajduje się pakiet. Ta wartość używa katalogu wyjściowego projektu, takich jak Bin\Debug.|  
|PackageExtension|Ciąg, który reprezentuje rozszerzenie nazwy pliku do dołączenia do pakietu. Wartość domyślna to wsp.|  
|Assemblydeploymenttarget programu MSBuild|Ciąg, który reprezentuje lokalizację, w którym zestaw projektów jest wdrażany na serwerze programu SharePoint. Jego wartość jest GlobalAssemblyCache (ustawienie domyślne) lub aplikacji sieci Web. Tę właściwość można ustawić w taki sposób, w oknie dialogowym właściwości.|  
|PackageWithValidation|Wartość logiczna określająca, czy sprawdzanie poprawności jest wykonywane przed pakowania. Ta właściwość umożliwia ignorowanie błędów sprawdzania poprawności podczas tworzenia pakietów.|  
|ValidatePackageDependsOn|Ciąg, który definiuje dodatkowe obiekty docelowe w celu wykonania przed docelowej ValidatePackage.|  
|TokenReplacementFileExensions|Ciąg, który definiuje pliki, które mają tokenów, który został zastąpiony podczas pakowania.|  
  
## <a name="use-msbuild-properties-in-the-properties-page"></a>Użyj właściwości programu MsBuild na stronie właściwości
 Aby zapewnić elastyczność, zamiast zakodowane sprzętowo ciągi w **wiersz polecenia przed wdrożeniem** i **wiersz polecenia po wdrożeniu** pola na stronie właściwości programu SharePoint, można użyć programu SharePoint właściwości argumentów. Na przykład, zamiast określania określonego [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] ciąg witryny programu SharePoint, należy użyć `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Można użyć dowolnego [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] składni zmiennych `$(` *propertyName* `)` lub składni zmiennych środowiskowych `%` *propertyName* `%` Aby określić właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)  
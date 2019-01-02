---
title: Narzędzia niestandardowe | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8b18ee5c1c84b8e6480ffa9f91f739796f0991
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834415"
---
# <a name="custom-tools"></a>Narzędzia niestandardowe
*Narzędzia niestandardowe* umożliwiają skojarzenie narzędzie za pomocą elementu w projekcie i uruchomienia tego narzędzia, zawsze wtedy, gdy plik jest zapisywany. Niektóre narzędzia niestandardowe czasami określane jako *generatorów jednoplikowych*, są często używane do implementowania tłumaczy, które generują kod z danych i na odwrót. Na przykład można utworzyć generatorów jednoplikowych [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] kod poza źródłowy *.settings* i *resx* plików. Kod źródłowy wygenerowanego udostępnia silnie typizowane dane w *.settings* i *resx* plików. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typów projektów obsługuje narzędzi niestandardowych; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] typów projektów nie obsługują. Swój własny typ projektu może również obsługiwać narzędzia niestandardowe.  
  
 Narzędzia niestandardowe są zarejestrowane składniki z zaimplementowanymi `IVsSingleFileGenerator` interfejsu.  
  
 Narzędzia niestandardowe są skojarzone z `ProjectItem` interfejs obiektu i są podobne do projektantów i edytorów. Niestandardowe narzędzie przyjmuje pliku, reprezentowane przez `ProjectItem` jako dane wejściowe i zapisuje nowy plik, którego nazwa pliku są dostarczane przez `DefaultExtension` metody.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie generatorów jednoplikowych](../../extensibility/internals/implementing-single-file-generators.md)  
 Opisuje sposób używania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejs do implementacji niestandardowego narzędzia.  
  
 [Pojedynczy plik Zarejestruj generatory](../../extensibility/internals/registering-single-file-generators.md)  
 Zawiera opis wszystkie wpisy rejestru dla niestandardowego narzędzia.  
  
 [Udostępnianie typów projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 W tym artykule wyjaśniono, jak systemy projektu obsługują projektantów wizualnych do dostępu do wygenerowanych klas i typów plików tymczasowych przenośny plik wykonywalny (PE).  
  
 [Utrwalanie właściwości elementu projektu](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Pokazuje, jak można utrwalić właściwości elementu projektu, takich jak tworzenie pliku źródłowego, w pliku projektu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Zawiera szczegółowe informacje na temat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, który przekształca jeden plik wejściowy w pliku pojedynczego wyjścia, który może być skompilowany lub dodane do projektu.  
  
 <xref:EnvDTE.ProjectItem>  
 Wyjaśnia `ProjectItem` interfejs, który reprezentuje element w projekcie.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Zawiera szczegółowe informacje na temat `DefaultExtension` metody, która pobiera rozszerzenie nazwy pliku, który znajduje się na nazwę pliku wyjściowego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie projektów](../../extensibility/extending-projects.md)  
 Opisuje sposób używania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty i rozwiązania do organizowania plików kodu i plików zasobów i sposób implementowania kontroli źródła.
---
title: Narzędzia niestandardowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98dce865af4dd1f8498dcd697b53abdb8608abed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793428"
---
# <a name="custom-tools"></a>Narzędzia niestandardowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Narzędzia niestandardowe* umożliwiają skojarzenie narzędzie za pomocą elementu w projekcie i uruchomienia tego narzędzia, zawsze wtedy, gdy plik jest zapisywany. Niektóre narzędzia niestandardowe czasami określane jako *generatorów jednoplikowych*, są często używane do implementowania tłumaczy, które generują kod z danych i na odwrót. Na przykład można utworzyć generatorów jednoplikowych [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] kodu pliki .settings i resx poza źródłowego. Kod źródłowy wygenerowanego udostępnia silnie typizowane dane w plikach .settings i resx. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] typów projektów obsługuje narzędzi niestandardowych; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] typów projektów nie obsługują. Swój własny typ projektu może również obsługiwać narzędzia niestandardowe.  
  
 Narzędzia niestandardowe są zarejestrowane składniki z zaimplementowanymi `IVsSingleFileGenerator` interfejsu.  
  
 Narzędzia niestandardowe są skojarzone z `ProjectItem` interfejs obiektu i są podobne do projektantów i edytorów. Niestandardowe narzędzie przyjmuje pliku, reprezentowane przez `ProjectItem` jako dane wejściowe i zapisuje nowy plik, którego nazwa pliku są dostarczane przez `DefaultExtension` metody.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie generatorów jednoplikowych](../../extensibility/internals/implementing-single-file-generators.md)  
 Opisuje sposób używania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejs do implementacji niestandardowego narzędzia.  
  
 [Określanie Namespace domyślnego projektu](../../misc/determining-the-default-namespace-of-a-project.md)  
 W tym artykule opisano, jak określić poprawną przestrzeń nazw na podstawie języka używany.  
  
 [Rejestrowanie generatorów jednoplikowych](../../extensibility/internals/registering-single-file-generators.md)  
 Zawiera opis wszystkie wpisy rejestru dla niestandardowego narzędzia.  
  
 [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)  
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
 Opisuje sposób używania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekty i rozwiązania do organizowania plików kodu i plików zasobów i sposób implementowania kontroli źródła.


---
title: Narzędzia niestandardowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 594d564cf4a18eb0b673abd9b45b7d70e20381b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196917"
---
# <a name="custom-tools"></a>Narzędzia niestandardowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Narzędzia niestandardowe* umożliwiają skojarzenie narzędzia z elementem w projekcie i uruchamianie tego narzędzia za każdym razem, gdy plik zostanie zapisany. Niektóre niestandardowe narzędzia, nazywane czasami *generatorami pojedynczych plików*, są często używane do implementowania tłumaczeń generujących kod na podstawie danych i na odwrót. Na przykład generatory pojedynczych plików tworzą [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] kodu źródłowego z plików. Settings i. resx. Wygenerowany kod źródłowy zapewnia dostęp z jednoznacznie określonym dostępem do danych w plikach. Settings i. resx. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Typy projektów i obsługują niestandardowe narzędzia; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] typy projektów nie są. Własne typy projektów również mogą obsługiwać niestandardowe narzędzia.  
  
 Narzędzia niestandardowe są zarejestrowanymi składnikami, które implementują `IVsSingleFileGenerator` interfejs.  
  
 Narzędzia niestandardowe są skojarzone z `ProjectItem` obiektem interfejsu i są podobne do projektantów i edytorów. Narzędzie niestandardowe pobiera plik reprezentowany przez `ProjectItem` dane wejściowe i zapisuje nowy plik, którego nazwa pliku jest dostarczana przez `DefaultExtension` metodę.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie generatorów jednoplikowych](../../extensibility/internals/implementing-single-file-generators.md)  
 Opisuje sposób korzystania z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejsu w celu zaimplementowania niestandardowego narzędzia.  
  
 [Określanie domyślnej przestrzeni nazw projektu](../../misc/determining-the-default-namespace-of-a-project.md)  
 Opisuje sposób określania poprawnej przestrzeni nazw na podstawie używanego języka.  
  
 [Rejestrowanie generatorów jednoplikowych](../../extensibility/internals/registering-single-file-generators.md)  
 Zawiera opisy wszystkich wpisów rejestru dla niestandardowego narzędzia.  
  
 [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Wyjaśnia, jak systemy projektów zapewniają obsługę projektantów wizualizacji w celu uzyskiwania dostępu do wygenerowanych klas i typów za pomocą tymczasowych przenośnych plików wykonywalnych (PE).  
  
 [Utrwalanie właściwości elementu projektu](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Pokazuje, jak zachować właściwość elementu projektu, na przykład autora pliku źródłowego w pliku projektu.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Zawiera szczegółowe informacje na temat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , który przekształca pojedynczy plik wejściowy w jeden plik wyjściowy, który można skompilować lub dodać do projektu.  
  
 <xref:EnvDTE.ProjectItem>  
 Wyjaśnia `ProjectItem` interfejs, który reprezentuje element w projekcie.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Zawiera szczegółowe informacje na temat `DefaultExtension` metody, która pobiera rozszerzenie nazwy pliku, które jest przyznany do nazwy pliku wyjściowego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie projektów](../../extensibility/extending-projects.md)  
 Opisuje sposób używania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektów i rozwiązań do organizowania plików kodu i plików zasobów oraz sposobu implementacji kontroli źródła.

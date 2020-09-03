---
title: Struktura pakietu VSPackage (pakietu VSPackage kontroli źródła) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08bb0a296daca0de1c02b905a75fb10ce05f254e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205998"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura pakietu VSPackage (pakiet VSPackage kontroli kodu źródłowego)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zestaw SDK pakietu kontroli źródła zawiera wytyczne dotyczące tworzenia pakietu VSPackage, które umożliwiają implementowanie kontroli źródła w celu zintegrowania jej funkcji kontroli źródła ze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiskiem. Pakietu VSPackage jest składnikiem COM, który zwykle jest ładowany na żądanie przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowane środowisko programistyczne (IDE) na podstawie usług anonsowanych przez pakiet w jego wpisach rejestru. Każdy pakietu VSPackage musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Pakietu VSPackage zazwyczaj zużywa usługi oferowane przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE i proffers niektóre usługi.  
  
 Pakietu VSPackage deklaruje elementy menu i ustanawia domyślny stan elementu za pośrednictwem pliku. vsct. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE wyświetla elementy menu w tym stanie do momentu załadowania pakietu VSPackage. Następnie implementacja pakietu VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody jest wywoływana w celu włączenia lub wyłączenia elementów menu.  
  
## <a name="source-control-package-characteristics"></a>Charakterystyki pakietu kontroli źródła  
 Pakietu VSPackage kontroli źródła jest głęboko zintegrowany z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Semantyka pakietu VSPackage obejmuje:  
  
- Interfejs, który ma być zaimplementowany przez pakietu VSPackage ( `IVsPackage` interfejs)  
  
- Implementacja polecenia interfejsu użytkownika (plik. vsct i implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu)  
  
- Rejestracja pakietu VSPackage z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
  Pakietu VSPackage kontroli źródła musi komunikować się z tymi innymi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jednostkami:  
  
- Projekty  
  
- Edytory  
  
- Rozwiązania  
  
- Windows  
  
- Uruchomiona tabela dokumentów  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Usługi środowiska Visual Studio, które mogą być używane  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Usługa SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Interfejsy VSIP zaimplementowane i wywoływane  
 Pakiet kontroli źródła jest pakietu VSPackage i w związku z tym może współdziałać bezpośrednio z innymi pakietów VSPackage zarejestrowanymi w usłudze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Aby zapewnić pełną szerokość funkcji kontroli źródła, pakietu VSPackage kontroli źródła może odnosić się do interfejsów udostępnianych przez projekty lub powłokę.  
  
 Każdy projekt w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] musi implementować, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> aby mógł zostać rozpoznany jako projekt w środowisku [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Jednak ten interfejs nie jest wystarczająco wyspecjalizowany dla kontroli źródła. Projekty, które powinny znajdować się pod kontrolą źródła, implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Ten interfejs jest używany przez pakietu VSPackage kontroli źródła w celu wykonywania zapytań dotyczących projektu i zapewniania symboli i informacji wiążących (informacje niezbędne do ustanowienia połączenia między lokalizacją serwera a lokalizacją dysku projektu, który jest pod kontrolą źródła).  
  
 Pakietu VSPackage kontroli źródła implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , która z kolei umożliwia projektom zarejestrowanie się w celu kontroli źródła i pobranie ich symboli stanu.  
  
 Aby zapoznać się z pełną listą interfejsów, które należy wziąć pod uwagę pakietu VSPackage kontroli źródła, zobacz [pokrewne usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

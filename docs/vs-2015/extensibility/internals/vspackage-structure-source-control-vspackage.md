---
title: Struktura pakietu VSPackage (pakiet VSPackage kontroli) | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778053"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura pakietu VSPackage (pakiet VSPackage kontroli kodu źródłowego)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zestaw SDK pakietu kontroli źródła zawiera wytyczne dotyczące tworzenia pakietu VSPackage, który umożliwia implementujący kontroli źródła w celu zintegrowania jej funkcji kontroli źródła przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska. Pakietu VSPackage jest składnik COM, który zazwyczaj jest ładowany na żądanie przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE) na podstawie usług, które są anonsowane przez pakiet w nim wpisów rejestru. Każdego pakietu VSPackage musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Pakietu VSPackage zwykle korzysta z usług oferowanych przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE i proffers niektórych usług własnych.  
  
 Pakietu VSPackage deklaruje jego elementy menu i ustanawia domyślny stan elementu przy użyciu pliku vsct. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Środowisko IDE Wyświetla elementy menu w tym stanie do momentu załadowania pakietu VSPackage. Następnie VSPackage implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda jest wywoływana, aby włączyć lub wyłączyć elementy menu.  
  
## <a name="source-control-package-characteristics"></a>Właściwości pakietu kontroli źródła  
 Głęboko zintegrowane pakietu VSPackage kontroli źródła [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Semantyka pakietu VSPackage obejmują:  
  
- Interfejs do zaimplementowania bycia pakietu VSPackage ( `IVsPackage` interfejsu)  
  
- Implementacja poleceń interfejsu użytkownika (pliku vsct i stosowania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu)  
  
- Rejestrowanie pakietów VSPackage przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
  Kontrola źródła pakietu VSPackage muszą komunikować się z tych innych [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jednostki:  
  
- Projekty  
  
- Edytory  
  
- Rozwiązania  
  
- Windows  
  
- Uruchamianie tabeli dokumentu  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Usługi środowiska Visual Studio, które mogą być używane  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider Service  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP interfejsy implementowane oraz nazywany  
 Pakiet kontroli źródła jest pakietu VSPackage, a w związku z tym można korzystać bezpośrednio z innymi pakietami VSPackage, które są zarejestrowane w usłudze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. W celu zapewnienia pełnego zakresu funkcji kontroli źródła, kontroli źródła pakietu VSPackage poradzenie sobie z dostarczanych przez projektów lub powłoki.  
  
 Każdy projekt w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> uznawana za projektu w ramach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Jednak ten interfejs nie jest przeznaczone wystarczający do kontroli źródła. Projekty, które powinny być w obszarze źródło sterowania Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Ten interfejs jest wykorzystywany przez kontrolę źródła pakietu VSPackage, aby wyszukać projekt służący do jego zawartości, a do tego celu symbole i informacje o powiązaniu (informacje potrzebne do nawiązania połączenia między lokalizacją serwera i lokalizację dysku projektu, który znajduje się w kontroli źródła).  
  
 Implementuje pakietu VSPackage kontroli źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, co z kolei pozwala projektów, które rejestrują się do kontroli źródła i pobierać symbole ich stanu.  
  
 Aby uzyskać pełną listę interfejsów, które należy wziąć pod uwagę pakietu VSPackage kontroli źródła, zobacz [powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

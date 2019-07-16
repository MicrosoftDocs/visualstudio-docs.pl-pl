---
title: Obsługa kontroli kodu źródłowego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1166197a5c79dcb0d1ddf4018227914346a6172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156079"
---
# <a name="supporting-source-control"></a>Obsługa kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje wyewidencjonowania pliku, zaewidencjonowania i inne operacje kontroli źródła dla projektu lub edytorze. Jako klient kontroli źródła [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] służy do interakcji z pakietem kontroli źródła, takich jak [!INCLUDE[vsvss](../../includes/vsvss-md.md)], które obejmują archiwizacji, przechowywanie wersji i możliwości kontroli dynamicznie definiowane zestawu plików.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Model pakietów kontroli kodu źródłowego](../../extensibility/internals/model-for-source-control-packages.md)  
 Opisuje interfejsy musi implementować typ projektu, do obsługi kontroli źródła.  
  
 [Decyzje dotyczące projektu](../../extensibility/internals/source-control-design-decisions.md)  
 Zawiera pytania, na których odpowiedzi zmienić sposób implementacji typu projektu.  
  
 [Szczegóły konfiguracji](../../extensibility/internals/source-control-configuration-details.md)  
 W tym artykule opisano, jak Obsługa kontroli kodu źródłowego zmienia implementacji typu projektu.  
  
 [Dodatkowe wskazówki dotyczące projektów i edytorów](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 W tym artykule omówiono najlepsze rozwiązania dotyczące typów projektów i edytorów.  
  
 [Szczegóły środowiska uruchomieniowego](../../extensibility/internals/source-control-runtime-details.md)  
 Opisuje sposób rejestrowania projektu, gdy użytkownik doda go do systemu kontroli źródła.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Wskazuje, że do środowiska lub pakiet kontroli "source", który plik ma zostać zmienione w pamięci lub zapisany.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Umożliwia projektów i hierarchie rejestrują się z kontroli źródła i uzyskiwania informacji o stan kontroli źródła.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Zaimplementowane w systemie projektu w celu zapewnienia kontroli źródła plików projektu i elementy projektu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Używane przez projektów, aby wysyłać zapytania do środowiska, aby uzyskać uprawnienia do dodawania, usuń lub zmień nazwę pliku lub katalogu w ramach rozwiązania.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Powiadamia klientów o zmianach wprowadzonych do projektu pliki lub katalogi.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera omówienie projektów jako podstawowe bloki konstrukcyjne [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE). Podano linki do dodatkowych tematów, które wyjaśniają, jak kontrolować projektów, tworzenie i kompilowanie kodu.

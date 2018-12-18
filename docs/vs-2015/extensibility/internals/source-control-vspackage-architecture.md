---
title: Architektura pakietu VSPackage kontroli źródła | Dokumentacja firmy Microsoft
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
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5fc639214757649dcc1bee191b7b268d7b6fdbcc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802151"
---
# <a name="source-control-vspackage-architecture"></a>Architektura pakietu VSPackage kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakiet kontroli źródła jest pakietu VSPackage, który korzysta z usługi, których [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowisko IDE. W zamian pakiet kontroli źródła zapewnia jej funkcje, jak usługi kontroli źródła. Ponadto pakiet kontroli źródła jest bardziej wszechstronna alternatywna niż wtyczka do kontroli źródła do integracji kontroli źródła do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Wtyczka do kontroli źródła implementującej interfejs API wtyczki kontroli źródła przestrzega strict kontraktu. Na przykład wtyczka nie można zastąpić domyślną [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejsu użytkownika (UI). Ponadto API wtyczki kontroli źródła nie uwzględnia wtyczki do zaimplementowania swój własny model kontroli źródła. Pakiet kontroli źródła, jednak pozwala pokonać oba te ograniczenia. Pakiet kontroli źródła, ma pełną kontrolę nad możliwości kontroli źródła [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] użytkownika. Ponadto pakiet kontroli źródła można użyć własnej model kontroli źródła i logiki i można zdefiniować, wszystkie interfejsy użytkownika związane z kontroli źródła.  
  
## <a name="source-control-package-components"></a>Składniki pakietu kontroli źródła  
 Jak pokazano na diagramie architektury [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] składnika o nazwie klasy zastępczej kontroli źródła jest pakietu VSPackage, który jest zintegrowany pakiet kontroli źródła o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Klasy zastępczej kontroli źródła obsługuje następujące zadania.  
  
- Udostępnia wspólny interfejs użytkownika, który jest wymagany do kontroli źródła pakietu rejestracji.  
  
- Ładuje pakiet kontroli źródła.  
  
- Ustawia pakiet kontroli źródła jako aktywny/nieaktywny.  
  
  Klasy zastępczej kontroli źródła szuka usługi active pakietu kontroli źródła i kieruje wszystkie przychodzące wywołania usługi z poziomu środowiska IDE tego pakietu.  
  
  Pakiet karty kontroli źródła jest specjalny kontroli źródła pakietu, który [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] udostępnia. Ten pakiet jest głównym składnikiem do obsługi źródła wtyczek kontroli oparte na interfejsie API wtyczki kontroli źródła. Po aktywny wtyczki, wtyczka do kontroli źródła wycinka kontroli źródła wysyła jego zdarzenia do pakietu karty kontroli źródła. Z kolei pakietu karty Kontrola źródła komunikuje się z wtyczka do kontroli źródła, za pomocą interfejsu API wtyczki kontroli źródła, a także udostępnia domyślny interfejs użytkownika, który jest typowe dla wtyczek kontroli wszystkie źródła.  
  
  Gdy pakiet kontroli źródła jest aktywny pakiet, z drugiej strony, wycinka kontroli źródła bezpośrednio komunikuje się z pakietu przy użyciu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] interfejsy kontroli źródła pakietu. Pakiet kontroli źródła jest odpowiedzialny za hostowanie własnego źródła kontrolki interfejsu użytkownika.  
  
  ![Grafika przedstawiająca architekturę kontroli źródła](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
  W przypadku pakietu kontroli źródła [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nie dostarcza kod do kontroli źródła lub interfejsu API do integracji. Natomiast to podejście, opisane w temacie [tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md) gdy wtyczka do kontroli źródła musi implementować sztywne zbiór funkcji i wywołania zwrotne.  
  
  Podobnie jak wszelkie VSPackage kontroli źródła pakietu jest obiekt COM, które mogą być tworzone za pomocą `CoCreateInstance`. Pakietu VSPackage udostępnia sam [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE poprzez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Podczas tworzenia wystąpienia pakietu VSPackage otrzymuje wskaźnik lokacji i <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejs zapewniający dostęp do pakietu VSPackage dostępne usługi i interfejsy w środowisku IDE.  
  
  Zapisywanie pakietu na podstawie pakietu VSPackage kontroli źródła wymaga bardziej zaawansowanych doświadczenie programowania niż pisanie oparte na interfejsie API wtyczki kontroli źródła wtyczek.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-vspackages.md)


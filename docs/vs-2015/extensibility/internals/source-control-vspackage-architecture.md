---
title: Architektura pakietu VSPackage kontroli źródła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3cca9e39714f87024b01ab2c925189aacbe22785
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183412"
---
# <a name="source-control-vspackage-architecture"></a>Architektura pakietu VSPackage kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakiet kontroli źródła jest pakietu VSPackage, który korzysta z usług [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] udostępnianych przez środowisko IDE. W powrocie pakiet kontroli źródła udostępnia swoją funkcjonalność jako usługę kontroli źródła. Ponadto pakiet kontroli źródła jest bardziej wszechstronną alternatywą niż Wtyczka kontroli źródła do integracji kontroli źródła z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Wtyczka do kontroli źródła, która implementuje interfejs API wtyczki kontroli źródła przestrzega zasad przez ścisły kontrakt. Na przykład wtyczka nie może zastąpić domyślnego [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejsu użytkownika. Ponadto interfejs API dodatku plug-in kontroli źródła nie pozwala na zaimplementowanie własnego modelu kontroli źródła przez wtyczkę. Pakiet kontroli źródła, jednak przechodzą oba te ograniczenia. Pakiet kontroli źródła ma pełną kontrolę nad doświadczeniem w zakresie kontroli źródła przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] użytkownika. Ponadto pakiet kontroli źródła może używać własnego modelu kontroli źródła i logiki, a także definiować wszystkie interfejsy użytkownika powiązane z kontrolą źródła.  
  
## <a name="source-control-package-components"></a>Składniki pakietu kontroli źródła  
 Jak pokazano na diagramie architektury, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] składnik o nazwie stub kontroli źródła jest pakietu VSPackage, który integruje pakiet kontroli źródła z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Procedura wejścia kontroli źródła obsługuje następujące zadania.  
  
- Udostępnia wspólny interfejs użytkownika, który jest wymagany do rejestracji pakietu kontroli źródła.  
  
- Ładuje pakiet kontroli źródła.  
  
- Ustawia pakiet kontroli źródła jako aktywny/nieaktywny.  
  
  Procedura wejścia kontroli źródła szuka aktywnej usługi dla pakietu kontroli źródła i przekierowuje wszystkie wywołania usługi przychodzącej ze środowiska IDE do tego pakietu.  
  
  Pakiet adaptera kontroli źródła jest specjalnym pakietem kontroli źródła, który [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zapewnia. Ten pakiet jest centralnym składnikiem obsługującym wtyczki kontroli źródła na podstawie interfejsu API wtyczki kontroli źródła. Gdy wtyczka kontroli źródła jest aktywną wtyczką, skrót kontroli źródła wysyła swoje zdarzenia do pakietu adaptera kontroli źródła. Z kolei pakiet adaptera kontroli źródła komunikuje się z wtyczką kontroli źródła przy użyciu interfejsu API wtyczki kontroli źródła, a także udostępnia domyślny interfejs użytkownika, który jest wspólny dla wszystkich wtyczek kontroli źródła.  
  
  Gdy pakiet kontroli źródła jest aktywnym pakietem, po drugiej stronie procedura kontroli źródła bezpośrednio komunikuje się z pakietem przy użyciu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] interfejsów pakietu kontroli źródła. Pakiet kontroli źródła jest odpowiedzialny za hostowanie własnego interfejsu użytkownika kontroli źródła.  
  
  ![Grafika architektury kontroli źródła](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
  W przypadku pakietu kontroli źródła program nie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dostarcza kodu kontroli źródła ani interfejsu API do integracji. Tym samym, z podejściem opisanym w temacie [tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md) , w której Wtyczka kontroli źródła musi implementować sztywny zestaw funkcji i wywołań zwrotnych.  
  
  Podobnie jak każdy pakietu VSPackage, pakiet kontroli źródła jest obiektem COM, który można utworzyć za pomocą `CoCreateInstance` . Pakietu VSPackage udostępnia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowisko IDE przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Po utworzeniu wystąpienia pakietu VSPackage otrzymuje wskaźnik lokacji i <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejs, który zapewnia dostęp pakietu VSPackage do dostępnych usług i interfejsów w IDE.  
  
  Pisanie pakietu kontroli źródła opartego na pakietu VSPackage wymaga bardziej zaawansowanej znajomości programowania niż w przypadku wtyczki kontroli źródła wtyczki opartej na interfejsie API.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

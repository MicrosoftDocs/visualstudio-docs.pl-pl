---
title: Architektura pakietu VSPackage kontroli źródła | Microsoft Docs
description: Dowiedz się więcej o architekturze pakietu kontroli źródła, który jest pakietu VSPackage, który zapewnia funkcjonalność programu Visual Studio jako usługę kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e4de5f46746f79e1c7598e1c2a2a6af6ae1d92a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912686"
---
# <a name="source-control-vspackage-architecture"></a>Architektura pakietu VSPackage kontroli kodu źródłowego
Pakiet kontroli źródła jest pakietu VSPackage, który korzysta z usług [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnianych przez środowisko IDE. W powrocie pakiet kontroli źródła udostępnia swoją funkcjonalność jako usługę kontroli źródła. Ponadto pakiet kontroli źródła jest bardziej wszechstronną alternatywą niż Wtyczka kontroli źródła do integracji kontroli źródła z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Wtyczka do kontroli źródła, która implementuje interfejs API wtyczki kontroli źródła przestrzega zasad przez ścisły kontrakt. Na przykład wtyczka nie może zastąpić domyślnego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika. Ponadto interfejs API dodatku plug-in kontroli źródła nie pozwala na zaimplementowanie własnego modelu kontroli źródła przez wtyczkę. Pakiet kontroli źródła, jednak przechodzą oba te ograniczenia. Pakiet kontroli źródła ma pełną kontrolę nad doświadczeniem w zakresie kontroli źródła przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użytkownika. Ponadto pakiet kontroli źródła może używać własnego modelu kontroli źródła i logiki, a także definiować wszystkie interfejsy użytkownika powiązane z kontrolą źródła.

## <a name="source-control-package-components"></a>Składniki pakietu Source-Control
 Jak pokazano na diagramie architektury, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składnik o nazwie stub kontroli źródła jest pakietu VSPackage, który integruje pakiet kontroli źródła z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Procedura wejścia kontroli źródła obsługuje następujące zadania.

- Udostępnia wspólny interfejs użytkownika, który jest wymagany do rejestracji pakietu kontroli źródła.

- Ładuje pakiet kontroli źródła.

- Ustawia pakiet kontroli źródła jako aktywny/nieaktywny.

  Procedura wejścia kontroli źródła szuka aktywnej usługi dla pakietu kontroli źródła i przekierowuje wszystkie wywołania usługi przychodzącej ze środowiska IDE do tego pakietu.

  Pakiet adaptera kontroli źródła jest specjalnym pakietem kontroli źródła, który [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia. Ten pakiet jest centralnym składnikiem obsługującym wtyczki kontroli źródła na podstawie interfejsu API wtyczki kontroli źródła. Gdy wtyczka kontroli źródła jest aktywną wtyczką, skrót kontroli źródła wysyła swoje zdarzenia do pakietu adaptera kontroli źródła. Z kolei pakiet adaptera kontroli źródła komunikuje się z wtyczką kontroli źródła przy użyciu interfejsu API wtyczki kontroli źródła, a także udostępnia domyślny interfejs użytkownika, który jest wspólny dla wszystkich wtyczek kontroli źródła.

  Gdy pakiet kontroli źródła jest aktywnym pakietem, po drugiej stronie procedura kontroli źródła bezpośrednio komunikuje się z pakietem za pomocą [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfejsów pakietu Source-Control. Pakiet kontroli źródła jest odpowiedzialny za hostowanie własnego interfejsu użytkownika kontroli źródła.

  ![Grafika architektury kontroli źródła](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  W przypadku pakietu kontroli źródła program nie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza kodu kontroli źródła ani interfejsu API do integracji. Tym samym, z podejściem opisanym w temacie [tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md) , w której Wtyczka kontroli źródła musi implementować sztywny zestaw funkcji i wywołań zwrotnych.

  Podobnie jak każdy pakietu VSPackage, pakiet kontroli źródła jest obiektem COM, który można utworzyć za pomocą `CoCreateInstance` . Pakietu VSPackage udostępnia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko IDE przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Po utworzeniu wystąpienia pakietu VSPackage otrzymuje wskaźnik lokacji i <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejs, który zapewnia dostęp pakietu VSPackage do dostępnych usług i interfejsów w IDE.

  Pisanie pakietu kontroli źródła opartego na pakietu VSPackage wymaga bardziej zaawansowanej znajomości programowania niż w przypadku wtyczki kontroli źródła wtyczki opartej na interfejsie API.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

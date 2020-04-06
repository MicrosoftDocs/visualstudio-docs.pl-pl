---
title: Kontrola źródła VSPackage Architektura | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705083"
---
# <a name="source-control-vspackage-architecture"></a>Architektura pakietu VSPackage kontroli kodu źródłowego
Pakiet kontroli źródła jest VSPackage, który używa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usług, które ide zapewnia. W zamian pakiet kontroli źródła zapewnia jego funkcjonalność jako usługi kontroli źródła. Ponadto pakiet kontroli źródła jest bardziej wszechstronną alternatywą niż wtyczka kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]do integracji sterowania źródłem w .

 Wtyczka kontroli źródła, która implementuje interfejs API wtyczki dodatku Source Control jest przestrzegana przez ścisłą umowę. Na przykład wtyczka nie może [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zastąpić domyślnego interfejsu użytkownika(UI). Ponadto interfejs API wtyczki kontroli źródła nie umożliwia dodatku plug-in implementowania własnego modelu kontroli źródła. Pakiet kontroli źródła, jednak pokonuje oba te ograniczenia. Pakiet kontroli źródła ma pełną kontrolę nad środowisko [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kontroli źródła użytkownika. Ponadto pakiet kontroli źródła można użyć własnego modelu kontroli źródła i logiki i można zdefiniować wszystkie interfejsy użytkownika związane z kontrolą źródła.

## <a name="source-control-package-components"></a>Składniki pakietu kontroli źródła
 Jak pokazano na diagramie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] architektury, składnik o nazwie Source Control Stub jest VSPackage, który integruje pakiet kontroli źródła z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Źródło Formant Skrót obsługuje następujące zadania.

- Udostępnia wspólny interfejs użytkownika, który jest wymagany do rejestracji pakietu kontroli źródła.

- Ładuje pakiet kontroli źródła.

- Ustawia pakiet kontroli źródła jako aktywny/nieaktywny.

  Źródło Formant Ów Odcinek wyszukuje aktywną usługę dla pakietu kontroli źródła i trasy wszystkich wywołań usługi przychodzącej z IDE do tego pakietu.

  Pakiet karty kontroli źródła jest specjalny pakiet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kontroli źródła, który zapewnia. Ten pakiet jest centralnym składnikiem obsługi wtyczek kontroli źródła opartych na interfejsie API dodatku Plug-in dodatku Source Control. Gdy wtyczka kontroli źródła jest aktywną wtyczką, skrót kontroli źródła wysyła swoje zdarzenia do pakietu karty kontroli źródła. Z kolei pakiet karty kontroli źródła komunikuje się z wtyczką kontroli źródła za pomocą interfejsu API wtyczki kontroli źródła, a także zapewnia domyślny interfejs użytkownika, który jest wspólny dla wszystkich wtyczek kontroli źródła.

  Gdy pakiet kontroli źródła jest aktywny pakiet, z drugiej strony Source Control Stub bezpośrednio komunikuje się z pakietem przy użyciu interfejsów pakietu kontroli [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] źródła. Pakiet kontroli źródła jest odpowiedzialny za hostowanie własnego interfejsu użytkownika kontroli źródła.

  ![Grafika przedstawiająca architekturę kontroli źródła](../../extensibility/internals/media/vsipsccarch.gif "VsIPSCCArch")

  Dla pakietu kontroli źródła, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie dostarcza kod kontroli źródła lub interfejsu API do integracji. Kontrast to z [podejściem opisanym w Tworzenie wtyczki kontroli źródła, gdzie](../../extensibility/internals/creating-a-source-control-plug-in.md) wtyczka kontroli źródła musi implementować sztywny zestaw funkcji i wywołań zwrotnych.

  Podobnie jak każdy vspackage, pakiet kontroli źródła jest obiektem `CoCreateInstance`COM, który można utworzyć za pomocą . VSPackage udostępnia się [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ide poprzez implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Po utworzeniu wystąpienia vsPackage odbiera wskaźnik lokacji <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> i interfejs, który zapewnia dostęp vsPackage do dostępnych usług i interfejsów w IDE.

  Pisanie pakietu kontroli źródła opartego na programie VSPackage wymaga bardziej zaawansowanej wiedzy na temat programowania niż pisanie wtyczki opartej na interfejsie API opartej na usłudze Source Control Plug-in.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

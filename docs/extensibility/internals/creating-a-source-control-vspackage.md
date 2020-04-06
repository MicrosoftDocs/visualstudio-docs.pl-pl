---
title: Tworzenie vspackage formantu źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709189"
---
# <a name="create-a-source-control-vspackage"></a>Tworzenie formantu źródła VSPackage
Ta dokumentacja zawiera łącza do przeglądu architektury pakietu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kontroli źródła zintegrowane z , interfejs API, który jest zdefiniowany przez interfejsy, które mają być zaimplementowane i usługi, które mają być używane, a przykład, który ilustruje implementację pakietu kontroli źródła proste.

 Za pomocą formantu źródłowego VSPackage można utworzyć ścieżkę [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]głębokiej integracji dla kontroli źródła w celu integracji z programem . Umożliwia pakiet ominąć domyślny interfejs użytkownika kontroli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]źródła obsługiwany przez , odpowiadać na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] żądania kontroli źródła z systemu projektu i interakcji ze składnikami, takimi jak **Eksplorator rozwiązań**. Upoważnia [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partnerów z mechanizmem do tworzenia VSPackage, które można zintegrować z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przy użyciu modelu usługi.

## <a name="in-this-section"></a>W tej sekcji
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 W tym artykule omówiono pakiet kontroli źródła, który jest bardziej zaawansowaną alternatywą dla wtyczki kontroli źródła do implementowania funkcji kontroli źródła w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Architektura](../../extensibility/internals/source-control-vspackage-architecture.md)

 Przedstawia diagram i wyjaśnia składniki pakietu kontroli źródła.

- [Funkcje](../../extensibility/internals/source-control-vspackage-features.md)

 Opisuje różne funkcje pakietu kontroli źródła.

- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Opisuje strukturę VSPackage, że pakiet kontroli źródła musi zaimplementować dla głębokiej integracji.

## <a name="related-sections"></a>Powiązane sekcje
- [Tworzenie wtyczki formantu źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)

 W tym artykule omówiono sposób tworzenia wtyczki kontroli źródła, która dostarcza funkcje kontroli źródła w interfejsie użytkownika kontroli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] źródła (UI).

- [Kontrola źródła](../../extensibility/internals/source-control.md)

 W tym artykule omówiono opcje implementowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kontroli źródła jako zintegrowanej funkcji programu .

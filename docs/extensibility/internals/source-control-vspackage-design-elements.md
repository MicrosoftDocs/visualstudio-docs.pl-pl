---
title: Elementy projektu pakietu VSPackage kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e10825bb9bc9659728fbaaeb023a595745b7bcd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642706"
---
# <a name="source-control-vspackage-design-elements"></a>Elementy projektu pakietu VSPackage kontroli kodu źródłowego
Tematy w tej sekcji opisują Struktura pakietu VSPackage musi implementować dla głęboka Integracja kontroli źródła. Zawiera również listę interfejsów, można wdrożyć usługi, że źródło kontrolować pakietu VSPackage i interfejsy oraz usługi pakietu VSPackage kontroli źródła mogą korzystać z innych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składników w celu obsługi źródła kontrolowania modelu i funkcji.

## <a name="in-this-section"></a>W tej sekcji
- [Struktura pakietu VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definiuje strukturę do kontroli źródła pakietu VSPackage.

- [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Wyświetla listę interfejsów związane z pakietu kontroli źródła i usług.

- [Dostępne usługi](../../extensibility/internals/services-provided-source-control-vspackage.md)

 W tym artykule opisano usługi kontroli źródła, które są dostarczane przez pakietu VSPackage kontroli źródła.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)

 W tym artykule omówiono sposób tworzenia kontroli źródła pakietu VSPackage, który nie tylko zapewnia funkcji kontroli źródła, ale mogą być używane do dostosowywania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] źródłowej kontrolki interfejsu użytkownika.
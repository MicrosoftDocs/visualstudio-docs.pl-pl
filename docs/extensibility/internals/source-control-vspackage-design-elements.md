---
title: Kontrola źródła VSPackage Elementy projektowe | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5e94829f781c058d9b0ea56cdec6c03c71ffe0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705008"
---
# <a name="source-control-vspackage-design-elements"></a>Elementy projektu pakietu VSPackage kontroli kodu źródłowego
Tematy w tej sekcji określ struktury kontroli źródła VSPackage musi zaimplementować dla głębokiej integracji. Zawiera również listę interfejsów i usług, które vspackage kontroli źródła można zaimplementować, a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsy i usługi kontroli źródła VSPackage można użyć z innych składników do obsługi jego modelu kontroli źródła i funkcji.

## <a name="in-this-section"></a>W tej sekcji
- [Struktura pakietu VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definiuje strukturę formantu źródła VSPackage.

- [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Wyświetla listę interfejsów i usług związanych z pakietem kontroli źródła.

- [Dostępne usługi](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Opisuje usługę kontroli źródła świadczoną przez formant źródłowy VSPackage.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)

 W tym artykule omówiono sposób tworzenia formantu źródła VSPackage, który nie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tylko dostarcza funkcje kontroli źródła, ale może służyć do dostosowywania interfejsu użytkownika kontroli źródła.

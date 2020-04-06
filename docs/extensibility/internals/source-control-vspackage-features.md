---
title: Funkcje vspackage kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a01b9d8fbf5f8d0645b5245d21b05aba9e7dacea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705015"
---
# <a name="source-control-vspackage-features"></a>Funkcje pakietu VSPackage kontroli kodu źródłowego
W tej sekcji opisano różne funkcje formantu źródła VSPackage. Przedstawiono szczegóły rejestracji i wyboru dla takiego VSPackage i omówiono trzy główne funkcje związane z kontrolą źródła: obsługa query-edit query-save (QEQS) zdarzenia, wymiana glifów i niestandardowy interfejs użytkownika (UI) dla funkcji kontroli źródła.

## <a name="in-this-section"></a>W tej sekcji
- [Rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 W tym artykule opisano mechanizmy rejestracji i wyboru pakietu.

- [Edytowanie i zapisywanie zapytania](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 W tym artykule wyjaśniono rolę zdarzeń zapisywania kwerendy-kwerendy i sposób ich obsługi przez formant źródłowy VSPackage.

- [Kontrola symboli](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Opisuje poziomy kontroli glifów i jak je zaimplementować.

- [Niestandardowy interfejs użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Konspektuje elementy interfejsu użytkownika, które vspackage formantu źródła można określić.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)

 W tym artykule omówiono sposób tworzenia formantu źródła VSPackage, który nie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tylko dostarcza funkcje kontroli źródła, ale może służyć do dostosowywania interfejsu użytkownika kontroli źródła.

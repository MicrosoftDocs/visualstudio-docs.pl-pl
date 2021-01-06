---
title: Funkcje pakietu VSPackage kontroli źródła | Microsoft Docs
description: Dowiedz się więcej o funkcjach pakietu VSPackage kontroli źródła, w tym informacje o rejestracji/wyborze oraz o niektórych funkcjach głównych związanych z kontrolą źródła.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8dd887488adc5813ad51c9fa2a25648e25ab4876
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876223"
---
# <a name="source-control-vspackage-features"></a>Funkcje pakietu VSPackage kontroli kodu źródłowego
W tej sekcji opisano różne funkcje kontroli źródła pakietu VSPackage. Przedstawia ona szczegóły rejestracji i wyboru dla tego pakietu VSPackage oraz omawia trzy główne funkcje związane z kontrolą źródła: obsługa zdarzeń Query-Edit Query-Save (QEQS), zastąpienie symboli i niestandardowy interfejs użytkownika (UI) dla funkcji kontroli źródła.

## <a name="in-this-section"></a>W tej sekcji
- [Rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Opisuje mechanizmy rejestracji i wyboru pakietu.

- [Edytowanie i zapisywanie zapytania](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Wyjaśnia rolę Query-Edit zdarzeń Query-Save i sposobu ich obsługi przez pakietu VSPackage kontroli źródła.

- [Kontrola symboli](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Opisuje poziomy kontrolki glifów oraz sposób ich implementacji.

- [Niestandardowy interfejs użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Zawiera opis elementów interfejsu użytkownika, które może określić pakietu VSPackage kontroli źródła.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)

 W tym artykule omówiono sposób tworzenia pakietu VSPackage kontroli źródła, które nie tylko dostarczają funkcji kontroli źródła, ale mogą służyć do dostosowywania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika kontroli źródła.

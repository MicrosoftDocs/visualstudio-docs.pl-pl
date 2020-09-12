---
title: Kiedy zaimplementować pakietu VSPackage kontroli źródła
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16f96191115a509e07b5263f1d10d53ea3b2cc9c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037045"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Określanie, czy zaimplementować pakietu VSPackage kontroli źródła

Ta sekcja zawiera szczegółowe informacje na temat wyboru wtyczek kontroli źródła i pakietów VSPackage kontroli źródła w celu rozszerzenia rozwiązań kontroli źródła, a także zawiera szczegółowe wskazówki dotyczące wybierania odpowiedniej ścieżki integracji.

## <a name="small-source-control-solution-with-limited-resources"></a>Małe rozwiązanie kontroli źródła z ograniczoną ilością zasobów

 Jeśli masz ograniczone zasoby i nie można go obciążać kosztem napisania pakietu kontroli źródła, możesz utworzyć wtyczki kontroli źródła dla wtyczki opartej na interfejsie API. Dzięki temu można współpracować z pakietami kontroli źródła, a także przełączać się między wtyczkami i pakietami kontroli źródła na żądanie. Aby uzyskać więcej informacji, zobacz [rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Duże rozwiązanie kontroli źródła z bogatym zestawem funkcji

 Jeśli chcesz zaimplementować rozwiązanie kontroli źródła, które zapewnia bogaty model kontroli źródła, który nie jest odpowiednio przechwytywany przy użyciu wtyczki kontroli źródła, możesz rozważyć pakiet kontroli źródła jako ścieżkę integracji. Ma to zastosowanie szczególnie w przypadku, gdy zastąpisz pakiet adaptera kontroli źródła (który komunikuje się z wtyczkami kontroli źródła i udostępnia podstawowy interfejs użytkownika kontroli źródła) własnym, aby umożliwić obsługę zdarzeń kontroli źródła w sposób niestandardowy. Jeśli masz już zadowalający interfejs użytkownika kontroli źródła i chcesz zachować to środowisko w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , opcja pakiet kontroli źródła umożliwia wykonywanie tych czynności. Pakiet kontroli źródła nie jest ogólny i został zaprojektowany wyłącznie do użytku z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 Jeśli chcesz zaimplementować rozwiązanie kontroli źródła, które zapewnia elastyczność i bogatszą kontrolę nad logiką i interfejsem użytkownika kontroli źródła, możesz preferować trasę integracji pakietu kontroli źródła. Można:

1. Zarejestruj własne pakietu VSPackage kontroli źródła (zobacz [rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Zastąp domyślny interfejs użytkownika kontroli źródła własnym INTERFEJSem użytkownika (zobacz [niestandardowy interfejs użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. Określ glify, które mają być używane i obsługujące Eksplorator rozwiązań zdarzenia glifów (zobacz [kontrolka symbolu](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. Obsługa zdarzeń związanych z edycją zapytań i zapisywaniem zapytań (zobacz [zapytanie Edycja zapytania Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>Zobacz także

- [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)

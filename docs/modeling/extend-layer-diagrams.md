---
title: Rozszerzanie diagramów zależności
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5519328ef69f98737a7744f0162bdc0951433a60
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082896"
---
# <a name="extend-dependency-diagrams"></a>Rozszerzanie diagramów zależności

Można napisać kod do tworzenia i aktualizowania diagramów zależności i do sprawdzania poprawności strukturę kodu programu względem diagramów zależności w programie Visual Studio. Możesz dodać polecenia, które są wyświetlane w menu skrótów (kontekstu), diagramy Dostosowywanie gestów przeciągania i upuszczania oraz dostęp do warstwy modelu z poziomu szablonów tekstu. Można spakować te rozszerzenia w Visual Studio Integration rozszerzenie (VSIX) i rozdystrybuować je innym użytkownikom programu Visual Studio.

 Aby uzyskać więcej informacji dotyczących diagramów zależności zobacz:

- [Diagramy zależności: informacje](../modeling/layer-diagrams-reference.md)

- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

## <a name="prereqs"></a> Wymagania

Musisz mieć zainstalowane na komputerze, gdzie chcesz rozwijać swoje rozszerzenia warstwy następujące elementy:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Modeling SDK for Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Konieczne jest posiadanie odpowiedniej wersji programu Visual Studio zainstalowany na komputerze, na którym chcesz uruchomić swoje rozszerzenia warstwy.

Aby dowiedzieć się, które wersje programu Visual Studio obsługują diagramów zależności, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>W tej sekcji
 [Dodawanie poleceń i gestów do diagramów zależności](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Dodawanie właściwości niestandardowych do diagramów zależności](../modeling/add-custom-properties-to-layer-diagrams.md)

## <a name="see-also"></a>Zobacz też

- [Diagramy zależności: informacje](../modeling/layer-diagrams-reference.md)
- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)
- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

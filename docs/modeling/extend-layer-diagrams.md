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
ms.openlocfilehash: 8888dfeef0a519aed66fc3c66be8c5bf6d215b02
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955222"
---
# <a name="extend-dependency-diagrams"></a>Rozszerzanie diagramów zależności
Można napisać kod do tworzenia i aktualizowania diagramów zależności i do sprawdzania poprawności strukturę kodu programu względem diagramów zależności w programie Visual Studio. Możesz dodać polecenia, które są wyświetlane w menu skrótów (kontekstu), diagramy Dostosowywanie gestów przeciągania i upuszczania oraz dostęp do warstwy modelu z poziomu szablonów tekstu. Można spakować te rozszerzenia w Visual Studio Integration rozszerzenie (VSIX) i rozdystrybuować je innym użytkownikom programu Visual Studio.

 Aby uzyskać więcej informacji dotyczących diagramów zależności zobacz:

-   [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)

-   [Diagramy zależności: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md)

-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

##  <a name="prereqs"></a> Wymagania
 Musisz mieć zainstalowane na komputerze, gdzie chcesz rozwijać swoje rozszerzenia warstwy następujące elementy:

-   Visual Studio

-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

-   Modeling SDK for Visual Studio


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 Konieczne jest posiadanie odpowiedniej wersji programu Visual Studio zainstalowany na komputerze, na którym chcesz uruchomić swoje rozszerzenia warstwy. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md).

 Aby dowiedzieć się, które wersje programu Visual Studio obsługują diagramów zależności, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>W tej sekcji
 [Dodawanie poleceń i gestów do diagramów zależności](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Dodawanie właściwości niestandardowych do diagramów zależności](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md)

 [Rozwiązywanie problemów z rozszerzeniami dla diagramów zależności](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Zobacz też

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Diagramy zależności: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md)
- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

---
title: Rozszerzanie diagramów zależności
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302946"
---
# <a name="extend-dependency-diagrams"></a>Rozszerzanie diagramów zależności

Można napisać kod, aby utworzyć i zaktualizować diagramy zależności i sprawdzić poprawność struktury kodu programu względem diagramów zależności w programie Visual Studio. Można dodawać polecenia wyświetlane w menu skrótów (kontekstowych) diagramów, dostosowywać gesty przeciągania i upuszczania oraz uzyskiwać dostęp do modelu warstwy za pomocą szablonów tekstu. Rozszerzenia te można spakować do rozszerzenia integracji programu Visual Studio (VSIX) i rozpowszechniać je do innych użytkowników programu Visual Studio.

## <a name="requirements"></a>Wymagania

Na komputerze musi być zainstalowane następujące elementy:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- SDK modelowania dla programu Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Na komputerze musi być zainstalowana odpowiednia wersja programu Visual Studio, na której chcesz uruchomić rozszerzenia warstwy. Aby zobaczyć, które wersje diagramów zależności usługi Visual Studio obsługują diagramy zależności, zobacz [Obsługa architektury i narzędzi do modelowania w wersji.](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="see-also"></a>Zobacz też

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)
- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

---
title: Rozszerzanie diagramów zależności
description: Dowiedz się, jak napisać kod do tworzenia i aktualizowania diagramów zależności oraz jak weryfikować strukturę kodu programu względem diagramów zależności w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2ed8700cfb18aacf41464bfdfacaedac557bb00
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388909"
---
# <a name="extend-dependency-diagrams"></a>Rozszerzanie diagramów zależności

Możesz napisać kod, aby tworzyć i aktualizować diagramy zależności oraz weryfikować strukturę kodu programu względem diagramów zależności w Visual Studio. Można dodawać polecenia wyświetlane w menu skrótów (kontekstowych) diagramów, dostosowywać gesty przeciągania i upuszczania oraz uzyskać dostęp do modelu warstwy z szablonów tekstowych. Możesz spakować te rozszerzenia do rozszerzenia Visual Studio Integration Extension (VSIX) i rozpowszechnić je wśród innych Visual Studio użytkowników.

## <a name="requirements"></a>Wymagania

Na komputerze, na którym chcesz tworzyć rozszerzenia warstw, musisz mieć zainstalowane następujące elementy:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Zestaw SDK modelowania dla Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Na komputerze, na którym chcesz uruchamiać rozszerzenia warstw, Visual Studio mieć zainstalowaną odpowiednią wersję programu . Aby sprawdzić, które wersje aplikacji Visual Studio diagramy zależności, zobacz Obsługa wersji dla architektury [i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="see-also"></a>Zobacz też

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)
- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

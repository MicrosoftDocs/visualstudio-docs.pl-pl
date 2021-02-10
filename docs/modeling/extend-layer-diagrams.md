---
title: Rozszerzanie diagramów zależności
description: Dowiedz się, w jaki sposób można napisać kod, aby tworzyć i aktualizować diagramy zależności oraz jak sprawdzać strukturę kodu programu względem diagramów zależności w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10e0e07b6a8ee4245e19628e03bfdf484f94d34c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935147"
---
# <a name="extend-dependency-diagrams"></a>Rozszerzanie diagramów zależności

Można napisać kod, aby tworzyć i aktualizować diagramy zależności oraz sprawdzać strukturę kodu programu względem diagramów zależności w programie Visual Studio. Można dodawać polecenia, które pojawiają się w menu skrótów (kontekstu) diagramów, dostosowuje gesty przeciągania i upuszczania oraz uzyskiwać dostęp do modelu warstwy z szablonów tekstowych. Można spakować te rozszerzenia w rozszerzeniu integracji programu Visual Studio (VSIX) i przekazać je innym użytkownikom programu Visual Studio.

## <a name="requirements"></a>Wymagania

Na komputerze, na którym chcesz opracowywać rozszerzenia warstwy, muszą być zainstalowane następujące elementy:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Modeling SDK dla programu Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Na komputerze, na którym chcesz uruchomić rozszerzenia warstwy, musi być zainstalowana odpowiednia wersja programu Visual Studio. Aby sprawdzić, które wersje programu Visual Studio obsługują diagramy zależności, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Zobacz też

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)
- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

---
title: Dodawanie rozszerzeń do definicji DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9e4c80dee056d559822006627c86f4b4884942c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991139"
---
# <a name="add-extensions-to-dsl-definitions"></a>Dodawanie rozszerzeń do definicji języka DSL

Rozszerzenie definicji DSL umożliwia tworzenie pakietu rozszerzenia języka specyficznego dla domeny (DSL). Rozszerzenia DSL, który jest zawarty w Visual Studio Integration rozszerzenie (VSIX), można zainstalować na komputerze użytkownika w taki sam sposób jak element DSL. Dodatkowe funkcje można dynamicznie włączone i wyłączone w czasie wykonywania. Językami DSL nie muszą być jawnie zaprojektowane dla rozszerzenia, a rozszerzenia można zaprojektować później lub przez osoby trzecie, bez zmiany rozszerzonej DSL.

Rozszerzenia DSL mogą obejmować następujące funkcje:

-   Właściwości elementów modelu i prezentacji

-   Dekoratory dla kształtów i łączników

-   Klasy, relacje, kształty i łączniki

-   Ograniczenia sprawdzania poprawności

-   Karty i elementów przybornika

Użytkownik rozszerzonej DSL można tworzyć i zapisywanie modelu, który zawiera wystąpienia dodatkowe funkcje. Model może zostać odczytany przez innych użytkowników, którzy mają zainstalowane odpowiednie rozszerzenie. Użytkownicy, którzy nie zainstalowano rozszerzenia nie można użyć dodatkowych funkcji, ale można zaktualizować i zapisywanie modelu bez utraty dodatkowe funkcje.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też

- [Wpisy w blogu pokrewne](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

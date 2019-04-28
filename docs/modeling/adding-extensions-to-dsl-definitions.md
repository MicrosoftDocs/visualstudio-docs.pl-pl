---
title: Dodawanie rozszerzeń do definicji DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5c02fc28e7ffec4765d94758c838ab149e7ac3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62960491"
---
# <a name="add-extensions-to-dsl-definitions"></a>Dodawanie rozszerzeń do definicji języka DSL

Rozszerzenie definicji DSL umożliwia tworzenie pakietu rozszerzenia języka specyficznego dla domeny (DSL). Rozszerzenia DSL, który jest zawarty w Visual Studio Integration rozszerzenie (VSIX), można zainstalować na komputerze użytkownika w taki sam sposób jak element DSL. Dodatkowe funkcje można dynamicznie włączone i wyłączone w czasie wykonywania. Językami DSL nie muszą być jawnie zaprojektowane dla rozszerzenia, a rozszerzenia można zaprojektować później lub przez osoby trzecie, bez zmiany rozszerzonej DSL.

Rozszerzenia DSL mogą obejmować następujące funkcje:

- Właściwości elementów modelu i prezentacji

- Dekoratory dla kształtów i łączników

- Klasy, relacje, kształty i łączniki

- Ograniczenia sprawdzania poprawności

- Karty i elementów przybornika

Użytkownik rozszerzonej DSL można tworzyć i zapisywanie modelu, który zawiera wystąpienia dodatkowe funkcje. Model może zostać odczytany przez innych użytkowników, którzy mają zainstalowane odpowiednie rozszerzenie. Użytkownicy, którzy nie zainstalowano rozszerzenia nie można użyć dodatkowych funkcji, ale można zaktualizować i zapisywanie modelu bez utraty dodatkowe funkcje.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też

- [Wpisy w blogu pokrewne](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

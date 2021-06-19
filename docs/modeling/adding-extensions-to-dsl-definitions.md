---
title: Dodawanie rozszerzeń do definicji DSL
description: Dowiedz się, jak rozszerzenie definicji DSL umożliwia tworzenie pakietu rozszerzeń dla języka specyficznego dla domeny (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d9f1c92ebb879517d497af41fe98cec4492bd95
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384892"
---
# <a name="add-extensions-to-dsl-definitions"></a>Dodawanie rozszerzeń do definicji języka DSL

Rozszerzenie definicji DSL umożliwia utworzenie pakietu rozszerzeń dla języka specyficznego dla domeny (DSL). Rozszerzenie DSL, które znajduje się w rozszerzeniu Visual Studio Integration Extension (VSIX), można zainstalować na komputerze użytkownika w taki sam sposób jak DSL. Dodatkowe funkcje można dynamicznie włączać i wyłączać w czasie uruchamiania. Nie trzeba jawnie projektować rozszerzeń dla rozszerzeń, a rozszerzenia mogą być projektowane później lub przez inne firmy bez zmiany rozszerzonego DSL.

Rozszerzenia DSL mogą obejmować następujące funkcje:

- Właściwości elementów modelu i prezentacji

- Dekoratory kształtów i łączników

- Klasy, relacje, kształty i łączniki

- Ograniczenia walidacji

- Elementy i karty przybornika

Użytkownik rozszerzonego DSL może utworzyć i zapisać model, który zawiera wystąpienia dodatkowych funkcji. Model może być odczytywany przez innych użytkowników, którzy mają zainstalowane odpowiednie rozszerzenie. Użytkownicy, którzy nie mają zainstalowanego rozszerzenia, nie mogą korzystać z dodatkowych funkcji, ale mogą aktualizować i zapisywać model bez utraty dodatkowych funkcji.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też

- [Powiązane wpisy w blogu](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

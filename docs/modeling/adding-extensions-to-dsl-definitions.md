---
title: Dodawanie rozszerzeń do definicji DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 767973705d004a46644a51ba20ad9292ab80cb39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654368"
---
# <a name="add-extensions-to-dsl-definitions"></a>Dodawanie rozszerzeń do definicji języka DSL

Rozszerzenie definicji DSL umożliwia utworzenie pakietu rozszerzeń dla języka specyficznego dla domeny (DSL). Rozszerzenie DSL, które jest zawarte w rozszerzeniu integracji programu Visual Studio (VSIX), można zainstalować na komputerze użytkownika w taki sam sposób, jak w przypadku połączenia DSL. Dodatkowe funkcje mogą być dynamicznie włączane i wyłączane w czasie wykonywania. Językami DSL nie muszą być jawnie przeznaczone do rozszerzenia, a rozszerzenia mogą być zaprojektowane w późniejszym czasie lub przez inne osoby, bez zmiany rozszerzonego rozwiązania DSL.

Rozszerzenia DSL mogą zawierać następujące funkcje:

- Właściwości elementów model i prezentacja

- Dekoratory dla kształtów i łączników

- Klasy, relacje, kształty i łączniki

- Ograniczenia walidacji

- Elementy i karty przybornika

Użytkownik z rozszerzoną funkcją DSL może utworzyć i zapisać model, który zawiera wystąpienia dodatkowych funkcji. Model może być odczytywany przez innych użytkowników, którzy zainstalowali odpowiednie rozszerzenie. Użytkownicy, którzy nie zainstalowali rozszerzenia, nie mogą korzystać z dodatkowych funkcji, ale mogą aktualizować i zapisywać model bez utraty dodatkowych funkcji.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też

- [Powiązane wpisy w blogu](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

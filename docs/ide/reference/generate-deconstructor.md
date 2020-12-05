---
title: Generuj szybką akcję dekonstruktora
description: Dowiedz się, jak za pomocą menu szybkie akcje i refaktoryzacje natychmiast wygenerować element zastępczy metody dla nowego dekonstruktora.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ff2ac7682eff1c3da0597a95945a6a0b016d9213
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617256"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generuj Konstruktor w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

**Co:** Umożliwia natychmiastowe wygenerowanie elementu pośredniczącego metody dla nowego dekonstruktora.

**Kiedy:** Chcesz prawidłowo dekonstruować typ.

**Dlaczego:** Można ręcznie wpisać dekonstruktor, ale ta funkcja generuje skrót dla użytkownika z poprawnymi parametrami out.

## <a name="generate-a-deconstructor"></a>Generuj Konstruktor

1. Zadeklaruj nowy typ z określonymi pożądanymi parametrami out. Ta deklaracja spowoduje błąd, gdy nie można znaleźć wystąpienia dekonstrukcji pasującego do deklaracji.

   ![Brak błędu dekonstruktora](media/deconstruct.png)

2. Wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Za pomocą kursora w deklaracji wybierz pozycję Ctrl +. Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Wybierz :::image type="icon" source="media/screwdriver.png"::: ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstu znajduje się już w pustym wierszu w klasie.

      ![Generuj poprawkę kodu dekonstruktora](media/deconstruct-codefix.png)

3. Wybierz pozycję **Generuj metodę "MyInternalClass. dekonstrukcja"** , aby wygenerować Konstruktor.

   ![Otrzymany kod dekonstruktora](media/deconstruct-result.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
---
title: Generuj szybką akcję dekonstruktora
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5a3a89d15d05b44575fede98d3043d706b24c1d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531886"
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
      - Wybierz ikonę ![śrubokręt](media/screwdriver.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w pustym wierszu w klasie.

      ![Generuj poprawkę kodu dekonstruktora](media/deconstruct-codefix.png)

3. Wybierz pozycję **Generuj metodę "MyInternalClass. dekonstrukcja"** , aby wygenerować Konstruktor.

   ![Otrzymany kod dekonstruktora](media/deconstruct-result.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
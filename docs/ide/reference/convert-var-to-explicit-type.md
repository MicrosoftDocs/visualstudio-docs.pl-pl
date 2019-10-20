---
title: Kod refaktoryzacji do zamiany var z typem jawnym
ms.date: 05/15/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 566d064ac0ac1b9c48ee8e75697cef39b2ec4ee1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661689"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refaktoryzacja w celu zastąpienia wariancji typem jawnym

Użyj tego refaktoryzacji, aby zastąpić [wariancję](/dotnet/csharp/language-reference/keywords/var) w deklaracji zmiennej lokalnej z typem jawnym.

To Refaktoryzacja dotyczy:

- C#

## <a name="why-to-use-an-explicit-type"></a>Dlaczego należy używać typu jawnego

Poniżej przedstawiono kilka powodów, dla których należy zadeklarować zmienną z typem jawnym:

- Aby poprawić czytelność kodu.

- Gdy nie chcesz inicjować zmiennej w deklaracji.

Należy jednak użyć funkcji [var](/dotnet/csharp/language-reference/keywords/var) , gdy zmienna jest inicjowana z typem anonimowym, a właściwości obiektu są dostępne w późniejszym momencie. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienneC#lokalne ()](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Jak z niej korzystać

1. Umieść karetkę dla słowa kluczowego `var`.

1. Naciśnij klawisz **Ctrl** + **.** lub kliknij ikonę śrubokrętu ![screwdriver ikonę ](../media/screwdriver-icon.png) na marginesie pliku kodu.

   ![Użyj jawnego menu szybkie akcje typu](media/use-explicit-type.png)

1. Wybierz opcję **Użyj typu jawnego**. Lub wybierz pozycję **Podgląd zmian** , aby otworzyć okno dialogowe [Podgląd zmian](../../ide/preview-changes.md) , a następnie wybierz pozycję **Zastosuj**.

## <a name="see-also"></a>Zobacz także

- [Niejawnie wpisane zmienneC#()](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
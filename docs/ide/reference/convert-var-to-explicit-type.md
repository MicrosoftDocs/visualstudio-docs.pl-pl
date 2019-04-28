---
title: Refaktoryzacja kodu, aby zastąpić var jawnego typu
ms.date: 05/15/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2708bca578b613fac77e9b8ce77b1b2aff8f0945
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968158"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refaktoryzacja, aby zastąpić var jawnego typu

Użyj tej refaktoryzacji, aby zamienić [var](/dotnet/csharp/language-reference/keywords/var) w deklaracji zmiennej lokalnej z typem jawnym.

Ta Refaktoryzacja mają zastosowanie do:

- C#

## <a name="why-to-use-an-explicit-type"></a>Dlaczego Użyj jawnego typu

Poniżej przedstawiono przyczyny, aby zadeklarować zmienną z typem jawnym:

- Aby zwiększyć czytelność kodu.

- Jeśli nie chcesz zainicjować zmienną w deklaracji.

Jednak [var](/dotnet/csharp/language-reference/keywords/var) musi być użyty, gdy zmienna jest inicjowana za pomocą typu anonimowego i właściwości obiektu są dostępne w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Jak z niej korzystać

1. Umieść karetkę na `var` — słowo kluczowe.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikonę śrubokręt](../media/screwdriver-icon.png) ikonę na marginesie pliku kodu.

   ![Użyj jawnego typu w menu Szybkie akcje](media/use-explicit-type.png)

1. Wybierz **Użyj jawnego typu**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

## <a name="see-also"></a>Zobacz także

- [Niejawnie wpisane zmienne (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
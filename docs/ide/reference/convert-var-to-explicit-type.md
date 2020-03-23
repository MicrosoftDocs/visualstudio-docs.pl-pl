---
title: Kod refaktoryzatora zastępujący var typem jawnym
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 4ec388564e1851402f085f6bbaefba08dbea212c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595777"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refaktoryzacja w celu zastąpienia var typem jawnym

Ta refaktoryzacja służy do zastępowania [var](/dotnet/csharp/language-reference/keywords/var) w deklaracji zmiennej lokalnej typem jawnym.

Ten refaktoryzator ma zastosowanie do:

- C#

## <a name="why-to-use-an-explicit-type"></a>Dlaczego warto używać typu jawnego

Oto kilka powodów, dla których warto zadeklarować zmienną o jawnym typie:

- Aby poprawić czytelność kodu.

- Jeśli nie chcesz inicjować zmiennej w deklaracji.

Jednak [var](/dotnet/csharp/language-reference/keywords/var) musi być używany, gdy zmienna jest inicjowana z typem anonimowym i właściwości obiektu są dostępne w późniejszym punkcie. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Korzystanie

1. Umieść cieszę `var` na słowie kluczowym.

1. Naciśnij **klawisze Ctrl**+**.** lub kliknij ikonę ![ikony](../media/screwdriver-icon.png) śrubokręta na marginesie pliku kodu.

   ![Użyj menu szybkie akcje typu jawnego](media/use-explicit-type.png)

1. Wybierz **opcję Użyj typu jawnego**. Możesz też wybrać **opcję Podgląd zmian,** aby otworzyć okno dialogowe [Podgląd zmian,](../../ide/preview-changes.md) a następnie wybierz pozycję **Zastosuj**.

## <a name="see-also"></a>Zobacz też

- [Niejawnie wpisane zmienne (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)

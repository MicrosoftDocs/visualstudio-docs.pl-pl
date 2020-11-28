---
title: Kod refaktoryzacji do zamiany var z typem jawnym
description: Dowiedz się, jak używać funkcji Szybkie akcje, aby zamienić wariancję na wyrażenie zmiennej lokalnej z typem jawnym.
ms.custom: SEO-VS-2020
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a9270ca6cf7407d196eca211b6a76c6dc6a8be78
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305534"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refaktoryzacja w celu zastąpienia wariancji typem jawnym

Użyj tego refaktoryzacji, aby zastąpić [wariancję](/dotnet/csharp/language-reference/keywords/var) w deklaracji zmiennej lokalnej z typem jawnym.

To Refaktoryzacja dotyczy:

- C#

## <a name="why-to-use-an-explicit-type"></a>Dlaczego należy używać typu jawnego

Poniżej przedstawiono kilka powodów, dla których należy zadeklarować zmienną z typem jawnym:

- Aby poprawić czytelność kodu.

- Gdy nie chcesz inicjować zmiennej w deklaracji.

Należy jednak użyć funkcji [var](/dotnet/csharp/language-reference/keywords/var) , gdy zmienna jest inicjowana z typem anonimowym, a właściwości obiektu są dostępne w późniejszym momencie. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Sposób użycia

1. Umieść karetkę na `var` słowie kluczowym.

1. Naciśnij klawisz **Ctrl** + **.** lub kliknij ![ ikonę ikony śrubokrętu śrubokrętu ](../media/screwdriver-icon.png) na marginesie pliku kodu.

   ![Użyj jawnego menu szybkie akcje typu](media/use-explicit-type.png)

1. Wybierz opcję **Użyj typu jawnego**. Lub wybierz pozycję **Podgląd zmian** , aby otworzyć okno dialogowe [Podgląd zmian](../../ide/preview-changes.md) , a następnie wybierz pozycję **Zastosuj**.

## <a name="see-also"></a>Zobacz też

- [Niejawnie wpisane zmienne (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)

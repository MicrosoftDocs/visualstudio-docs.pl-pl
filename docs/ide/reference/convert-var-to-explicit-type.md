---
title: Kod refaktoryzacji do zamiany var z typem jawnym
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595777"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refaktoryzacja w celu zastąpienia wariancji typem jawnym

Użyj tego refaktoryzacji, aby zastąpić [wariancję](/dotnet/csharp/language-reference/keywords/var) w deklaracji zmiennej lokalnej z typem jawnym.

Ta Refaktoryzacja mają zastosowanie do:

- Język C#

## <a name="why-to-use-an-explicit-type"></a>Dlaczego należy używać typu jawnego

Poniżej przedstawiono kilka powodów, dla których należy zadeklarować zmienną z typem jawnym:

- Aby poprawić czytelność kodu.

- Gdy nie chcesz inicjować zmiennej w deklaracji.

Należy jednak użyć funkcji [var](/dotnet/csharp/language-reference/keywords/var) , gdy zmienna jest inicjowana z typem anonimowym, a właściwości obiektu są dostępne w późniejszym momencie. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienneC#lokalne ()](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Jak z niej korzystać

1. Umieść karetkę dla słowa kluczowego `var`.

1. Naciśnij klawisz **Ctrl**+ **.** lub kliknij ikonę śrubokrętu ![ikonę śrubokrętu](../media/screwdriver-icon.png) na marginesie pliku kodu.

   ![Użyj jawnego menu szybkie akcje typu](media/use-explicit-type.png)

1. Wybierz opcję **Użyj typu jawnego**. Lub wybierz pozycję **Podgląd zmian** , aby otworzyć okno dialogowe [Podgląd zmian](../../ide/preview-changes.md) , a następnie wybierz pozycję **Zastosuj**.

## <a name="see-also"></a>Zobacz także

- [Niejawnie wpisane zmienneC#()](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)

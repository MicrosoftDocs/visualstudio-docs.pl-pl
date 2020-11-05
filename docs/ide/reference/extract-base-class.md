---
title: Wyodrębnij klasę bazową
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8eb87ff8e3acc141c49a495b155fb769e03fb89b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402289"
---
# <a name="extract-base-class"></a>Wyodrębnij klasę bazową

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Wyodrębnij klasę bazową.

**Kiedy:** Chcesz wyodrębnić członków z wybranej klasy do nowej klasy bazowej.

**Dlaczego:** Ręczne ściąganie członków może zająć dużo czasu i wypróbować przepływ pracy. 

## <a name="how-to"></a>Porady

1. Umieść karetkę na nazwie klasy lub wyróżnionej składowej.

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

3. Wybierz opcję **Ściągnij elementy członkowskie do nowej klasy bazowej**.

    ![Okno dialogowe wyodrębniania klasy bazowej](media/extract-base-class.png)

Zostanie otwarte okno dialogowe **Wyodrębnij klasę bazową** , w którym można określić nazwę klasy bazowej i lokalizację, w której należy ją umieścić. Można wybrać elementy członkowskie, które mają zostać przeniesione do nowej klasy bazowej, i wybrać, aby uczynić elementy abstrakcyjne, zaznaczając pole wyboru w kolumnie Utwórz abstrakcyjny.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

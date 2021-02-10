---
title: Wyodrębnianie klasy bazowej
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8c389ac6285b3f20dcdf05833f1ff3202d155c4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962811"
---
# <a name="extract-base-class"></a>Wyodrębnianie klasy bazowej

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

Zostanie otwarte okno dialogowe **Wyodrębnij klasę bazową**, w którym można określić nazwę klasy bazowej i lokalizację, w której należy ją umieścić. Można wybrać elementy członkowskie, które mają zostać przeniesione do nowej klasy bazowej, i wybrać, aby uczynić elementy abstrakcyjne, zaznaczając pole wyboru w kolumnie Utwórz abstrakcyjny.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

---
title: Wyodrębnianie klasy bazowej
description: To Refaktoryzacja wyodrębnia elementy członkowskie z wybranej klasy do nowej klasy bazowej.
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
ms.openlocfilehash: 9d7a21bbd3e51ee6a6776ca728a545cbbb731cab
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466280"
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

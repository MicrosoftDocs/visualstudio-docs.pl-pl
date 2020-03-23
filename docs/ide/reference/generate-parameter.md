---
title: Generowanie refaktoryzacji parametrów
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094349"
---
# <a name="generate-parameter"></a>Generowanie parametru

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Automatycznie generuje parametr metody.

**Kiedy:** Odwołujesz się do zmiennej w metodzie, która nie istnieje w bieżącym kontekście i otrzymujesz błąd; można wygenerować parametr jako poprawkę kodu. 

**Dlaczego?** Można szybko zmodyfikować podpis metody bez utraty kontekstu.

## <a name="how-to"></a>Porady

1. Umieść kursor w nazwie zmiennej i naciśnij klawisz **Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
1. Wybierz **polecenie Generuj parametr**.

   ![Generowanie parametru](media/generate-parameter.png) 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

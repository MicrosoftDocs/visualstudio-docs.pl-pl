---
title: Uzupełnianie przez funkcję IntelliSense niezaimportowanych typów
description: Jak używać uzupełnianie przez funkcję IntelliSense dla typów, które jeszcze nie zaimportowano jeszcze z `using` dyrektywy.
ms.date: 06/20/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f313cfa8520e4c13b310be0f9223466c529ca18f
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67313207"
---
# <a name="intellisense-completion-for-unimported-types"></a>Uzupełnianie przez funkcję IntelliSense niezaimportowanych typów

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Funkcja IntelliSense podaje uzupełniania niezaimportowanych typów.

**Kiedy:** Aby dodać typ, który ma już zależności w projekcie, ale instrukcja importu nie został jeszcze dodany do pliku. 

**Dlaczego:** Nie trzeba ręcznie dodaj instrukcję importu do pliku.

## <a name="how-to"></a>Instrukcje

1. Po rozpoczęciu przy użyciu typu, który ma zależność w projekcie, IntelliSense zapewni sugestie.
2. Naciśnij klawisz **kartę**. 

   Instrukcja importu zostaną dodane do pliku.

   ![Uzupełnianie przez funkcję IntelliSense niezaimportowanych typów](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

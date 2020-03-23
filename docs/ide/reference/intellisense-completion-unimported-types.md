---
title: Zakończenie intellisense dla typów nieprzekażonych
description: Jak używać intellisense zakończenia dla typów, które nie `using` zostały jeszcze zaimportowane z dyrektywą.
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
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094260"
---
# <a name="intellisense-completion-for-unimported-types"></a>Zakończenie intellisense dla typów nieprzekażonych

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** IntelliSense zapewnia ukończenie dla typów nieprzekażonych.

**Kiedy:** Chcesz dodać typ, który ma już zależność w projekcie, ale instrukcja importu nie została jeszcze dodana do pliku. 

**Dlaczego?** Nie trzeba ręcznie dodawać instrukcji importu do pliku.

## <a name="how-to"></a>Porady

1. Po uruchomieniu przy użyciu typu, który ma zależność w projekcie, IntelliSense daje sugestie.
2. Naciśnij **klawisz Tab**. 

   Instrukcja importu zostanie dodana do pliku.

   ![Zakończenie intellisense dla typów nieprzekażonych](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

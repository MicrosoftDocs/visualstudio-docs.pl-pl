---
title: Konwertuj typ anonimowy na klasę
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
ms.openlocfilehash: 2379ce588eeb4773e562f630ade37e28d7f17315
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094288"
---
# <a name="convert-anonymous-type-to-class"></a>Konwertowanie typu anonimowego na klasę

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Konwertuj typ anonimowy na klasę.

**Kiedy:** Masz typ anonimowy, który chcesz nadal kontynuować w klasie.

**Dlaczego?** Typy anonimowe są przydatne, jeśli używasz ich tylko lokalnie. W miarę rozwoju kodu miło jest mieć łatwy sposób promowania ich do klasy.

## <a name="how-to"></a>Porady

1. Umieść kursor w typie anonimowym.
2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

   ![Konwertuj typ anonimowy na klasę](media/convert-anon-to-class.png)

2. Naciśnij **klawisz Enter,** aby zaakceptować refaktoryzowanie.

   ![Konwertuj typ anonimowy na klasę zaakceptowany](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

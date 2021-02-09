---
title: Konwertuj typ anonimowy na klasę
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje, aby przekonwertować typ anonimowy na klasę w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: 19e755e4b56675265d85a416684f2b42bd7ccd13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907655"
---
# <a name="convert-anonymous-type-to-class"></a>Konwertowanie typu anonimowego na klasę

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Konwertuj typ anonimowy na klasę.

**Kiedy:** Masz typ anonimowy, który chcesz kontynuować Kompilowanie w klasie.

**Dlaczego:** Typy anonimowe są przydatne, jeśli są używane lokalnie. Wraz ze wzrostem ilości kodu można łatwo wspierać je do klasy.

## <a name="how-to"></a>Porady

1. Umieść kursor w typie anonimowym.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   ![Konwertuj typ anonimowy na klasę](media/convert-anon-to-class.png)

2. Naciśnij klawisz **Enter** , aby zaakceptować refaktoryzację.

   ![Konwertuj typ anonimowy na zaakceptowaną klasę](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

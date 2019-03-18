---
title: Przekonwertować typu anonimowego na klasę
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f29e31fb87d8b18e7f5a46d16f90217ee08d51f6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58154585"
---
# <a name="convert-anonymous-type-to-class"></a>Konwertowanie typu anonimowego na klasę

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Do klasy, należy przekonwertować typu anonimowego.

**Kiedy:** Masz typ anonimowy, który chcesz, aby kontynuować tworzenie w klasie.

**Dlaczego:** Typy anonimowe są przydatne, jeśli tylko używasz je lokalnie. Wraz z rozwojem kodu to miły łatwy sposób podwyższenie im poziomu klasa.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w typu anonimowego.
2. Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

   ![Przekonwertować typu anonimowego na klasę](media/convert-anon-to-class.png)

2. Naciśnij klawisz **Enter** do akceptowania refaktoryzacji.

   ![Przekonwertować typu anonimowego na klasy zaakceptowane](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

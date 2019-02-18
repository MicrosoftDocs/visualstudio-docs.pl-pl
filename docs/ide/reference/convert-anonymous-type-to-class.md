---
title: Przekonwertować typu anonimowego na klasę
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e3613f365b2510111f6854087a597df387ab1a4c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335945"
---
# <a name="convert-anonymous-type-to-class"></a>Przekonwertować typu anonimowego na klasę

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

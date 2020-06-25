---
title: Generuj prywatne pole i właściwość z konstruktora
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56bd361d2bffb4ff17b03ac6743837032d1934e1
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283726"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Generuj prywatne pole i właściwość z konstruktora

To Refaktoryzacja dotyczy: 

- C# 

**Co:** Generuj prywatne pole lub właściwość z konstruktora. 

**Kiedy:** Chcesz szybko dodać i zainicjować prywatne pole lub właściwość z konstruktora.

**Dlaczego:** Pisanie prywatnych pól i właściwości może być czasochłonne i powtarzane. Korzystanie z tego refaktoryzacji jest szybkie i sprawia, że program jest bardziej niezawodny.

## <a name="how-to"></a>Porady 

1. Umieść kursor na nazwie parametru w konstruktorze.

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   
3. Następnie wybierz jedną z opcji:

- **Utwórz i zainicjuj pole** lub **Utwórz i zainicjuj Właściwość**.

   ![Generowanie pola prywatnego z poziomu konstruktora](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Zobacz też 

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

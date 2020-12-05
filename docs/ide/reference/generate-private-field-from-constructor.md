---
title: Generuj prywatne pole i właściwość z konstruktora
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje w celu wygenerowania prywatnego pola lub właściwości z konstruktora.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e989efed8b58746312ed5f5a510efa049393f3db
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617464"
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

## <a name="see-also"></a>Zobacz także 

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

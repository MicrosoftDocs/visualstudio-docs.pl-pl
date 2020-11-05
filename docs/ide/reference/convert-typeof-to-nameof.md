---
title: Konwertuj element typeof na element nameof
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 96bd4d67302fb09e5c1cb7837ad73b345ad88c81
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400327"
---
# <a name="convert-typeof-to-nameof"></a>Konwertuj `typeof` na `nameof`

To Refaktoryzacja dotyczy:

- C#
- Visual Basic

**Co:** Umożliwia konwertowanie wystąpienia programu na `typeof(<QualifiedType>).Name` `nameof(<QualifiedType>)` w języku C# i wystąpienia `GetType(<QualifiedType>).Name` na `NameOf(<QualifiedType>)` w Visual Basic.

**Kiedy:**  Wszystkie wystąpienia elementu `typeof(<QualifiedType>).Name` Where `someType` nie są typem ogólnym. To wykluczenie jest konieczne, ponieważ ten przypadek nie zwraca tej samej wartości ciągu co `nameof(<QualifiedType>)` . Ta sama wartość dotyczy wystąpienia Visual Basic.

**Dlaczego:** Użycie `nameof` zamiast nazwy `type` pozwala uniknąć odbicia przy pobieraniu `type` obiektu i stanowi bardziej pragmatyczny sposób pisania.

## <a name="how-to"></a>Porady

1. Umieść kursor w ramach `typeof(<QualifiedType>).Name` wystąpienia dla języka C# lub `GetType(<QualifiedType>).Name` w Visual Basic.

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

3. Wybierz jedną z następujących opcji:

    - C#
      <br>Wybierz opcję **Konwertuj modyfikator "typeof" na "nameof"** : ![ Konwertuj element typeof na nameof](media/convert-type-of.PNG)

    - Visual Basic
      <br>Wybierz pozycję **Konwertuj "GetType" na "nameof"** : ![ Konwertuj element typeof na nameof](media/convert-get-type.PNG)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

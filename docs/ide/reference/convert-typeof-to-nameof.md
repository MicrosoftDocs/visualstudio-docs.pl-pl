---
title: Konwertuj element typeof na element nameof
description: Dowiedz się, jak używać menu szybkie akcje i refaktoryzacje w programie Visual Studio, aby konwertować typeof na nameof w języku C# i GetType do NameOf w Visual Basic.
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
ms.openlocfilehash: ce76b82e2ebc68634be7cf4d463f6b8216d81e06
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761202"
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
      <br>Wybierz opcję **Konwertuj modyfikator "typeof" na "nameof"**: ![ zrzut ekranu przedstawiający menu szybkie akcje i refaktoryzacje w programie Visual Studio z wybraną opcją Konwertuj wartość "typeof" na wartość "nameof", a pokazane zmiany kodu w języku C#.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Wybierz pozycję **Konwertuj "GetType" na "nameof"**: ![ zrzut ekranu przedstawiający menu szybkie akcje i refaktoryzacje w programie Visual Studio z wybraną opcją Konwertuj wartość "GetType" na wartość "NameOf" i Visual Basic wyświetlenia zmian w kodzie.](media/convert-get-type.PNG)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

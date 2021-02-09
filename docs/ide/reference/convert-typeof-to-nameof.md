---
title: Konwertuj element typeof na element nameof
description: Dowiedz się, jak używać menu szybkie akcje i refaktoryzacje w programie Visual Studio, aby konwertować typeof na nameof w języku C# i GetType do NameOf w Visual Basic.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f93c5232f852e1390eac9e2ebb57235abc5e1f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919690"
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

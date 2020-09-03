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
ms.openlocfilehash: 233393114883c2a9833aa7ec82f0d78f0ef33bae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88251304"
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
  <br>Wybierz opcję **Konwertuj modyfikator "typeof" na "nameof",** 
   ![ Konwertuj element typeof na nameof](media/convert-type-of.PNG)

- Visual Basic
  <br>Wybierz pozycję **Konwertuj "GetType" na element "nameof"** ![ convert typeof na nameof](media/convert-get-type.PNG)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)

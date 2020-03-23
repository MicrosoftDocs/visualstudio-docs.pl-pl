---
title: Opcje refaktoryzacji statycznej funkcji lokalnej
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c297457c910c484c05c974c581e89c75e0ad44e5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77144837"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Statyczne funkcje lokalne refaktoryzowania i szybkie akcje

W tym artykule opisano dwie funkcje produktywności związane ze statycznymi funkcjami lokalnymi. Jednym z nich jest refaktoryzacji, która sprawia, że funkcja lokalna statyczne, a drugi jest szybka akcja, która generuje kod do przekazywania zmiennych do statycznej funkcji lokalnej.

## <a name="make-local-function-static"></a>Tworzenie funkcji statycznych z funkcji lokalnych

Ten refaktoryzator ma zastosowanie do:

- C#

**Co:** Sprawia, że funkcja lokalna statyczne i przekazuje w zmiennych zdefiniowanych poza funkcją do deklaracji funkcji i wywołań.

**Kiedy:** Chcesz, aby funkcja lokalna była statyczna i dla wszystkich zmiennych, które mają być zdefiniowane w zakresie funkcji.

**Dlaczego?** Statyczne funkcje lokalne zwiększa czytelność: wiedząc, że określony kod jest izolowany ułatwia zrozumienie, ponowne czytanie i ponowne użycie. Statyczne funkcje lokalne zapewniają również zakres, aby zapobiec zanieczyszczaniu klasy z funkcją statyczną, która jest wywoływana tylko w jednej metodzie.

### <a name="how-to"></a>Porady

1. Umieść swoją cieszę na lokalnej nazwie funkcji.

2. Naciśnij **klawisze Ctrl**+**.** (kropka), aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

   ![Tworzenie funkcji statycznych z funkcji lokalnych](media/make-local-function-static.png)

3. Wybierz **pozycję Opcję "Udostępnij funkcję statyczną" wybierz opcję "Zrób lokalną funkcję".**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Jawnie przekazuje zmienną w statycznej funkcji lokalnej

Ta szybka akcja dotyczy:

- C#

**Co:** Przekazuje zmienną jawnie do lokalnej funkcji statycznej.

**Kiedy:** Chcesz, aby funkcja lokalna była statyczna, ale nadal używać zmiennych zainicjowanych poza nią.

**Dlaczego?** Za pomocą statycznych funkcji lokalnych zapewnia wyjaśnienie dla czytelników, ponieważ wiedzą, że można go zadeklarować i wywołać tylko w określonym kontekście programu. Zapewnia elastyczność definiowania zmiennych poza tym kontekstem, ale nadal można przekazać je jako argumenty do statycznej funkcji lokalnej.

### <a name="how-to"></a>Porady

1. Umieść cieszę na zmiennej, w której jest używana w statycznej funkcji lokalnej.

2. Naciśnij **klawisze Ctrl**+**.** (kropka), aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

   ![Jawnie przekaż zmienną w statycznej funkcji lokalnej](media/pass-variable-explicitly-static-local-function.png)

3. Wybierz pozycję **Przekaż jawnie zmienną do lokalnej funkcji statycznej**

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
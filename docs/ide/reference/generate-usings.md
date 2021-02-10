---
title: Generowanie deklaracji using
description: Dowiedz się, w jaki sposób używać menu szybkie akcje i refaktoryzacje, aby natychmiast dodać niezbędne operacje importowania lub użyć dyrektyw dla kodu kopiowania i wklejania.
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
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 0f73b50dc34e95161c4c85cd559abcf5c9bac60b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967998"
---
# <a name="add-missing-usings-in-visual-studio"></a>Dodaj brakujące użycia w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe dodanie niezbędnych importów lub [dyrektyw](/dotnet/csharp/language-reference/keywords/using-directive) dla kodu kopiowania i wklejania.

**Kiedy:** Typowym sposobem jest skopiowanie kodu z różnych miejsc w projekcie lub w innych źródłach i wklejenie go do nowego kodu. Ta szybka akcja umożliwia znalezienie brakujących dyrektyw Imports dla kodu kopiującego i wklejonego, a następnie poprosi o ich dodanie. Ta naprawa kodu może również dodać odwołania z projektu do projektu.

**Dlaczego:** Ponieważ szybka akcja automatycznie dodaje wymagane Importy, nie trzeba ręcznie kopiować `using` dyrektyw wymaganych przez kod.

## <a name="add-missing-usings-refactoring"></a>Dodaj brakujące składniki przy użyciu refaktoryzacji

1. Skopiuj kod z pliku i wklej go do nowego, bez uwzględniania `using` dyrektyw niezbędnych. W wyniku błędu następuje poprawka kodu, która dodaje brakujące `using` dyrektywy.

    > [!NOTE]
    > Tę sugestię należy włączyć w obszarze **narzędzia > opcje > edytorze tekstów > C# > Advanced > przy użyciu dyrektyw**.

2. Wybierz kombinację klawiszy CTRL +. , aby otworzyć menu **szybkie akcje i operacje refaktoryzacji** .

    ![Generowanie deklaracji using](media/generate-using-codefix.png)

3. Wybierz pozycję **using \<your reference\> ;** , aby dodać brakujące odwołanie.

    ![Generuj wynik użycia](media/generate-using-result.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)

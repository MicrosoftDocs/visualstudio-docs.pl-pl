---
title: Generowanie deklaracji using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 78786e6e6e7a8e5d8a8766138cb1a54a49416f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610891"
---
# <a name="add-missing-usings-in-visual-studio"></a>Dodaj brakujące użycia w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

**Co:** Umożliwia natychmiastowe dodanie niezbędnych importów lub [dyrektyw](/dotnet/csharp/language-reference/keywords/using-directive) dla kodu kopiowania i wklejania.

**Kiedy:** Typowym sposobem jest skopiowanie kodu z różnych miejsc w projekcie lub w innych źródłach i wklejenie go do nowego kodu. Ta szybka akcja umożliwia znalezienie brakujących dyrektyw Imports dla kodu kopiującego i wklejonego, a następnie poprosi o ich dodanie.

**Dlaczego:** Ponieważ szybka akcja automatycznie dodaje wymagane Importy, nie trzeba ręcznie kopiować dyrektyw `using` wymaganych przez kod.

## <a name="add-missing-usings-refactoring"></a>Dodaj brakujące składniki przy użyciu refaktoryzacji

1. Skopiuj kod z pliku i wklej go do nowego, bez uwzględniania niezbędnych dyrektyw `using`. W wyniku błędu następuje poprawka kodu, która dodaje brakujące dyrektywy `using`.

    > [!NOTE]
    > Tę sugestię należy włączyć w obszarze **narzędzia > opcje > edytorze tekstów > C# > Advanced > przy użyciu dyrektyw**.

2. Wybierz kombinację klawiszy CTRL +. , aby otworzyć menu **szybkie akcje i operacje refaktoryzacji** .

    ![Generowanie deklaracji using](media/generate-using-codefix.png)

3. Wybierz pozycję **using \<your reference \>;,** aby dodać brakujące odwołanie.

    ![Generuj wynik użycia](media/generate-using-result.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)

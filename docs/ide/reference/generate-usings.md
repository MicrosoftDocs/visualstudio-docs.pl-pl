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
ms.openlocfilehash: f3b3435e10d6bb9a71fd16b9286759b136c167f4
ms.sourcegitcommit: ea5e02720d71185f8e27fbea205024371b0c7ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544541"
---
# <a name="add-missing-usings-in-visual-studio"></a>Dodaj brakujące użycia w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Co:** Umożliwia natychmiastowe dodanie niezbędnych importów lub [dyrektyw](/dotnet/csharp/language-reference/keywords/using-directive) dla kodu kopiowania i wklejania.

**Kiedy:** Typowym sposobem jest skopiowanie kodu z różnych miejsc w projekcie lub w innych źródłach i wklejenie go do nowego kodu. Ta szybka akcja umożliwia znalezienie brakujących dyrektyw Imports dla kodu kopiującego i wklejonego, a następnie poprosi o ich dodanie. Ta naprawa kodu może również dodać odwołania z projektu do projektu.

**Dlaczego:** Ponieważ szybka akcja automatycznie dodaje wymagane Importy, nie trzeba ręcznie kopiować dyrektyw `using` wymaganych przez kod.

## <a name="add-missing-usings-refactoring"></a>Dodaj brakujące składniki przy użyciu refaktoryzacji

1. Skopiuj kod z pliku i wklej go do nowego, bez uwzględniania niezbędnych dyrektyw `using`. W wyniku błędu następuje poprawka kodu, która dodaje brakujące dyrektywy `using`.

    > [!NOTE]
    > Tę sugestię należy włączyć w obszarze **narzędzia > opcje > edytorze tekstów > C# > Advanced > przy użyciu dyrektyw**.

2. Wybierz kombinację klawiszy CTRL +. , aby otworzyć menu **szybkie akcje i operacje refaktoryzacji** .

    ![Generowanie deklaracji using](media/generate-using-codefix.png)

3. Wybierz pozycję **using \<odwołanie\>;,** aby dodać brakujące odwołanie.

    ![Generuj wynik użycia](media/generate-using-result.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)

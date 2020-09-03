---
title: Generowanie deklaracji using
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 903b160bac0e8096062e09fd78ff4c92c46cf8ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094321"
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

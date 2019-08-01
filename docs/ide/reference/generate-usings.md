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
ms.openlocfilehash: d971bcdaca4efdf587c7e441f1b0b28d21388dee
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416482"
---
# <a name="add-missing-usings-in-visual-studio"></a>Dodaj brakujące użycia w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Whatman** Umożliwia natychmiastowe dodanie niezbędnych instrukcji Imports lub [using](/dotnet/csharp/language-reference/keywords/using-statement) dla kodu kopiowania i wklejania.

**Czasie** Typowym sposobem jest skopiowanie kodu z różnych miejsc w projekcie lub w innych źródłach i wklejenie go do nowego kodu. Ta szybka akcja znajduje brakujące instrukcje Imports dla kodu kopiowania i wklejania, a następnie prosi o ich dodanie.

**Zalet** Ponieważ szybka akcja automatycznie dodaje wymagane Importy, nie trzeba ręcznie kopiować `using` instrukcji wymaganych przez kod.

## <a name="add-missing-usings-refactoring"></a>Dodaj brakujące składniki przy użyciu refaktoryzacji

1. Skopiuj kod z pliku i wklej go do nowego, bez uwzględniania niezbędnych `using` instrukcji. Wynikiem błędu jest dołączenie poprawki kodu, która dodaje brakujące `using` instrukcje.

    > [!NOTE]
    > Tę sugestię należy włączyć w obszarze **narzędzia > opcje > edytorze tekstów > C# > Advanced > przy użyciu dyrektyw**.

2. Wybierz kombinację klawiszy CTRL +. , aby otworzyć menu **szybkie akcje i operacje refaktoryzacji** .

    ![Generowanie deklaracji using](media/generate-using-codefix.png)

3. Wybierz **pozycję \<przy użyciu\>odwołania;** aby dodać brakujące odwołanie.

    ![Generuj wynik użycia](media/generate-using-result.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)

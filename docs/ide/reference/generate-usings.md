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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094321"
---
# <a name="add-missing-usings-in-visual-studio"></a>Dodawanie brakujących za pomocą programu Visual Studio

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe dodanie niezbędnych importów lub [za pomocą dyrektyw](/dotnet/csharp/language-reference/keywords/using-directive) dla kodu kopiowania i wklejanych.

**Kiedy:** Jest powszechną praktyką, aby skopiować kod z różnych miejsc w projekcie lub innych źródeł i wkleić go do nowego kodu. Ta szybka akcja znajduje brakujące dyrektywy importu dla kodu kopiowania i wklejenia, a następnie monituje o ich dodanie. Ta poprawka kodu można również dodać odwołania z projektu do projektu.

**Dlaczego?** Ponieważ szybka akcja automatycznie dodaje niezbędne importy, nie trzeba ręcznie `using` kopiować dyrektyw, które są potrzebne do kodu.

## <a name="add-missing-usings-refactoring"></a>Dodawanie brakujących użycia refaktoryzacji

1. Skopiuj kod z pliku i wklej `using` go do nowego bez uwzględnienia niezbędnych dyrektyw. Wynikowy błąd towarzyszy poprawka kodu, która dodaje `using` brakujące dyrektywy.

    > [!NOTE]
    > Tę sugestię należy włączyć w **obszarze Opcje > narzędzia > Edytor tekstu > C# > Zaawansowane > Korzystanie z dyrektyw**.

2. Wybierz pozycję Ctrl+. , aby otworzyć menu **Szybkie akcje i Refaktoryzowania.**

    ![Generowanie deklaracji using](media/generate-using-codefix.png)

3. Wybierz ** \<za\>pomocą odwołania ;** aby dodać brakujące odwołanie.

    ![Generowanie wyników użycia](media/generate-using-result.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)

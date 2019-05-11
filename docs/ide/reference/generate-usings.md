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
ms.openlocfilehash: 9124054dec08fde94ec98ca9e3ebdfb6e48d7384
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531632"
---
# <a name="generate-usings-in-visual-studio"></a>Generowanie z użycia w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Co:** Umożliwia to natychmiastowe dodanie odpowiednie Importy lub [za pomocą instrukcji](/dotnet/csharp/language-reference/keywords/using-statement) kopiowania i wklejony kod.

**Kiedy:** Jest to powszechną praktyką było skopiować kod z różnych miejsc w projekcie lub innych źródeł, a następnie wklej je do nowego kodu. Tej szybkiej akcji znajduje brakujące importuje oświadczenia dotyczące kopiowania i wklejony kod, a następnie wyświetla je dodać.

**Dlaczego:** Szybka akcja automatycznie doda odpowiednie Importy, dlatego nie musisz ręcznie skopiować `using` instrukcji, których potrzebuje Twój kod.

## <a name="generate-usings-refactoring"></a>Generowanie refaktoryzacji deklaracje Using

1. Skopiuj kod z plikiem i wklej go do nowej bez uwzględniania niezbędne `using` instrukcji. Błąd wynikowe towarzyszy poprawki kodu, który dodaje brakujący `using` instrukcji.

    > [!NOTE]
    > Należy włączyć tę sugestię w **Narzędzia > Opcje > Edytor tekstu > C# > Zaawansowane > przy użyciu dyrektywy**.

2. Wybierz klawisze Ctrl +. Aby otworzyć **szybkie akcje i Refaktoryzacje** menu.

    ![Generowanie deklaracji using](media/generate-using-codefix.png)

3. Wybierz **przy użyciu \<użytkownikowi\>;** można dodać brakujące odwołania.

    ![Generowanie wyników deklaracje Using](media/generate-using-result.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)

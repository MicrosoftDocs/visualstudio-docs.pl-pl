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
ms.openlocfilehash: 0ce1b620a6d8aba7e4aea767745891dff6d9f869
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790051"
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
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)

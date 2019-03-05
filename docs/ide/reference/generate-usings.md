---
title: Generowanie deklaracje Using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 9fd34b40bdd1167eca7fa1dff8ab60bcc787b7c7
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57325295"
---
# <a name="generate-usings-in-visual-studio"></a>Generowanie z użycia w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Co:** **Co:** Umożliwia to natychmiastowe dodanie odpowiednie Importy lub [za pomocą instrukcji](/dotnet/csharp/language-reference/keywords/using-statement) kopiowania i wklejony kodu.

**Kiedy:** Jest to powszechną praktyką, aby skopiować i wkleić kod z różnych miejsc w projekcie lub innych źródeł kodu. Tej szybkiej akcji analizuje Brak Import dla kopiowania i wklejony kod, a następnie wyświetla je dodać.

**Dlaczego:** Automatyczne dodanie odpowiednie Importy, użytkownik nie musi ręcznie kopiować potrzebną `using` instrukcji.

## <a name="generate-usings-refactoring"></a>Generowanie refaktoryzacji deklaracje Using

1. Skopiuj i Wklej kod z innego pliku bez uwzględniania niezbędne `using` instrukcji. Ten błąd jest teraz powiązany poprawki kodu, który dodaje brakujący `using` instrukcji.

    > [!NOTE] 
    > Tę sugestię musi być włączona w programie **Narzędzia > Opcje > Edytor tekstu > C# > Zaawansowane > przy użyciu dyrektywy**.

2. Naciśnij klawisz **Ctrl**+**.** Aby otworzyć **szybkie akcje i Refaktoryzacje** menu. 

    ![Generowanie deklaracje Using](media/generate-using-codefix.png)

3. Wybierz **przy użyciu \<użytkownikowi\>;** można dodać brakujące odwołania.

    ![Generowanie wyników deklaracje Using](media/generate-using-result.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
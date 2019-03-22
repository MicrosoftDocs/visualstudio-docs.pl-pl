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
ms.openlocfilehash: afd4b758332d9357dc20dd84e726d72da4d2db74
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355192"
---
# <a name="generate-usings-in-visual-studio"></a>Generowanie z użycia w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Co:** Umożliwia to natychmiastowe dodanie odpowiednie Importy lub [za pomocą instrukcji](/dotnet/csharp/language-reference/keywords/using-statement) kopiowania i wklejony kodu.

**Kiedy:** Jest to powszechną praktyką, aby skopiować i wkleić kod z różnych miejsc w projekcie lub innych źródeł kodu. Tej szybkiej akcji analizuje Brak Import dla kopiowania i wklejony kod, a następnie wyświetla je dodać.

**Dlaczego:** Automatyczne dodanie odpowiednie Importy, użytkownik nie musi ręcznie kopiować potrzebną `using` instrukcji.

## <a name="generate-usings-refactoring"></a>Generowanie refaktoryzacji deklaracje Using

1. Skopiuj i Wklej kod z innego pliku bez uwzględniania niezbędne `using` instrukcji. Ten błąd jest teraz powiązany poprawki kodu, który dodaje brakujący `using` instrukcji.

    > [!NOTE] 
    > Tę sugestię musi być włączona w programie **Narzędzia > Opcje > Edytor tekstu > C# > Zaawansowane > przy użyciu dyrektywy**.

2. Naciśnij klawisz **Ctrl**+**.** Aby otworzyć **szybkie akcje i Refaktoryzacje** menu. 

    ![Generowanie deklaracji using](media/generate-using-codefix.png)

3. Wybierz **przy użyciu \<użytkownikowi\>;** można dodać brakujące odwołania.

    ![Generowanie wyników deklaracje Using](media/generate-using-result.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)

---
title: Refaktoryzuj pole do właściwości
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: db0bd17cd0bead3807f857b2198b8d4ea4c72ffb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569715"
---
# <a name="encapsulate-a-field-refactoring"></a>Hermetyzuj pole refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- Język C#

- Język Visual Basic

**Co:** umożliwia przekształcając pole właściwości i aktualizowanie wszystkich użycia tego pola, aby używać nowo utworzonej właściwości.

**Kiedy:** chcesz przenieść pole do właściwości i zaktualizuj wszystkie odwołania do tego pola.

**Dlaczego:** ma zostać zapewniony dostęp innych klas do pola, ale nie mają bezpośredniego dostępu do tych klas.  Dzięki zawijaniu pola we właściwości, można napisać kod, aby sprawdzić wartość jest przypisany, na przykład.

## <a name="how-to"></a>Instrukcje

1. Zaznacz lub umieść kursor tekst wewnątrz nazwy pola do hermetyzacji:

   - C#:

       ![Wyróżniony kod-C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/encapsulate-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl + R**, następnie **klawisze Ctrl + E**.  (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz opcję **hermetyzowania pola** wpis z menu podręcznego okna podglądu.
   - **Myszy**
      - Wybierz **Edytuj > Refaktoryzuj > Hermetyzuj pole**.
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz opcję **hermetyzowania pola** wpis z menu podręcznego okna podglądu.

   Wybór | Opis
   --------- | -----------
   **Hermetyzuj pola (i używaj właściwości)** | Hermetyzuje pola z właściwością i aktualizuje wszystkie użycia pola, aby używać wygenerowanej właściwości
   **Hermetyzuj pola (ale nadal używaj pola)** | Hermetyzuje pola z właściwością, ale pozostawia użycia wszystkie pola w charakterze

   Właściwość jest tworzony i odwołania do pola są aktualizowane, jeśli wybrana.

   > [!TIP]
   > Użyj **podgląd zmian** link w oknie podręcznym [aby zobaczyć, jaki będzie wynik](../../ide/preview-changes.md) przed zatwierdzeniem do niego.

   - C#:

      ![Hermetyzuj wynik właściwości-C#](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Hermetyzuj właściwość wynik - Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)

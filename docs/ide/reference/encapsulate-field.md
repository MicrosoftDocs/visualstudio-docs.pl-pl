---
title: Refaktoryzacja pola do właściwości
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0e47a62fcea8306c22564e50adde436b4f35e549
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654468"
---
# <a name="encapsulate-a-field-refactoring"></a>Hermetyzacja refaktoryzacji pola

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia włączenie pola do właściwości i zaktualizowanie wszystkich użycia tego pola w celu użycia nowo utworzonej właściwości.

**Kiedy:** Chcesz przenieść pole do właściwości i zaktualizować wszystkie odwołania do tego pola.

**Dlaczego:** Chcesz nadać innym klasom dostęp do pola, ale nie chcesz, aby te klasy miały bezpośredni dostęp.  Zawijając pole we właściwości, można napisać kod, aby zweryfikować przypisaną wartość, na przykład.

## <a name="how-to"></a>Instrukcje

1. Podświetl lub umieść kursor tekstu w nazwie pola do hermetyzacji:

   - C#:

       ![Wyróżniony kod —C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/encapsulate-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisze **Ctrl + R**, a następnie **Ctrl + E**.  (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** i wybrać opcję **Hermetyzuj wpis pola** w menu podręcznym okna podglądu.
   - **Wskaźnik**
      - Wybierz pozycję **edytuj > refaktoryzację > pole hermetyzowane**.
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** i wybierz opcję **Hermetyzuj wpis pola** w menu podręcznym okna podglądu.

   Wybór | Opis
   --------- | -----------
   **Hermetyzowanie pola (i używanie właściwości)** | Hermetyzuje pole z właściwością i aktualizuje wszystkie użycia pola, aby użyć wygenerowanej właściwości
   **Hermetyzuj pole (ale nadal używaj pola)** | Hermetyzuje pole z właściwością, ale pozostawia wszystkie niezmienione użycie pola

   Ta właściwość jest tworzona i odwołania do pola są aktualizowane, jeśli są zaznaczone.

   > [!TIP]
   > Użyj linku **Podgląd zmian** w oknie podręcznym, [Aby zobaczyć, co wynik będzie](../../ide/preview-changes.md) przed zatwierdzeniem.

   - C#:

      ![Hermetyzuj wynik właściwości-C#](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Hermetyzuj wynik właściwości — Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
---
title: Refaktoryzuje pole do właściwości
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569715"
---
# <a name="encapsulate-a-field-refactoring"></a>Hermetyzowanie refaktoryzacji pól

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia przekształcenie pola w właściwość i zaktualizowanie wszystkich użycia tego pola w celu użycia nowo utworzonej właściwości.

**Kiedy:** Chcesz przenieść pole do właściwości i zaktualizować wszystkie odwołania do tego pola.

**Dlaczego?** Chcesz dać innym klasom dostęp do pola, ale nie chcesz, aby te klasy miały bezpośredni dostęp.  Zawijając pole we właściwości, można napisać kod, aby sprawdzić wartość przypisaną, na przykład.

## <a name="how-to"></a>Porady

1. Wyróżnij lub umieść kursor tekstowy w nazwie pola, aby hermetyzować:

   - C#:

       ![Wyróżniony kod - C #](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/encapsulate-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl+R**, a następnie **klawisze Ctrl+E**.  (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzację** i wybrać pozycję **pola Hermetyzuj** z okna podglądu.
   - **Mysz**
      - Wybierz **pozycję Edytuj > refaktoryzację > zhermetyzowania pola**.
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **Szybkie akcje i Refaktoryzowania** i wybierz pozycję **pola Hermetyzuj** z okna podglądu.

   Wybór | Opis
   --------- | -----------
   **Hermetyzowanie pola (i używanie właściwości)** | Hermetyzuje pole właściwością i aktualizuje wszystkie użycia pola, aby użyć wygenerowanej właściwości
   **Hermetyzowanie pola (ale nadal używaj pola)** | Hermetyzuje pole właściwością, ale pozostawia wszystkie zastosowania pola nietknięte

   Właściwość jest tworzona, a odwołania do tego pola są aktualizowane, jeśli jest zaznaczona.

   > [!TIP]
   > Użyj łącza **Zmiany podglądu** w oknie podręcznym, [aby zobaczyć, jaki będzie wynik](../../ide/preview-changes.md) przed zatwierdzeniem go.

   - C#:

      ![Encapsulate Wynik właściwości - C #](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Hermetyzowanie wyniku właściwości — Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)

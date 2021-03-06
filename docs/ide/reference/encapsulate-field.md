---
title: Refaktoryzacja pola do właściwości
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje, aby przekonwertować pole na właściwość.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: dd2c6c1946b900cc422060891537544f318bd994
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882052"
---
# <a name="encapsulate-a-field-refactoring"></a>Hermetyzacja refaktoryzacji pola

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia włączenie pola do właściwości i zaktualizowanie wszystkich użycia tego pola w celu użycia nowo utworzonej właściwości.

**Kiedy:** Chcesz przenieść pole do właściwości i zaktualizować wszystkie odwołania do tego pola.

**Dlaczego:** Chcesz nadać innym klasom dostęp do pola, ale nie chcesz, aby te klasy miały bezpośredni dostęp.  Zawijając pole we właściwości, można napisać kod, aby zweryfikować przypisaną wartość, na przykład.

## <a name="how-to"></a>Porady

1. Podświetl lub umieść kursor tekstu w nazwie pola do hermetyzacji:

   - C#:

       ![Wyróżniony kod — C #](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/encapsulate-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisze **Ctrl + R**, a następnie **Ctrl + E**.  (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** i wybrać opcję **Hermetyzuj wpis pola** w menu podręcznym okna podglądu.
   - **Mysz**
      - Wybierz pozycję **edytuj > refaktoryzację > pole hermetyzowane**.
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** i wybierz opcję **Hermetyzuj wpis pola** w menu podręcznym okna podglądu.

   Zaznaczenie | Opis
   --------- | -----------
   **Hermetyzowanie pola (i używanie właściwości)** | Hermetyzuje pole z właściwością i aktualizuje wszystkie użycia pola, aby użyć wygenerowanej właściwości
   **Hermetyzuj pole (ale nadal używaj pola)** | Hermetyzuje pole z właściwością, ale pozostawia wszystkie niezmienione użycie pola

   Ta właściwość jest tworzona i odwołania do pola są aktualizowane, jeśli są zaznaczone.

   > [!TIP]
   > Użyj linku **Podgląd zmian** w oknie podręcznym, [Aby zobaczyć, co wynik będzie](../../ide/preview-changes.md) przed zatwierdzeniem.

   - C#:

      ![Hermetyzowanie wyniku właściwości-C #](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Hermetyzuj wynik właściwości — Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)

---
title: Wyodrębnianie metody
description: Przeksztą fragment kodu do własnej metody, wybierając kod i wpisując Ctrl+R, Ctrl+M.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 50f14cc2a7eafe5d65e0c6a6af54bafa2ebb5a1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569702"
---
# <a name="extract-a-method-refactoring"></a>Wyodrębnianie refaktoryzacji metody

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia przekształcenie fragmentu kodu w własną metodę.

**Kiedy:** Masz fragment istniejącego kodu w jakiejś metodzie, która musi być wywoływana z innej metody.

**Dlaczego?** Można skopiować/wkleić ten kod, ale to prowadzi do powielania. Lepszym rozwiązaniem jest refaktoryzator tego fragmentu do własnej metody, która może być wywoływana swobodnie za pomocą innej metody.

## <a name="how-to"></a>Porady

1. Wyróżnij kod, który ma zostać wyodrębniony:

   - C#:

       ![Wyróżniony kod- C #](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/extractmethod-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl+R**, a następnie **klawisze Ctrl+M**. (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania,** a następnie wybrać **opcję Wyodrębnij metodę** z okna podglądu.
   - **Mysz**
      - Wybierz **opcję Edytuj > refaktoryzowania > metody wyodrębniania**.
      - Kliknij prawym przyciskiem myszy kod i wybierz polecenie **Refaktoryzator > Wyodrębnij > metody wyodrębniania**.
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **Szybkie akcje i Refaktoryzowania** i wybierz polecenie **Wyodrębnij metodę** z okna podglądu.

   Metoda zostanie natychmiast utworzona. W tym miejscu można teraz zmienić nazwę metody po prostu wpisując nową nazwę.

   > [!TIP]
   > Można również zaktualizować komentarze i inne ciągi, aby użyć tej nowej nazwy, a także [zmiany podglądu](../../ide/preview-changes.md) przed zapisaniem, używając pól wyboru w polu **Zmień nazwę,** które pojawia się w prawym górnym rogu ide.

   - C#:

      ![Zmień nazwę metody - C #](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Zmień nazwę metody — Visual Basic](media/extractmethod-rename-vb.png)

3. Gdy ze zmiany będziesz zadowolony, wybierz przycisk **Zastosuj** lub naciśnij klawisz **Enter,** a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)

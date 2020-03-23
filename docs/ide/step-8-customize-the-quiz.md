---
title: 'Krok 8: Dostosuj quiz'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e568a9fa844802ddab934264cbc316d3514fe577
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579369"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Dostosuj quiz

W ostatniej części samouczka zapoznajesz się z kilkoma sposobami dostosowania quizu i rozwinięcie tego, czego już się nauczyłeś. Na przykład zastanów się, jak program tworzy losowe problemy z podziałem, dla których odpowiedź nigdy nie jest ułamkiem. Aby dowiedzieć się `timeLabel` więcej, obróć formant w inny kolor i daj uczestnikowi quizu wskazówkę.

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-customize-the-quiz"></a>Aby dostosować quiz

- Gdy tylko pięć sekund pozostaje w quizie, włącz **timeLabel** kontroli czerwony, ustawiając jego **BackColor** właściwości.

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Zresetuj kolor po zakończeniu quizu.

- Daj uczestnikowi quizu wskazówkę, odtwarzając dźwięk, gdy <xref:System.Windows.Forms.NumericUpDown> poprawna odpowiedź zostanie wprowadzona do formantu. (Należy napisać program obsługi zdarzeń dla <xref:System.Windows.Forms.NumericUpDown.ValueChanged> każdego zdarzenia formantu, który jest uruchamiany za każdym razem, gdy osoba biorąca udział w quizie zmienia wartość formantu).

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego samouczka, zobacz **[Samouczek 3: Tworzenie pasującej gry](../ide/tutorial-3-create-a-matching-game.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 7: Dodawanie problemów z mnożeniem i dzieleniem](../ide/step-7-add-multiplication-and-division-problems.md).

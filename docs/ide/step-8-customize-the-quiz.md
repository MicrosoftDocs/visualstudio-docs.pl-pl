---
title: Krok 8. Dostosowywanie testu
description: Dowiedz się, jak przekształcić kontrolkę timeLabel w inny kolor i nadać jej wskazówkę.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ba836ea8eff45d02b487541e5120e670e6cc09e
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295406"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8. Dostosowywanie testu

W ostatniej części samouczka zapoznajesz się z innymi sposobami dostosowywania quizu i rozwinięcia tego, co już znasz. Na przykład należy zastanowić się, jak program tworzy losowe problemy dotyczące dzielenia, dla których odpowiedź nigdy nie jest częścią. Aby dowiedzieć się więcej, Zmień `timeLabel` kolor kontrolki na inny i nadaj wskazówkę quizu.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-customize-the-quiz"></a>Aby dostosować Quiz

- Gdy tylko pięć sekund pozostanie w quizie, Zmień wartość kontrolki **timeLabel** na czerwony, ustawiając jej właściwość **BackColor** .

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Zresetuj kolor, gdy quiz jest ustawiony na wartość.

- Nadaj quizowi wskazówkę, odtwarzając dźwięk po wprowadzeniu odpowiedniej odpowiedzi do <xref:System.Windows.Forms.NumericUpDown> kontrolki. (Należy napisać procedurę obsługi zdarzeń dla każdego zdarzenia kontrolki <xref:System.Windows.Forms.NumericUpDown.ValueChanged> , które jest wyzwalane za każdym razem, gdy osoba przyjmująca Quiz zmieni wartość kontrolki).

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego samouczka, zobacz **[samouczek 3: Tworzenie gry w dopasowywanie](../ide/tutorial-3-create-a-matching-game.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).

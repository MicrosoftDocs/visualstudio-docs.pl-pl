---
title: Krok 8. Dostosowywanie quizu
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32c35c0eccc4c6a4972774219dc07b606b72243c
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776025"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8. Dostosowywanie quizu

W ostatniej części samouczka zapoznajesz się z innymi sposobami dostosowywania quizu i rozwinięcia tego, co już znasz. Na przykład należy zastanowić się, jak program tworzy losowe problemy dotyczące dzielenia, dla których odpowiedź nigdy nie jest częścią. Aby dowiedzieć się więcej, Zmień kolor kontrolki `timeLabel` na inny, a następnie Przekaż wskazówkę do wskazówki.

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

- Nadaj quizowi wskazówkę, odtwarzając dźwięk po wprowadzeniu prawidłowej odpowiedzi do kontrolki <xref:System.Windows.Forms.NumericUpDown>. (Należy napisać procedurę obsługi zdarzeń dla każdego zdarzenia <xref:System.Windows.Forms.NumericUpDown.ValueChanged> kontrolki, które jest wyzwalane za każdym razem, gdy osoba zażąda zmiany wartości kontrolki.)

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego samouczka, zobacz **[samouczek 3: Tworzenie gry w dopasowywanie](../ide/tutorial-3-create-a-matching-game.md)** .

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).

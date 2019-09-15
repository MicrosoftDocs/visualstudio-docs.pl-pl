---
title: Krok 8. Dostosowywanie testu
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68d46ad5c585dca9fd48f39a2e47ac95f5a11c8
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987848"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8. Dostosowywanie testu

W ostatniej części samouczka zapoznajesz się z innymi sposobami dostosowywania quizu i rozwinięcia tego, co już znasz. Na przykład należy zastanowić się, jak program tworzy losowe problemy dotyczące dzielenia, dla których odpowiedź nigdy nie jest częścią. Aby dowiedzieć się więcej, `timeLabel` Zmień kolor kontrolki na inny i nadaj wskazówkę quizu.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. 
> - Aby zapoznać się z omówieniem samouczka, [zobacz Samouczek 2: Utwórz Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)matematyczny z limitem czasu. 
> - Aby pobrać kompletną wersję kodu, zobacz [kompletny przykładowy samouczek quizu Matematycznego](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-customize-the-quiz"></a>Aby dostosować Quiz

- Gdy tylko pięć sekund pozostanie w quizie, Zmień wartość kontrolki **timeLabel** na czerwony, ustawiając jej właściwość **BackColor** .

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  > [!IMPORTANT]
  > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  Zresetuj kolor, gdy quiz jest ustawiony na wartość.

- Nadaj quizowi wskazówkę, odtwarzając dźwięk po wprowadzeniu odpowiedniej odpowiedzi do <xref:System.Windows.Forms.NumericUpDown> kontrolki. (Należy napisać procedurę obsługi zdarzeń dla każdego <xref:System.Windows.Forms.NumericUpDown.ValueChanged> zdarzenia kontrolki, które jest wyzwalane za każdym razem, gdy osoba przyjmująca Quiz zmieni wartość kontrolki).

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego samouczka, zobacz  **[samouczek 3: Utwórz pasującą grę](../ide/tutorial-3-create-a-matching-game.md).**

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7: Dodawanie problemów](../ide/step-7-add-multiplication-and-division-problems.md)mnożenia i dzielenia.

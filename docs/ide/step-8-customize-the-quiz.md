---
title: Krok 8. Dostosowywanie testu
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1868cd30cc41187ac995e71ee86d81dd0fb83d5a
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416466"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8. Dostosowywanie testu
W ostatniej części samouczka zapoznajesz się z innymi sposobami dostosowywania quizu i rozwinięcia tego, co już znasz. Na przykład należy zastanowić się, jak program tworzy losowe problemy dotyczące dzielenia, dla których odpowiedź nigdy nie jest częścią. Aby dowiedzieć się więcej, `timeLabel` Zmień kolor kontrolki na inny i nadaj wskazówkę quizu.

## <a name="to-customize-the-quiz"></a>Aby dostosować Quiz

- Gdy tylko pięć sekund pozostanie w quizie, Zmień wartość kontrolki **timeLabel** na czerwony, ustawiając jej właściwość **BackColor**

```csharp
timeLabel.BackColor = Color.Red;
```

```vb
timeLabel.BackColor = Color.Red
```

Zresetuj kolor, gdy quiz jest ustawiony na wartość.

- Nadaj quizowi wskazówkę, odtwarzając dźwięk po wprowadzeniu odpowiedniej odpowiedzi do <xref:System.Windows.Forms.NumericUpDown> kontrolki. (Należy napisać procedurę obsługi zdarzeń dla każdego <xref:System.Windows.Forms.NumericUpDown.ValueChanged> zdarzenia kontrolki, które jest wyzwalane za każdym razem, gdy osoba przyjmująca Quiz zmieni wartość kontrolki).

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby pobrać kompletną wersję quizu, zobacz [kompletny przykładowy samouczek quizu Matematycznego](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

- Aby przejść do następnego samouczka, zobacz [samouczek 3: Utwórz pasującą grę](../ide/tutorial-3-create-a-matching-game.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7: Dodawanie problemów](../ide/step-7-add-multiplication-and-division-problems.md)mnożenia i dzielenia.

---
title: Krok 8. Dostosowywanie kwizu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e42726ca7a91fbde87295bbc7c88f1a2ee054949
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55852958"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8. Dostosowywanie kwizu
W ostatniej części tego samouczka dowiesz się o kilka sposobów na dostosowywanie kwizu i rozszerzają co już znasz. Na przykład zastanów się, jak program stwarza problemy dzielenia losowych, w których odpowiedź jest nigdy nie ułamek. Aby dowiedzieć się więcej, należy wyłączyć `timeLabel` kontrolować różne kolory i przypisz quizu wskazówką.

## <a name="to-customize-the-quiz"></a>Dostosowywanie kwizu

-   Kiedy tylko pięć sekund pozostają w quizie, Włącz **timeLabel** kontrolować red przez ustawienie jego **BackColor** właściwości (`timeLabel.BackColor = Color.Red;`). Resetuj kolor po umieszczeniu quizu.

-   Daj quizu wskazówkę, odtwarzanie dźwięku w momencie poprawną odpowiedź do <xref:System.Windows.Forms.NumericUpDown> kontroli. (Należy napisać program obsługi zdarzeń dla każdego formantu <xref:System.Windows.Forms.NumericUpDown.ValueChanged> zdarzenie, które są generowane w każdym przypadku, gdy osoba wypełniająca quiz zmienia wartość kontrolki.)

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby pobrać pełną wersję quizu, zobacz [przykładowy samouczek quiz matematyczny pełną](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

-   Aby przejść do następnego samouczka, zobacz [Tutorial 3: Utwórz pasujący obiekt typu gier](../ide/tutorial-3-create-a-matching-game.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 7: Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).

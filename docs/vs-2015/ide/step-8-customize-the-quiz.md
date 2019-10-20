---
title: Krok 8. Dostosowywanie quizu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6084daea11d981477bbee6f210e1faf718b58d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646923"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Dostosowywanie kwizu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W ostatniej części samouczka zapoznajesz się z innymi sposobami dostosowywania quizu i rozwinięcia tego, co już znasz. Na przykład należy zastanowić się, jak program tworzy losowe problemy dotyczące dzielenia, dla których odpowiedź nigdy nie jest częścią. Aby dowiedzieć się więcej, Zmień kolor kontrolki `timeLabel` na inny, a następnie Przekaż wskazówkę do wskazówki.

### <a name="to-customize-the-quiz"></a>Aby dostosować Quiz

- Gdy tylko pięć sekund pozostanie w quizie, Zmień wartość kontrolki **timeLabel** na czerwony, ustawiając jej właściwość **BackColor** (`timeLabel.BackColor = Color.Red;`). Zresetuj kolor, gdy quiz jest ustawiony na wartość.

- Nadaj quizowi wskazówkę, odtwarzając dźwięk, gdy prawidłowa odpowiedź zostanie wprowadzona do formantu NumericUpDown. (Należy napisać procedurę obsługi zdarzeń dla każdego zdarzenia `ValueChanged()` kontrolki, które jest wyzwalane za każdym razem, gdy osoba zażąda zmiany wartości kontrolki.)

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby pobrać kompletną wersję quizu, zobacz [kompletny przykładowy samouczek quizu Matematycznego](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

- Aby przejść do następnego samouczka, zobacz [samouczek 3: Tworzenie gry w dopasowywanie](../ide/tutorial-3-create-a-matching-game.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).

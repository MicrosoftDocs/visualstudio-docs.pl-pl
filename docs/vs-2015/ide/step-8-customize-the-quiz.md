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
ms.openlocfilehash: ded65e85a2ae11e96c21fdd852ea12daa4bbcdf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299984"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Dostosowywanie kwizu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W ostatniej części samouczka zapoznajesz się z innymi sposobami dostosowywania quizu i rozwinięcia tego, co już znasz. Na przykład należy zastanowić się, jak program tworzy losowe problemy dotyczące dzielenia, dla których odpowiedź nigdy nie jest częścią. Aby dowiedzieć się więcej, Zmień `timeLabel` kolor kontrolki na inny i nadaj wskazówkę quizu.

### <a name="to-customize-the-quiz"></a>Aby dostosować Quiz

- Gdy tylko pięć sekund pozostanie w quizie, Zmień wartość kontrolki **timeLabel** na czerwony, ustawiając jej właściwość **BackColor** ( `timeLabel.BackColor = Color.Red;` ). Zresetuj kolor, gdy quiz jest ustawiony na wartość.

- Nadaj quizowi wskazówkę, odtwarzając dźwięk, gdy prawidłowa odpowiedź zostanie wprowadzona do formantu NumericUpDown. (Należy napisać procedurę obsługi zdarzeń dla każdego zdarzenia kontrolki `ValueChanged()` , które jest wyzwalane za każdym razem, gdy osoba przyjmująca Quiz zmieni wartość kontrolki).

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego samouczka, zobacz [samouczek 3: Tworzenie gry w dopasowywanie](../ide/tutorial-3-create-a-matching-game.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).

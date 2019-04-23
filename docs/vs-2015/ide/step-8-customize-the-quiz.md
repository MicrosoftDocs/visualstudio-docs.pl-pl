---
title: Krok 8. Dostosowywanie kwizu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 75bde59c6e4b61c2775f188383fc9058a6c31242
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109754"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8. Dostosowywanie testu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W ostatniej części tego samouczka dowiesz się o kilka sposobów na dostosowywanie kwizu i rozszerzają co już znasz. Na przykład zastanów się, jak program stwarza problemy dzielenia losowych, w których odpowiedź jest nigdy nie ułamek. Aby dowiedzieć się więcej, należy wyłączyć `timeLabel` kontrolować różne kolory i przypisz quizu wskazówką.  
  
### <a name="to-customize-the-quiz"></a>Dostosowywanie kwizu  
  
- Kiedy tylko pięć sekund pozostają w quizie, Włącz **timeLabel** kontrolować red przez ustawienie jego **BackColor** właściwości (`timeLabel.BackColor = Color.Red;`). Resetuj kolor po umieszczeniu quizu.  
  
- Nadaj quizu wskazówką przez odtwarzanie dźwięku w momencie poprawną odpowiedź do formantu NumericUpDown. (Należy napisać program obsługi zdarzeń dla każdego formantu `ValueChanged()` zdarzenie, które są generowane w każdym przypadku, gdy osoba wypełniająca quiz zmienia wartość kontrolki.)  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby pobrać pełną wersję quizu, zobacz [przykładowy samouczek pełnej wersji quizu matematycznego](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
- Aby przejść do następnego samouczka, zobacz [Tutorial 3: Stwórz grę pasujący obiekt typu](../ide/tutorial-3-create-a-matching-game.md).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 7: Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).

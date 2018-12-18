---
title: 'Krok 8: Dostosowywanie kwizu'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d020e2d83e7e631fefcb1503eb8f1938894986
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672122"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Dostosowywanie kwizu
W ostatniej części tego samouczka dowiesz się o kilka sposobów na dostosowywanie kwizu i rozszerzają co już znasz. Na przykład zastanów się, jak program stwarza problemy dzielenia losowych, w których odpowiedź jest nigdy nie ułamek. Aby dowiedzieć się więcej, należy wyłączyć `timeLabel` kontrolować różne kolory i przypisz quizu wskazówką.  

## <a name="to-customize-the-quiz"></a>Dostosowywanie kwizu  

-   Kiedy tylko pięć sekund pozostają w quizie, Włącz **timeLabel** kontrolować red przez ustawienie jego **BackColor** właściwości (`timeLabel.BackColor = Color.Red;`). Resetuj kolor po umieszczeniu quizu.  
  
-   Daj quizu wskazówkę, odtwarzanie dźwięku w momencie poprawną odpowiedź do <xref:System.Windows.Forms.NumericUpDown> kontroli. (Należy napisać program obsługi zdarzeń dla każdego formantu <xref:System.Windows.Forms.NumericUpDown.ValueChanged> zdarzenie, które są generowane w każdym przypadku, gdy osoba wypełniająca quiz zmienia wartość kontrolki.)  
  
## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby pobrać pełną wersję quizu, zobacz [przykładowy samouczek quiz matematyczny pełną](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Aby przejść do następnego samouczka, zobacz [Tutorial 3: tworzenie pasujący obiekt typu gier](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7: Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).

---
title: Krok 9. Spróbuj innych funkcji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 495d98f4061c258c78b2b74929428aec4eb3ec0c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65678941"
---
# <a name="step-9-try-other-features"></a>Krok 9. Wypróbowywanie innych funkcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby dowiedzieć się więcej, spróbuj zmienić ikony i kolory, dodać czasomierz gry i dźwięki. Aby gra była bardziej wymagająca, spróbuj zwiększyć planszę i dostosować czasomierz.  
  
 Aby pobrać pełną wersję przykładu, zobacz [przykładowy samouczek gry w dopasowywanie pełną](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
### <a name="to-try-other-features"></a>Aby wypróbować inne funkcje  
  
- Zamień ikony i kolory na własne.  
  
    > [!TIP]
    > Spójrz etykiety [Forecolor](https://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) właściwości.  
  
- Dodaj czasomierz gry, który śledzi, jak długo graczowi zajmuje zakończenie gry.  
  
    > [!TIP]
    > Aby to zrobić, możesz dodać etykietę wyświetlającą czas, który upłynął, na formularzu powyżej TableLayoutPanel, i dodaj inny czasomierz do formularza w celu śledzenia czasu. Użyj kodu uruchamiającego czasomierz, gdy gracz rozpoczyna grę, i zatrzymującego czasomierz po dopasowaniu ostatnich dwóch ikon.  
  
- Dodaj dźwięk, gdy gracz znajdzie dopasowanie, inny dźwięk, gdy gracz odkrywa dwie ikony, które nie pasują, a trzeci dźwięk, gdy program ukrywa ikony ponownie.  
  
    > [!TIP]
    > Aby odtwarzać dźwięki, możesz użyć przestrzeni nazw System.media. Zobacz [Play Sounds in Windows Forms App (C# .NET)](http://youtu.be/qOh4ooHg1UU) lub [jak do Play Audio In Visual Basic](http://youtu.be/-4oPDeQrtMs) Aby uzyskać więcej informacji.  
  
- Utrudnij grę, zwiększając planszę.  
  
    > [!TIP]
    > Potrzebujesz czegoś więcej niż tylko dodać wiersze i kolumny do TableLayoutPanel — musisz również wziąć pod uwagę liczbę ikon, które tworzysz.  
  
- Utrudnij grę, ukrywając pierwszą ikonę, jeśli gracz reaguje zbyt wolno i nie wybiera drugiej ikony w określonym czasie.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [Forum języka Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) i [Forum Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
- Są tam dostępne wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w języku Visual Basic, zobacz [Visual Basic Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w języku Visual C#, zobacz [ C# podstawy: Development for Absolute Beginners](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

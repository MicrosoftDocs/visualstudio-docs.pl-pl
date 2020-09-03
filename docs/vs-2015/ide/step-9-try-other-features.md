---
title: Krok 9. Wypróbuj inne funkcje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 379fc9c28b8d36f7bd606719a443b16108f0095d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299983"
---
# <a name="step-9-try-other-features"></a>Krok 9. Próbowanie innych funkcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby dowiedzieć się więcej, spróbuj zmienić ikony i kolory, dodać czasomierz gry i dźwięki. Aby gra była bardziej wymagająca, spróbuj zwiększyć planszę i dostosować czasomierz.

### <a name="to-try-other-features"></a>Aby wypróbować inne funkcje

- Zamień ikony i kolory na własne.

    > [!TIP]
    > Spróbuj wyszukać Właściwość [ForeColor](https://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) etykiety.

- Dodaj czasomierz gry, który śledzi, jak długo graczowi zajmuje zakończenie gry.

    > [!TIP]
    > Aby to zrobić, możesz dodać etykietę wyświetlającą czas, który upłynął, na formularzu powyżej TableLayoutPanel, i dodaj inny czasomierz do formularza w celu śledzenia czasu. Użyj kodu uruchamiającego czasomierz, gdy gracz rozpoczyna grę, i zatrzymującego czasomierz po dopasowaniu ostatnich dwóch ikon.

- Dodaj dźwięk, gdy gracz znajdzie dopasowanie, inny dźwięk, gdy gracz odkrywa dwie ikony, które nie pasują, a trzeci dźwięk, gdy program ukrywa ikony ponownie.

    > [!TIP]
    > Aby odtwarzać dźwięki, możesz użyć przestrzeni nazw System.media. Zobacz [Odtwórz dźwięki w aplikacji Windows Forms (C# .NET)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) lub [odtwórz dźwięk w Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) , aby uzyskać więcej informacji.

- Utrudnij grę, zwiększając planszę.

    > [!TIP]
    > Potrzebujesz czegoś więcej niż tylko dodać wiersze i kolumny do TableLayoutPanel — musisz również wziąć pod uwagę liczbę ikon, które tworzysz.

- Utrudnij grę, ukrywając pierwszą ikonę, jeśli gracz reaguje zbyt wolno i nie wybiera drugiej ikony w określonym czasie.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [forum Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) i [Visual C# forum](https://social.msdn.microsoft.com/Forums/en-US/home).

- Są tam dostępne wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w Visual Basic, zobacz [Visual Basic podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w Visual C#, zobacz [podstawy języka C#: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy odtwarzacz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

---
title: 'Krok 9: Wypróbuj inne funkcje'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32ac2f1977bb0b8b391651ed7ed459b9dc560330
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579731"
---
# <a name="step-9-try-other-features"></a>Krok 9: Wypróbuj inne funkcje
Aby dowiedzieć się więcej, spróbuj zmienić ikony i kolory, dodać czasomierz gry i dźwięki. Aby gra była bardziej wymagająca, spróbuj zwiększyć planszę i dostosować czasomierz.

Aby pobrać ukończoną wersję próbki, zobacz [Próbka samouczka pełnej dopasowania gry](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Aby wypróbować inne funkcje

- Zamień ikony i kolory na własne.

    > [!TIP]
    > Spróbuj spojrzeć na etykietę [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) właściwości.

- Dodaj czasomierz gry, który śledzi, jak długo graczowi zajmuje zakończenie gry.

    > [!TIP]
    > Aby to zrobić, można dodać etykietę, aby wyświetlić czas, <xref:System.Windows.Forms.TableLayoutPanel>jaki upłynął w formularzu powyżej , i dodać kolejny czasomierz do formularza, aby śledzić czas. Użyj kodu uruchamiającego czasomierz, gdy gracz rozpoczyna grę, i zatrzymującego czasomierz po dopasowaniu ostatnich dwóch ikon.

- Dodaj dźwięk, gdy gracz znajdzie dopasowanie, inny dźwięk, gdy gracz odkrywa dwie ikony, które nie pasują, a trzeci dźwięk, gdy program ukrywa ikony ponownie.

    > [!TIP]
    > Aby odtwarzać dźwięki, <xref:System.Media> można użyć obszaru nazw. Aby uzyskać więcej informacji, zobacz [Odtwarzanie dźwięków w aplikacji Windows Forms (C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) lub [Jak odtwarzać dźwięk w języku Visual Basic.](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be)

- Utrudnij grę, zwiększając planszę.

    > [!TIP]
    > Musisz zrobić więcej niż tylko dodać wiersze i kolumny do TableLayoutPanel — musisz również wziąć pod uwagę liczbę utworzonych ikon.

- Utrudnij grę, ukrywając pierwszą ikonę, jeśli gracz reaguje zbyt wolno i nie wybiera drugiej ikony w określonym czasie.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Są tam dostępne wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej o programowaniu w języku Visual Basic, zobacz [Visual Basic podstawy: Rozwój dla początkujących .](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) Aby dowiedzieć się więcej o programowaniu w języku C#, zobacz [C# podstawy: Rozwój dla początkujących absolutnych](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

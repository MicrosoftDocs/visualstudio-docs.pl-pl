---
title: Krok 9. Spróbuj innych funkcji
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ee28eba43bd323679b4175d8144b1836ac606a8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093374"
---
# <a name="step-9-try-other-features"></a>Krok 9. Spróbuj innych funkcji
Aby dowiedzieć się więcej, spróbuj zmienić ikony i kolory, dodać czasomierz gry i dźwięki. Aby gra była bardziej wymagająca, spróbuj zwiększyć planszę i dostosować czasomierz.

 Aby pobrać pełną wersję przykładu, zobacz [pełną pasującego przykładowy samouczek gry](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Aby wypróbować inne funkcje

- Zamień ikony i kolory na własne.

    > [!TIP]
    >  Spójrz etykiety [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) właściwości.

- Dodaj czasomierz gry, który śledzi, jak długo graczowi zajmuje zakończenie gry.

    > [!TIP]
    >  Aby to zrobić, należy dodać etykietę wyświetlającą czas, który upłynął w powyższym formularzu <xref:System.Windows.Forms.TableLayoutPanel>, i Dodaj inny czasomierz do formularza w celu śledzenia czasu. Użyj kodu uruchamiającego czasomierz, gdy gracz rozpoczyna grę, i zatrzymującego czasomierz po dopasowaniu ostatnich dwóch ikon.

- Dodaj dźwięk, gdy gracz znajdzie dopasowanie, inny dźwięk, gdy gracz odkrywa dwie ikony, które nie pasują, a trzeci dźwięk, gdy program ukrywa ikony ponownie.

    > [!TIP]
    >  Aby odtwarzać dźwięki, możesz użyć <xref:System.Media> przestrzeni nazw. Zobacz [odtwarzać dźwięki w aplikacji Windows Forms (C#)](http://youtu.be/qOh4ooHg1UU) lub [odtwarzanie dźwięku w języku Visual Basic](http://youtu.be/-4oPDeQrtMs) Aby uzyskać więcej informacji.

- Utrudnij grę, zwiększając planszę.

    > [!TIP]
    >  Należy do więcej niż tylko dodać wiersze i kolumny do TableLayoutPanel — należy także wziąć pod uwagę liczbę ikon, które tworzysz.

- Utrudnij grę, ukrywając pierwszą ikonę, jeśli gracz reaguje zbyt wolno i nie wybiera drugiej ikony w określonym czasie.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [forum języka Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) i [forum Visual C#](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral).

- Są tam dostępne wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w języku Visual Basic, zobacz [podstawy Visual Basic: Tworzenie dla całkowicie początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w języku Visual C#, zobacz [ C# podstawy: Tworzenie dla całkowicie początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

---
title: Krok 9. Wypróbowywanie innych funkcji
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aff87247afb79d62867da9e55f7a059192789d79
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118843"
---
# <a name="step-9-try-other-features"></a>Krok 9. Wypróbowywanie innych funkcji
Aby dowiedzieć się więcej, spróbuj zmienić ikony i kolory, dodać czasomierz gry i dźwięki. Aby gra była bardziej wymagająca, spróbuj zwiększyć planszę i dostosować czasomierz.

Aby pobrać kompletną wersję przykładu, zobacz [kompletny przykładowy samouczek gry](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Aby wypróbować inne funkcje

- Zamień ikony i kolory na własne.

    > [!TIP]
    > Spróbuj wyszukać Właściwość [ForeColor](<xref:System.Windows.Forms.Control.ForeColor%2A>) etykiety.

- Dodaj czasomierz gry, który śledzi, jak długo graczowi zajmuje zakończenie gry.

    > [!TIP]
    > W tym celu można dodać etykietę, aby wyświetlić czas, który upłynął w formularzu powyżej <xref:System.Windows.Forms.TableLayoutPanel>, i dodać kolejny czasomierz do formularza w celu śledzenia czasu. Użyj kodu uruchamiającego czasomierz, gdy gracz rozpoczyna grę, i zatrzymującego czasomierz po dopasowaniu ostatnich dwóch ikon.

- Dodaj dźwięk, gdy gracz znajdzie dopasowanie, inny dźwięk, gdy gracz odkrywa dwie ikony, które nie pasują, a trzeci dźwięk, gdy program ukrywa ikony ponownie.

    > [!TIP]
    > Aby odtwarzać dźwięki, można użyć <xref:System.Media> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [OdtwórzC#dźwięki w aplikacji Windows Forms ()](http://youtu.be/qOh4ooHg1UU) lub [Odtwórz dźwięk w programie Visual Basic](http://youtu.be/-4oPDeQrtMs) .

- Utrudnij grę, zwiększając planszę.

    > [!TIP]
    > Musisz wykonać więcej czynności niż tylko dodać wiersze i kolumny do TableLayoutPanel — należy również rozważyć liczbę utworzonych ikon.

- Utrudnij grę, ukrywając pierwszą ikonę, jeśli gracz reaguje zbyt wolno i nie wybiera drugiej ikony w określonym czasie.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [forum Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) i [forum C# wizualne](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral).

- Są tam dostępne wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w [Visual Basic, zobacz Visual Basic podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat C#programowania w [ wizualizacji, zobacz C# podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy odtwarzacz został](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)wygrany.

---
title: Krok 9. Wypróbowywanie innych funkcji
description: Dowiedz się, jak zmienić ikony i kolory, dodać czasomierz gier, dodać dźwięki i zwiększyć swoją tablicę.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 66d570787ac4948a635d71686711efc1e8cf86ba
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295393"
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
    > W tym celu można dodać etykietę, aby wyświetlić czas, który upłynął w formularzu powyżej <xref:System.Windows.Forms.TableLayoutPanel> , i dodać kolejny czasomierz do formularza w celu śledzenia czasu. Użyj kodu uruchamiającego czasomierz, gdy gracz rozpoczyna grę, i zatrzymującego czasomierz po dopasowaniu ostatnich dwóch ikon.

- Dodaj dźwięk, gdy gracz znajdzie dopasowanie, inny dźwięk, gdy gracz odkrywa dwie ikony, które nie pasują, a trzeci dźwięk, gdy program ukrywa ikony ponownie.

    > [!TIP]
    > Aby odtwarzać dźwięki, można użyć <xref:System.Media> przestrzeni nazw. Zobacz [Odtwórz dźwięki w aplikacji Windows Forms (C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) lub [jak odtworzyć dźwięk w Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) , aby uzyskać więcej informacji.

- Utrudnij grę, zwiększając planszę.

    > [!TIP]
    > Musisz wykonać więcej czynności niż tylko dodać wiersze i kolumny do TableLayoutPanel — należy również rozważyć liczbę utworzonych ikon.

- Utrudnij grę, ukrywając pierwszą ikonę, jeśli gracz reaguje zbyt wolno i nie wybiera drugiej ikony w określonym czasie.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Są tam dostępne wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w Visual Basic, zobacz [Visual Basic podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w języku C#, zobacz [podstawy języka c#: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy odtwarzacz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

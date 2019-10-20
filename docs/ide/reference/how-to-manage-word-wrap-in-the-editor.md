---
title: Zawijanie wierszy
ms.date: 11/07/2018
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30bfe549100a06df6b9a8163cad1e3d519c3a91b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663118"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Instrukcje: Zarządzanie zawijaniem wierszy w edytorze

Możesz ustawić i wyczyścić opcję **zawijania wyrazów** . Gdy ta opcja jest ustawiona, część długiej linii, która wykracza poza bieżącą szerokość okna edytora kodu, zostanie wyświetlona w następnym wierszu. Gdy ta opcja jest wyczyszczona, na przykład w celu ułatwienia używania numeracji wierszy, można przewijać w prawo, aby zobaczyć zakończenia długich wierszy.

> [!NOTE]
> Ten temat dotyczy tylko programu Visual Studio w systemie Windows. Visual Studio dla komputerów Mac obecnie nie obsługuje zawijania tekstu.

## <a name="to-set-word-wrap-preferences"></a>Aby ustawić preferencje zawijania wierszy

1. W menu **Narzędzia** wybierz pozycję **Opcje**.

2. W folderze **Edytor tekstu** wybierz opcje **Ogólne** w podfolderze **wszystkie języki** , aby ustawić tę opcję globalnie.

     oraz

     Wybierz **Ogólne** opcje w podfolderze języka, w którym planujesz programowanie.

3. W obszarze **Ustawienia**wybierz lub wyczyść opcję **zawijania wyrazów** .

     Gdy zaznaczona jest opcja **zawijania wyrazów** , opcja **Pokaż wizualne glify dla zawijania wyrazów** jest włączona.

4. Wybierz opcję **Pokaż glify wizualne dla zawijania wyrazów** , jeśli wolisz wyświetlić wskaźnik strzałki powrotu, w której długi wiersz jest zawijany do drugiego wiersza. Usuń zaznaczenie tej opcji, jeśli wolisz nie wyświetlać strzałek wskaźnika.

    > [!NOTE]
    > Te strzałki przypomnień nie są dodawane do kodu; są one przeznaczone tylko do wyświetlania.

## <a name="known-issues"></a>Znane problemy

Jeśli znasz opcję zawijania wyrazów w Notatniku + +, tekście subwapna lub Visual Studio Code, weź pod uwagę następujące kwestie, w których program Visual Studio działa inaczej w stosunku do innych redaktorów:

* [Potrójne kliknięcie nie zaznacza cały wiersz](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Polecenie Wytnij nie usuwa całego wiersza](https://developercommunity.visualstudio.com/content/problem/138259/cut-command-should-delete-logical-line.html)
* [Naciśnięcie klawisza End dwa razy nie powoduje przeniesienia kursora do końca wiersza](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../../ide/writing-code-in-the-code-and-text-editor.md)

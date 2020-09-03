---
title: Zawijanie wierszy
ms.date: 11/07/2018
ms.topic: how-to
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4bf76643ce1ea6e2f449c54fbc31d441418becf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770337"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Instrukcje: Zarządzanie zawijaniem wierszy w edytorze

Możesz ustawić i wyczyścić opcję **zawijania wyrazów** . Gdy ta opcja jest ustawiona, część długiej linii, która wykracza poza bieżącą szerokość okna edytora kodu, zostanie wyświetlona w następnym wierszu. Gdy ta opcja jest wyczyszczona, na przykład w celu ułatwienia używania numeracji wierszy, można przewijać w prawo, aby zobaczyć zakończenia długich wierszy.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Edytor źródła: zawijanie wierszy](/visualstudio/mac/source-editor#word-wrap).

## <a name="to-set-word-wrap-preferences"></a>Aby ustawić preferencje zawijania wierszy

1. W menu **Tools** (Narzędzia) wybierz pozycję **Options** (Opcje).

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
* [Naciśnięcie klawisza End dwa razy nie powoduje przeniesienia kursora do końca wiersza](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../../ide/writing-code-in-the-code-and-text-editor.md)

---
title: Zawijanie wyrazów
ms.date: 11/07/2018
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02ef55b44d57cecadb690637c17c0a35e9cb0659
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531613"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Instrukcje: Zarządzanie zawijaniem wierszy w edytorze

Można ustawić lub wyczyścić **zawijanie** opcji. Gdy ta opcja jest ustawiona, część długi wiersz, który wykracza poza bieżącym szerokość okna edytora kodu jest wyświetlany w następnym wierszu. Po wyczyszczeniu tej opcji, na przykład w celu ułatwienia korzystania numerowanie wierszy można przewijać po prawej stronie, aby zobaczyć zakończenia długie wiersze.

> [!NOTE]
> Ten temat dotyczy tylko programu Visual Studio w Windows. Visual Studio dla komputerów Mac nie obsługuje obecnie zawijanie wyrazów.

## <a name="to-set-word-wrap-preferences"></a>Można ustawić preferencje zawijania programu word

1. Na **narzędzia** menu, wybierz opcję **opcje**.

2. W **edytora tekstów** folderu, wybierz **ogólne** opcji na liście **wszystkie języki** podfolder, aby ustawić tę opcję, globalnie.

     — lub —

     Wybierz **ogólne** opcje w podfolderze dla języka, możesz programowania.

3. W obszarze **ustawienia**, zaznacz lub wyczyść **zawijanie** opcji.

     Gdy **zawijanie** opcja jest zaznaczona, **Pokaż zualne przy zawijaniu wierszy** opcja jest włączona.

4. Wybierz **wyświetlane zualne zawijanie** opcję, jeśli chcesz wyświetlić wskaźnik zwracany strzałkę, gdzie długi wiersz zawijana drugi wiersz. Usuń zaznaczenie tej opcji, jeśli nie chcesz wyświetlić strzałki wskaźnika.

    > [!NOTE]
    > Tych strzałek monitu nie są dodawane do kodu; są one tylko w celach wyświetlania.

## <a name="known-issues"></a>Znane problemy

Jeśli jesteś zaznajomiony z zawijaniem wierszy w Notatniku ++, Sublime Text lub Visual Studio Code, należy pamiętać o następujących problemów gdzie program Visual Studio zachowuje się inaczej do innych edytorów:

* [Potrójna kliknij nie wybierze cały wiersz](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Polecenia Wytnij nie powoduje usunięcia cały wiersz](https://developercommunity.visualstudio.com/content/problem/138259/cut-command-should-delete-logical-line.html)
* [Naciskając klawisz End dwukrotnie nie przenosi kursor do końca wiersza](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Zobacz także

- [Opcje edytora tekstowego, okno dialogowe](../../ide/reference/text-editor-options-dialog-box.md)
- [Funkcje edytora kodu](../../ide/writing-code-in-the-code-and-text-editor.md)

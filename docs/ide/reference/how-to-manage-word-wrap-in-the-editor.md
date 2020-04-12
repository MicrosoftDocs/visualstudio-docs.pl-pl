---
title: Zawijanie wierszy
ms.date: 11/07/2018
ms.topic: conceptual
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
ms.openlocfilehash: f68da0d937c27d0fb3175ca87d8d749c3f1e90aa
ms.sourcegitcommit: 316dd2182dd56b0cbde49f0cd82e9f75baa2530f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223648"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Jak: Zarządzanie zawijaniem wyrazów w edytorze

Można ustawić i wyczyścić opcję **zawijania wyrazów.** Gdy ta opcja jest ustawiona, część długiej linii, która wykracza poza bieżącą szerokość okna Edytor kodu, jest wyświetlana w następnym wierszu. Gdy ta opcja jest wyczyszczona, na przykład, aby ułatwić korzystanie z numeracji linii, można przewinąć w prawo, aby zobaczyć końce długich linii.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. Aby zapoznać się z programem Visual Studio na komputerze Mac, zobacz [Edytor źródeł: Zawijanie wyrazów](/visualstudio/mac/source-editor#word-wrap).

## <a name="to-set-word-wrap-preferences"></a>Aby ustawić preferencje zawijania wyrazów

1. W menu **Tools** (Narzędzia) wybierz pozycję **Options** (Opcje).

2. W folderze **Edytor tekstu** wybierz opcję **Opcje ogólne** w podfolderze **Wszystkie języki,** aby ustawić tę opcję globalnie.

     — lub —

     Wybierz opcje **ogólne** w podfolderze dla języka, w którym programujesz.

3. W obszarze **Ustawienia**zaznacz lub wyczyść opcję **zawijanie wyrazu.**

     Po **zaznaczeniu opcji Zawijanie wyrazu** włączona jest opcja **Pokaż glify wizualne dla zawijanych wyrazów.**

4. Wybierz opcję **Pokaż glify wizualne dla otoki wyrazu,** jeśli wolisz wyświetlić wskaźnik strzałki powrotnej, w którym długa linia zawija się na drugą linię. Wyczyść tę opcję, jeśli nie chcesz wyświetlać strzałek wskaźnika.

    > [!NOTE]
    > Te strzałki przypomnienia nie są dodawane do kodu; są one przeznaczone wyłącznie do celów wyświetlania.

## <a name="known-issues"></a>Znane problemy

Jeśli znasz zawijanie wyrazów w Notatnik++, Tekst wysublimowany lub kod programu Visual Studio, należy pamiętać o następujących problemach, w których program Visual Studio zachowuje się inaczej niż inni redaktorzy:

* [Potrójne kliknięcie nie wybiera całej linii](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Dwukrotne naciśnięcie klawisza End nie powoduje przesuń kursora na koniec wiersza](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../../ide/writing-code-in-the-code-and-text-editor.md)

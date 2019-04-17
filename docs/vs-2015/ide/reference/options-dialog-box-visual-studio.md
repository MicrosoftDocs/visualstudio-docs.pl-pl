---
title: Okno dialogowe Opcje | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 17abd78c193eb103597aa94f048bd715434e27a9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649657"
---
# <a name="options-dialog-box-visual-studio"></a>Opcje — Okno dialogowe [Visual Studio]
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Opcje** okno dialogowe umożliwia konfigurowanie zintegrowanego środowiska programistycznego (IDE) do Twoich potrzeb. Na przykład można ustanowić domyślną lokalizację zapisywania dla projektów, zmienić domyślny wygląd i zachowanie systemu windows i tworzenie skrótów do często używanych poleceń. Dostępne są również opcje specyficzne dla języka programowania i platform. Możesz uzyskać dostęp **opcje** z **narzędzia** menu.

> [!NOTE]
>  Dostępne opcje w oknach dialogowych i nazwy i lokalizacje poleceń menu, który zostanie wyświetlony, mogą różnić się od opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="layout-of-the-options-dialog-box"></a>Układ okna dialogowego Opcje
 **Opcje** okno dialogowe jest podzielona na dwie części: okienka nawigacji po lewej stronie i obszar wyświetlacza po prawej stronie. Kontrolka drzewa w okienku nawigacji zawiera węzły folderów, takie jak środowisko, Edytor tekstu, projekty i rozwiązania i kontroli źródła. Rozwiń węzeł dowolnego folderu, aby wyświetlić listę stron opcji, które zawiera. Po wybraniu węzła dla określonej strony, dostępne opcje są wyświetlane w obszarze.

 Opcje funkcji IDE nie są wyświetlane w okienku nawigacji, dopóki ta funkcja jest ładowany do pamięci. Dlatego te same opcje mogą nie być wyświetlane po rozpoczęciu nowej sesji, który były wyświetlane jako zakończonego ostatni. Podczas tworzenia projektu lub uruchom polecenie, które używa określonej aplikacji węzłów na odpowiednie opcje są dodawane do okna dialogowego Opcje. Dodawane są opcje następnie pozostaną dostępne, tak długo, jak funkcja IDE pozostaje w pamięci.

> [!NOTE]
>  Niektóre ustawienia kolekcji ograniczyć liczbę stron, które są wyświetlane w okienku nawigacji w oknie dialogowym Opcje. Możesz wyświetlić wszystkie strony, wybierając **Pokaż wszystkie ustawienia**.

## <a name="how-options-are-applied"></a>Jak opcje są stosowane
 Kliknięcie przycisku OK w **opcje** okno dialogowe zapisuje wszystkie ustawienia na wszystkich stronach. Klikając przycisk Anuluj, na dowolnej stronie anuluje wszystkie żądania zmiany, wraz ze wszystkimi wprowadzone przed chwilą drugiej **opcje** stron. Niektóre zmiany ustawień opcji, takich jak te wprowadzone na [czcionki i kolory, środowisko, opcje, okno dialogowe](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), tylko będzie obowiązywać po zakończeniu zamknij i otwórz ponownie program Visual Studio.

### <a name="show-all-settings"></a>Pokaż wszystkie ustawienia
 Zaznaczenie lub usunięcie zaznaczenia **Pokaż wszystkie ustawienia** stosuje wszystkie zmiany wprowadzone w **opcje** okno dialogowe, nawet jeśli nie zostało jeszcze kliknięte polecenie **OK**.

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie edytora](../../ide/customizing-the-editor.md)

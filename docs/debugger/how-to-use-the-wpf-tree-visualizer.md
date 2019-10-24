---
title: 'Instrukcje: korzystanie z wizualizatora drzewa WPF | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0adcca4acd5fc72d301d707ccdd831c86ef3e48f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731921"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Porady: korzystanie z wizualizatora drzewa WPF
Można użyć wizualizatora drzewa WPF do eksplorowania drzewa wizualnego obiektu WPF i wyświetlić właściwości zależności WPF dla obiektów, które są zawarte w tym drzewie. Aby uzyskać więcej informacji na temat drzew wizualizacji, zobacz [drzewa w WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Omówienie właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Po otwarciu wizualizatora drzewa WPF zobaczysz dwa okienka: **drzewo wizualizacji** po lewej stronie i **Właściwości** _nazwy_ **:** _w okienku po_ prawej stronie. Zaznacz dowolny obiekt w okienku **drzewa wizualnego** , a **Właściwości** **:** _Typ_ , okienko jest automatycznie aktualizowane, aby pokazać właściwości tego obiektu.

### <a name="to-open-the-wpf-tree-visualizer"></a>Aby otworzyć wizualizator drzewa WPF

1. W oknie etykietki danych, okno **czujki** , okno **autouzupełniania** lub okno **lokalne** obok nazwy obiektu WPF kliknij strzałkę obok ikony lupy.

     Zostanie wyświetlona lista wizualizatorów.

2. Kliknij przycisk **wizualizator drzewa WPF**.

### <a name="to-search-the-visual-tree"></a>Aby przeszukać drzewo wizualne

- W okienku **drzewa wizualnego** wpisz ciąg, który chcesz wyszukać w polu **wyszukiwania** .

  Wizualizator drzewa WPF natychmiast znajduje pierwszy obiekt w drzewie wizualnym odpowiadający wpisanemu ciągowi. Wpisz więcej znaków, aby znaleźć dokładniejsze dopasowanie.

  - Aby przejść do następnego dopasowania w drzewie wizualnym, kliknij przycisk **dalej**.

  - Aby powrócić do poprzedniego dopasowania, kliknij przycisk **poprzedni**.

  - Aby wyczyścić kryteria wyszukiwania, kliknij przycisk **Wyczyść**.

### <a name="to-search-the-properties-list"></a>Aby przeszukać listę właściwości

- W okienku **Właściwości** _nazwy_ **:** _wpisz ciąg_ , który chcesz wyszukać w polu **Filtr** .

  Wizualizator drzewa WPF natychmiast znajdzie właściwości, które pasują do wpisanego ciągu; teraz na liście są wyświetlane tylko te właściwości, które pasują do wpisanego ciągu. Wpisz więcej znaków, aby znaleźć bardziej dokładne dopasowanie.

  - Aby wyczyścić kryteria wyszukiwania, kliknij przycisk **Wyczyść**.

### <a name="to-close-the-visualizer"></a>Aby zamknąć wizualizator

- Kliknij ikonę **Zamknij** w prawym górnym rogu okna dialogowego.

## <a name="see-also"></a>Zobacz także
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
- [Drzewa w WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Przegląd właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview)

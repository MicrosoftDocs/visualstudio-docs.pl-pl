---
title: 'Instrukcje: Korzystanie z wizualizatora drzewa WPF | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 7276690152e74599df6183cf602aca518e3b944f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685330"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Instrukcje: Korzystanie z wizualizatora drzewa platformy WPF
Można użyć wizualizatora drzewa WPF, aby zapoznać się z drzewa wizualnego obiektu WPF i wyświetlić właściwości zależności WPF dla obiektów, które są zawarte w drzewie. Aby uzyskać więcej informacji na temat drzewa wizualnego, zobacz [drzewa w WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Aby uzyskać więcej informacji na temat właściwości zależności zobacz [Przegląd właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Po otwarciu wizualizatora drzewa WPF, zobaczysz dwa okienka: **drzewa wizualnego** po lewej stronie i **właściwości** _nazwa_**:**  _Typ_ w okienku po prawej stronie. Zaznacz dowolny obiekt w **drzewa wizualnego** okienku i **właściwości** _nazwa_**:**_typu_ okienka automatycznie aktualizowane, aby wyświetlić właściwości tego obiektu.

### <a name="to-open-the-wpf-tree-visualizer"></a>Aby otworzyć z wizualizatora drzewa WPF

1.  W DataTip **Obejrzyj** oknie **automatyczne** oknie lub **lokalne** oknie obok nazwy obiektów programu WPF, kliknij strzałkę obok ikony lupy.

     Zostanie wyświetlona lista wizualizatorów.

2.  Kliknij przycisk **wizualizatora drzewa WPF**.

### <a name="to-search-the-visual-tree"></a>Aby przeszukać drzewo wizualne

-   W **drzewa wizualnego** okienko, wpisz ciąg, aby wyszukać w **wyszukiwania** pole.

     Z wizualizatora drzewa WPF natychmiast znajduje pierwszy obiekt w drzewie wizualnym, który pasuje do ciągu, które zostały wpisane. Wpisz więcej znaków, aby znaleźć bardziej dokładne dopasowanie.

    -   Aby przejść do następnego dopasowania w obrębie drzewa wizualnego, kliknij przycisk **dalej**.

    -   Aby wrócić do poprzedniego dopasowania, kliknij przycisk **poprzedni**.

    -   Aby wyczyścić kryteria wyszukiwania, kliknij pozycję **wyczyść**.

### <a name="to-search-the-properties-list"></a>Lista właściwości wyszukiwania

-   W **właściwości** _nazwa_**:**_typu_ okienko, wpisz ciąg, aby wyszukać w **filtrowania**pole.

     Z wizualizatora drzewa WPF natychmiast wyszukuje właściwości, które pasuje do ciągu, które zostały wpisane; teraz na liście zostaną wyświetlone tylko te właściwości, które są dopasowywania ciągu, które zostały wpisane. Wpisz więcej znaków, aby znaleźć bardziej dokładne dopasowanie.

    -   Aby wyczyścić kryteria wyszukiwania, kliknij pozycję **wyczyść**.

### <a name="to-close-the-visualizer"></a>Aby zamknąć wizualizatora

-   Kliknij przycisk **Zamknij** ikonę w prawym górnym rogu okna dialogowego.

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
- [Drzewa w WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Przegląd właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview)

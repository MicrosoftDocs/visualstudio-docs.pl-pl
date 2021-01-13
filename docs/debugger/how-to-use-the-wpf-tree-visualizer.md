---
title: Użyj wizualizatora drzewa WPF | Microsoft Docs
description: Użyj wizualizatora Windows Presentation Foundation (WPF) do eksplorowania drzewa wizualnego obiektu WPF i wyświetlania właściwości zależności WPF w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 83b11ec1c091d2a63ed89cd3089bc3b507b0db8f
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149030"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Porady: korzystanie z wizualizatora drzewa WPF
Można użyć wizualizatora drzewa WPF do eksplorowania drzewa wizualnego obiektu WPF i wyświetlić właściwości zależności WPF dla obiektów, które są zawarte w tym drzewie. Aby uzyskać więcej informacji na temat drzew wizualizacji, zobacz [drzewa w WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Omówienie właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Po otwarciu wizualizatora drzewa WPF zobaczysz dwa okienka: **drzewo wizualizacji** po lewej stronie i **Właściwości** _nazwy_**:**_w okienku po_ prawej stronie. Zaznacz dowolny obiekt w okienku **drzewa wizualnego** , a **Właściwości** **:**_Typ_ , okienko jest automatycznie aktualizowane, aby pokazać właściwości tego obiektu.

 > [!NOTE]
 > Możesz również użyć [aktywnego drzewa wizualnego i Eksploratora właściwości na żywo](../xaml-tools/inspect-xaml-properties-while-debugging.md) , aby przeanalizować drzewo wizualne obiektów WPF. Wizualizator drzewa WPF jest starszą funkcją i nie jest aktywnym programowaniem.

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

- W okienku **Właściwości** _nazwy_**:**_wpisz ciąg_ , który chcesz wyszukać w polu **Filtr** .

  Wizualizator drzewa WPF natychmiast znajdzie właściwości, które pasują do wpisanego ciągu; teraz na liście są wyświetlane tylko te właściwości, które pasują do wpisanego ciągu. Wpisz więcej znaków, aby znaleźć bardziej dokładne dopasowanie.

  - Aby wyczyścić kryteria wyszukiwania, kliknij przycisk **Wyczyść**.

### <a name="to-close-the-visualizer"></a>Aby zamknąć wizualizator

- Kliknij ikonę **Zamknij** w prawym górnym rogu okna dialogowego.

## <a name="see-also"></a>Zobacz także
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
- [Drzewa w WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Przegląd Właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview)

---
title: 'Instrukcje: Korzystanie z wizualizatora drzewa WPF | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6cd353610cc3d9122c14f608f0278d4afc501e0f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686847"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Instrukcje: Korzystanie z wizualizatora drzewa platformy WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć wizualizatora drzewa WPF, aby zapoznać się z drzewa wizualnego obiektu WPF i wyświetlić właściwości zależności WPF dla obiektów, które są zawarte w drzewie. Aby uzyskać więcej informacji na temat drzewa wizualnego, zobacz [drzewa w WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Aby uzyskać więcej informacji na temat właściwości zależności zobacz [Przegląd właściwości zależności](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
 Po otwarciu wizualizatora drzewa WPF, zobaczysz dwa okienka: **drzewa wizualnego** po lewej stronie i **właściwości** _nazwa_**:**  _Typ_ w okienku po prawej stronie. Zaznacz dowolny obiekt w **drzewa wizualnego** okienku i **właściwości** _nazwa_**:**_typu_ okienka automatycznie aktualizowane, aby wyświetlić właściwości tego obiektu.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Aby otworzyć z wizualizatora drzewa WPF  
  
1. W DataTip **Obejrzyj** oknie **automatyczne** oknie lub **lokalne** oknie obok nazwy obiektów programu WPF, kliknij strzałkę obok ikony lupy.  
  
     Zostanie wyświetlona lista wizualizatorów.  
  
2. Kliknij przycisk **wizualizatora drzewa WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Aby przeszukać drzewo wizualne  
  
- W **drzewa wizualnego** okienko, wpisz ciąg, aby wyszukać w **wyszukiwania** pole.  
  
     Z wizualizatora drzewa WPF natychmiast znajduje pierwszy obiekt w drzewie wizualnym, który pasuje do ciągu, które zostały wpisane. Wpisz więcej znaków, aby znaleźć bardziej dokładne dopasowanie.  
  
    - Aby przejść do następnego dopasowania w obrębie drzewa wizualnego, kliknij przycisk **dalej**.  
  
    - Aby wrócić do poprzedniego dopasowania, kliknij przycisk **poprzedni**.  
  
    - Aby wyczyścić kryteria wyszukiwania, kliknij pozycję **wyczyść**.  
  
### <a name="to-search-the-properties-list"></a>Lista właściwości wyszukiwania  
  
- W **właściwości** _nazwa_**:**_typu_ okienko, wpisz ciąg chcesz wyszukać w **filtrowania**pole.  
  
     Z wizualizatora drzewa WPF natychmiast wyszukuje właściwości, które pasuje do ciągu, które zostały wpisane; teraz na liście zostaną wyświetlone tylko te właściwości, które są dopasowywania ciągu, które zostały wpisane. Wpisz więcej znaków, aby znaleźć bardziej dokładne dopasowanie.  
  
    - Aby wyczyścić kryteria wyszukiwania, kliknij pozycję **wyczyść**.  
  
### <a name="to-close-the-visualizer"></a>Aby zamknąć wizualizatora  
  
- Kliknij przycisk **Zamknij** ikonę w prawym górnym rogu okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Korzystanie z wizualizatora](../misc/how-to-use-a-visualizer.md)   
 [Tworzenie niestandardowych Wizualizatorów](../debugger/create-custom-visualizers-of-data.md)   
 [Drzewa w WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Przegląd właściwości zależności](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)

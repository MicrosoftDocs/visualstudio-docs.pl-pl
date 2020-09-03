---
title: 'Instrukcje: korzystanie z wizualizatora drzewa WPF | Microsoft Docs'
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
ms.openlocfilehash: 381dc45351ae03e615afbdd31239869e3dba8e4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825432"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Porady: korzystanie z wizualizatora drzewa WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć wizualizatora drzewa WPF do eksplorowania drzewa wizualnego obiektu WPF i wyświetlić właściwości zależności WPF dla obiektów, które są zawarte w tym drzewie. Aby uzyskać więcej informacji na temat drzew wizualizacji, zobacz [drzewa w WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Omówienie właściwości zależności](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
 Po otwarciu wizualizatora drzewa WPF zobaczysz dwa okienka: **drzewo wizualizacji** po lewej stronie i **Właściwości** _nazwy_**:**_w okienku po_ prawej stronie. Zaznacz dowolny obiekt w okienku **drzewa wizualnego** , a **Właściwości** _Name_**:**_Typ_ , okienko jest automatycznie aktualizowane, aby pokazać właściwości tego obiektu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: korzystanie z wizualizatora](../misc/how-to-use-a-visualizer.md)   
 [Tworzenie wizualizacji niestandardowych](../debugger/create-custom-visualizers-of-data.md)   
 [Drzewa w WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Przegląd Właściwości zależności](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)

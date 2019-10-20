---
title: 'Instrukcje: zwiększanie kodu wygenerowanego przez projektanta O-R | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1d60090ca16907e16bb58970d793124c5bb2dec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665946"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Instrukcje: zwiększanie kodu wygenerowanego przez projektanta O/R
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod wygenerowany przez [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jest ponownie generowany po wprowadzeniu zmian do klas jednostek i innych obiektów na powierzchni projektanta. Ze względu na ten kod, każdy kod dodawany do wygenerowanego kodu jest zwykle zastępowany, gdy projektant ponownie generuje kod. @No__t_0 zapewnia możliwość generowania plików klas częściowych, w których można dodać kod, który nie zostanie nadpisany. Jednym z przykładów dodawania własnego kodu do kodu wygenerowanego przez [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jest dodanie walidacji danych do klas LINQ to SQL (Entity). Aby uzyskać więcej informacji, zobacz [jak: Dodawanie walidacji do klas jednostek](../data-tools/how-to-add-validation-to-entity-classes.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-code-to-an-entity-class"></a>Dodawanie kodu do klasy jednostki

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Aby utworzyć klasę częściową i dodać kod do klasy jednostki

1. Otwórz lub Utwórz nowy plik klas LINQ to SQL (plik**DBML** ) w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań** /**Eksplorator bazy danych**).

2. W [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] kliknij prawym przyciskiem myszy klasę, dla której chcesz dodać walidację, a następnie kliknij polecenie **Wyświetl kod**.

     Zostanie otwarty Edytor kodu z klasą częściową dla wybranej klasy jednostki.

3. Dodaj swój kod w deklaracji klasy częściowej dla klasy Entity.

## <a name="adding-code-to-a-datacontext"></a>Dodawanie kodu do elementu DataContext

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Aby utworzyć klasę częściową i dodać kod do elementu DataContext

1. Otwórz lub Utwórz nowy plik klas LINQ to SQL (plik**DBML** ) w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań** /**Eksplorator bazy danych**).

2. W [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] kliknij prawym przyciskiem myszy pusty obszar w projektancie, a następnie kliknij polecenie **Wyświetl kod**.

     Zostanie otwarty Edytor kodu z klasą częściową dla kontekstu DataContext.

3. Dodaj swój kod w deklaracji klasy częściowej dla elementu DataContext.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w](../data-tools/linq-to-sql-tools-in-visual-studio2.md) przewodniku po programie Visual Studio [: tworzenie klas LINQ to SQL (Projektant O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) wskazówki [: Dodawanie walidacji do klas jednostek](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)

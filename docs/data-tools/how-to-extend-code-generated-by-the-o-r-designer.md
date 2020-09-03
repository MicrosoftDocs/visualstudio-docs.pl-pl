---
title: 'Instrukcje: zwiększanie kodu wygenerowanego przez projektanta O-R'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b4c0ac8cff82250169171e1d842e64a34a4523ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282114"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Instrukcje: zwiększanie kodu wygenerowanego przez projektanta O/R
Kod generowany przez **projektanta O/R** jest generowany ponownie po wprowadzeniu zmian do klas jednostek i innych obiektów na powierzchni projektanta. Ze względu na ten kod, każdy kod dodawany do wygenerowanego kodu jest zwykle zastępowany, gdy projektant ponownie generuje kod. **Projektant O/R** zapewnia możliwość generowania plików klas częściowych, w których można dodać kod, który nie jest zastępowany. Jednym z przykładów dodawania własnego kodu do kodu wygenerowanego przez **projektanta O/R** jest dodawanie walidacji danych do klas LINQ to SQL (jednostek). Aby uzyskać więcej informacji, zobacz [jak: Dodawanie walidacji do klas jednostek](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Dodaj kod do klasy jednostki

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Aby utworzyć klasę częściową i dodać kod do klasy jednostki

1. Otwórz lub Utwórz nowy plik klas LINQ to SQL (plik**DBML** ) w **projektancie o/R**. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań** lub **Eksplorator bazy danych**.)

2. W **projektancie o/R**kliknij prawym przyciskiem myszy klasę, dla której chcesz dodać walidację, a następnie kliknij polecenie **Wyświetl kod**.

     Zostanie otwarty Edytor kodu z klasą częściową dla wybranej klasy jednostki.

3. Dodaj swój kod w deklaracji klasy częściowej dla klasy Entity.

## <a name="add-code-to-a-datacontext"></a>Dodawanie kodu do elementu DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Aby utworzyć klasę częściową i dodać kod do elementu DataContext

1. Otwórz lub Utwórz nowy plik klas LINQ to SQL (plik**DBML** ) w **projektancie o/R**. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań** lub **Eksplorator bazy danych**.)

2. W **projektancie o/R**kliknij prawym przyciskiem myszy pusty obszar w projektancie, a następnie kliknij polecenie **Wyświetl kod**.

     Zostanie otwarty Edytor kodu z klasą częściową dla kontekstu DataContext.

3. Dodaj swój kod w deklaracji klasy częściowej dla elementu DataContext.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index)

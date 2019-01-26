---
title: 'Instrukcje: Rozszerzanie kodu wygenerowanego przez projektanta O R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 275d281c8e127f5ef7278881244252615efd2827
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966169"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Instrukcje: Rozszerzanie kodu wygenerowanego przez projektanta O/R
Kod wygenerowany przez **O/R Designer** zostanie ponownie wygenerowany, gdy zmiany zostaną wprowadzone do klas jednostek i innych obiektów na powierzchni projektowej. Ze względu na to ponowne generowanie kodu każdy kod, który dodasz do wygenerowanego kodu jest zazwyczaj zastąpione, gdy projektant generuje kod. **O/R Designer** umożliwia generowanie plików klasy częściowej, w których można dodać kod, który nie jest zastępowany. Przykładem dodając własny kod do kodu generowanego przez **O/R Designer** jest dodawanie sprawdzania poprawności danych do programu LINQ do klas SQL (jednostka). Aby uzyskać więcej informacji, zobacz [jak: Dodawanie walidacji do klas jednostek](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Dodaj kod do klasy jednostki

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Utwórz klasę częściową i dodać kod do klasy jednostki

1.  Otwórz lub Utwórz nowy plik LINQ to SQL klas (**dbml** pliku) w **O/R Designer**. (Kliknij dwukrotnie **dbml** w pliku **Eksploratora rozwiązań** lub **Eksplorator bazy danych**.)

2.  W **O/R Designer**, kliknij prawym przyciskiem myszy klasę, dla którego chcesz dodać sprawdzanie poprawności, a następnie kliknij przycisk **Wyświetl kod**.

     Zostanie otwarty Edytor kodu klasę częściową dla klasy wybranego obiektu.

3.  Dodaj swój kod w deklaracji klasy częściowej klasy jednostki.

## <a name="add-code-to-a-datacontext"></a>Dodawanie kodu do elementu DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Utwórz klasę częściową i dodać kod do elementu DataContext

1.  Otwórz lub Utwórz nowy plik LINQ to SQL klas (**dbml** pliku) w **O/R Designer**. (Kliknij dwukrotnie **dbml** w pliku **Eksploratora rozwiązań** lub **Eksplorator bazy danych**.)

2.  W **O/R Designer**, kliknij prawym przyciskiem myszy pusty obszar w projektancie, a następnie kliknij przycisk **Wyświetl kod**.

     Edytor kodu otwiera częściowej klasy kontekstu danych.

3.  Dodaj swój kod w deklaracji klasy częściowej dla kontekstu danych.

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: Tworzenie zapytań LINQ do klas SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
---
title: 'Instrukcje: Rozszerzanie kodu wygenerowanego przez projektanta O R | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6aedac18548112335da49012d471fb98eef2ef2c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786902"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Instrukcje: Rozszerzanie kodu wygenerowanego przez narzędzie Object Relational Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Kod wygenerowany przez [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] zostanie ponownie wygenerowany, gdy zmiany zostaną wprowadzone do klas jednostek i innych obiektów na powierzchni projektowej. Ze względu na to ponowne generowanie kodu każdy kod, który dodasz do wygenerowanego kodu jest zazwyczaj zastąpione, gdy projektant generuje kod. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Umożliwia generowanie plików klasy częściowej, w których można dodać kod, który nie zostanie nadpisany. Przykładem dodając własny kod do kodu generowanego przez [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jest dodawanie sprawdzania poprawności danych do programu LINQ do klas SQL (jednostka). Aby uzyskać informacje, zobacz [jak: Dodawanie walidacji do klas jednostek](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Dodawanie kodu do klasy jednostki  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Utwórz klasę częściową i dodać kod do klasy jednostki  
  
1.  Otwórz lub Utwórz nowy plik LINQ to SQL klas (**dbml** pliku) w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie **dbml** w pliku **Eksploratora rozwiązań**/**Eksplorator bazy danych**.)  
  
2.  W [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], kliknij prawym przyciskiem myszy klasę, dla którego chcesz dodać sprawdzanie poprawności, a następnie kliknij przycisk **Wyświetl kod**.  
  
     Zostanie otwarty Edytor kodu klasę częściową dla klasy wybranego obiektu.  
  
3.  Dodaj swój kod w deklaracji klasy częściowej klasy jednostki.  
  
## <a name="adding-code-to-a-datacontext"></a>Dodawanie kodu do elementu DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Utwórz klasę częściową i dodać kod do elementu DataContext  
  
1.  Otwórz lub Utwórz nowy plik LINQ to SQL klas (**dbml** pliku) w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie **dbml** w pliku **Eksploratora rozwiązań**/**Eksplorator bazy danych**.)  
  
2.  W [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], kliknij prawym przyciskiem myszy pusty obszar w projektancie, a następnie kliknij przycisk **Wyświetl kod**.  
  
     Edytor kodu otwiera częściowej klasy kontekstu danych.  
  
3.  Dodaj swój kod w deklaracji klasy częściowej dla kontekstu danych.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Przewodnik: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Przewodnik: Dodawanie walidacji do klas jednostek](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)

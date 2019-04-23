---
title: Metody DataContext (Projektant O-R) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 97a36c38eb0c4a96cb7182300c2f9aca6da68e8a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042756"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element DataContext] (assetId:///T:System.Data.Linq.DataContext?qualifyHint=False & autoUpgrade = True) metody (w kontekście [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) to metody <xref:System.Data.Linq.DataContext> klasę uruchamianą przechowywane procedury i funkcje w bazie danych.  
  
 <xref:System.Data.Linq.DataContext> Klasa jest [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasę, która działa jako kanał między bazy danych programu SQL Server i [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klas jednostek mapowany do tej bazy danych. <xref:System.Data.Linq.DataContext> Klasa zawiera informacje o parametrach połączenia i metody nawiązywania połączenia z bazą danych i manipulowania danymi w bazie danych. Domyślnie <xref:System.Data.Linq.DataContext> klasa zawiera kilka metod, które można wywoływać, takich jak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodę, która wysyła zaktualizowane dane z [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasy do bazy danych. Można również utworzyć dodatkowe <xref:System.Data.Linq.DataContext> metod, które mapują do procedur przechowywanych i funkcji. Innymi słowy, wywoływanie tych metod niestandardowego uruchomi procedura składowana lub funkcja w bazie danych, <xref:System.Data.Linq.DataContext> metody jest zamapowany. Możesz dodać nowe metody <xref:System.Data.Linq.DataContext> klasy tak, jak należy dodać metody umożliwiające rozszerzenie dowolnej klasy. Jednak w dyskusje na temat <xref:System.Data.Linq.DataContext> metod w kontekście [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], jest <xref:System.Data.Linq.DataContext> metod, które mapują do procedur przechowywanych i funkcji, które są przedmiotem.  
  
## <a name="methods-pane"></a>Okienko metod  
 <xref:System.Data.Linq.DataContext> metody, które mapują do procedur przechowywanych i funkcji są wyświetlane w okienku metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Okienko metod jest okienko wzdłuż boku **jednostek** okienko (główna powierzchnia projektowa). Okienko metod zawiera listę wszystkich <xref:System.Data.Linq.DataContext> metod, które zostały utworzone przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Domyślnie jest pusta, okienko metod Przeciągnij procedury składowanej lub funkcji z **Eksploratora serwera**/**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] utworzyć <xref:System.Data.Linq.DataContext> metod i wypełnij okienko metod. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Otwórz i Zamknij okienko metod, klikając prawym przyciskiem myszy [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , a następnie klikając polecenie **Ukryj okienko metod** lub **Pokaż okienko metod**, lub użyj skrótu klawiaturowego CTRL + 1.  
  
## <a name="two-types-of-datacontext-methods"></a>Dwa typy metod DataContext  
 Metody DataContext są tych metod, które mapują do procedur przechowywanych i funkcji w bazie danych. Można tworzyć i Dodawanie metody DataContext w okienku metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Istnieją dwa odrębne rodzaje <xref:System.Data.Linq.DataContext> metod; te, które zwracają jeden lub więcej zestawów wyników i te, które nie obsługują:  
  
- <xref:System.Data.Linq.DataContext> metody, które zwracają jeden lub więcej zestawów wyników:  
  
     Utworzyć ten rodzaju <xref:System.Data.Linq.DataContext> metody, gdy tylko wymaganych przez aplikację do uruchamiania procedur składowanych i funkcji w bazie danych i zwracają wyniki. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, a <xref:System.Data.Linq.IMultipleResults>.  
  
- <xref:System.Data.Linq.DataContext> metody, które nie zwracają zestaw wyników: takich jak wstawia, aktualizacji i usuwania dla klasy określonej jednostki.  
  
     Utworzyć ten rodzaju <xref:System.Data.Linq.DataContext> metody, gdy aplikacja ma do uruchamiania procedur składowanych, zamiast przy użyciu domyślnego [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zachowanie zapisywanie zmodyfikowanych danych między klasami jednostki oraz bazy danych. Aby uzyskać więcej informacji, zobacz [jak: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>Zwracane typy metod DataContext  
 Podczas przeciągania procedur przechowywanych i funkcji z **Eksploratora serwera**/**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> metoda różni się w zależności od tego, gdzie można upuścić elementu. Upuszczenie elementów bezpośrednio na istniejącej klasy jednostki tworzy <xref:System.Data.Linq.DataContext> metody z typem zwracanym klasy jednostki; upuszczanie elementów na pustym obszarem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (w obu okienku) tworzy <xref:System.Data.Linq.DataContext> metodę, która zwraca Typ jest generowane automatycznie. Automatycznie wygenerowany typ, który jest tworzony o nazwie zgodnej z procedury składowanej lub funkcji i właściwości, które mapują do pól zwrócone przez procedurę składowaną lub funkcję.  
  
> [!NOTE]
>  Możesz zmienić typ zwracany <xref:System.Data.Linq.DataContext> metoda po dodaniu do okienka metod. Aby sprawdzić lub zmienić typ zwracany <xref:System.Data.Linq.DataContext> metody, zaznacz ją i sprawdź **typie zwracanym** właściwość **właściwości** okna. Aby uzyskać więcej informacji, zobacz [jak: Zmień zwracany typ metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Obiekty, które przeciągniesz z bazy danych na powierzchnię projektanta O/R będzie miała automatycznie na podstawie nazwy obiektów w bazie danych. Przeciągnięcie tego samego obiektu w więcej niż jeden raz, na końcu nową nazwę, która odróżnia nazwy jest dołączany numer. Gdy nazwy obiektów bazy danych zawiera spacje lub znaki nieobsługiwane w języku Visual Basic lub C#, miejsca lub nieprawidłowy znak jest zastępowany znaku podkreślenia.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Procedury składowane](http://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)   
 [Instrukcje: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Instrukcje: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Przewodnik: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Przewodnik: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)

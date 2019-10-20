---
title: Metody DataContext (w przypadku projektanta O-R) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9d7e0eee35e0f1e62247865bd539aab8d21349d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657393"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetId:///T: System. Data. LINQ. DataContext? qualifyHintd = false & autoupgrade = true) metody (w kontekście [narzędzi LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) to metody klasy <xref:System.Data.Linq.DataContext>, która uruchamia procedury składowane i funkcje w Database.

 Klasa <xref:System.Data.Linq.DataContext> jest klasą [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)], która działa jako kanał między bazą danych SQL Server i [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasy jednostek mapowanych do tej bazy danych. Klasa <xref:System.Data.Linq.DataContext> zawiera informacje o parametrach połączenia oraz metody łączenia się z bazą danych i manipulowania danymi w bazie danych programu. Domyślnie Klasa <xref:System.Data.Linq.DataContext> zawiera kilka metod, które można wywołać, takich jak Metoda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, która wysyła zaktualizowane dane z klas [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] do bazy danych. Możesz również utworzyć dodatkowe metody <xref:System.Data.Linq.DataContext>, które mapują na procedury składowane i funkcje. Innymi słowy, wywołanie tych metod niestandardowych spowoduje uruchomienie procedury składowanej lub funkcji przechowywanej w bazie danych, do której jest zamapowana Metoda <xref:System.Data.Linq.DataContext>. Nowe metody można dodać do klasy <xref:System.Data.Linq.DataContext> tak samo jak w przypadku dodawania metod w celu poszerzenia dowolnej klasy. Jednak w dyskusjach dotyczących <xref:System.Data.Linq.DataContext> metod w kontekście [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jest to <xref:System.Data.Linq.DataContext> metody, które mapują na procedury składowane i funkcje, które są omawiane.

## <a name="methods-pane"></a>Okienko metod
 Metody <xref:System.Data.Linq.DataContext>, które są mapowane na procedury składowane i funkcje, są wyświetlane w okienku metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Okienko metody jest okienkiem obok okienka **jednostki** (głównej powierzchni projektowej). W okienku metody znajduje się lista wszystkich <xref:System.Data.Linq.DataContext> metod utworzonych przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Domyślnie okienko metody jest puste; Przeciągnij procedury składowane lub funkcje z **Eksplorator serwera** /**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], aby utworzyć metody <xref:System.Data.Linq.DataContext> i wypełnić okienko metody. Aby uzyskać więcej informacji, zobacz [How to: Create DataContext Methods zamapowany na procedury składowane i funkcje (Projektant O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Otwórz i zamknij okienko metody, klikając prawym przyciskiem myszy [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], a następnie klikając polecenie **Ukryj okienko metody** lub **Pokaż okienko metody**, lub użyj skrótu klawiaturowego Ctrl + 1.

## <a name="two-types-of-datacontext-methods"></a>Dwa typy metod DataContext
 Metody DataContext to te metody, które mapują na procedury składowane i funkcje w bazie danych. Metody DataContext można tworzyć i dodawać w okienku metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Istnieją dwa różne typy metod <xref:System.Data.Linq.DataContext>; te, które zwracają jeden lub więcej zestawów wyników, i te, które nie:

- Metody <xref:System.Data.Linq.DataContext>, które zwracają jeden lub więcej zestawów wyników:

     Utwórz ten rodzaj metody <xref:System.Data.Linq.DataContext>, gdy aplikacja musi uruchamiać procedury składowane i funkcje w bazie danych i zwracać wyniki. Aby uzyskać więcej informacji, zobacz [How to: Create DataContext Methods zamapowanych na procedury składowane i funkcje (Projektant O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), system. Data. LINQ. ISingleResult \<T > i <xref:System.Data.Linq.IMultipleResults>.

- <xref:System.Data.Linq.DataContext> metod, które nie zwracają zestawów wyników: takich jak INSERT, Updates i usunięć dla określonej klasy jednostki.

     Utwórz ten rodzaj metody <xref:System.Data.Linq.DataContext>, gdy aplikacja musi uruchamiać procedury składowane zamiast korzystać z domyślnego zachowania [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] do zapisywania zmodyfikowanych danych między klasą jednostki a bazą danych. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Zwracane typy metod DataContext
 Gdy przeciągasz procedury składowane i funkcje z **Eksplorator serwera** /**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], zwracany typ wygenerowanej metody <xref:System.Data.Linq.DataContext> różni się w zależności od miejsca, w którym element zostanie porzucany. Porzucenie elementów bezpośrednio do istniejącej klasy Entity tworzy metodę <xref:System.Data.Linq.DataContext> z typem zwracanym klasy Entity; upuszczanie elementów na pusty obszar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (w obu okienka) tworzy metodę <xref:System.Data.Linq.DataContext>, która zwraca typ wygenerowany automatycznie. Tworzony automatycznie wygenerowany typ ma nazwę zgodną z nazwą procedury składowanej lub funkcją oraz właściwościami mapowanymi do pól zwracanych przez procedurę składowaną lub funkcję.

> [!NOTE]
> Zwracany typ metody <xref:System.Data.Linq.DataContext> można zmienić po dodaniu jej do okienka metody. Aby sprawdzić lub zmienić zwracany typ metody <xref:System.Data.Linq.DataContext>, zaznacz ją i sprawdź Właściwość **zwracanego typu** w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [How to: zmiana zwracanego typu metody DataContext (Projektant O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Obiekty przeciągane z bazy danych na powierzchnię projektanta O/R będą automatycznie nazwane na podstawie nazwy obiektów w bazie danych. Jeśli przeciągniesz ten sam obiekt więcej niż raz, do końca nowej nazwy jest dołączany numer odróżniający nazwy. Gdy nazwy obiektów bazy danych zawierają spacje lub znaki nieobsługiwane w Visual Basic lub C#, spacja lub nieprawidłowy znak jest zastępowany podkreśleniem.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [procedury składowane](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) [: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (Projektant O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [instrukcje: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania, i usuwa (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) wskazówki [: Dostosowywanie zachowania INSERT, Update i DELETE klasy jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) [przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)

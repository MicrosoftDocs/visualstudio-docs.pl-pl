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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657393"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetId:///T: System. Data. LINQ. DataContext? qualifyHintd = false&autoupgrade = true) metody (w kontekście [narzędzi LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) to metody <xref:System.Data.Linq.DataContext> klasy, która uruchamia procedury składowane i funkcje w bazie danych.

 <xref:System.Data.Linq.DataContext>Klasa jest [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasą, która działa jako kanał między bazą danych SQL Server i [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasami jednostek mapowanymi do tej bazy danych. <xref:System.Data.Linq.DataContext>Klasa zawiera informacje o parametrach połączenia oraz metody łączenia się z bazą danych i manipulowania danymi w bazie danych programu. Domyślnie <xref:System.Data.Linq.DataContext> Klasa zawiera kilka metod, które można wywołać, takich jak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Metoda, która wysyła zaktualizowane dane z [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klas do bazy danych. Możesz również utworzyć dodatkowe <xref:System.Data.Linq.DataContext> metody, które mapują na procedury składowane i funkcje. Innymi słowy, wywołanie tych metod niestandardowych spowoduje uruchomienie procedury składowanej lub funkcji przechowywanej w bazie danych, <xref:System.Data.Linq.DataContext> do której metoda jest zamapowana. Nowe metody można dodać do <xref:System.Data.Linq.DataContext> klasy tak samo jak w przypadku dodawania metod w celu rozbudowania dowolnej klasy. Jednak w dyskusjach dotyczących <xref:System.Data.Linq.DataContext> metod w kontekście [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , są to <xref:System.Data.Linq.DataContext> metody, które mapują na procedury składowane i funkcje, które są omawiane.

## <a name="methods-pane"></a>Okienko metod
 <xref:System.Data.Linq.DataContext> metody, które są mapowane na procedury składowane i funkcje, są wyświetlane w okienku metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Okienko metody jest okienkiem obok okienka **jednostki** (głównej powierzchni projektowej). W okienku metody są wyświetlane wszystkie <xref:System.Data.Linq.DataContext> metody, które zostały utworzone przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Domyślnie okienko metody jest puste; Przeciągnij procedury składowane lub funkcje z **Eksplorator serwera** / **Eksplorator bazy danych** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] do tworzenia <xref:System.Data.Linq.DataContext> metod i wypełnij okienko metody. Aby uzyskać więcej informacji, zobacz [How to: Create DataContext Methods zamapowany na procedury składowane i funkcje (Projektant O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Otwórz i zamknij okienko metody, klikając prawym przyciskiem myszy, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a następnie klikając polecenie **Ukryj metody okienka** lub **Pokaż okienko metody**lub użyj skrótu klawiaturowego Ctrl + 1.

## <a name="two-types-of-datacontext-methods"></a>Dwa typy metod DataContext
 Metody DataContext to te metody, które mapują na procedury składowane i funkcje w bazie danych. Metody DataContext można tworzyć i dodawać w okienku metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Istnieją dwa odrębne typy <xref:System.Data.Linq.DataContext> metod: te, które zwracają jeden lub więcej zestawów wyników, a także te, które to nie są

- <xref:System.Data.Linq.DataContext> metody, które zwracają jeden lub więcej zestawów wyników:

     Utwórz ten rodzaj <xref:System.Data.Linq.DataContext> metody, gdy aplikacja musi uruchamiać procedury składowane i funkcje w bazie danych i zwracać wyniki. Aby uzyskać więcej informacji, zobacz [How to: Create DataContext Methods zamapowanych na procedury składowane i funkcje (Projektant O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), system. Data. LINQ. ISingleResult \<T> i <xref:System.Data.Linq.IMultipleResults> .

- <xref:System.Data.Linq.DataContext> metody, które nie zwracają zestawów wyników: takie jak INSERT, Updates i usunięć dla określonej klasy jednostki.

     Utwórz ten rodzaj <xref:System.Data.Linq.DataContext> metody, gdy aplikacja musi uruchamiać procedury składowane zamiast korzystać z domyślnego [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zachowania do zapisywania zmodyfikowanych danych między klasą jednostki a bazą danych. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Zwracane typy metod DataContext
 Gdy przeciągniesz procedury składowane i funkcje z **Eksplorator serwera** / **Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , zwracany typ wygenerowanej <xref:System.Data.Linq.DataContext> metody różni się w zależności od tego, gdzie porzucasz element. Porzucenie elementów bezpośrednio do istniejącej klasy jednostek tworzy <xref:System.Data.Linq.DataContext> metodę z typem zwracanym klasy Entity; upuszczanie elementów na pusty obszar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (w obu okienka) tworzy <xref:System.Data.Linq.DataContext> metodę zwracającą automatycznie wygenerowany typ. Tworzony automatycznie wygenerowany typ ma nazwę zgodną z nazwą procedury składowanej lub funkcją oraz właściwościami mapowanymi do pól zwracanych przez procedurę składowaną lub funkcję.

> [!NOTE]
> Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu jej do okienka metod. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz ją i sprawdź Właściwość **zwracanego typu** w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [How to: zmiana zwracanego typu metody DataContext (Projektant O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Obiekty przeciągane z bazy danych na powierzchnię projektanta O/R będą automatycznie nazwane na podstawie nazwy obiektów w bazie danych. Jeśli przeciągniesz ten sam obiekt więcej niż raz, do końca nowej nazwy jest dołączany numer odróżniający nazwy. Gdy nazwy obiektów bazy danych zawierają spacje lub znaki nieobsługiwane w Visual Basic lub C#, spacja lub nieprawidłowy znak jest zastępowany podkreśleniem.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [procedury składowane](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) [: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (Projektant o/r)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [instrukcje: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [przewodników: Dostosowywanie zachowań insert, Update i DELETE klasy jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) [Przewodnik: tworzenie klas LINQ to SQL (Projektant o-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)

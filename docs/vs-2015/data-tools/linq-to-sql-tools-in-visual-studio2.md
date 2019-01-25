---
title: LINQ to SQL Tools | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d7dcb33add9726a341c1b4b92c032be7c289c2d2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758088"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL Tools w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


LINQ do SQL była pierwszym technologii mapowania obiektowo relacyjny, wydane przez firmę Microsoft. Działa dobrze w przypadku podstawowych scenariuszy i może być obsługiwany w programie Visual Studio, ale nie jest już opracowywane active. Użyj programu LINQ to SQL podczas obsługi starszych aplikacji, który już jest używany lub w prostej aplikacji, użyj programu SQL Server, które nie wymagają mapowania wielu tabel. Ogólnie rzecz biorąc nowe aplikacje powinny używać programu Entity Framework, gdy wymagana jest warstwa Mapowania obiektowo relacyjny.

 W programie Visual Studio, tworzyć LINQ do klas SQL, które reprezentują tabele SQL przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Ma dwa różne obszary, na jego powierzchnię projektową: jednostki w okienku po lewej stronie, a okienko metod po prawej stronie. W okienku jednostek jest główna powierzchnia projektowa wyświetlającą klas jednostek, skojarzeń i hierarchii dziedziczenia. Okienko metod jest powierzchni projektu, który wyświetla <xref:System.Data.Linq.DataContext> metod, które są mapowane do procedur przechowywanych i funkcji.

 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Udostępnia powierzchnia projektowania wizualnego służące do tworzenia [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) klasy encji i skojarzeń (relacji), które są oparte na obiektach w bazie danych. Innymi słowy [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] służy do tworzenia modelu obiektów w aplikacji, która mapuje do obiektów w bazie danych. Polecenie to generuje także silnie typizowanego <xref:System.Data.Linq.DataContext> używany do wysyłania i odbierania danych między klasami jednostki i bazy danych. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Również zapewnia funkcje procedurom składowanym w mapie i funkcje <xref:System.Data.Linq.DataContext> metody zwracający dane i wypełnianie klas jednostek. Na koniec [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] zapewnia możliwość projektowania relacje dziedziczenia między klasami jednostki.

## <a name="opening-the-or-designer"></a>Otwieranie Relational Designer
 Aby dodać LINQ w modelu entity SQL do projektu, wybierz **projektu &#124; Dodaj nowy element** , a następnie wybierz **klasy LINQ do SQL** z listy elementów projektu:

 ![Klasy LINQ do SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata klasy LINQ do SQL")

 Visual Studio tworzy plik dbml i dodaje go do rozwiązania. Jest to plik mapowania XML i jego pliki kod pokrewny.

 ![LINQ to SQL klas w Eksploratorze rozwiązań](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL klas w Eksploratorze rozwiązań")

 Po wybraniu pliku dbml, Visual Studio wyświetla na powierzchnię Projektanta obiektów relacyjnych, która umożliwia wizualne Tworzenie modelu. Poniższa ilustracja przedstawia projektanta po tabele Northwind Customers i Orders mają zostało przeciągnięte z poziomu Eksploratora serwera. Należy pamiętać, relacji między tabelami.

 ![LINQ do SQL projektanta](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ do SQL projektanta")

> [!IMPORTANT]
>  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Jest mapowania relacyjnych prostego obiektu, ponieważ obsługuje on tylko relacji mapowanie 1:1. Innymi słowy klasa jednostka może mieć tylko relacji mapowanie 1:1 z tabeli bazy danych lub widoku. Mapowanie złożonych, takie jak mapowanie klasę jednostki do tabeli dołączonym do nie jest obsługiwana; na użytek złożonych mapowania Entity Framework. Ponadto projektanta jest generator kodu jednokierunkowe. Oznacza to, że tylko zmiany wprowadzone do powierzchni projektanta są odzwierciedlane w pliku kodu. Ręczne zmiany w pliku kodu nie są odzwierciedlane w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Wszelkie zmiany wprowadzone ręcznie w pliku kodu zostaną zastąpione, gdy projektant jest zapisywana i wygenerowania kodu. Aby uzyskać informacje o tym, jak dodać kod użytkownika i rozszerzać klasy generowane przez [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], zobacz [jak: Rozszerzanie kodu wygenerowanego przez projektanta O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Tworzenie i konfigurowanie kontekstu danych
 Po dodaniu **klasy LINQ do SQL** elementu do projektu i Otwórz [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], powierzchni projektowej pusty reprezentuje pusty <xref:System.Data.Linq.DataContext> gotowe do skonfigurowania. <xref:System.Data.Linq.DataContext> jest skonfigurowany z informacjami o połączeniu, dostarczone przez pierwszy element, który jest zostało przeciągnięte na powierzchnię projektu... W związku z tym <xref:System.Data.Linq.DataContext> jest konfigurowana przy użyciu informacji o połączeniu z pierwszego elementu na powierzchni projektowej. Aby uzyskać więcej informacji na temat <xref:System.Data.Linq.DataContext> , zobacz klasę [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Tworzenie klas jednostek mapowane na bazę danych, tabele i widoki
 Można utworzyć klasy jednostek zamapowanych na tabele i widoki, przeciągając bazy danych tabel i widoków z **Eksploratora serwera**/**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Jak wskazano w poprzedniej sekcji <xref:System.Data.Linq.DataContext> jest skonfigurowany z informacjami o połączeniu, dostarczone przez pierwszy element, który jest zostało przeciągnięte na powierzchnię projektu. Jeśli kolejne elementu, który używa innego połączenia jest dodawany do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], można zmienić połączenia dla <xref:System.Data.Linq.DataContext>. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie typu LINQ do klas SQL zamapowanych na tabele i widoki (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Tworzenie metod DataContext, które wywołują procedur przechowywanych i funkcji
 Możesz utworzyć <xref:System.Data.Linq.DataContext> metody, które wywołują (są mapowane na) procedur składowanych i funkcji, przeciągając je z **Eksploratora serwera**/**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Procedury składowane i funkcje, które są dodawane do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jako metody <xref:System.Data.Linq.DataContext>.

> [!NOTE]
>  Podczas przeciągania procedur przechowywanych i funkcji z **Eksploratora serwera**/**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> metoda różni się w zależności od tego, gdzie można upuścić elementu. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurowanie DataContext zapisują dane pomiędzy klasami jednostki i bazy danych za pomocą procedur składowanych
 Jak wspomniano wcześniej, możesz utworzyć <xref:System.Data.Linq.DataContext> metody, które wywołują procedur przechowywanych i funkcji. Ponadto można także przypisać procedury składowane, które mogą być używane dla domyślnej [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zachowania w czasie wykonywania, który wykonuje wstawiania, aktualizacji i usuwa. Aby uzyskać więcej informacji, zobacz [jak: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Dziedziczenie i Relational Designer
 Inne obiekty, takie jak [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasy można użyć dziedziczenia i pochodzić z innych klas. W bazie danych relacje dziedziczenia są tworzone na kilka sposobów. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Obsługuje dziedziczenia pojedynczej tabeli, co jest często stosowana w systemach relacyjnych. Aby uzyskać więcej informacji, zobacz [jak: Skonfigurować dziedziczenie za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Zapytania LINQ to SQL
 Klas jednostek utworzonych przez [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] są przeznaczone do użytku z programem [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Aby uzyskać więcej informacji, zobacz [jak: Zapytanie dotyczące informacji](http://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oddzielanie DataContext wygenerowany i kod klasy jednostek w różnych obszarach nazw
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Zapewnia **Namespace kontekstu** i **Namespace jednostki** właściwości <xref:System.Data.Linq.DataContext>. Te właściwości określają, jakie przestrzeni nazw <xref:System.Data.Linq.DataContext> i kodu klasy jednostki jest generowany na. Właściwości te są domyślnie pusta i <xref:System.Data.Linq.DataContext> i klas jednostek są generowane w przestrzeni nazw aplikacji. Aby wygenerować kod w przestrzeni nazw, innym niż przestrzeń nazw aplikacji, wprowadź wartość w **Namespace kontekstu** i/lub **Namespace jednostki** właściwości.

## <a name="in-this-section"></a>W tej sekcji
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) opisano zagadnienia, które <xref:System.Data.Linq.DataContext> metody są i jak je utworzyć.

 [Dane klasy dziedziczenia (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md) omówienie pojęć dotyczących dziedziczenia pojedynczej tabeli i jak jest zaimplementowana w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Instrukcje: Tworzenie typu LINQ do klas SQL zamapowanych na tabele i widoki (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) zawiera opis sposobu tworzenia klas jednostek, które są mapowane do tabel i widoków w bazie danych.

 [Instrukcje: Utwórz skojarzenie (Relacja) między klasy LINQ do SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) w tym artykule opisano sposób tworzenia relacji między [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klas jednostek.

 [Instrukcje: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) w tym artykule opisano sposób tworzenia <xref:System.Data.Linq.DataContext> metody, które Uruchom procedurami składowanymi i funkcjami, gdy zostaną wywołane.

 [Instrukcje: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) w tym artykule opisano sposób konfigurowania <xref:System.Data.Linq.DataContext> do procedur składowanych zapisywania danych z obiektu klasy z powrotem do bazy danych.

 [Instrukcje: Zmień zwracany typ metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) w tym artykule opisano sposób ustawiania zwracany typ <xref:System.Data.Linq.DataContext> metody na typ klasy jednostki lub typ wygenerowany automatycznie utworzone przez projektanta O/R.

 [Instrukcje: Dodawanie walidacji do klas jednostek](../data-tools/how-to-add-validation-to-entity-classes.md) w tym artykule opisano sposób generowania metod częściowych, które umożliwiają dodawanie kodu podczas zmiany właściwości i aktualizacje klasy jednostka.

 [Instrukcje: Włącz pluralizacja włączać i wyłączać (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) opisano, jak włączyć i wyłączyć automatyczne zmienianie nazw klas, które są dodawane do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Instrukcje: Skonfigurować dziedziczenie za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) w tym artykule opisano sposób konfigurowania klas jednostek za pomocą dziedziczenia pojedynczej tabeli z [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Instrukcje: Rozszerzanie kod wygenerowany przez projektanta O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) opisano, jak i gdzie dodać kod, który nie zostanie nadpisany podczas zmiany obiektów w Projektancie obiektów relacyjnych ponownie wygenerować kod.

 [Przewodnik: Tworzenie klasy LINQ do SQL przez dziedziczenie za pomocą pojedynczej tabeli (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) zawiera instrukcje krok po kroku dotyczące konfigurowania klas jednostek za pomocą dziedziczenia pojedynczej tabeli z [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Przewodnik: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) zawiera instrukcje krok po kroku dotyczące konfigurowania <xref:System.Data.Linq.DataContext> do procedur składowanych zapisywania danych z obiektu klasy z powrotem do bazy danych.

## <a name="reference-content"></a>Odwołania do zawartości
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Zobacz też
 [Narzędzia Visual Studio data tools dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [— często zadawane pytania](http://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

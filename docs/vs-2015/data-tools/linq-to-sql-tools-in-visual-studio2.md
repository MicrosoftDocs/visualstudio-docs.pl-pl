---
title: Narzędzia LINQ to SQL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 470cfabd54fa5f2b92001a635477c60d45fac538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651515"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Narzędzia LINQ to SQL Tools w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL była technologią mapowania pierwszej Object-relacyjną wydaną przez firmę Microsoft. Dobrze sprawdza się w scenariuszach podstawowych i nadal jest obsługiwane w programie Visual Studio, ale nie jest już w fazie aktywnej. Użyj LINQ to SQL w przypadku zachowania starszej aplikacji, która już korzysta z niej lub w prostych aplikacjach, które używają SQL Server i nie wymaga mapowania wielotabelowego. Ogólnie rzecz biorąc, nowe aplikacje powinny używać Entity Framework, gdy wymagana jest warstwa mapowania obiektowo-relacyjnego.

 W programie Visual Studio tworzysz klasy LINQ to SQL reprezentujące tabele SQL przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Ma dwa różne obszary na powierzchni projektowej: okienko jednostki po lewej stronie i okienko metody po prawej stronie. Okienko jednostki jest główną powierzchnią projektową, która wyświetla klasy jednostki, skojarzenia i hierarchie dziedziczenia. Okienko metody jest powierzchnią projektową, która wyświetla <xref:System.Data.Linq.DataContext> metody, które są mapowane na procedury składowane i funkcje.

 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) Udostępnia powierzchnię projektowania wizualizacji na potrzeby tworzenia klas jednostek [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) i skojarzeń (relacji), które są oparte na obiektach w bazie danych. Innymi słowy, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jest używany do tworzenia modelu obiektów w aplikacji, która mapuje do obiektów w bazie danych. Generuje również silnie wpisaną wartość <xref:System.Data.Linq.DataContext> , która jest używana do wysyłania i odbierania danych między klasami jednostek a bazą danych. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Udostępnia również funkcje do mapowania procedur składowanych i funkcji w celu <xref:System.Data.Linq.DataContext> zwracania danych i wypełniania klas jednostek. Na koniec [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] zapewnia możliwość projektowania relacji dziedziczenia między klasami jednostek.

## <a name="opening-the-or-designer"></a>Otwieranie projektanta O/R
 Aby dodać LINQ to SQL model jednostki do projektu, wybierz pozycję **projekt &#124; Dodaj nowy element** , a następnie wybierz  **LINQ to SQL klasy** z listy elementów projektu:

 ![Klasy LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata klasy LINQ to SQL")

 Program Visual Studio tworzy plik. dbml i dodaje go do rozwiązania. Jest to plik mapowania XML i powiązane z nim pliki kodu.

 ![Klasy LINQ to SQL w Eksplorator rozwiązań](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "klasy raddata LINQ to SQL w Eksplorator rozwiązań")

 Po wybraniu pliku. dbml program Visual Studio wyświetli powierzchnię projektanta O/R, która umożliwia wizualne tworzenie modelu. Na poniższej ilustracji przedstawiono projektanta po przeciągnięciu tabel klienci i zamówienia Northwind z Eksplorator serwera. Zwróć uwagę na relacje między tabelami.

 ![Projektant LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "Projektant LINQ to SQL raddata")

> [!IMPORTANT]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Jest prostym mapowaniem relacyjnym obiektów, ponieważ obsługuje tylko 1:1 relacji mapowania. Innymi słowy, Klasa jednostki może mieć tylko skojarzenie mapowania 1:1 z tabelą lub widokiem bazy danych. Mapowanie złożone, takie jak mapowanie klasy jednostki do sprzężonej tabeli, nie jest obsługiwane. Użyj Entity Framework na potrzeby mapowania złożonego. Ponadto Projektant jest jednokierunkowym generatorem kodu. Oznacza to, że tylko zmiany wprowadzane do powierzchni projektanta są uwzględniane w pliku kodu. Ręczne zmiany w pliku kodu nie są uwzględniane w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Wszelkie zmiany wprowadzane ręcznie w pliku kodu są zastępowane podczas zapisywania projektanta i ponownego generowania kodu. Aby uzyskać informacje na temat dodawania kodu użytkownika i zwiększania klas generowanych przez [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , zobacz [How to: rozszerzając kod wygenerowany przez projektanta O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Tworzenie i Konfigurowanie elementu DataContext
 Po dodaniu elementu **LINQ to SQL klas** do projektu i otwarciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , pustej powierzchni projektowej reprezentuje pustą, <xref:System.Data.Linq.DataContext> gotową do skonfigurowania. <xref:System.Data.Linq.DataContext>program jest skonfigurowany z informacjami o połączeniu udostępnianymi przez pierwszy element, który jest przeciągany na powierzchnię projektu. W związku z tym, <xref:System.Data.Linq.DataContext> jest skonfigurowany przy użyciu informacji o połączeniu z pierwszego elementu upuszczanych na powierzchnię projektu. Aby uzyskać więcej informacji na temat <xref:System.Data.Linq.DataContext> klasy, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Tworzenie klas jednostek, które są mapowane na tabele i widoki bazy danych
 Można tworzyć klasy jednostek mapowane na tabele i widoki, przeciągając tabele i widoki bazy danych z **Eksplorator serwera** / **Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Jak wskazano w poprzedniej sekcji, <xref:System.Data.Linq.DataContext> skonfigurowano informacje o połączeniu z użyciem pierwszego elementu, który jest przeciągany na powierzchnię projektu. Jeśli kolejny element, który używa innego połączenia, zostanie dodany do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , możesz zmienić połączenie dla <xref:System.Data.Linq.DataContext> . Aby uzyskać więcej informacji, zobacz [How to: Create LINQ to SQL Classes zmapowane do tabel i widoków (Projektant O/R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Tworzenie metod elementu DataContext, które wywołują procedury składowane i funkcje
 Można tworzyć <xref:System.Data.Linq.DataContext> metody, które wywołują (są mapowane do) procedury składowane i funkcje, przeciągając je z **Eksplorator serwera** / **Eksplorator bazy danych** do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Procedury składowane i funkcje są dodawane do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] metod AS <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> Gdy przeciągniesz procedury składowane i funkcje z **Eksplorator serwera** / **Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , zwracany typ wygenerowanej <xref:System.Data.Linq.DataContext> metody różni się w zależności od tego, gdzie porzucasz element. Aby uzyskać więcej informacji, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurowanie elementu DataContext do korzystania z procedur składowanych w celu zapisywania danych między klasami jednostek a bazą danych
 Jak wspomniano wcześniej, można utworzyć <xref:System.Data.Linq.DataContext> metody, które wywołują procedury składowane i funkcje. Ponadto można również przypisać procedury składowane, które mogą być używane dla domyślnego [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zachowania środowiska uruchomieniowego, które wykonuje operacje wstawiania, aktualizacji i usuwania. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Dziedziczenie i Projektant O/R
 Podobnie jak w przypadku innych obiektów, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasy mogą używać dziedziczenia i pochodzić z innych klas. W bazie danych relacje dziedziczenia są tworzone na kilka sposobów. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Program obsługuje koncepcję dziedziczenia pojedynczej tabeli, ponieważ jest ona często implementowana w systemach relacyjnych. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie dziedziczenia przy użyciu narzędzia O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Zapytania LINQ to SQL
 Klasy jednostek utworzone przez program [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] są przeznaczone do użycia z [LINQ (zapytanie zintegrowane z językiem)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Aby uzyskać więcej informacji, zobacz [jak: zapytanie o informacje](https://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Rozdzielenie wygenerowanego elementu DataContext i kodu klasy jednostki na różne przestrzenie nazw
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Zapewnia **przestrzeń nazw kontekstu** i właściwości **przestrzeni nazw jednostki** w obiekcie <xref:System.Data.Linq.DataContext> . Te właściwości określają, w której przestrzeni nazw <xref:System.Data.Linq.DataContext> jest generowany kod klasy jednostki i. Domyślnie te właściwości są puste i <xref:System.Data.Linq.DataContext> klasy jednostek są generowane w przestrzeni nazw aplikacji. Aby wygenerować kod w przestrzeni nazw innej niż przestrzeń nazw aplikacji, wprowadź wartość w polu **przestrzeń nazw kontekstu** i/lub właściwości **przestrzeni nazw jednostki** .

## <a name="in-this-section"></a>W tej sekcji
 [Metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md) Wyjaśnia <xref:System.Data.Linq.DataContext> , jakie metody są i jak je utworzyć.

 [Dziedziczenie klasy danych (Projektant O/R)](../data-tools/data-class-inheritance-o-r-designer.md) Opisuje koncepcję dziedziczenia pojedynczej tabeli i sposób jej implementacji w programie [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Instrukcje: tworzenie klas LINQ to SQL mapowanych na tabele i widoki (Projektant O/R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) Opisuje sposób tworzenia klas jednostek, które są mapowane na tabele i widoki w bazie danych.

 [Instrukcje: Tworzenie skojarzenia (relacji) między klasami LINQ to SQL (Projektant O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) Opisuje sposób tworzenia relacji między [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasami jednostek.

 [Instrukcje: Tworzenie metod DataContext mapowanych na procedury składowane i funkcje (Projektant O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) Opisuje sposób tworzenia <xref:System.Data.Linq.DataContext> metod, które uruchamiają procedury składowane lub funkcje, gdy są wywoływane.

 [Instrukcje: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) Opisuje sposób konfigurowania programu <xref:System.Data.Linq.DataContext> do korzystania z procedur składowanych podczas zapisywania danych z klas jednostek z powrotem do bazy danych.

 [Instrukcje: zmiana zwracanego typu metody DataContext (Projektant O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) Opisuje sposób ustawiania zwracanego typu <xref:System.Data.Linq.DataContext> metody jako typu klasy jednostki lub automatycznie generowanego typu utworzonego przez projektanta O/R.

 [Instrukcje: Dodawanie walidacji do klas jednostek](../data-tools/how-to-add-validation-to-entity-classes.md) Opisuje sposób generowania metod częściowych, które umożliwiają dodawanie kodu podczas zmian właściwości i aktualizacji klas jednostek.

 [Instrukcje: Włączanie i wyłączanie pluralizacja (Projektant O/R)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) Opisuje sposób włączania i wyłączania automatycznego zmieniania nazw klas, które są dodawane do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Instrukcje: Konfigurowanie dziedziczenia przy użyciu projektanta o/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Opisuje sposób konfigurowania klas jednostek przy użyciu dziedziczenia pojedynczej tabeli przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Instrukcje: zwiększanie kodu wygenerowanego przez projektanta O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) W tym artykule opisano, jak i gdzie dodać kod, który nie zostanie nadpisany, gdy zmiany w obiektach w Projektancie O/R ponownie generują kod.

 [Przewodnik: tworzenie klas LINQ to SQL przy użyciu dziedziczenia pojedynczej tabeli (Projektant O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) Zawiera instrukcje krok po kroku dotyczące konfigurowania klas jednostek przy użyciu dziedziczenia pojedynczej tabeli przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Przewodnik: Dostosowywanie zachowania INSERT, Update i DELETE klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) Zawiera instrukcje krok po kroku dotyczące konfigurowania programu <xref:System.Data.Linq.DataContext> do korzystania z procedur składowanych podczas zapisywania danych z klas jednostek z powrotem do bazy danych.

## <a name="reference-content"></a>Zawartość referencyjna
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Zobacz też
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) — [często zadawane pytania](https://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [uzyskiwania dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

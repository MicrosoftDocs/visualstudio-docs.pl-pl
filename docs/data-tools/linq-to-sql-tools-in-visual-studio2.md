---
title: Omówienie narzędzia LINQ to SQL O/R Designer
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 55f6fa2ad9eda2d701563d1fa99c76f5cd5c7c1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282010"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Narzędzia LINQ to SQL w programie Visual Studio

LINQ to SQL była technologią mapowania pierwszej Object-relacyjną wydaną przez firmę Microsoft. Dobrze działa w podstawowych scenariuszach i nadal jest obsługiwane w programie Visual Studio, ale nie jest już w trakcie aktywnego programowania. Użyj LINQ to SQL w przypadku zachowania starszej aplikacji, która już jej używa, lub w prostych aplikacjach, które używają SQL Server i nie wymagają mapowania wielotabelowego. Ogólnie rzecz biorąc, nowe aplikacje powinny używać Entity Framework, gdy wymagana jest warstwa mapowania obiektowo-relacyjnego.

## <a name="install-the-linq-to-sql-tools"></a>Instalowanie narzędzi LINQ to SQL

W programie Visual Studio tworzysz klasy LINQ to SQL reprezentujące tabele SQL przy użyciu **Object Relational Designer** (**Projektant O/R**). Projektant O/R jest interfejsem użytkownika do edycji plików DBML. Edytowanie plików. dbml za pomocą powierzchni projektanta wymaga narzędzi LINQ to SQL, które nie są instalowane domyślnie w ramach żadnego z obciążeń programu Visual Studio.

Aby zainstalować narzędzia LINQ to SQL, uruchom Instalatora programu Visual Studio, wybierz **Modyfikuj**, a następnie wybierz kartę **poszczególne składniki** , a następnie wybierz pozycję **Narzędzia LINQ to SQL** w kategorii **Narzędzia kodu** .

## <a name="what-is-the-or-designer"></a>Co to jest Projektant O/R

**Projektant o/R** ma dwa oddzielne obszary na swojej powierzchni projektowej: okienko jednostki po lewej stronie i okienko metody po prawej stronie. Okienko jednostki jest główną powierzchnią projektową, która wyświetla klasy jednostki, skojarzenia i hierarchie dziedziczenia. Okienko metody jest powierzchnią projektową, która wyświetla <xref:System.Data.Linq.DataContext> metody, które są mapowane na procedury składowane i funkcje.

**Projektant O/R** udostępnia powierzchnię projektowania wizualizacji na potrzeby tworzenia klas jednostek [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) i skojarzeń (relacji) opartych na obiektach w bazie danych. Innymi słowy, **Projektant o/R** tworzy model obiektów w aplikacji, która mapuje do obiektów w bazie danych. Generuje również silnie wpisaną wartość <xref:System.Data.Linq.DataContext> , która wysyła i odbiera dane między klasami jednostki a bazą danych. **Projektant O/R** udostępnia również funkcje do mapowania procedur składowanych i funkcji w celu <xref:System.Data.Linq.DataContext> zwracania danych i wypełniania klas jednostek. Na koniec **Projektant o/R** zapewnia możliwość projektowania relacji dziedziczenia między klasami jednostek.

## <a name="open-the-or-designer"></a>Otwórz projektanta O/R

Aby dodać LINQ to SQL model jednostki do projektu, wybierz pozycję **projekt**  >  **Dodaj nowy element**, a następnie wybierz **klasy LINQ to SQL** z listy elementów projektu:

![Klasy LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Program Visual Studio tworzy plik *. dbml* i dodaje go do rozwiązania. Jest to plik mapowania XML i powiązane z nim pliki kodu.

![Klasy LINQ to SQL w Eksplorator rozwiązań](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Po wybraniu pliku *. dbml* program Visual Studio wyświetli powierzchnię **projektanta o/R** , która umożliwia wizualne tworzenie modelu. Na poniższej ilustracji przedstawiono projektanta po `Customers` `Orders` przeciągnięciu tabeli Northwind i tabel z **Eksplorator serwera**. Zwróć uwagę na relacje między tabelami.

![Projektant LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **Projektant o/R** to proste mapowanie relacyjne obiektów, ponieważ obsługuje tylko 1:1 relacji mapowania. Innymi słowy, Klasa jednostki może mieć tylko skojarzenie mapowania 1:1 z tabelą lub widokiem bazy danych. Mapowanie złożone, takie jak mapowanie klasy jednostki do sprzężonej tabeli, nie jest obsługiwane. Użyj Entity Framework na potrzeby mapowania złożonego. Ponadto Projektant jest jednokierunkowym generatorem kodu. Oznacza to, że tylko zmiany wprowadzane do powierzchni projektanta są uwzględniane w pliku kodu. Ręczne wprowadzanie zmian w pliku kodu nie są odzwierciedlone w **projektancie o/R**. Wszelkie zmiany wprowadzane ręcznie w pliku kodu są zastępowane podczas zapisywania projektanta i ponownego generowania kodu. Aby uzyskać informacje na temat dodawania kodu użytkownika i zwiększania klas generowanych przez **projektanta o/r**, zobacz [How to: rozszerzając kod wygenerowany przez projektanta o/r](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Tworzenie i Konfigurowanie elementu DataContext

Po dodaniu elementu **LINQ to SQL klas** do projektu i otwarciu **projektanta O/R**, pustej powierzchni projektowej reprezentuje pustą, <xref:System.Data.Linq.DataContext> gotową do skonfigurowania. <xref:System.Data.Linq.DataContext>program jest skonfigurowany z informacjami o połączeniu udostępnianymi przez pierwszy element, który jest przeciągany na powierzchnię projektu. W związku z tym, <xref:System.Data.Linq.DataContext> jest skonfigurowany przy użyciu informacji o połączeniu z pierwszego elementu upuszczanych na powierzchnię projektu. Aby uzyskać więcej informacji na temat <xref:System.Data.Linq.DataContext> klasy, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Tworzenie klas jednostek, które są mapowane na tabele i widoki bazy danych

Można tworzyć klasy jednostek zamapowane na tabele i widoki, przeciągając tabele i widoki bazy danych z **Eksplorator serwera** lub **Eksplorator bazy danych** do **projektanta O/R**. Jak wskazano w poprzedniej sekcji, <xref:System.Data.Linq.DataContext> skonfigurowano informacje o połączeniu z użyciem pierwszego elementu, który jest przeciągany na powierzchnię projektu. Jeśli kolejny element, który używa innego połączenia, zostanie dodany do **projektanta O/R**, można zmienić połączenie dla <xref:System.Data.Linq.DataContext> . Aby uzyskać więcej informacji, zobacz [How to: Create LINQ to SQL Classes zmapowane do tabel i widoków (Projektant O/R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Twórz metody DataContext, które wywołują procedury składowane i funkcje

Można tworzyć <xref:System.Data.Linq.DataContext> metody, które wywołują (są mapowane do) procedury składowane i funkcje, przeciągając je z **Eksplorator serwera** lub **Eksplorator bazy danych** do **projektanta O/R**. Procedury składowane i funkcje są dodawane do **projektanta O/R** jako metody <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> Gdy przeciągasz procedury składowane i funkcje z **Eksplorator serwera** lub **Eksplorator bazy danych** do **projektanta O/R**, zwracany typ wygenerowanej <xref:System.Data.Linq.DataContext> metody różni się w zależności od miejsca, w którym element zostanie porzucany. Aby uzyskać więcej informacji, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Skonfiguruj element DataContext, aby używać procedur składowanych do zapisywania danych między klasami jednostek a bazą danych

Jak wspomniano wcześniej, można utworzyć <xref:System.Data.Linq.DataContext> metody, które wywołują procedury składowane i funkcje. Ponadto można również przypisać procedury składowane, które są używane dla domyślnego LINQ to SQL zachowanie w czasie wykonywania, które wykonuje operacje wstawiania, aktualizacji i usuwania. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Dziedziczenie i Projektant O/R

Podobnie jak w przypadku innych obiektów, klasy LINQ to SQL mogą używać dziedziczenia i pochodzić z innych klas. W bazie danych relacje dziedziczenia są tworzone na kilka sposobów. **Projektant O/R** obsługuje koncepcję dziedziczenia pojedynczej tabeli, ponieważ jest ona często zaimplementowana w systemach relacyjnych. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie dziedziczenia przy użyciu narzędzia O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Zapytania LINQ to SQL

Klasy jednostek utworzone przez **projektanta O/R** są przeznaczone do użycia z [zapytaniem Integrated Language (LINQ)](/dotnet/csharp/linq/). Aby uzyskać więcej informacji, zobacz [jak: zapytanie o informacje](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oddzielanie wygenerowanego elementu DataContext i kodu klasy jednostki do różnych przestrzeni nazw

**Projektant O/R** zapewnia **przestrzeń nazw kontekstu** i właściwości **przestrzeni nazw jednostki** na <xref:System.Data.Linq.DataContext> . Te właściwości określają, w której przestrzeni nazw <xref:System.Data.Linq.DataContext> jest generowany kod klasy jednostki i. Domyślnie te właściwości są puste i <xref:System.Data.Linq.DataContext> klasy jednostek są generowane w przestrzeni nazw aplikacji. Aby wygenerować kod w przestrzeni nazw innej niż przestrzeń nazw aplikacji, wprowadź wartość w polu **przestrzeń nazw kontekstu** i/lub właściwości **przestrzeni nazw jednostki** .

## <a name="reference-content"></a>Zawartość referencyjna

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Zobacz też

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Często zadawane pytania (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)

---
title: 'Instrukcje: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (Projektant O-R) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 957c1fe49d222a691160eadc4b2cf08f8a20a65a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782066"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Instrukcje: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Procedury składowane, które mogą być dodawane do Projektanta obiektów relacyjnych lub wykonywane co typowe <xref:System.Data.Linq.DataContext> metody. One może również zastąpić to ustawienie domyślne [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zachowania w czasie wykonywania, który wykonuje wstawiania, aktualizacji i usuwa podczas zmiany są zapisywane z klas jednostek bazy danych (na przykład w przypadku, gdy wywołanie <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody).  
  
> [!NOTE]
>  Jeśli Twoja procedura składowana ma zwracać wartości, które muszą zostać odesłany do klienta (na przykład wartości obliczane w procedurze składowanej), utworzyć parametry wyjściowe w przechowywanych procedur. Jeśli nie możesz użyć parametrów wyjściowych, zapisu przesłonięcia implementację metody częściowej, zamiast polegania na generowany przez projektanta O/R. Wartości wygenerowanych w bazie danych elementów członkowskich muszą być podane odpowiednie wartości po pomyślnym ukończeniu operacji WSTAWIANIA lub aktualizacji. Aby uzyskać więcej informacji, zobacz [obowiązki dewelopera w zastępowanie domyślne zachowanie](http://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] uchwyty wygenerowanych w bazie danych wartości automatycznie tożsamości (automatycznego przyrostu), rowguidcol (identyfikator GUID generowany przez bazy danych) i kolumn sygnatur czasowych. Wartości generowanych przez bazę danych w innych typów kolumn spowoduje nieoczekiwane wartości null. Aby zwrócić wartości wygenerowanych w bazie danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> do `true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> do jednej z następujących czynności: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync>, lub <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Konfigurowanie zachowania aktualizacji klasę jednostki  
 Domyślnie, logika aktualizacji bazy danych (operacje wstawiania, aktualizacji i usunięć) za pomocą zmian wprowadzonych do danych w [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klas jednostek są dostarczane przez [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] środowiska uruchomieniowego. Środowisko uruchomieniowe tworzy domyślne polecenia Insert, Update i Delete, które opierają się na schemat tabeli (kolumny i informacje o kluczu podstawowym). Gdy zachowanie domyślne jest niepożądany, możesz skonfigurować zachowanie aktualizacji, przypisując określonych procedur składowanych do wykonania niezbędnych operacji wstawiania, aktualizacji, i usuwa wymagane do manipulowania danymi w tabeli. Ponadto można to zrobić, jeśli domyślne zachowanie nie jest generowany, na przykład, gdy Twoje klas jednostek mapy do widoków. Na koniec można zastąpić domyślne zachowanie aktualizacji, gdy baza danych wymaga dostępu do tabel za pomocą procedur składowanych.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Aby przypisać procedur składowanych, aby zastąpić domyślne zachowanie klasę jednostki  
  
1.  Otwórz **LINQ to SQL** pliku w projektancie. (Kliknij dwukrotnie plik dbml w **Eksploratora rozwiązań**.)  
  
2.  W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł **procedur składowanych** i Znajdź procedur przechowywanych, które chcesz użyć dla Insert, Update, i/lub polecenia Delete klasy jednostki.  
  
3.  Przeciągnij procedurę składowaną do Projektanta obiektów relacyjnych.  
  
     Procedura składowana jest dodawany do okienka metod jako <xref:System.Data.Linq.DataContext> metody. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Wybierz klasę jednostki, dla którego chcesz użyć procedury składowanej do wykonywania aktualizacji.  
  
5.  W **właściwości** okna, wybierz polecenie, aby zastąpić (**Wstaw**, **aktualizacji**, lub **Usuń**).  
  
6.  Kliknij przycisk wielokropka (...) obok wyrazy **Użyj środowiska uruchomieniowego** otworzyć **Konfigurowanie zachowania** okno dialogowe.  
  
7.  Wybierz **dostosować**.  
  
8.  Wybierz odpowiednią procedurę składowaną w **Dostosuj** listy.  
  
9. Sprawdź listę **argumenty metody** i **właściwości klasy** do sprawdzenia, czy **argumenty metody** mapy do odpowiedniego **właściwości klasy**. Mapowanie oryginalnego argumenty metody (Original_*ArgumentName*) do oryginalne właściwości (*PropertyName* (oryginalne)) dla polecenia Update i Delete.  
  
    > [!NOTE]
    >  Domyślnie argumenty metody są mapowane na właściwości klasy, gdy nazwy są zgodne. Zmieniona właściwość, których nazwy nie są już zgodne między tabelą i Klasa jednostki, trzeba wybrać właściwość odpowiednik klasy do mapowania na, jeśli projektant nie może określić poprawne mapowania.  
  
10. Kliknij przycisk **OK** lub **zastosować**.  
  
    > [!NOTE]
    >  Można kontynuować, skonfiguruj zachowanie dla każdej kombinacji klasy/zachowania, tak długo, jak możesz kliknąć pozycję **Zastosuj** po wprowadzeniu każdej zmiany. Jeśli zmienisz klasy lub zachowania przed kliknięciem przycisku **Zastosuj**, okno dialogowe ostrzeżenia, zapewniając pojawi się możliwości, aby zastosować zmiany.  
  
     Aby przywrócić za pomocą domyślnej logiki czasu wykonywania aktualizacji, kliknij wielokropek obok Insert, Update, lub Usuń polecenie w **właściwości** okna, a następnie wybierz **korzystania ze środowiska uruchomieniowego** w  **Konfigurowanie zachowania** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Przewodnik: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Operacje wstawiania, aktualizowania i usuwania](http://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)

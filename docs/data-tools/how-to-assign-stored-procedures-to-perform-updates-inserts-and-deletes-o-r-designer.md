---
title: Użyj procedur składowanych w LINQ to SQL, aby zaktualizować dane (Projektant O/R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8028171cf3255de3484bb89a374bfc22a2625b1a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586552"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Instrukcje: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (Projektant O/R)

Procedury składowane można dodać do **projektanta o/R** i wykonać jako typowe metody <xref:System.Data.Linq.DataContext>. Mogą one również służyć do przesłonięcia domyślnego LINQ to SQL zachowanie w czasie wykonywania, które wykonuje operacje wstawiania, aktualizacji i usuwania, gdy zmiany są zapisywane z klas jednostek do bazy danych (na przykład podczas wywoływania metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A>).

> [!NOTE]
> Jeśli procedura składowana zwraca wartości, które muszą być wysłane z powrotem do klienta (na przykład wartości obliczone w procedurze składowanej), utwórz parametry wyjściowe w procedurach składowanych. Jeśli nie możesz użyć parametrów wyjściowych, napisz implementację metody częściowej zamiast zastępować zastąpień generowanych przez projektanta O/R. Elementy członkowskie zamapowane do wartości generowanych przez bazę danych muszą być ustawione na odpowiednie wartości po pomyślnym zakończeniu operacji wstawiania lub aktualizowania. Aby uzyskać więcej informacji, zobacz [obowiązki dewelopera w celu przesłania domyślnego zachowania](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL automatycznie obsługuje wartości generowane przez bazę danych dla tożsamości (automatyczne zwiększanie), ROWGUIDCOL (identyfikator GUID generowany przez bazę danych) i kolumny sygnatur czasowych. Wartości wygenerowane przez bazę danych w innych typach kolumn nieoczekiwanie spowodują wartość null. Aby zwrócić wartości generowane przez bazę danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> na **true** i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> do jednego z następujących: [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)lub [AutoSync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Skonfiguruj zachowanie aktualizacji klasy jednostki

Domyślnie logika do aktualizowania bazy danych (wstawia, aktualizuje i usuwa) ze zmianami, które zostały wprowadzone do danych w LINQ to SQL klas jednostek, jest zapewniana przez środowisko uruchomieniowe LINQ to SQL. Środowisko uruchomieniowe tworzy domyślne polecenia INSERT, UPDATE i DELETE, które są oparte na schemacie tabeli (informacje o kolumnie i kluczu podstawowym). Gdy zachowanie domyślne nie jest wymagane, można skonfigurować zachowanie aktualizacji, przypisując określone procedury składowane do wykonywania niezbędnych operacji wstawiania, aktualizacji i usuwania wymaganych do manipulowania danymi w tabeli. Można to również zrobić, gdy domyślne zachowanie nie jest generowane, na przykład gdy klasy jednostek mapują się na widoki. Na koniec można zastąpić domyślne zachowanie aktualizacji, gdy baza danych wymaga dostępu do tabeli za pomocą procedur składowanych.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Aby przypisać procedury składowane w celu zastąpienia domyślnego zachowania klasy jednostki

1. Otwórz plik **LINQ to SQL** w projektancie. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań**).

2. W **Eksplorator serwera** lub **Eksplorator bazy danych**rozwiń węzeł **procedury składowane** i zlokalizuj procedury składowane, których chcesz użyć dla poleceń INSERT, Update i/lub DELETE klasy Entity.

3. Przeciągnij procedurę składowaną do **projektanta O/R**.

     Procedura składowana jest dodawana do okienka metod jako metoda <xref:System.Data.Linq.DataContext>. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wybierz klasę jednostki, dla której chcesz użyć procedury składowanej do przeprowadzania aktualizacji.

5. W oknie **Właściwości** wybierz polecenie przesłonięcie (**Wstaw**, **zaktualizuj**lub **Usuń**).

6. Kliknij przycisk wielokropka (...) obok wyrazów **Użyj środowiska uruchomieniowego** , aby otworzyć okno dialogowe **Konfigurowanie zachowania** .

7. Wybierz **dostosować**.

8. Wybierz żądaną procedurę przechowywaną na liście **Dostosuj** .

9. Zbadaj listę **argumentów metody** i **właściwości klasy** , aby sprawdzić, czy **argumenty metody** są mapowane na odpowiednie **właściwości klasy**. Mapuj oryginalne argumenty metody (`Original_<ArgumentName>`) na oryginalne właściwości (`<PropertyName> (Original)`) dla poleceń `Update` i `Delete`.

    > [!NOTE]
    > Domyślnie argumenty metody są mapowane na właściwości klasy, gdy nazwy są zgodne. Jeśli zmienione nazwy właściwości nie są już zgodne między tabelą a klasą jednostki, może być konieczne wybranie równoważnej właściwości klasy do zamapowania, jeśli projektant nie może określić poprawnego mapowania.

10. Kliknij przycisk **OK** lub **się**.

    > [!NOTE]
    > Można nadal skonfigurować zachowanie dla każdej kombinacji klas i zachowań, o ile po wprowadzeniu każdej zmiany klikniesz przycisk **Zastosuj** . Jeśli zmienisz klasę lub zachowanie przed kliknięciem przycisku **Zastosuj**, pojawi się okno dialogowe ostrzeżenia z możliwością zastosowania zmian.

Aby przywrócić użycie domyślnej logiki środowiska uruchomieniowego dla aktualizacji, kliknij przycisk wielokropka obok polecenia **Wstaw**, **zaktualizuj**lub **Usuń** w oknie **Właściwości** , a następnie wybierz pozycję **Użyj środowiska uruchomieniowego** w oknie dialogowym **Konfigurowanie zachowania** .

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Operacje INSERT, Update i Delete (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)

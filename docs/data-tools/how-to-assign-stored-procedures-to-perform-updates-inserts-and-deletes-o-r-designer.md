---
title: Użyj procedur składowanych w LINQ to SQL, aby zaktualizować dane
description: Procedury składowane w LINQ to SQL Object Relational Designer (Projektant O/R) służą do przeprowadzania aktualizacji, wstawiania i usuwania danych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f0b7ab161a252e1d3a89ef856325963bddffdc56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866856"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)

Procedury składowane można dodać do **projektanta o/R** i wykonać jako typowe <xref:System.Data.Linq.DataContext> metody. Mogą one również służyć do przesłonięcia domyślnego LINQ to SQL zachowanie w czasie wykonywania, które wykonuje operacje wstawiania, aktualizacji i usuwania, gdy zmiany są zapisywane z klas jednostek do bazy danych (na przykład podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody).

> [!NOTE]
> Jeśli procedura składowana zwraca wartości, które muszą być wysłane z powrotem do klienta (na przykład wartości obliczone w procedurze składowanej), utwórz parametry wyjściowe w procedurach składowanych. Jeśli nie możesz użyć parametrów wyjściowych, napisz implementację metody częściowej zamiast zastępować zastąpień generowanych przez projektanta O/R. Elementy członkowskie zamapowane do wartości generowanych przez bazę danych muszą być ustawione na odpowiednie wartości po pomyślnym zakończeniu operacji wstawiania lub aktualizowania. Aby uzyskać więcej informacji, zobacz [obowiązki dewelopera w celu przesłania domyślnego zachowania](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL automatycznie obsługuje wartości generowane przez bazę danych dla tożsamości (automatyczne zwiększanie), ROWGUIDCOL (identyfikator GUID generowany przez bazę danych) i kolumny sygnatur czasowych. Wartości wygenerowane przez bazę danych w innych typach kolumn nieoczekiwanie spowodują wartość null. Aby zwrócić wartości generowane przez bazę danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> **wartość true** i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> jedną z następujących opcji: [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)lub [AutoSync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Skonfiguruj zachowanie aktualizacji klasy jednostki

Domyślnie logika do aktualizowania bazy danych (wstawia, aktualizuje i usuwa) ze zmianami, które zostały wprowadzone do danych w LINQ to SQL klas jednostek, jest zapewniana przez środowisko uruchomieniowe LINQ to SQL. Środowisko uruchomieniowe tworzy domyślne polecenia INSERT, UPDATE i DELETE, które są oparte na schemacie tabeli (informacje o kolumnie i kluczu podstawowym). Gdy zachowanie domyślne nie jest wymagane, można skonfigurować zachowanie aktualizacji, przypisując określone procedury składowane do wykonywania niezbędnych operacji wstawiania, aktualizacji i usuwania wymaganych do manipulowania danymi w tabeli. Można to również zrobić, gdy domyślne zachowanie nie jest generowane, na przykład gdy klasy jednostek mapują się na widoki. Na koniec można zastąpić domyślne zachowanie aktualizacji, gdy baza danych wymaga dostępu do tabeli za pomocą procedur składowanych.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Aby przypisać procedury składowane w celu zastąpienia domyślnego zachowania klasy jednostki

1. Otwórz plik **LINQ to SQL** w projektancie. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań**).

2. W **Eksplorator serwera** lub **Eksplorator bazy danych** rozwiń węzeł **procedury składowane** i zlokalizuj procedury składowane, których chcesz użyć dla poleceń INSERT, Update i/lub DELETE klasy Entity.

3. Przeciągnij procedurę składowaną do **projektanta O/R**.

     Procedura składowana jest dodawana do okienka metod jako <xref:System.Data.Linq.DataContext> Metoda. Aby uzyskać więcej informacji, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wybierz klasę jednostki, dla której chcesz użyć procedury składowanej do przeprowadzania aktualizacji.

5. W oknie **Właściwości** wybierz polecenie przesłonięcie (**Wstaw**, **zaktualizuj** lub **Usuń**).

6. Kliknij przycisk wielokropka (...) obok wyrazów **Użyj środowiska uruchomieniowego** , aby otworzyć okno dialogowe **Konfigurowanie zachowania** .

7. Wybierz pozycję **Dostosuj**.

8. Wybierz żądaną procedurę przechowywaną na liście **Dostosuj** .

9. Zbadaj listę **argumentów metody** i **właściwości klasy** , aby sprawdzić, czy **argumenty metody** są mapowane na odpowiednie **właściwości klasy**. Mapuj oryginalne argumenty metody ( `Original_<ArgumentName>` ) na oryginalne właściwości ( `<PropertyName> (Original)` ) dla `Update` `Delete` poleceń i.

    > [!NOTE]
    > Domyślnie argumenty metody są mapowane na właściwości klasy, gdy nazwy są zgodne. Jeśli zmienione nazwy właściwości nie są już zgodne między tabelą a klasą jednostki, może być konieczne wybranie równoważnej właściwości klasy do zamapowania, jeśli projektant nie może określić poprawnego mapowania.

10. Kliknij przycisk **OK** lub **się**.

    > [!NOTE]
    > Można nadal skonfigurować zachowanie dla każdej kombinacji klas i zachowań, o ile po wprowadzeniu każdej zmiany klikniesz przycisk **Zastosuj** . Jeśli zmienisz klasę lub zachowanie przed kliknięciem przycisku **Zastosuj**, pojawi się okno dialogowe ostrzeżenia z możliwością zastosowania zmian.

Aby przywrócić użycie domyślnej logiki środowiska uruchomieniowego dla aktualizacji, kliknij przycisk wielokropka obok polecenia **Wstaw**, **zaktualizuj** lub **Usuń** w oknie **Właściwości** , a następnie wybierz pozycję **Użyj środowiska uruchomieniowego** w oknie dialogowym **Konfigurowanie zachowania** .

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Operacje INSERT, Update i Delete (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)

---
title: 'Instrukcje: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (Projektant O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2054a55f0633d5d4add51fee2e933d9f4d829fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609980"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Procedury składowane można dodać do projektanta O/R i wykonać jako typowe <xref:System.Data.Linq.DataContext> metody. Mogą one również służyć do przesłonięcia domyślnego [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zachowania środowiska uruchomieniowego, które wykonuje operacje wstawiania, aktualizacji i usuwania, gdy zmiany są zapisywane z klas jednostek do bazy danych (na przykład podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody).

> [!NOTE]
> Jeśli procedura składowana zwraca wartości, które muszą być wysłane z powrotem do klienta (na przykład wartości obliczone w procedurze składowanej), utwórz parametry wyjściowe w procedurach składowanych. Jeśli nie możesz użyć parametrów wyjściowych, napisz implementację metody częściowej zamiast zastępować zastąpień generowanych przez projektanta O/R. Elementy członkowskie zamapowane do wartości generowanych przez bazę danych muszą być ustawione na odpowiednie wartości po pomyślnym zakończeniu operacji wstawiania lub aktualizowania. Aby uzyskać więcej informacji, zobacz [obowiązki dewelopera w celu przesłania domyślnego zachowania](https://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] automatycznie obsługuje wartości generowane przez bazę danych dla tożsamości (automatyczne zwiększanie), ROWGUIDCOL (GUID) i kolumn sygnatur czasowych. Wartości wygenerowane przez bazę danych w innych typach kolumn nieoczekiwanie spowodują wartość null. Aby zwrócić wartości generowane przez bazę danych, należy ręcznie ustawić wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> `true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> na jedną z następujących opcji: <xref:System.Data.Linq.Mapping.AutoSync> , <xref:System.Data.Linq.Mapping.AutoSync> , lub <xref:System.Data.Linq.Mapping.AutoSync> .

## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Konfigurowanie zachowania aktualizacji klasy jednostki
 Domyślnie logika do aktualizowania bazy danych (wstawia, aktualizuje i usuwa) ze zmianami, które zostały wprowadzone do danych w [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasach jednostek, jest udostępniana przez [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] środowisko uruchomieniowe. Środowisko uruchomieniowe tworzy domyślne polecenia INSERT, Update i DELETE, które są oparte na schemacie tabeli (informacje o kolumnie i kluczu podstawowym). Gdy zachowanie domyślne nie jest wymagane, można skonfigurować zachowanie aktualizacji, przypisując określone procedury składowane do wykonywania niezbędnych operacji wstawiania, aktualizacji i usuwania wymaganych do manipulowania danymi w tabeli. Można to również zrobić, gdy domyślne zachowanie nie jest generowane, na przykład gdy klasy jednostek mapują się na widoki. Na koniec można zastąpić domyślne zachowanie aktualizacji, gdy baza danych wymaga dostępu do tabeli za pomocą procedur składowanych.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Aby przypisać procedury składowane w celu zastąpienia domyślnego zachowania klasy jednostki

1. Otwórz plik **LINQ to SQL** w projektancie. (Kliknij dwukrotnie plik. dbml w **Eksplorator rozwiązań**).

2. W **Eksplorator serwera** / **Eksplorator bazy danych**rozwiń węzeł **procedury składowane** i zlokalizuj procedury składowane, których chcesz użyć dla poleceń INSERT, Update i/lub DELETE klasy Entity.

3. Przeciągnij procedurę składowaną do projektanta O/R.

     Procedura składowana jest dodawana do okienka metod jako <xref:System.Data.Linq.DataContext> Metoda. Aby uzyskać więcej informacji, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wybierz klasę jednostki, dla której chcesz użyć procedury składowanej do przeprowadzania aktualizacji.

5. W oknie **Właściwości** wybierz polecenie przesłonięcie (**Wstaw**, **zaktualizuj**lub **Usuń**).

6. Kliknij przycisk wielokropka (...) obok wyrazów **Użyj środowiska uruchomieniowego** , aby otworzyć okno dialogowe **Konfigurowanie zachowania** .

7. Wybierz pozycję **Dostosuj**.

8. Wybierz żądaną procedurę przechowywaną na liście **Dostosuj** .

9. Zbadaj listę **argumentów metody** i **właściwości klasy** , aby sprawdzić, czy **argumenty metody** są mapowane na odpowiednie **właściwości klasy**. Mapuj oryginalne argumenty metody (Original_*ArgumentName*) na oryginalne właściwości (*PropertyName* (oryginalna)) dla poleceń Update i DELETE.

    > [!NOTE]
    > Domyślnie argumenty metody są mapowane na właściwości klasy, gdy nazwy są zgodne. Jeśli zmienione nazwy właściwości nie są już zgodne między tabelą a klasą jednostki, może być konieczne wybranie równoważnej właściwości klasy do zamapowania, jeśli projektant nie może określić poprawnego mapowania.

10. Kliknij przycisk **OK** lub **się**.

    > [!NOTE]
    > Można nadal skonfigurować zachowanie dla każdej kombinacji klas/zachowań, o ile po wprowadzeniu każdej zmiany klikniesz przycisk **Zastosuj** . Jeśli zmienisz klasę lub zachowanie przed kliknięciem przycisku **Zastosuj**, zostanie wyświetlone okno dialogowe z ostrzeżeniem z możliwością zastosowania wszelkich zmian.

     Aby przywrócić użycie domyślnej logiki środowiska uruchomieniowego dla aktualizacji, kliknij przycisk wielokropka obok polecenia Wstaw, zaktualizuj lub Usuń w oknie **Właściwości** , a następnie wybierz pozycję **Użyj środowiska uruchomieniowego** w oknie dialogowym **Konfigurowanie zachowania** .

## <a name="see-also"></a>Zobacz też
 Wskazówki dotyczące [LINQ to SQL narzędzi w](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [ramach metod DataContext programu Visual Studio (Projektant o/r)](../data-tools/datacontext-methods-o-r-designer.md) [: tworzenie klas LINQ to SQL (projektant o-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [operacji INSERT, Update i DELETE](https://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)

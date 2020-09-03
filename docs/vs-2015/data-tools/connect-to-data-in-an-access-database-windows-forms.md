---
title: Nawiązywanie połączenia z danymi w bazie danych programu Access (Windows Forms) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8426e9fcaa29bef36b6701c78d622f6f42fd1171
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651132"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Łączenie z danymi w bazie danych programu Access (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz połączyć się z bazą danych programu Access (plik. mdf lub plik accdb) za pomocą programu Visual Studio. Po zdefiniowaniu połączenia dane są wyświetlane w oknie **źródła danych** . Stamtąd można przeciągnąć tabele lub widoki na formularze.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby użyć tych procedur, potrzebny jest projekt aplikacji Windows Forms i baza danych programu Access (plik accdb) lub baza danych programu Access 2000 – 2003 (plik. mdb). Wykonaj procedurę, która odnosi się do typu Twojego pliku.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Tworzenie zestawu danych dla pliku accdb
 Możesz połączyć się z bazami danych utworzonymi za pośrednictwem programu Access 2013, Office 365, Access 2010 lub Access 2007, wykonując poniższą procedurę.

#### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych

1. Otwórz aplikację Windows Forms, do której chcesz połączyć dane.

2. W menu **Widok** wybierz **inne**  >  **źródła danych**systemu Windows.

     ![Wyświetl inne źródła danych systemu Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

     ![Dodaj nowe źródło danych](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")

4. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** , a następnie wybierz przycisk **dalej**.

5. Wybierz pozycję **zestaw danych** na stronie **Wybierz model bazy danych** , a następnie wybierz przycisk **dalej**.

6. Na stronie **Wybierz połączenie danych** wybierz pozycję **nowe połączenie** , aby skonfigurować nowe połączenie danych.

7. Zmień **Źródło danych** , aby **dostawca danych .NET Framework OLE DB**.

     ![Zmień Dostawca danych na OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")

    > [!IMPORTANT]
    > Mimo że źródło danych **pliku bazy danych programu Microsoft Access (OLE DB)** może wyglądać jak właściwy wybór, ten typ źródła danych jest używany tylko dla plików bazy danych. mdb.

8. W obszarze **dostawca OLE DB**wybierz pozycję **Microsoft Office 12,0 dostęp do aparatu bazy danych OLE DB dostawcy**.

     ![OLE DB dostęp do dostawcy Microsoft Office 12,0](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

9. W polu **Nazwa serwera lub pliku**określ ścieżkę i nazwę pliku accdb, z którym chcesz się połączyć, a następnie wybierz przycisk **OK**.

    > [!NOTE]
    > Jeśli plik bazy danych ma nazwę użytkownika i hasło, określ je przed wybraniem **przycisku OK**.

10. Na stronie **Wybierz połączenie danych** wybierz pozycję **dalej** .

11. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej** .

12. Rozwiń węzeł **tabele** na stronie **Wybierz obiekty bazy danych** .

13. Zaznacz dowolne tabele lub widoki, które mają się pojawić w zestawie danych, a następnie wybierz pozycję **Zakończ**.

     Zestaw danych zostanie dodany do projektu, a tabele i widoki są wyświetlane w oknie **źródła danych** .

## <a name="creating-the-dataset-for-an-mdb-file"></a>Tworzenie zestawu danych dla pliku. mdb
 Zestaw danych można utworzyć, uruchamiając **Kreatora konfiguracji źródła danych**.

#### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych

1. Otwórz aplikację Windows Forms, do której chcesz połączyć dane.

2. W menu **Widok** wybierz **inne**  >  **źródła danych**systemu Windows.

     ![Wyświetl inne źródła danych systemu Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

4. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** , a następnie wybierz przycisk **dalej**.

5. Wybierz pozycję **zestaw danych** na stronie **Wybierz model bazy danych** , a następnie wybierz przycisk **dalej**.

6. Na stronie **Wybierz połączenie danych** wybierz pozycję **nowe połączenie** , aby skonfigurować nowe połączenie danych.

7. Jeśli źródło danych nie jest **plikiem bazy danych programu Microsoft Access (OLE DB)**, wybierz pozycję **Zmień** , aby otworzyć okno dialogowe **Zmień źródło danych** i wybierz **plik bazy danych programu Microsoft Access**, a następnie wybierz przycisk **OK**.

8. W polu **Nazwa pliku bazy danych**określ ścieżkę i nazwę pliku. mdb, z którym chcesz się połączyć, a następnie wybierz przycisk **OK**.

     ![Dodaj plik bazy danych dostępu do połączenia](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. Na stronie **Wybierz połączenie danych** wybierz pozycję **dalej** .

10. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej** .

11. Rozwiń węzeł **tabele** na stronie **Wybierz obiekty bazy danych** .

12. Zaznacz dowolne tabele lub widoki, które mają się pojawić w zestawie danych, a następnie wybierz pozycję **Zakończ**.

     Zestaw danych zostanie dodany do projektu, a tabele i widoki są wyświetlane w oknie **źródła danych** .

## <a name="security"></a>Zabezpieczenia
 Przechowywanie poufnych informacji (takich jak hasło) może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).

## <a name="next-steps"></a>Następne kroki
 Właśnie utworzony zestaw danych jest teraz dostępny w oknie **źródła danych** . Teraz można wykonać dowolne z następujących zadań:

- Wybierz pozycję elementy w oknie **źródła danych** i przeciągnij je do formularza (zobacz [Powiązywanie formantów Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Otwórz źródło danych w Projektant obiektów Dataset, aby dodać lub edytować obiekty wchodzące w skład zestawu danych.

- Dodaj logikę walidacji <xref:System.Data.DataTable.ColumnChanging> do <xref:System.Data.DataTable.RowChanging> zdarzenia lub tabel danych w zestawie danych (zobacz [Validate Data in DataSets](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Zobacz też

 [Przygotowywanie aplikacji do odbierania](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [formantów powiązań danych do danych w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md) [Sprawdzanie poprawności](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) [danych](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)
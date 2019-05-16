---
title: Łączenie z danymi w bazie danych programu Access (Windows Forms) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 120297a7e1b3c1e973f1775d769ab6deb8c2902a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705562"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Łączenie z danymi w bazie danych programu Access (formularze Windows)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazy danych programu Access (plik mdf lub pliku accdb) można nawiązać za pomocą programu Visual Studio. Po zdefiniowaniu połączenia, dane są wyświetlane w **źródeł danych** okna. Stamtąd można przeciągnąć tabele lub widoki na formularze.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby korzystać z tych procedur, należy na projekt aplikacji Windows Forms i bazy danych programu Access (plik accdb) lub bazy danych programu Access 2000-2003 (plik mdb). Wykonaj procedurę, która odnosi się do typu Twojego pliku.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>Tworzenie zestawu danych dla pliku accdb  
 Możesz połączyć się z bazami danych utworzonymi za pomocą programu Access 2013, Office 365, Access 2010 lub Access 2007 za pomocą poniższej procedury.  
  
#### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych  
  
1. Otwórz aplikację Windows Forms, z którym chcesz się połączyć dane.  
  
2. Na **widoku** menu, wybierz opcję **Windows inne** > **źródeł danych**.  
  
     ![Wyświetl inne źródła danych Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.  
  
     ![Dodaj nowe źródło danych](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4. Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie wybierz pozycję **dalej**.  
  
5. Wybierz **Dataset** na **wybierz Model bazy danych** strony, a następnie wybierz pozycję **dalej**.  
  
6. Na **wybierz połączenie danych** wybierz opcję **nowe połączenie** Aby skonfigurować nowe połączenie danych.  
  
7. Zmiana **źródła danych** do **.NET Framework Data Provider for OLE DB**.  
  
     ![Zmień dostawcą danych OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    > Mimo, że źródło danych **plik bazy danych programu Microsoft Access (OLE DB)** może wydawać się właściwym wyborem, użyj tego typu źródła danych tylko dla plików bazy danych .mdb.  
  
8. W **dostawcy OLE DB**, wybierz opcję **Office 12.0 Access bazy danych aparatu dostawcy Microsoft OLE DB**.  
  
     ![OLE DB dostawcy pakietu Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. W **nazwę serwera lub pliku**, określ ścieżkę i nazwę pliku accdb, z którą chcesz połączyć, a następnie wybierz **OK**.  
  
    > [!NOTE]
    > Jeśli plik bazy danych ma nazwę użytkownika i hasło, podaj je przed wybraniem **OK**.  
  
10. Wybierz **dalej** na **wybierz połączenie danych** strony.  
  
11. Wybierz **dalej** na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.  
  
12. Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.  
  
13. Wybierz dowolne tabel lub widoków w zestawie danych, a następnie wybierz **Zakończ**.  
  
     Zestaw danych zostanie dodany do projektu, a tabele i widoki pojawią się **źródeł danych** okna.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>Tworzenie zestawu danych dla pliku MDB  
 Utwórz zestaw danych, uruchamiając **Kreatora konfiguracji źródła danych**.  
  
#### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych  
  
1. Otwórz aplikację Windows Forms, z którym chcesz się połączyć dane.  
  
2. Na **widoku** menu, wybierz opcję **Windows inne** > **źródeł danych**.  
  
     ![Wyświetl inne źródła danych Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.  
  
4. Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie wybierz pozycję **dalej**.  
  
5. Wybierz **Dataset** na **wybierz Model bazy danych** strony, a następnie wybierz pozycję **dalej**.  
  
6. Na **wybierz połączenie danych** wybierz opcję **nowe połączenie** Aby skonfigurować nowe połączenie danych.  
  
7. Jeśli źródło danych jest **plik bazy danych programu Microsoft Access (OLE DB)**, wybierz opcję **zmiany** otworzyć **Zmień źródło danych** okno dialogowe, a następnie wybierz **firmy Microsoft Dostęp do pliku bazy danych**, a następnie wybierz pozycję **OK**.  
  
8. W **nazwa pliku bazy danych**, określ ścieżkę i nazwę pliku mdb, z którą chcesz połączyć, a następnie wybierz **OK**.  
  
     ![Dodaj plik bazy danych programu Access połączenia](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. Wybierz **dalej** na **wybierz połączenie danych** strony.  
  
10. Wybierz **dalej** na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.  
  
11. Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.  
  
12. Wybierz dowolne tabel lub widoków w zestawie danych, a następnie wybierz **Zakończ**.  
  
     Zestaw danych zostanie dodany do projektu, a tabele i widoki pojawią się **źródeł danych** okna.  
  
## <a name="security"></a>Zabezpieczenia  
 Przechowywanie poufnych informacji (takich jak hasło) może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="next-steps"></a>Następne kroki  
 Nowo utworzony zestaw danych jest teraz dostępna w **źródeł danych** okna. Można teraz wykonać dowolne z następujących zadań:  
  
- Zaznacz elementy w **źródeł danych** okna i przeciągnij je na formularzu (zobacz [formanty powiązania formularzy Windows do danych w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
- Otwórz źródło danych w Projektancie obiektów Dataset, aby dodać lub edytować obiekty, które składają się dataset.  
  
- Dodaj logikę walidacji do <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> wydarzenia tabel danych w zestawie danych (zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>Zobacz też

 [Przygotowanie aplikacji na odbieranie danych](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Sprawdzanie poprawności danych](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Wskazówki dotyczące danych](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)
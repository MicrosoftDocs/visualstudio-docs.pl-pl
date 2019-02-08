---
title: Łączenie z danymi w bazie danych programu Access (formularze Windows)
ms.date: 09/15/2017
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: efad211c5807aa4a018ede3c9018cf69f4668747
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933785"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Łączenie z danymi w bazie danych programu Access (formularze Windows)

Można połączyć z bazą danych programu Access (albo *.mdf* pliku lub *accdb* plików) za pomocą programu Visual Studio. Po zdefiniowaniu połączenia, dane są wyświetlane w **źródeł danych** okna. Stamtąd można przeciągnąć tabele lub widoki na formularze.

## <a name="prerequisites"></a>Wymagania wstępne

Aby korzystać z tych procedur, potrzebny jest projekt aplikacji Windows Forms i jednej bazie danych programu Access (*accdb* plików) lub bazy danych programu Access 2000-2003 (*.mdb* pliku). Wykonaj procedurę, która odnosi się do typu Twojego pliku.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Tworzenie zestawu danych dla pliku accdb

Możesz połączyć się z bazami danych utworzonymi za pomocą programu Access 2013, Office 365, Access 2010 lub Access 2007 za pomocą poniższej procedury.

### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych

1.  Otwórz aplikację Windows Forms, z którym chcesz się połączyć dane.

2.  Aby otworzyć **źródeł danych** okna na **widoku** menu, wybierz opcję **Windows inne** > **źródeł danych**.

     ![Wyświetl inne źródła danych Windows](../data-tools/media/viewdatasources.png)

3.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

     **Kreatora konfiguracji źródła danych** zostanie otwarty.

4.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie wybierz pozycję **dalej**.

5.  Wybierz **Dataset** na **wybierz Model bazy danych** strony, a następnie wybierz pozycję **dalej**.

6.  Na **wybierz połączenie danych** wybierz opcję **nowe połączenie** Aby skonfigurować nowe połączenie danych.

     **Dodaj połączenie** zostanie otwarte okno dialogowe.

7.  Wybierz **zmiany** znajdujący się obok **źródła danych** pola tekstowego.

     **Zmień źródło danych** zostanie otwarte okno dialogowe.

8.  Na liście źródeł danych, wybierz opcję  **\<innych\>**. W **dostawcy danych** listę rozwijaną, wybierz opcję **.NET Framework Data Provider for OLE DB**, następnie wybierz **OK**.

9. Ponownie **Dodaj połączenie** okno dialogowe, wybierz opcję **Office 12.0 Access bazy danych aparatu dostawcy Microsoft OLE DB** z **dostawcy OLE DB** listy rozwijanej.

     ![OLE DB dostawcy pakietu Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png)

     > [!NOTE]
     > Jeśli nie widzisz **Office 12.0 Access bazy danych aparatu dostawcy Microsoft OLE DB** w dostawcy OLE DB listy rozwijanej, użytkownik może być konieczne zainstalowanie [sterownik systemu Office 2007: składniki łączności danych](https://www.microsoft.com/download/confirmation.aspx?id=23734).

9. W **nazwę serwera lub pliku** polu tekstowym wpisz ścieżkę i nazwę pliku *accdb* pliku chcesz nawiązać połączenie, a następnie wybierz **OK**. (Jeśli plik bazy danych ma nazwę użytkownika i hasło, podaj je przed wybraniem **OK**.)

10. Wybierz **dalej** na **wybierz połączenie danych** strony.

     Mogą być wyświetlane okno dialogowe informujące, plik danych nie jest w bieżącym projekcie. Wybierz **tak** lub **nie**.

11. Wybierz **dalej** na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.

12. Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.

13. Wybierz dowolne tabel lub widoków w zestawie danych, a następnie wybierz **Zakończ**.

     Zestaw danych zostanie dodany do projektu, a tabele i widoki pojawią się **źródeł danych** okna.

## <a name="create-the-dataset-for-an-mdb-file"></a>Tworzenie zestawu danych dla pliku MDB

Utwórz zestaw danych, uruchamiając **Kreatora konfiguracji źródła danych**.

### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych

1.  Otwórz aplikację Windows Forms, z którym chcesz się połączyć dane.

2.  Na **widoku** menu, wybierz opcję **Windows inne** > **źródeł danych**.

     ![Wyświetl inne źródła danych Windows](../data-tools/media/viewdatasources.png)

3.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

     **Kreatora konfiguracji źródła danych** zostanie otwarty.

4.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie wybierz pozycję **dalej**.

5.  Wybierz **Dataset** na **wybierz Model bazy danych** strony, a następnie wybierz pozycję **dalej**.

6.  Na **wybierz połączenie danych** wybierz opcję **nowe połączenie** Aby skonfigurować nowe połączenie danych.

7.  Jeśli źródło danych jest **plik bazy danych programu Microsoft Access (OLE DB)**, wybierz opcję **zmiany** otworzyć **Zmień źródło danych** okno dialogowe, a następnie wybierz **firmy Microsoft Dostęp do pliku bazy danych**, a następnie wybierz pozycję **OK**.

8.  W **nazwa pliku bazy danych**, określ ścieżkę i nazwę *.mdb* pliku chcesz nawiązać połączenie, a następnie wybierz **OK**.

     ![Dodaj plik bazy danych programu Access połączenia](../data-tools/media/dataaddconnectionaccessmdb.png)

9. Wybierz **dalej** na **wybierz połączenie danych** strony.

10. Wybierz **dalej** na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.

11. Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.

12. Wybierz dowolne tabel lub widoków w zestawie danych, a następnie wybierz **Zakończ**.

     Zestaw danych zostanie dodany do projektu, a tabele i widoki pojawią się **źródeł danych** okna.

## <a name="security"></a>Zabezpieczenia

Przechowywanie poufnych informacji (takich jak hasło) może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrona informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Następne kroki

Nowo utworzony zestaw danych jest teraz dostępna w **źródeł danych** okna. Można teraz wykonać dowolne z następujących zadań:

-   Zaznacz elementy w **źródeł danych** okna i przeciągnij je na formularzu (zobacz [formanty powiązania formularzy Windows do danych w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

-   Otwórz źródło danych w **Projektanta obiektów Dataset** można dodawać lub edytować obiekty, które składają się dataset.

-   Dodaj logikę walidacji do <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> wydarzenia tabel danych w zestawie danych (zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Zobacz także

- [Dodawanie połączeń](../data-tools/add-new-connections.md)
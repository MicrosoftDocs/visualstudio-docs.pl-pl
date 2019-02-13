---
title: Łączenie z danymi w bazie danych programu Access (formularze Windows)
ms.date: 02/12/2019
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
ms.openlocfilehash: 293df62cc82295a9d2eea577df4e3f46dd14cef6
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227647"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Łączenie z danymi w bazie danych programu Access (formularze Windows)

Można połączyć z bazą danych programu Access (albo *.mdf* pliku lub *accdb* plików) za pomocą programu Visual Studio. Po zdefiniowaniu połączenia, dane są wyświetlane w **źródeł danych** okna. Stamtąd można przeciągnąć tabele lub widoki na formularze.

## <a name="prerequisites"></a>Wymagania wstępne

Aby korzystać z tych procedur, potrzebny jest projekt aplikacji Windows Forms i jednej bazie danych programu Access (*accdb* plików) lub bazy danych programu Access 2000-2003 (*.mdb* pliku). Wykonaj procedurę, która odnosi się do typu Twojego pliku.

## <a name="create-a-dataset-for-an-accdb-file"></a>Tworzenie zestawu danych dla pliku accdb

Możesz połączyć się z bazami danych utworzonymi za pomocą programu Access 2013, Office 365, Access 2010 lub Access 2007 za pomocą poniższej procedury.

1. Otwórz aplikację Windows Forms, z którym chcesz się połączyć dane.

2. Aby otworzyć **źródeł danych** okna na **widoku** menu, wybierz opcję **Windows inne** > **źródeł danych**.

   ![Wyświetl inne źródła danych Windows](../data-tools/media/viewdatasources.png)

3. W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

   **Kreatora konfiguracji źródła danych** zostanie otwarty.

4. Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie wybierz pozycję **dalej**.

5. Wybierz **Dataset** na **wybierz Model bazy danych** strony, a następnie wybierz pozycję **dalej**.

6. Na **wybierz połączenie danych** wybierz opcję **nowe połączenie** Aby skonfigurować nowe połączenie danych.

   **Dodaj połączenie** zostanie otwarte okno dialogowe.

7. Jeśli **źródła danych** nie jest ustawiony na **plik bazy danych programu Microsoft Access (OLE DB)**, wybierz opcję **zmiany** przycisku.

   **Zmień źródło danych** zostanie otwarte okno dialogowe. Na liście źródeł danych, wybierz opcję **plik bazy danych programu Microsoft Access**. W **dostawcy danych** listę rozwijaną, wybierz opcję **.NET Framework Data Provider for OLE DB**, a następnie wybierz **OK**.

8. Wybierz **Przeglądaj** obok **nazwa pliku bazy danych**, a następnie przejdź do usługi *accdb* pliku, a następnie wybierz **Otwórz**.

9. Wprowadź nazwę użytkownika i hasło (jeśli jest to konieczne), a następnie wybierz **OK**.

10. Wybierz **dalej** na **wybierz połączenie danych** strony.

     Mogą być wyświetlane okno dialogowe informujące, plik danych nie jest w bieżącym projekcie. Wybierz **tak** lub **nie**.

11. Wybierz **dalej** na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.

12. Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.

13. Wybierz tabele lub widoki, które chcesz uwzględnić w zestawie danych, a następnie wybierz **Zakończ**.

     Zestaw danych zostanie dodany do projektu, a tabele i widoki pojawią się **źródeł danych** okna.

## <a name="create-a-dataset-for-an-mdb-file"></a>Tworzenie zestawu danych dla pliku MDB

Utwórz zestaw danych, uruchamiając **Kreatora konfiguracji źródła danych**.

1. Otwórz aplikację Windows Forms, z którym chcesz się połączyć dane.

2. Na **widoku** menu, wybierz opcję **Windows inne** > **źródeł danych**.

   ![Wyświetl inne źródła danych Windows](../data-tools/media/viewdatasources.png)

3. W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

    **Kreatora konfiguracji źródła danych** zostanie otwarty.

4. Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie wybierz pozycję **dalej**.

5. Wybierz **Dataset** na **wybierz Model bazy danych** strony, a następnie wybierz pozycję **dalej**.

6. Na **wybierz połączenie danych** wybierz opcję **nowe połączenie** Aby skonfigurować nowe połączenie danych.

7. Jeśli źródło danych jest **plik bazy danych programu Microsoft Access (OLE DB)**, wybierz opcję **zmiany** otworzyć **Zmień źródło danych** okno dialogowe, a następnie wybierz **firmy Microsoft Dostęp do pliku bazy danych**, a następnie wybierz pozycję **OK**.

8. W **nazwa pliku bazy danych**, określ ścieżkę i nazwę *.mdb* pliku chcesz nawiązać połączenie, a następnie wybierz **OK**.

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

- Zaznacz elementy w **źródeł danych** okna i przeciągnij je na formularzu (zobacz [formanty powiązania formularzy Windows do danych w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Otwórz źródło danych w **Projektanta obiektów Dataset** można dodawać lub edytować obiekty, które składają się dataset.

- Dodaj logikę walidacji do <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> wydarzenia tabel danych w zestawie danych (zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Zobacz także

- [Dodawanie połączeń](../data-tools/add-new-connections.md)
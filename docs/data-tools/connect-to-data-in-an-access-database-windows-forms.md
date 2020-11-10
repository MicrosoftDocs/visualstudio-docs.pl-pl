---
title: Łączenie z danymi w bazie danych programu Access
description: Dowiedz się, jak nawiązać połączenie z danymi w bazie danych programu Access (plik. mdb lub. accdb. plik) w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/18/2019
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting
- connecting to data, Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 156acfd56789ec13201738e72c6df283e257e94f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436865"
---
# <a name="connect-to-data-in-an-access-database"></a>Łączenie z danymi w bazie danych programu Access

Możesz połączyć się z bazą danych programu Access (plik *mdb* lub plik *accdb* ) za pomocą programu Visual Studio. Po zdefiniowaniu połączenia dane są wyświetlane w oknie **źródła danych** . Z tego miejsca możesz przeciągnąć tabele lub widoki na powierzchnię projektu.

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tych procedur, potrzebny jest projekt Windows Forms lub WPF oraz baza danych programu Access (plik *accdb* ) lub baza danych programu Access 2000-2003 (plik *. mdb* ). Wykonaj procedurę, która odnosi się do typu Twojego pliku.

## <a name="create-a-dataset-for-an-accdb-file"></a>Tworzenie zestawu danych dla pliku accdb

Nawiąż połączenie z bazami danych utworzonymi przy użyciu Microsoft 365, Access 2013, Access 2010 lub Access 2007, wykonując poniższą procedurę.

1. Otwórz projekt aplikacji Windows Forms lub WPF w programie Visual Studio.

2. Aby otworzyć okno **źródła danych** , w menu **Widok** wybierz inne źródła danych **systemu Windows**  >  **Data Sources**.

   ![Wyświetl inne źródła danych systemu Windows](../data-tools/media/viewdatasources.png)

3. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

   Zostanie otwarty **Kreator konfiguracji źródła danych** .

4. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** , a następnie wybierz przycisk **dalej**.

5. Wybierz pozycję **zestaw danych** na stronie **Wybierz model bazy danych** , a następnie wybierz przycisk **dalej**.

6. Na stronie **Wybierz połączenie danych** wybierz pozycję **nowe połączenie** , aby skonfigurować nowe połączenie danych.

   Zostanie otwarte okno dialogowe **Dodaj połączenie** .

7. Jeśli **Źródło danych** nie jest ustawione na **plik bazy danych programu Microsoft Access** , wybierz przycisk **Zmień** .

   Zostanie otwarte okno dialogowe **Zmień źródło danych** . Z listy źródeł danych wybierz **plik bazy danych programu Microsoft Access**. Z listy rozwijanej **dostawca danych** wybierz pozycję **.NET Framework dostawca danych dla OLE DB** , a następnie wybierz przycisk **OK**.

8. Wybierz pozycję **Przeglądaj** obok pozycji **Nazwa pliku bazy danych** , a następnie przejdź do pliku *accdb* i wybierz polecenie **Otwórz**.

9. Wprowadź nazwę użytkownika i hasło (w razie potrzeby), a następnie wybierz przycisk **OK**.

10. Na stronie **Wybierz połączenie danych** wybierz pozycję **dalej** .

    Może pojawić się okno dialogowe z informacją, że plik danych nie znajduje się w bieżącym projekcie. Wybierz opcję **tak** lub **nie**.

11. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej** .

12. Rozwiń węzeł **tabele** na stronie **Wybierz obiekty bazy danych** .

13. Wybierz tabele lub widoki, które chcesz uwzględnić w zestawie danych, a następnie wybierz pozycję **Zakończ**.

    Zestaw danych zostanie dodany do projektu, a tabele i widoki są wyświetlane w oknie **źródła danych** .

## <a name="create-a-dataset-for-an-mdb-file"></a>Tworzenie zestawu danych dla pliku. mdb

Połącz się z bazami danych utworzonymi przy użyciu programu Access 2000-2003, wykonując poniższą procedurę.

1. Otwórz projekt aplikacji Windows Forms lub WPF w programie Visual Studio.

2. W menu **Widok** wybierz **inne**  >  **źródła danych** systemu Windows.

   ![Wyświetl inne źródła danych systemu Windows](../data-tools/media/viewdatasources.png)

3. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

    Zostanie otwarty **Kreator konfiguracji źródła danych** .

4. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** , a następnie wybierz przycisk **dalej**.

5. Wybierz pozycję **zestaw danych** na stronie **Wybierz model bazy danych** , a następnie wybierz przycisk **dalej**.

6. Na stronie **Wybierz połączenie danych** wybierz pozycję **nowe połączenie** , aby skonfigurować nowe połączenie danych.

7. Jeśli źródło danych nie jest **plikiem bazy danych programu Microsoft Access (OLE DB)** , wybierz pozycję **Zmień** , aby otworzyć okno dialogowe **Zmień źródło danych** i wybierz **plik bazy danych programu Microsoft Access** , a następnie wybierz przycisk **OK**.

8. W polu **Nazwa pliku bazy danych** określ ścieżkę i nazwę pliku *. mdb* , z którym chcesz się połączyć, a następnie wybierz przycisk **OK**.

   ![Dodaj plik bazy danych dostępu do połączenia](../data-tools/media/add-connection-access-db.png)

9. Na stronie **Wybierz połączenie danych** wybierz pozycję **dalej** .

10. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej** .

11. Rozwiń węzeł **tabele** na stronie **Wybierz obiekty bazy danych** .

12. Zaznacz dowolne tabele lub widoki, które mają się pojawić w zestawie danych, a następnie wybierz pozycję **Zakończ**.

    Zestaw danych zostanie dodany do projektu, a tabele i widoki są wyświetlane w oknie **źródła danych** .

## <a name="next-steps"></a>Następne kroki

Utworzony zestaw danych jest dostępny w oknie **źródła danych** . Teraz można wykonać dowolne z następujących zadań:

- Wybierz pozycję elementy w oknie **źródła danych** i przeciągnij je do formularza lub powierzchni projektowej (zobacz [bind Windows Forms formantów do danych w programie Visual Studio lub w](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) artykule [WPF — Omówienie powiązań danych](/dotnet/desktop-wpf/data/data-binding-overview)).

- Otwórz źródło danych w **Projektant obiektów DataSet** , aby dodać lub edytować obiekty wchodzące w skład zestawu danych.

- Dodaj logikę walidacji <xref:System.Data.DataTable.ColumnChanging> do <xref:System.Data.DataTable.RowChanging> zdarzenia lub tabel danych w zestawie danych (zobacz [Validate Data in DataSets](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Zobacz też

- [Dodawanie połączeń](../data-tools/add-new-connections.md)
- [Omówienie powiązania danych WPF](/dotnet/framework/wpf/data/data-binding-overview)
- [Windows Forms powiązania danych](/dotnet/framework/winforms/data-binding-and-windows-forms)

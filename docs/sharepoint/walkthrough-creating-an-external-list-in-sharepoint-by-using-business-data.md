---
title: Tworzenie listy zewnętrznej w programie SharePoint przy użyciu danych firmy
description: Utwórz model usługi BDC, który zwraca informacje o kontaktach z biznesową bazą danych, a następnie utwórz listę zewnętrzną w programie SharePoint przy użyciu tego modelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dbf996a2d44f94e4571a332fa7a86d861d820d45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847716"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Przewodnik: Tworzenie listy zewnętrznej w programie SharePoint przy użyciu danych firmowych

Usługa łączności danych biznesowych (BDC) umożliwia programowi SharePoint wyświetlanie danych biznesowych z aplikacji serwera zaplecza, usług sieci Web i baz danych.

W tym instruktażu pokazano, jak utworzyć model usługi BDC, która zwraca informacje o kontaktach w przykładowej bazie danych. Następnie utworzysz listę zewnętrzną w programie SharePoint przy użyciu tego modelu.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu.
- Dodawanie jednostki do modelu.
- Dodawanie metody wyszukiwania.
- Dodawanie określonej metody wyszukiwania.
- Testowanie projektu.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint.

- Dostęp do przykładowej bazy danych AdventureWorks. Aby uzyskać więcej informacji na temat sposobu instalowania bazy danych AdventureWorks, zobacz [SQL Server przykładowe bazy danych](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Tworzenie projektu zawierającego model usługi BDC

1. Na pasku menu w programie Visual Studio wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

2. W obszarze **Visual C#** lub **Visual Basic** rozwiń węzeł **SharePoint** , a następnie wybierz element **2010** .

3. W okienku **Szablony** wybierz **projekt SharePoint 2010**, nazwij projekt **AdventureWorksTest**, a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** . W tym kreatorze można określić lokację, która będzie używana do debugowania projektu i ustawienia poziomu zaufania rozwiązania.

4. Wybierz przycisk opcji **Wdróż jako rozwiązanie farmy** , aby ustawić poziom zaufania.

5. Wybierz przycisk **Zakończ** , aby zaakceptować domyślną lokalną witrynę programu SharePoint.

6. W **Eksplorator rozwiązań** wybierz węzeł projektu programu SharePoint.

7. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

     Zostanie otwarte okno dialogowe **Dodaj nowy element** .

8. W okienku **Szablony** wybierz pozycję **model łączności danych firmowych (tylko rozwiązanie farmy)**, nazwij projekt **AdventureWorksContacts**, a następnie wybierz przycisk **Dodaj** .

## <a name="add-data-access-classes-to-the-project"></a>Dodawanie klas dostępu do danych do projektu

1. Na pasku menu wybierz kolejno opcje **Narzędzia**  >  **Połącz z bazą danych**.

     Zostanie otwarte okno dialogowe **Dodaj połączenie** .

2. Dodaj połączenie do przykładowej bazy danych AdventureWorks SQL Server.

     Aby uzyskać więcej informacji, zobacz [Dodawanie/modyfikowanie połączenia (Microsoft SQL Server)](/previous-versions/dxb6fxah(v=vs.140)).

3. W **Eksplorator rozwiązań** wybierz węzeł projektu.

4. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

5. W okienku **zainstalowane szablony** wybierz węzeł **dane** .

6. W okienku **Szablony** wybierz **LINQ to SQL klas**.

7. W polu **Nazwa** Określ **AdventureWorks**, a następnie wybierz przycisk **Dodaj** .

     Do projektu zostanie dodany plik. dbml, a zostanie otwarty Object Relational Designer (Projektant O/R).

8. Na pasku menu wybierz polecenie **Wyświetl**  >  **Eksplorator serwera**.

9. W **Eksplorator serwera** rozwiń węzeł, który reprezentuje przykładową bazę danych AdventureWorks, a następnie rozwiń węzeł **tabele** .

10. Dodaj tabelę **Contact (osoba)** do projektanta O/R.

     Klasa jednostki jest tworzona i pojawia się na powierzchni projektowej. Klasa jednostki ma właściwości, które są mapowane na kolumny w tabeli Contact (osoba).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Usuwanie jednostki domyślnej z modelu usługi BDC

Projekt **model usługi łączności danych firmowych** dodaje do modelu jednostkę domyślną o nazwie jednostki Entity1. Usuń tę jednostkę. Później dodasz nową jednostkę. Rozpoczęcie od pustego modelu zmniejsza liczbę czynności wymaganych do ukończenia tego przewodnika.

1. W **Eksplorator rozwiązań** rozwiń węzeł **BdcModel1** , a następnie otwórz plik *BdcModel1. bdcm* .

2. Plik modelu usługi łączności danych biznesowych zostanie otwarty w Projektancie usługi BDC.

3. W projektancie Otwórz menu skrótów dla **jednostki Entity1**, a następnie wybierz polecenie **Usuń**.

4. W **Eksplorator rozwiązań** Otwórz menu skrótów dla *jednostki Entity1. vb* (w Visual Basic) lub *Entity1.cs* (w języku C#), a następnie wybierz polecenie **Usuń**.

5. Otwórz menu skrótów dla *Entity1Service. vb* (w Visual Basic) lub *Entity1Service.cs* (w języku C#), a następnie wybierz polecenie **Usuń**.

## <a name="add-an-entity-to-the-model"></a>Dodawanie jednostki do modelu

Dodaj jednostkę do modelu. Możesz dodać jednostki z **przybornika** programu Visual Studio do projektanta usługi BDC.

1. Na pasku menu wybierz **Widok**  >  **Przybornik**.

2. Na karcie **BusinessDataConnectivity** w **przyborniku** Dodaj **jednostkę** do projektanta usługi BDC.

     Nowa jednostka zostanie wyświetlona w projektancie. Program Visual Studio dodaje plik o nazwie *EntityService. vb* (w Visual Basic) lub *EntityService.cs* (w języku C#) do projektu.

3. Na pasku menu wybierz   >    >  **okno** właściwości widoku.

4. W oknie **Właściwości** ustaw wartość właściwości **Nazwa** na **kontakt**.

5. W projektancie Otwórz menu skrótów dla jednostki, wybierz polecenie **Dodaj**, a następnie wybierz **Identyfikator**.

     Nowy identyfikator zostanie wyświetlony w jednostce.

6. W oknie **Właściwości** Zmień nazwę identyfikatora na **ContactID**.

7. Z listy **Nazwa typu** wybierz **System. Int32**.

## <a name="add-a-specific-finder-method"></a>Dodaj konkretną metodę wyszukiwania

Aby umożliwić usłudze BDC Wyświetlanie określonego kontaktu, należy dodać określoną metodę wyszukiwania. Usługa BDC wywołuje określoną metodę wyszukiwania, gdy użytkownik wybierze element z listy, a następnie wybiera przycisk **Wyświetl element** na Wstążce.

Dodaj określoną metodę wyszukiwania do jednostki Contact przy użyciu okna **Szczegóły metody BDC** . Aby zwrócić określoną jednostkę, Dodaj kod do metody.

1. W projektancie BDC wybierz jednostkę **kontakt** .

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  >  **Szczegóły metody BDC** systemu Windows.

     Zostanie otwarte okno Szczegóły metody BDC.

3. Z listy **Dodaj metodę** wybierz opcję **Utwórz konkretną metodę wyszukiwania**.

     Program Visual Studio dodaje do modelu następujące elementy. Te elementy pojawiają się w oknie **Szczegóły metody BDC** .

    - Metoda o nazwie ReadItem.

    - Parametr wejściowy dla metody.

    - Parametr Return dla metody.

    - Deskryptor typu dla każdego parametru.

    - Wystąpienie metody dla metody.

4. W oknie **Szczegóły metody BDC** Otwórz listę, która jest wyświetlana dla deskryptora typu **kontaktu** , a następnie wybierz pozycję **Edytuj**.

     Zostanie otwarty **Eksplorator BDC** zawierający hierarchiczny widok modelu.

5. W oknie **Właściwości** Otwórz listę obok właściwości **TypeName** , wybierz kartę **bieżący projekt** , a następnie wybierz właściwość **kontakt** .

6. W **Eksploratorze BDC** Otwórz menu skrótów **kontaktu**, a następnie wybierz **Dodaj deskryptor typu**.

     Nowy deskryptor typu o nazwie **TypeDescriptor1** pojawia się w **Eksploratorze BDC**.

7. W oknie **Właściwości** ustaw wartość właściwości **Nazwa** na **ContactID**.

8. Otwórz listę obok właściwości **TypeName** , a następnie wybierz **Int32**.

9. Otwórz listę obok właściwości **Identyfikator** , a następnie wybierz **ContactID**.

10. Powtórz krok 6, aby utworzyć deskryptor typu dla każdego z poniższych pól.

    |Nazwa|Nazwa typu|
    |----------|---------------|
    |FirstName (Imię)|System. String|
    |LastName (Nazwisko)|System. String|
    |Telefon|System. String|
    |EmailAddress (Adres e-mail)|System. String|
    |EmailPromotion|System. Int32|
    |Nazwa|System. Boolean|
    |PasswordHash|System. String|
    |PasswordSalt|System. String|

11. W Projektancie usługi BDC w jednostce **kontaktowej** Otwórz metodę **ReadItem** .

     Plik kodu usługi kontaktowej zostanie otwarty w edytorze kodu.

12. W `ContactService` klasie Zastąp `ReadItem` metodę poniższym kodem. Ten kod wykonuje następujące zadania:

    - Pobiera rekord z tabeli kontaktowej bazy danych AdventureWorks.

    - Zwraca jednostkę Contact do usługi BDC.

    > [!NOTE]
    > Zamień wartość `ServerName` pola na nazwę serwera.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Dodawanie metody wyszukiwania

Aby umożliwić usłudze BDC wyświetlanie kontaktów na liście, należy dodać metodę wyszukiwania. Dodaj metodę wyszukiwania do jednostki Contact przy użyciu okna **Szczegóły metody BDC** . Aby zwrócić kolekcję jednostek do usługi BDC, Dodaj kod do metody.

1. W projektancie BDC wybierz jednostkę **kontakt** .

2. W oknie **Szczegóły metody BDC** Zwiń węzeł **ReadItem** .

3. Na liście **Dodaj metodę** w obszarze Metoda **ReadList** wybierz pozycję **Utwórz metodę wyszukiwania**.

     Program Visual Studio dodaje metodę, parametr Return i deskryptor typu.

4. W Projektancie usługi BDC w jednostce **kontaktowej** Otwórz metodę **ReadList** .

     Plik kodu dla usługi Contact zostanie otwarty w edytorze kodu.

5. W `ContactService` klasie Zastąp `ReadList` metodę poniższym kodem. Ten kod wykonuje następujące zadania:

   - Pobiera dane z tabeli kontakty bazy danych AdventureWorks.

   - Zwraca listę jednostek kontaktów do usługi BDC.

     > [!NOTE]
     > Zamień wartość `ServerName` pola na nazwę serwera.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Testowanie projektu

Po uruchomieniu projektu zostanie otwarta witryna programu SharePoint, a program Visual Studio doda model do usługi łączności danych firmowych. Utwórz listę zewnętrzną w programie SharePoint, która odwołuje się do jednostki Contact. Dane dotyczące kontaktów w bazie danych AdventureWorks pojawiają się na liście.

> [!NOTE]
> Aby można było debugować rozwiązanie, może być konieczne zmodyfikowanie ustawień zabezpieczeń w programie SharePoint. Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Wybierz klawisz **F5** .

     Zostanie otwarta witryna programu SharePoint.

2. W menu **Akcje witryny** wybierz polecenie **więcej opcji** .

3. Na stronie **Tworzenie** wybierz szablon **Lista zewnętrzna** , a następnie wybierz przycisk **Utwórz** .

4. Nazwij listę **kontaktów** niestandardowych.

5. Wybierz przycisk Przeglądaj obok pola **Typ zawartości zewnętrznej** .

6. W oknie dialogowym **Selektor typu zawartości zewnętrznej** wybierz element **AdventureWorksContacts. BdcModel1. Contact** , a następnie wybierz przycisk **Utwórz** .

     Program SharePoint tworzy listę zewnętrzną zawierającą kontakty z przykładowej bazy danych AdventureWorks.

7. Aby przetestować konkretną metodę wyszukiwania, wybierz osobę kontaktową z listy.

8. Na wstążce wybierz kartę **elementy** , a następnie wybierz polecenie **Wyświetl element** .

     Szczegóły wybranego kontaktu są wyświetlane w formularzu.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat sposobu projektowania modeli dla usługi BDC w programie SharePoint można znaleźć w następujących tematach:

- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md).
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md).
- [Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Zobacz też

[Projektowanie modelu](../sharepoint/designing-a-business-data-connectivity-model.md) 
 łączności danych firmy [Tworzenie modelu](../sharepoint/creating-a-business-data-connectivity-model.md) 
 łączności danych firmy Omówienie narzędzi projektowania [modelu BDC](../sharepoint/bdc-model-design-tools-overview.md) 
 [Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
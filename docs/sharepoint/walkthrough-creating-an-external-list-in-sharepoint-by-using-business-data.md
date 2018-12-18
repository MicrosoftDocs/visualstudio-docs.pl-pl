---
title: 'Wskazówki: Tworzenie listy zewnętrznej w SharePoint za pomocą danych biznesowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 18848f0ebd6ffa289ea09553de82f5b9eb893181
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295842"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Przewodnik: Tworzenie listy zewnętrznej w SharePoint za pomocą danych biznesowych

Usługa łączności danych biznesowych (BDC) umożliwia wyświetlanie danych biznesowych z serwerów zaplecza aplikacji, usług sieci Web i baz danych programu SharePoint.

W tym instruktażu przedstawiono sposób tworzenia modelu usługi BDC, który zwraca informacje o kontaktach w przykładowej bazie danych. Spowoduje to utworzenie listy zewnętrznej w SharePoint za pomocą tego modelu.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu.
- Dodawanie jednostki do modelu.
- Dodawanie metody wyszukiwania.
- Dodawanie określonej metody wyszukiwania.
- Testowanie projektu.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint.

- Dostęp do przykładowej bazy danych AdventureWorks. Aby uzyskać więcej informacji o sposobie instalowania bazy danych AdventureWorks, zobacz [baz danych programu SQL Server przykładowe](http://go.microsoft.com/fwlink/?LinkID=117483).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Utwórz projekt, który zawiera model usługi łączności danych biznesowych

1. Na pasku menu w programie Visual Studio, wybierz **pliku** > **New** > **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

2. W obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** elementu.

3. W **szablony** okienku wybierz **projekt programu SharePoint 2010**, nadaj projektowi nazwę **AdventureWorksTest**, a następnie wybierz **OK** przycisku .

     **Kreator ustawień niestandardowych SharePoint** pojawia się. W tym kreatorze można określić witryny, które będzie używane do debugowania projektu, a także Ustaw poziom zaufania rozwiązania.

4. Wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, aby ustawić poziom zaufania.

5. Wybierz **Zakończ** przycisk, aby zaakceptować domyślne lokalnej witryny programu SharePoint.

6. W **Eksploratora rozwiązań**, wybierz węzeł projektu programu SharePoint.

7. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

     **Dodaj nowy element** zostanie otwarte okno dialogowe.

8. W **szablony** okienku wybierz **modelu łączności danych biznesowych (tylko rozwiązanie farmy)**, nadaj projektowi nazwę **AdventureWorksContacts**, a następnie wybierz polecenie **Dodaj** przycisku.

## <a name="add-data-access-classes-to-the-project"></a>Dodawanie klas dostępu do danych do projektu

1. Na pasku menu wybierz **narzędzia** > **Połącz z bazą danych**.

     **Dodaj połączenie** zostanie otwarte okno dialogowe.

2. Dodawanie połączenia z przykładową bazą danych programu SQL Server AdventureWorks.

     Aby uzyskać więcej informacji, zobacz [Dodaj/Modyfikuj połączenie (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. W **Eksploratora rozwiązań**, wybierz węzeł projektu.

4. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

5. W **zainstalowane szablony** okienku wybierz **danych** węzła.

6. W **szablony** okienku wybierz **klasy LINQ do SQL**.

7. W **nazwa** określ **AdventureWorks**, a następnie wybierz **Dodaj** przycisku.

     Plik dbml zostanie dodany do projektu, i otwiera Object Relational Designer (O/R Designer).

8. Na pasku menu wybierz **widoku** > **Eksploratora serwera**.

9. W **Eksploratora serwera**, rozwiń węzeł, który reprezentuje przykładowej bazy danych AdventureWorks, a następnie rozwiń węzeł **tabel** węzła.

10. Dodaj **kontaktu (osoba)** tabeli w Projektancie obiektów relacyjnych.

     Klasa jednostki zostanie utworzony i wyświetlony na powierzchni projektowej. Klasa jednostki ma właściwości, które mapują do kolumn w tabeli Kontakt (osoba).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Usuwanie jednostki domyślnej z modelu usługi BDC

**Model usługi łączności danych biznesowych** projekt doda jednostki domyślnej, do modelu o nazwie jednostki Entity1. Usuń tę jednostkę. Później dodasz nowy obiekt. Począwszy od pustego modelu pozwala zmniejszyć liczbę kroków wymaganych do ukończeni instruktażu.

1. W **Eksploratora rozwiązań**, rozwiń węzeł **BdcModel1** węzeł, a następnie otwórz *BdcModel1.bdcm* pliku.

2. Plik modelu usługi łączności danych biznesowych zostanie otwarty w Projektancie usługi łączności danych biznesowych.

3. W projektancie, otwórz menu skrótów dla **jednostki Entity1**, a następnie wybierz **Usuń**.

4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla *Entity1.vb* (w języku Visual Basic) lub *Entity1.cs* (w języku C#), a następnie wybierz **Usuń** .

5. Otwórz menu skrótów dla *Entity1Service.vb* (w języku Visual Basic) lub *Entity1Service.cs* (w języku C#), a następnie wybierz **Usuń**.

## <a name="add-an-entity-to-the-model"></a>Dodawanie jednostki do modelu

Dodawanie jednostki do modelu. Można dodać jednostki w programie Visual Studio **przybornika** w Projektancie usługi łączności danych biznesowych.

1. Na pasku menu wybierz **widoku** > **przybornika**.

2. Na **BusinessDataConnectivity** karcie **przybornika**, Dodaj **jednostki** w Projektancie usługi łączności danych biznesowych.

     Nowa jednostka zostanie wyświetlony w projektancie. Program Visual Studio dodaje plik o nazwie *EntityService.vb* (w języku Visual Basic) lub *EntityService.cs* (w języku C#) do projektu.

3. Na pasku menu wybierz **widoku** > **właściwości** > **okna**.

4. W **właściwości** oknie **nazwa** wartość właściwości **skontaktuj się z pomocą**.

5. W projektancie, otwórz menu skrótów dla jednostki, wybierz polecenie **Dodaj**, a następnie wybierz **identyfikator**.

     Nowy identyfikator pojawia się w jednostce.

6. W **właściwości** okna, Zmień nazwę identyfikator ma **wartość ContactID**.

7. W **nazwy typu** wybierz **System.Int32**.

## <a name="add-a-specific-finder-method"></a>Dodawanie określonej metody wyszukiwania

Aby włączyć usługi łączności danych biznesowych do wyświetlania określonego kontaktu, należy dodać określonej metody wyszukiwania. Usługa łączności danych biznesowych wywołuje metodę określonej metody wyszukiwania, gdy użytkownik wybierze element na liście, a następnie **elementu widoku** przycisk na Wstążce.

Dodawanie określonej metody wyszukiwania do jednostki Contact przy użyciu **szczegóły metody BDC** okna. Aby przywrócić określonej jednostki, Dodaj kod do metody.

1. W Projektancie usługi łączności danych biznesowych, wybierz **skontaktuj się z pomocą** jednostki.

2. Na pasku menu wybierz **widoku** > **Windows inne** > **szczegóły metody BDC**.

     Zostanie otwarte okno Szczegóły metody BDC.

3. W **Dodaj metodę** wybierz **Tworzenie określonej metody wyszukiwania**.

     Visual Studio dodaje następujące elementy w modelu. Te elementy są wyświetlane w **szczegóły metody BDC** okna.

    - Metodę o nazwie ReadItem.

    - Parametr wejściowy metody.

    - Parametr zwracany przez metodę.

    - Deskryptor typu dla każdego parametru.

    - Wystąpienia metody dla metody.

4. W **szczegóły metody BDC** okna, Otwórz listę, która pojawia się dla **skontaktuj się z pomocą** deskryptor typu, a następnie wybierz **Edytuj**.

     **Eksplorator BDC** otwiera i udostępnia hierarchiczny widok modelu.

5. W **właściwości** okna, Otwórz listę obok **TypeName** właściwości, wybierz **bieżący projekt** kartę, a następnie wybierz **skontaktuj się z pomocą**właściwości.

6. W **Eksplorator BDC**, otwórz menu skrótów dla **skontaktuj się z pomocą**, a następnie wybierz **Dodaj deskryptor typu**.

     Nowy deskryptor typu, który nosi nazwę **TypeDescriptor1** pojawia się w **Eksplorator BDC**.

7. W **właściwości** oknie **nazwa** wartość właściwości **wartość ContactID**.

8. Otwórz listę obok **TypeName** właściwości, a następnie wybierz **Int32**.

9. Otwórz listę obok **identyfikator** właściwości, a następnie wybierz **wartość ContactID**.

10. Powtórz krok 6, aby utworzyć deskryptora typu dla każdego z poniższych pól.

    |Nazwa|Nazwa typu|
    |----------|---------------|
    |Imię|System.String|
    |Nazwisko|System.String|
    |Telefon|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. W Projektancie usługi łączności danych biznesowych na **skontaktuj się z pomocą** jednostki, otwórz **ReadItem** metody.

     Skontaktuj się z pliku kodu usługi zostanie otwarty w edytorze kodu.

12. W `ContactService` klasy, Zastąp `ReadItem` metoda następującym kodem. Kod będzie wykonywał następujące zadania:

    - Pobiera rekord z tabeli Kontakt bazy danych AdventureWorks.

    - Zwraca jednostki Contact do usługi łączności danych biznesowych.

    > [!NOTE]
    > Zastąp wartość `ServerName` pole z nazwą serwera.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Dodawanie metody wyszukiwania

Aby włączyć usługi BDC wyświetlić kontakty na liście, należy dodać metodę wyszukiwania. Dodawanie metody wyszukiwania do jednostki Contact przy użyciu **szczegóły metody BDC** okna. Aby przywrócić kolekcję jednostek usługi łączności danych biznesowych, należy dodać kod do metody.

1. W Projektancie usługi łączności danych biznesowych wybierz **skontaktuj się z pomocą** jednostki.

2. W **szczegóły metody BDC** oknie Zwiń **ReadItem** węzła.

3. W **Dodaj metodę** w obszarze **ReadList** metody wybierz **Utwórz metodę wyszukującą**.

     Visual Studio dodaje metodę, parametr zwracany i deskryptor typu.

4. W Projektancie usługi łączności danych biznesowych na **skontaktuj się z pomocą** jednostki, otwórz **ReadList** metody.

     Pliku kodu usługi kontaktów zostanie otwarty w edytorze kodu.

5. W `ContactService` klasy, Zastąp `ReadList` metoda następującym kodem. Kod będzie wykonywał następujące zadania:

   - Pobiera dane z tabeli kontaktów bazy danych AdventureWorks.

   - Zwraca listę jednostkami kontaktowymi do usługi łączności danych biznesowych.

     > [!NOTE]
     > Zastąp wartość `ServerName` pole z nazwą serwera.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Projekt testowy

Kiedy uruchamiasz projekt, otwiera się witryna SharePoint i Visual Studio dodaje modelu usługi łączności danych biznesowych. Tworzenie listy zewnętrznej w SharePoint, który odwołuje się do jednostki Contact. Dane o kontakty w usłudze bazy danych AdventureWorks są wyświetlane na liście.

> [!NOTE]
> Trzeba będzie zmodyfikować ustawienia zabezpieczeń w programie SharePoint, zanim można było debugować swoje rozwiązanie. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Wybierz **F5** klucza.

     Otwiera się witryna SharePoint.

2. Na **Akcje witryny** menu, wybierz **więcej opcji** polecenia.

3. Na **Utwórz** wybierz **listy zewnętrznej** szablonu, a następnie wybierz **Utwórz** przycisku.

4. Nadaj nazwę listy niestandardowej **kontakty**.

5. Wybierz przycisk przeglądania **typu zawartości zewnętrznej** pola.

6. W **zewnętrznych selektor typu zawartości** okna dialogowego wybierz **AdventureWorksContacts.BdcModel1.Contact** elementu, a następnie wybierz **Utwórz** przycisku.

     Program SharePoint tworzy listę zewnętrzną, która zawiera kontakty z przykładowej bazy danych AdventureWorks.

7. Aby przetestować konkretną metodę wyszukiwania, wybierz kontakt na liście.

8. Na Wstążce, wybierz **elementów** kartę, a następnie wybierz **elementu widoku** polecenia.

     Szczegóły kontaktu, która została wybrana są wyświetlane w formularzu.

## <a name="next-steps"></a>Następne kroki

Możesz dowiedzieć się więcej o projektowaniu modeli usługi łączności danych biznesowych w programie SharePoint w tych tematach:

- [Porady: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md).
- [Porady: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md).
- [Porady: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Zobacz także

[Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)  
[Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)  
[Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)  
[Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)

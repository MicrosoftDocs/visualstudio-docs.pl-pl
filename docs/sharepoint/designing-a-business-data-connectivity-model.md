---
title: Projektowanie modelu łączności danych biznesowych | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f322d18afdb8e14ee87ae31d30dd6bdd57b07c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431279"
---
# <a name="design-a-business-data-connectivity-model"></a>Projektowanie modelu łączności danych biznesowych
  Model usługi łączności danych biznesowych (BDC) można utworzyć przez dodanie jednostek i metody w pliku modelu. Jednostki w tym artykule opisano kolekcji pól danych. Na przykład jednostka może reprezentować tabelę w bazie danych. Metoda wykonuje zadania, takie jak dodawanie, usuwanie lub aktualizowanie danych reprezentowane przez jednostki. Aby uzyskać więcej informacji, zobacz [integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Dodawanie jednostek
 Jednostki można dodawać przez przeciąganie lub kopiowanie **jednostki** z programu Visual Studio **przybornika** w Projektancie usługi łączności danych biznesowych. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Definiowanie pól jednostki w klasie. Na przykład może dodać pole o nazwie `Address` do `Customer` klasy. Możesz dodać nową klasę do projektu lub użyj istniejącej klasy utworzone przy użyciu innych narzędzi, takich jak Object Relational Designer (O/R Designer). Nazwa podmiotu i nazwę klasy, która reprezentuje jednostkę nie muszą sobie odpowiadać. Można utworzyć relację między klasy do obiektu podczas definiowania metod w modelu.

## <a name="add-methods"></a>Dodaj metody
 Usługa łączności danych biznesowych wywołuje metody w modelu, gdy użytkownicy wyświetlanie, dodawanie, aktualizowanie lub usuwanie informacje listy lub składnik Web Part, który jest oparty na modelu. Należy dodać metodę do modelu dla każdego zadania, które użytkownik może wykonywać. Tworzenie metody, wybierając dowolną z pięciu typów podstawowe metody z **szczegóły metody BDC** okna. W poniższej tabeli opisano pięć podstawowych metod modelu usługi BDC.

|Metoda|Opis|
|------------|-----------------|
|Wyszukiwania|Zwraca kolekcję wystąpień jednostek. Wywołuje się, gdy użytkownik otwiera listę lub składnik Web Part. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md).|
|Specific Finder|Zwraca wystąpienie określonej jednostki. Wywołuje się, gdy użytkownik przegląda szczegółowe informacje o określony element na liście. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Kreator|Dodaje nowe dane do źródła danych jednostki. Wywołuje się, gdy użytkownicy wybiorą **nowy element** przycisk na Wstążce listę, która jest oparta na modelu. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md).|
|Updater|Modyfikuje danymi na liście. Wywołuje się, gdy użytkownicy zaktualizować informacje na liście. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md).|
|Deleter|Usuwa dane. Wywołuje się, gdy użytkownicy usunąć element z listy. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Zdefiniuj parametry metody
 Podczas tworzenia metody Visual Studio dodaje parametry wejściowe i wyjściowe, które są odpowiednie dla typu metody. Parametry te są tylko symbole zastępcze. W większości przypadków należy zmodyfikować parametry, aby przekazać, lub zwróć poprawny typ danych. Na przykład domyślnie metody wyszukiwania zwraca ciąg. W większości przypadków, którą chcesz zmodyfikować parametru zwracanego metody wyszukiwania, tak aby zwraca ono kolekcję jednostek. Można to wykonać, modyfikując deskryptor typu parametru. Deskryptor typu jest Kolekcja atrybutów, która opisuje typ danych parametru. Aby uzyskać więcej informacji, zobacz [jak: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Program Visual Studio umożliwia kopiowanie deskryptory typu między parametrami w modelu. Na przykład można zdefiniować deskryptor typu o nazwie `CustomerTD` w parametrze zwracanym `GetCustomer` metody. Możesz skopiować `CustomerTD` deskryptor w typu **Eksplorator BDC**, a następnie wklej ten deskryptor typu parametru wejściowego `CreateCustomer` metody. Ten sposób można uniknąć konieczności wcześniejszego definiowania deskryptora typu w tym samym więcej niż jeden raz.

## <a name="method-instances"></a>Metoda wystąpienia
 Podczas tworzenia metody Visual Studio dodaje wystąpienie domyślne metody. Wystąpienie metody jest odwołanie do metody, a także wartości domyślne dla parametrów. Jedna metoda może mieć wiele wystąpień metody. Każde wystąpienie jest kombinacją podpis metody i zestaw wartości domyślnych. Aby uzyskać więcej informacji, zobacz [jak: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Kiedy uruchamiasz projekt, metoda wystąpienia są wyświetlane na liście rozwijanej powyżej listy programu SharePoint. Użytkownicy mogą wybrać wystąpień metody, aby wyświetlić dane.

 Aby dodać wartości domyślne wystąpienie metody, należy bezpośrednio zmodyfikować plik XML modelu. Aby uzyskać więcej informacji, zobacz [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).

## <a name="add-filter-descriptors"></a>Dodać deskryptory filtrów
 Osoby korzystające z modelu może być można pobrać wystąpień jednostki, które spełniają pewne kryteria. Aby włączyć tę funkcję, możesz dodać Deskryptor filtru do metody. Deskryptory filtrów umożliwiają użytkownikom modelu do filtrowania zestawów wyników metody przez przekazanie wartości do metod, przed ich wykonania. Aby uzyskać więcej informacji, zobacz [jak: Dodaj parametry filtru do operacji w celu ograniczenia wystąpień z systemu zewnętrznego](http://go.microsoft.com/fwlink/?LinkID=169267).

 Program SharePoint udostępnia kilka funkcji, które umożliwiają użytkownikom podawanie wartości filtru. Na przykład składniki Web Part danych biznesowych zapewniają polu tekstowym filtru. Użytkowników można ograniczyć danymi na liście, wprowadzając wartość w polu tekstowym. Aby uzyskać więcej informacji na temat Dodawanie deskryptora filtru do metody, zobacz [jak: Dodawanie opisu filtru do metody wyszukiwania](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Deskryptor właściwości filtru
 Należy ustawić wartość z **skojarzone deskryptora typu**, **nazwa**, i **typu** właściwości Deskryptor filtru. Wszystkie pozostałe właściwości są opcjonalne.

 **Skojarzone deskryptora typu** właściwość dotyczy parametr wejściowy Deskryptor filtru. Gdy użytkownik poda wartość filtru, usługi łączności danych biznesowych przekazuje tę wartość do metody za pomocą parametru wejściowego.

 **Typu** właściwość opisuje filtrowania wzorzec, który chcesz użyć. W programie SharePoint należy wybrać wzorzec filtrowania ma wpływ na tekstu wyświetlanego w interfejsie użytkownika (UI). Na przykład wzorzec filtrowania Komparator tekst **jest równa** pojawia się jako kontroli nad składnika Web Part danych biznesowych. Aby uzyskać więcej informacji na temat każdego wzorca filtrowania zobacz [typy z filtrów obsługiwane przez usługi łączności danych biznesowych](http://go.microsoft.com/fwlink/?LinkId=169287).

 Aby uzyskać więcej informacji na temat właściwości Deskryptor filtru, zobacz [elementu FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).

### <a name="provide-default-values"></a>Podaj wartości domyślne
 W niektórych przypadkach użytkownik nie może być podać wartość filtru. Możesz podać wartość domyślną, dodając wartość domyślną do wystąpienia metody lub przez ustawienie wartości domyślne w kodzie metoda. Aby uzyskać więcej informacji o sposobie dodawania wartości domyślnej na wystąpienie metody, zobacz [elementu MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Na przykład jak ustawić wartość domyślna parametru wejściowego w kodzie metoda zobacz [jak: Dodawanie opisu filtru do metody wyszukiwania](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Walidacja modelu
 Podczas programowania, można sprawdzić poprawność modelu. Program Visual Studio identyfikuje problemy, które mogą uniemożliwić modelu zachowuje się zgodnie z oczekiwaniami. Te problemy występują w programie Visual Studio **lista błędów**.

 Sprawdzanie poprawności modelu, otwierając menu skrótów w Projektancie usługi łączności danych biznesowych, a następnie wybierając **weryfikacji**. Jeśli model zawiera błędy, pojawiają się na **lista błędów**. Można szybko przesuń kursor do kodu, który zawiera błąd, klikając dwukrotnie błąd na liście. Alternatywnie, możesz wybrać **F8** lub **Shift**+**F8** kluczy, aby krok do przodu lub do tyłu przez błędy na liście.

 Błędy sprawdzania poprawności może wystąpić, gdy naruszenia reguły modelu w jakiś sposób. Na przykład jeśli **IsCollection** właściwość deskryptor typu jest ustawiona na **true**, ale nie deskryptory typu podrzędnego istnieje, pojawi się błąd sprawdzania poprawności. Może być konieczne zapoznaj się z regułami modelu usługi BDC, aby zrozumieć pewne błędy, które są wyświetlane w programie Visual Studio **lista błędów**. Aby uzyskać więcej informacji o regułach modelu usługi BDC, zobacz [schematu BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).

## <a name="debug-the-solution-that-contains-the-model"></a>Debugowanie rozwiązań, który zawiera model
 Można debugować kodu, jak debuguje się dowolny kod w programie Visual Studio. Aby debugować kod, ustawić punkty przerwania w dowolnym miejscu w kodzie, a następnie uruchom debuger. Visual Studio otwiera witrynę programu SharePoint. W programie SharePoint, listy lub utworzyć składnik Web Part, który używa danych biznesowych. Następnie możesz przejrzeć swój kod. Aby uzyskać więcej informacji na temat debugowania projektów programu SharePoint, zobacz [rozwiązań SharePoint Rozwiązywanie problemów z](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Można również debugować kod w niestandardowe zestawy, które dodajesz do projektu. Jednak aby debugować kod w zestaw niestandardowy, należy dodać zestaw do pakietu rozwiązań. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie zestawów dodatkowych](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Aby uzyskać więcej informacji na temat dodawania niestandardowego zestawu do projektu, zobacz [jak: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).

### <a name="configure-bdc-security"></a>Konfigurowanie zabezpieczeń usługi łączności danych biznesowych
 Trzeba będzie zmodyfikować ustawienia zabezpieczeń w programie SharePoint, zanim można było debugować swoje rozwiązanie. Aby zmodyfikować te ustawienia, Otwórz aplikację usługi łączności danych biznesowych w programie SharePoint 2010 centralnego witryny sieci Web administracji. W **Set Permissions Store metadanych** okno dialogowe Dodawanie konta użytkownika, a następnie wybierz jedną z następujących opcji:

|Zadanie|Opcja|
|----------|------------|
|Umożliwia wdrażanie modeli usługi łączności danych biznesowych.|Edytowanie|
|Do utworzenia listy i składniki Web Part za pomocą zewnętrznego (jednostki) typów zawartości w modelu.|Wybór spośród klientów|
|Do tworzenia, odczytu, aktualizacji i usuwania danych jednostki.|Wykonywanie|

 Aby uzyskać więcej informacji o tych ustawieniach, zobacz [zarządzania usługi łączności danych biznesowych](http://go.microsoft.com/fwlink/?LinkID=178883).

 Można również ustawić uprawnień zabezpieczeń dla poszczególnych modeli lub typów zawartości zewnętrznej. Aby uzyskać więcej informacji na temat sposobu ustawiania uprawnień zabezpieczeń w modelu, zobacz [zarządzania modelu usługi łączności danych biznesowych](http://go.microsoft.com/fwlink/?LinkID=178884). Aby uzyskać więcej informacji na temat sposobu ustawiania uprawnień zabezpieczeń zewnętrznego typu zawartości, zobacz [zarządzania zewnętrznego typu zawartości](http://go.microsoft.com/fwlink/?LinkID=178885).

> [!NOTE]
> Użyj tych ustawień, aby debugować rozwiązanie na lokalnym serwerze programu SharePoint. Aby uzyskać więcej informacji o sposobie konfigurowania ustawień zabezpieczeń związane z usługi łączności danych biznesowych na serwerze programu SharePoint w środowisku produkcyjnym, zobacz [Omówienie zabezpieczeń usługi łączności danych biznesowych](http://go.microsoft.com/fwlink/?LinkID=178886).

### <a name="retract-models-that-become-corrupt"></a>Wycofaj modeli, które są uszkodzone
 Podczas pierwszego uruchomienia debugera, program Visual Studio wdroży cały model do programu SharePoint. Modelu w programie SharePoint za każdym razem po tej dacie jest aktualizacje ze wszystkimi zmianami, które wprowadzasz między wdrożeniami programu Visual Studio.

 Może to być sytuacje wymagające Visual Studio, aby wycofać całkowicie modelu z programu SharePoint. Na przykład modelu może być uszkodzona.  Aby przeprowadzić ponowne wdrożenie modelu do programu SharePoint, należy ustawić **aktualizacji przyrostowej** właściwości modelu, który ma **False**, a następnie uruchom debuger. **Aktualizacji przyrostowej** właściwość pojawia się w **właściwości** okna po wybraniu węzła, który reprezentuje model w **Eksplorator BDC**. Domyślnie, Nazwa modelu jest **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Zmienianie nazwy identyfikatorów jednostek w modelu
 Zmiana nazwy identyfikatora po wdrożeniu modelu, można otrzymać błąd wdrażania. Nie można rozwiązać ten problem, ustawiając **aktualizacji przyrostowej** właściwości modelu, który ma **False**. Wycofaj modelu ręcznie, a następnie należy ponownie wdrożyć rozwiązanie. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint Rozwiązywanie problemów z](../sharepoint/troubleshooting-sharepoint-solutions.md). Można uniknąć tego błędu, ustawiając **aktualizacji przyrostowej** właściwości **False** przed wdrożeniem początkowo modelu.

## <a name="locate-documentation-for-bdc-model-elements"></a>Znajdź dokumentację dotyczącą elementów modelu usługi łączności danych biznesowych
 Program Visual Studio dodaje XML element do modelu dla każdej jednostki, metody lub inny element, który tworzysz. Atrybuty elementów są wyświetlane jako właściwości w **właściwości** okna. Aby uzyskać informacji na temat elementów i atrybutów, które program Visual Studio generuje podczas projektowania modelu, zobacz [schematu BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)|Zawiera opis narzędzi, które umożliwiają wizualne projektowanie modelu łączności danych biznesowych.|
|[Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)|Dowiesz się, jak dodać typy zawartości zewnętrznej lub jednostki do modelu.|
|[Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)|Dowiesz się, jak dodać metodę, która umożliwia użytkownikom wyświetlić listę jednostek na liście lub składnik Web Part.|
|[Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)|Dowiesz się, jak dodać metodę, która umożliwia użytkownikom wyświetlić szczegóły określonej jednostki.|
|[Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)|Dowiesz się, jak dodać metodę, która umożliwia użytkownikom dodawanie rekordów do źródła danych bezpośrednio z listy lub składnik Web Part.|
|[Instrukcje: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)|Dowiesz się, jak dodać metodę, która umożliwia użytkownikom usunąć dane ze źródła danych za pomocą opcji w interfejsie użytkownika (UI) z listy lub składnik Web Part.|
|[Instrukcje: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)|Dowiesz się, jak dodać metodę, która umożliwia użytkownikom zmianę rekordów w źródle danych bezpośrednio z listy lub składnik Web Part.|
|[Instrukcje: Dodaj parametr do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Dowiesz się, jak dodać parametry wejściowe i z powrotem do metody za pomocą w oknie Szczegóły metody w programie Visual Studio.|
|[Instrukcje: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Dowiesz się, jak zdefiniować typ danych parametru w modelu.|
|[Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)|Dowiesz się, jak utworzyć wystąpienie metody, która wykonuje łączności danych biznesowych.|
|[Instrukcje: Dodawanie opisu filtru do metody wyszukiwania](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Dowiesz się, jak umożliwić użytkownikom ograniczyć liczbę wystąpień zwrócona przez metodę wyszukiwania.|
|[Tworzenie skojarzenia między jednostkami](../sharepoint/creating-an-association-between-entities.md)|W tym artykule opisano, jak można zdefiniować relacje między jednostkami w modelu. Składniki Web Part danych biznesowych, list zewnętrznych i aplikacjami niestandardowymi można wyświetlić te relacje danych w interfejsie użytkownika (UI).|
|[Instrukcje: Tworzenie skojarzenia między jednostkami](../sharepoint/how-to-create-an-association-between-entities.md)|Dowiesz się, jak zdefiniować relacje między jednostkami w modelu.|
|[Przewodnik: Lista zewnętrzna Createan w programie SharePoint za pomocą danych biznesowych](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Zawiera instrukcje krok po kroku, pokazujące, jak w celu utworzenia i przetestowania modelu, który wyświetla kontakty na liście programu SharePoint zewnętrznych.|
|[Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Omówienie tworzenia i projektowania modeli usługi łączności danych biznesowych.|

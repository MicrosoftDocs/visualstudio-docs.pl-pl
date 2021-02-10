---
title: Projektowanie modelu łączności danych firmy | Microsoft Docs
description: Zaprojektuj model łączności danych biznesowych (BDC). Dodaj jednostki i metody. Zdefiniuj parametry metody. Dodawanie deskryptorów filtrów. Sprawdź poprawność modelu usługi BDC.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fb1aa194688533855b7c5bd1d58a4e3b97ac749
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948846"
---
# <a name="design-a-business-data-connectivity-model"></a>Projektowanie modelu łączności danych firmy
  Możesz opracować model usługi łączności danych biznesowych (BDC), dodając jednostki i metody do pliku modelu. Jednostka opisuje zbiór pól danych. Na przykład jednostka może reprezentować tabelę w bazie danych. Metoda wykonuje zadanie takie jak dodawanie, usuwanie lub aktualizowanie danych reprezentowanych przez jednostki. Aby uzyskać więcej informacji, zobacz [Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Dodawanie jednostek
 Możesz dodać jednostkę, przeciągając lub kopiując **jednostkę** z **przybornika** programu Visual Studio do projektanta usługi BDC. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Zdefiniuj pola jednostki w klasie. Na przykład można dodać pole o nazwie `Address` do `Customer` klasy. Do projektu można dodać nową klasę lub użyć istniejącej klasy utworzonej przy użyciu innych narzędzi, takich jak Object Relational Designer (Projektant O/R). Nazwa jednostki i nazwa klasy reprezentującej jednostkę nie muszą być zgodne. Klasę należy powiązać z jednostką podczas definiowania metod w modelu.

## <a name="add-methods"></a>Dodawanie metod
 Usługa BDC wywołuje metody w modelu, gdy użytkownicy wyświetlają, dodają, aktualizują lub usuwają informacje na liście lub w składniku Web Part opartym na modelu. Należy dodać metodę do modelu dla każdego zadania, które użytkownik może wykonywać. Utwórz metody, wybierając spośród pięciu podstawowych typów metod z okna **Szczegóły metody BDC** . W poniższej tabeli opisano pięć podstawowych metod modelu usługi BDC.

|Metoda|Opis|
|------------|-----------------|
|Wyszukiwania|Zwraca kolekcję wystąpień jednostek. Wywoływana, gdy użytkownik otwiera listę lub składnik Web Part. Aby uzyskać więcej informacji, zobacz [jak: dodać metodę wyszukiwania](../sharepoint/how-to-add-a-finder-method.md).|
|Specific Finder|Zwraca określone wystąpienie jednostki. Wywołuje się, gdy użytkownik przegląda szczegóły określonego elementu na liście. Aby uzyskać więcej informacji, zobacz [jak: dodać konkretną metodę wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Kreator|Dodaje nowe dane do źródła danych jednostki. Wywoływana, gdy użytkownik wybierze przycisk **nowy element** na Wstążce listy, która jest oparta na modelu. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md).|
|Updater|Modyfikuje dane na liście. Wywoływana, gdy użytkownicy będą aktualizować informacje na liście. Aby uzyskać więcej informacji, zobacz [jak: dodać metodę Aktualizator](../sharepoint/how-to-add-an-updater-method.md).|
|Deleter|Usuwa dane. Wywoływana, gdy użytkownicy usuwają element z listy. Aby uzyskać więcej informacji, zobacz [jak: dodać metodę usuwania](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Definiuj parametry metody
 Podczas tworzenia metody program Visual Studio dodaje parametry wejściowe i wyjściowe, które są odpowiednie dla typu metody. Te parametry są tylko symbolami zastępczymi. W większości przypadków należy zmodyfikować parametry tak, aby przekazywać lub zwracały poprawny typ danych. Na przykład domyślnie Metoda wyszukiwania zwraca ciąg. W większości przypadków należy zmodyfikować parametr zwracany metody wyszukiwania, tak aby zwracała kolekcję jednostek. Można to zrobić, modyfikując deskryptor typu parametru. Deskryptor typu jest kolekcją atrybutów, które opisują typ danych parametru. Aby uzyskać więcej informacji, zobacz [How to: define The Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Program Visual Studio umożliwia kopiowanie deskryptorów typu między parametrami w modelu. Na przykład można zdefiniować deskryptor typu o nazwie `CustomerTD` dla parametru powrotu `GetCustomer` metody. Można skopiować `CustomerTD` deskryptor typu w **Eksploratorze BDC**, a następnie wkleić ten deskryptor typu do parametru wejściowego `CreateCustomer` metody. Zapobiega to konieczności definiowania tego samego deskryptora typu więcej niż raz.

## <a name="method-instances"></a>Wystąpienia metod
 Podczas tworzenia metody program Visual Studio dodaje domyślne wystąpienie metody. Wystąpienie metody jest odwołaniem do metody i wartościami domyślnymi parametrów. Pojedyncza Metoda może mieć wiele wystąpień metod. Każde wystąpienie jest kombinacją sygnatury metody i zestawu wartości domyślnych. Aby uzyskać więcej informacji, zobacz [How to: define The Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Po uruchomieniu projektu wystąpienia metod pojawiają się na liście rozwijanej nad listą programu SharePoint. Użytkownicy mogą wybrać wystąpienia metody, aby wyświetlić dane.

 Aby dodać wartości domyślne do wystąpienia metody, należy bezpośrednio zmodyfikować kod XML modelu. Aby uzyskać więcej informacji, zobacz [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Dodawanie deskryptorów filtrów
 Odbiorcy modelu mogą chcieć pobrać wystąpienia jednostki, które pasują do niektórych kryteriów. Aby włączyć tę funkcję, można dodać do metody Deskryptor filtru. Deskryptory filtru umożliwiają odbiorcom modelu filtrowanie zestawów wyników metody przez przekazywanie wartości do metod przed ich wykonaniem. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie parametrów filtru do operacji w celu ograniczenia wystąpień z systemu zewnętrznego](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 Program SharePoint udostępnia kilka funkcji, które umożliwiają użytkownikom udostępnianie wartości filtru. Na przykład dane biznesowe składniki Web Part zawierają pola tekstowego filtr. Użytkownicy mogą ograniczać dane na liście, wprowadzając wartość w polu tekstowym. Aby uzyskać więcej informacji na temat dodawania deskryptora filtru do metody, zobacz [jak: Dodawanie deskryptora filtru do metody wyszukiwania](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Właściwości deskryptora filtru
 Należy ustawić wartość **skojarzonego deskryptora typu**, **nazwę** i właściwości **typu** deskryptora filtru. Wszystkie inne właściwości są opcjonalne.

 Właściwość **deskryptora skojarzonego typu** wiąże Deskryptor filtru z parametrem wejściowym. Gdy użytkownik poda wartość filtru, usługa BDC przekazuje tę wartość do metody przy użyciu parametru wejściowego.

 Właściwość **Type** opisuje wzorzec filtrowania, który ma być używany. W programie SharePoint wybrany wzorzec filtrowania ma wpływ na tekst wyświetlany w interfejsie użytkownika. Na przykład w przypadku wzorca filtrowania komparator tekst **jest** wyświetlany jako kontrolka powyżej elementu Web Part danych firmowych. Aby uzyskać więcej informacji na temat poszczególnych wzorców filtrowania, zobacz [typy filtrów obsługiwanych przez ten kontroler BDC](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

 Aby uzyskać więcej informacji o właściwościach deskryptora filtru, zobacz element [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Podaj wartości domyślne
 W niektórych przypadkach użytkownik może nie podawać wartości filtru. Wartość domyślną można podać przez dodanie wartości domyślnej do wystąpienia metody lub przez ustawienie wartości domyślnej w kodzie metody. Aby uzyskać więcej informacji na temat dodawania wartości domyślnej do wystąpienia metody, zobacz element [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Aby zapoznać się z przykładem sposobu ustawiania wartości domyślnej parametru wejściowego w kodzie metody, zobacz [How to: Add a Descriptor Filter to a metoda Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Weryfikowanie modelu
 Podczas opracowywania można sprawdzić poprawność modelu. Program Visual Studio identyfikuje problemy, które mogą uniemożliwić zachowanie modelu zgodnie z oczekiwaniami. Te problemy są wyświetlane w **Lista błędów** programu Visual Studio.

 Możesz sprawdzić poprawność modelu, otwierając menu skrótów dla projektanta usługi BDC, a następnie wybierając polecenie **Weryfikuj**. Jeśli model zawiera błędy, pojawiają się one w **Lista błędów**. Możesz szybko przenieść kursor do kodu, który zawiera błąd przez dwukrotne kliknięcie na liście błędu. Alternatywnie można wielokrotnie wybrać klawisze **F8** lub **SHIFT** + **F8** , aby krok do przodu lub do tyłu przekroczyć błędy na liście.

 Błędy sprawdzania poprawności mogą wystąpić, gdy reguły modelu zostały naruszone w jakiś sposób. Na przykład, jeśli właściwość **IsCollection** typu deskryptora ma **wartość true**, ale nie istnieją żadne deskryptory typu podrzędnego, zostanie wyświetlony komunikat o błędzie walidacji. Może zajść konieczność odwoływania się do reguł modelu usługi BDC w celu poznania niektórych błędów, które pojawiają się w programie Visual Studio **Lista błędów**. Aby uzyskać więcej informacji na temat reguł modelu usługi BDC, zobacz [schemat BDCMetadata](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Debuguj rozwiązanie, które zawiera model
 Można debugować kod w taki sposób, jak debugowanie dowolnego kodu w programie Visual Studio. Aby debugować kod, ustaw punkty przerwania w dowolnym miejscu w kodzie, a następnie uruchom debuger. Program Visual Studio otwiera witrynę programu SharePoint. W programie SharePoint Utwórz listę lub składnik Web Part, który korzysta z danych firmowych. Następnie możesz przejść przez swój kod. Aby uzyskać więcej informacji na temat debugowania projektów programu SharePoint, zobacz [Rozwiązywanie problemów z rozwiązaniami programu SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Możesz również debugować kod w niestandardowych zestawach, które można dodać do projektu. Jednak aby debugować kod w zestawie niestandardowym, należy dodać zestaw do pakietu rozwiązania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie dodatkowych zestawów](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Aby uzyskać więcej informacji na temat dodawania niestandardowego zestawu do projektu, zobacz [jak to zrobić: dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).

### <a name="configure-bdc-security"></a>Konfigurowanie zabezpieczeń usługi BDC
 Aby można było debugować rozwiązanie, może być konieczne zmodyfikowanie ustawień zabezpieczeń w programie SharePoint. Aby zmodyfikować te ustawienia, Otwórz aplikację usługi łączności danych firmowych w witrynie sieci Web administracji centralnej programu SharePoint 2010. W oknie dialogowym **Ustawianie uprawnień do przechowywania metadanych** Dodaj konto użytkownika, a następnie wybierz jedną z następujących opcji:

|Zadanie|Opcja|
|----------|------------|
|Do wdrażania modeli w usłudze BDC.|Edytuj|
|Tworzenie list i składniki Web Part przy użyciu zewnętrznych typów zawartości (jednostek) w modelu.|Wybór w klientach|
|Tworzenie, odczytywanie, aktualizowanie i usuwanie danych jednostki.|Wykonaj polecenie|

 Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Zarządzanie usługą łączności danych firmowych](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14)).

 Możesz również ustawić uprawnienia zabezpieczeń dla poszczególnych modeli lub zewnętrznych typów zawartości. Aby uzyskać więcej informacji na temat sposobu ustawiania uprawnień zabezpieczeń dla modelu, zobacz [Zarządzanie modelami usługi BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)). Aby uzyskać więcej informacji na temat sposobu ustawiania uprawnień zabezpieczeń zewnętrznego typu zawartości, zobacz [Zarządzanie typem zawartości zewnętrznej](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14)).

> [!NOTE]
> Użyj tych ustawień, aby debugować rozwiązanie na lokalnym serwerze programu SharePoint. Aby uzyskać więcej informacji na temat konfigurowania ustawień zabezpieczeń związanych z usługą BDC na serwerze produkcyjnym programu SharePoint, zobacz [Omówienie zabezpieczeń usług łączności danych biznesowych](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14)).

### <a name="retract-models-that-become-corrupt"></a>Wycofywanie modeli, które uległy uszkodzeniu
 Przy pierwszym uruchomieniu debugera program Visual Studio wdraża cały model w programie SharePoint. Za każdym razem program Visual Studio aktualizuje model w programie SharePoint przy użyciu wszelkich zmian wprowadzonych między wdrożeniami.

 Mogą wystąpić sytuacje, w których program Visual Studio ma całkowicie wycofać model z programu SharePoint. Na przykład model może ulec uszkodzeniu.  Aby ponownie wdrożyć model w programie SharePoint, ustaw dla właściwości **aktualizacji przyrostowej** **wartość FAŁSZ**, a następnie uruchom debuger. Właściwość **aktualizacja przyrostowa** pojawia się w oknie **Właściwości** w przypadku wybrania węzła, który reprezentuje model w **Eksploratorze BDC**. Domyślnie nazwa modelu to **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Zmień nazwy identyfikatorów jednostek w modelu
 Jeśli zmienisz nazwę identyfikatora po wdrożeniu modelu, może wystąpić błąd wdrażania. Nie można rozwiązać tego błędu przez ustawienie dla właściwości **aktualizacji przyrostowej** modelu **wartości false**. Należy ręcznie wycofać model, a następnie ponownie wdrożyć rozwiązanie. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z rozwiązaniami programu SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). Można uniknąć tego błędu przez ustawienie dla właściwości **aktualizacji przyrostowej** **wartości FAŁSZ** przed początkowym wdrożeniem modelu.

## <a name="locate-documentation-for-bdc-model-elements"></a>Znajdź dokumentację dla elementów modelu usługi BDC
 Program Visual Studio dodaje do modelu element XML dla każdej utworzonej jednostki, metody lub innego elementu. Atrybuty elementu są wyświetlane jako właściwości w oknie **Właściwości** . Aby uzyskać informacje na temat elementów i atrybutów, które program Visual Studio generuje podczas projektowania modelu, zobacz [schemat BDCMetadata](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)|Opisuje narzędzia, za pomocą których można wizualnie projektować model dla usługi BDC.|
|[Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)|Pokazuje, jak dodać zewnętrzne typy zawartości lub jednostki do modelu.|
|[Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom wyświetlanie listy jednostek na liście lub w części sieci Web.|
|[Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom wyświetlanie szczegółów określonej jednostki.|
|[Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom dodawanie rekordów do źródła danych bezpośrednio z listy lub składnika Web Part.|
|[Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom usuwanie danych ze źródła danych przy użyciu opcji w interfejsie użytkownika (UI) listy lub części sieci Web.|
|[Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom zmianę rekordów danych w źródle danych bezpośrednio z listy lub składnika Web Part.|
|[Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Pokazuje, jak użyć okna Szczegóły metody w programie Visual Studio, aby dodać parametry wejściowe i zwrotne do metody.|
|[Instrukcje: Definiowanie deskryptora typu dla parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Pokazuje, w jaki sposób definiować typy danych parametrów w modelu.|
|[Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)|Pokazuje, jak utworzyć wystąpienie metody wykonywanej przez usługę BDC.|
|[Instrukcje: Dodawanie deskryptora filtru do metody wyszukiwania](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Pokazuje, jak umożliwić użytkownikom ograniczenie liczby wystąpień zwracanych przez metodę wyszukiwania.|
|[Tworzenie skojarzenia między jednostkami](../sharepoint/creating-an-association-between-entities.md)|Opisuje, w jaki sposób można definiować relacje między jednostkami w modelu. Dane biznesowe składniki Web Part, list zewnętrznych i aplikacji niestandardowych mogą wyświetlać te relacje danych w interfejsie użytkownika.|
|[Instrukcje: Tworzenie skojarzenia między jednostkami](../sharepoint/how-to-create-an-association-between-entities.md)|Pokazuje, w jaki sposób definiować relacje między jednostkami w modelu.|
|[Przewodnik: Createan listy zewnętrznej w programie SharePoint przy użyciu danych firmowych](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Zawiera instrukcje krok po kroku, które pokazują, jak utworzyć i przetestować model, który wyświetla kontakty na liście zewnętrznej programu SharePoint.|
|[Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Zawiera omówienie tworzenia i projektowania modeli dla usługi BDC.|

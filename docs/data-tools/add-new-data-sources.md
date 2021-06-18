---
title: Dodawanie nowych źródeł danych
description: Dodaj nowe źródła danych w Visual Studio. Źródło danych to obiekt .NET, który łączy się z magazynem danych i zapewnia dostęp do danych aplikacji .NET.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a377acba7b8c64503e5e5f821b5f3f833a8d73b2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308054"
---
# <a name="add-new-data-sources"></a>Dodawanie nowych źródeł danych

:::moniker range=">=vs-2019"
> [!NOTE]
> Funkcje opisane w tym artykule dotyczą tworzenia aplikacji .NET Framework Windows Forms WPF. Funkcje nie są obsługiwane w przypadku tworzenia aplikacji .NET Core, zarówno w przypadku platform WPF, jak i Windows Forms.
:::moniker-end

W kontekście narzędzi danych .NET w programie  Visual Studio termin źródło danych odnosi się do obiektów .NET, które łączą się z magazynem danych i udostępnią dane aplikacji .NET. Projektanci Visual Studio mogą korzystać z danych wyjściowych źródła danych w celu wygenerowania kodu, który wiąże dane z formularzami podczas przeciągania i upuszczania obiektów bazy danych z okna **Źródła** danych. Tego rodzaju źródło danych może być:

- Klasa w modelu Entity Framework, która jest skojarzona z jakąś bazą danych.

- Zestaw danych skojarzony z jakąś bazą danych.

- Klasa reprezentująca usługę sieciową, taką jak Windows Communication Foundation danych (WCF) lub usługa REST.

- Klasa reprezentująca usługę SharePoint.

- Klasa lub kolekcja w rozwiązaniu.

> [!NOTE]
> Jeśli nie używasz funkcji powiązania danych, zestawów danych, Entity Framework, LINQ to SQL, WCF lub SharePoint, pojęcie "źródła danych" nie ma zastosowania. Wystarczy połączyć się bezpośrednio z bazą danych przy użyciu obiektów SQLCommand i komunikować się bezpośrednio z bazą danych.

Źródła danych można tworzyć i edytować za pomocą Kreatora konfiguracji **źródła** danych w Windows Forms lub Windows Presentation Foundation danych. Na Entity Framework najpierw utwórz klasy jednostek, a następnie uruchom kreatora, wybierając pozycję **Project** Add New Data Source (Projektuj dodaj nowe źródło danych) (opisane bardziej szczegółowo w  >   dalszej części tego artykułu).

![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Data Sources — Okno

Po utworzeniu źródła danych zostanie ono wyświetlone w **oknie** narzędzia Źródła danych.

> [!TIP]
> Aby otworzyć **okno Źródła danych,** upewnij się, że projekt jest otwarty, a następnie naciśnij klawisz **Shift** Alt D lub wybierz +  +  **pozycję Wyświetl** inne źródła danych  >  systemu **Windows.**  >  

Źródło danych można przeciągać z okna **Źródła** danych na powierzchnię projektową lub kontrolkę formularza. Powoduje to wygenerowanie ujednoliwowego kodu, który wyświetla dane z magazynu danych.

Na poniższej ilustracji przedstawiono zestaw danych, który został porzucony do formularza systemu Windows. Jeśli wybierzesz **klawisz F5** w aplikacji, dane z podstawowej bazy danych będą wyświetlane w kontrolkach formularza.

![Operacja przeciągania źródła danych](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Źródło danych dla bazy danych lub pliku bazy danych

Możesz utworzyć zestaw danych lub model Entity Framework do użycia jako źródło danych dla bazy danych lub pliku bazy danych.

### <a name="dataset"></a>Zestaw danych

Aby utworzyć zestaw danych jako źródło danych, uruchom Kreatora konfiguracji **źródła** danych, wybierając pozycję **Projekt**  >  **Dodaj nowe źródło danych.** Wybierz typ **źródła** danych Baza danych i postępuj zgodnie z monitami, aby określić nowe lub istniejące połączenie z bazą danych albo plik bazy danych.

### <a name="entity-classes"></a>Klasy jednostek

Aby utworzyć Entity Framework jako źródło danych:

1. Uruchom kreatora **Entity Data Model,** aby utworzyć klasy jednostek. Wybierz **pozycję Projekt** Dodaj nowy element  >    >  **ADO.NET Entity Data Model**.

   ![Nowy Entity Framework projektu modelu](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Wybierz metodę, według której chcesz wygenerować model.

   ![Entity Data Model kreatora](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Dodaj model jako źródło danych. Wygenerowane klasy są wyświetlane w **Kreatorze konfiguracji źródła danych** po wybraniu **kategorii** Obiekty.

   ![Kreator konfiguracji źródła danych z klasami jednostek](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Źródło danych dla usługi

Aby utworzyć źródło danych z usługi, uruchom Kreatora konfiguracji **źródła** danych i **wybierz** typ źródła danych Usługi. Jest to skrót do okna dialogowego **Dodaj odwołanie do usługi,** do którego można również uzyskać dostęp, klikając prawym przyciskiem myszy projekt w oknie **Eksplorator rozwiązań** i wybierając polecenie **Dodaj odwołanie do usługi.**

Podczas tworzenia źródła danych z usługi program Visual Studio odwołanie do usługi do projektu. Visual Studio tworzy również obiekty proxy odpowiadające obiektom zwracanych przez usługę. Na przykład usługa, która zwraca zestaw danych, jest reprezentowana w projekcie jako zestaw danych; Usługa, która zwraca określony typ, jest reprezentowana w projekcie jako zwracany typ.

Źródło danych można utworzyć z następujących typów usług:

- [Usługi danych WCF](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Usługi WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- usługi sieci Web

    > [!NOTE]
    > Elementy wyświetlane w **oknie Źródła** danych zależą od danych zwracanych przez usługę. Niektóre usługi mogą nie dostarczać wystarczających informacji, aby Kreator konfiguracji **źródła** danych mógł tworzyć obiekty, które można powiązać. Jeśli na przykład usługa zwraca nietypowany zestaw danych,  po zakończeniu pracy kreatora w oknie Źródła danych nie będą wyświetlane żadne elementy. Wynika to z tego, że nietypowane zestawy danych nie zapewniają schematu, dlatego kreator nie ma wystarczającej ilości informacji, aby utworzyć źródło danych.

## <a name="data-source-for-an-object"></a>Źródło danych dla obiektu

Źródło danych można utworzyć z dowolnego obiektu, który uwidacznia jedną lub więcej właściwości publicznych, uruchamiając Kreatora konfiguracji źródła danych, a następnie wybierając typ **źródła** danych Obiekt.  Wszystkie właściwości publiczne obiektu są wyświetlane w **oknie Źródła** danych. Jeśli korzystasz z Entity Framework i wygenerowano model, w tym miejscu znajdziesz klasy jednostek, które są źródłami danych dla aplikacji.

Na stronie **Wybierz obiekty danych** rozwiń węzły w widoku drzewa, aby zlokalizować obiekty, z które chcesz powiązać. Widok drzewa zawiera węzły dla projektu oraz zestawów i innych projektów, do których odwołuje się projekt.

Jeśli chcesz powiązać z obiektem w zestawie lub projekcie, który  nie jest  wyświetlany w widoku drzewa, kliknij przycisk Dodaj odwołanie i użyj okna dialogowego Dodawanie odwołania, aby dodać odwołanie do zestawu lub projektu. Po dodaniu odwołania zestaw lub projekt zostanie dodany do widoku drzewa.

> [!NOTE]
> Może być konieczne skompilowanie projektu zawierającego obiekty, zanim obiekty pojawią się w widoku drzewa.

> [!NOTE]
> Aby zapewnić obsługę powiązania danych przeciągania i upuszczania, obiekty implementowane przez <xref:System.ComponentModel.ITypedList> interfejs lub muszą mieć konstruktor <xref:System.ComponentModel.IListSource> domyślny. W przeciwnym Visual Studio nie można utworzyć wystąpienia obiektu źródła danych i podczas przeciągania elementu na powierzchnię projektową jest wyświetlany błąd.

## <a name="data-source-for-a-sharepoint-list"></a>Źródło danych dla listy programu SharePoint

Źródło danych można utworzyć z listy programu  SharePoint, uruchamiając Kreatora konfiguracji źródła danych i wybierając typ źródła danych programu **SharePoint.** Program SharePoint uwidacznia dane za pośrednictwem WCF Data Services, więc tworzenie źródła danych programu SharePoint jest takie samo jak tworzenie źródła danych z usługi. Wybranie elementu programu SharePoint w Kreatorze konfiguracji źródła danych powoduje otwarcie **okna dialogowego** Dodaj odwołanie do usługi, w którym można nawiązać połączenie z usługą danych programu  **SharePoint,** wskazując serwer programu SharePoint. Wymaga to zestawu SHAREPoint SDK.

## <a name="see-also"></a>Zobacz też

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

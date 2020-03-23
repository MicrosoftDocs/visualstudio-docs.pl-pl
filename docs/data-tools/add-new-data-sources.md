---
title: Dodawanie nowych źródeł danych
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 555d32eb295e944060d2efe0b843e9d157b7c675
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302253"
---
# <a name="add-new-data-sources"></a>Dodawanie nowych źródeł danych

W kontekście narzędzi danych platformy .NET w programie Visual Studio termin *źródło danych* odnosi się do obiektów .NET, które łączą się z magazynem danych i udostępniają dane aplikacji .NET. Projektanci programu Visual Studio mogą korzystać z danych wyjściowych źródła danych do generowania kodu standardowego, który wiąże dane z formularzami podczas przeciągania i upuszczania obiektów bazy danych z okna **Źródła danych.** Tego rodzaju źródłem danych może być:

- Klasa w modelu entity framework, który jest skojarzony z pewnego rodzaju bazy danych.

- Zestaw danych, który jest skojarzony z pewnego rodzaju bazy danych.

- Klasa reprezentująca usługę sieciową, taką jak usługa danych Windows Communication Foundation (WCF) lub usługa REST.

- Klasa reprezentująca usługę programu SharePoint.

- Klasa lub kolekcja w rozwiązaniu.

> [!NOTE]
> Jeśli nie używasz funkcji wiązania danych, zestawów danych, entity framework, LINQ do SQL, WCF lub SharePoint, pojęcie "źródło danych" nie ma zastosowania. Wystarczy połączyć się bezpośrednio z bazą danych przy użyciu SQLCommand obiektów i komunikować się bezpośrednio z bazą danych.

Źródła danych są tworzę i edytowane przy użyciu **Kreatora konfiguracji źródła danych** w aplikacji Windows Forms lub Windows Presentation Foundation. W przypadku programu Entity Framework najpierw utwórz klasy encji, a następnie uruchom kreatora, wybierając **pozycję Project** > **Add New Data Source** (opisaną bardziej szczegółowo w dalszej części tego artykułu).

![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Data Sources — Okno

Po utworzeniu źródła danych pojawia się ono w oknie narzędzia **Źródła danych.**

> [!TIP]
> Aby otworzyć okno **Źródła danych,** upewnij się, że projekt jest otwarty, a następnie naciśnij **klawisz Shift**+**Alt**+**D** lub wybierz pozycję **Wyświetl** > inne**źródła danych**systemu**Windows** > .

Źródło danych z okna **Źródła danych** można przeciągnąć na powierzchnię projektu formularza lub formant. Powoduje to, że kod standardowy do generowania, który wyświetla dane z magazynu danych.

Na poniższej ilustracji przedstawiono zestaw danych, który został upuszczony do formularza systemu Windows. Jeśli wybierzesz **F5** w aplikacji, dane z podstawowej bazy danych pojawią się w formantach formularza.

![Operacja przeciągania źródła danych](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Źródło danych dla bazy danych lub pliku bazy danych

Można utworzyć zestaw danych lub model entity framework do użycia jako źródło danych dla bazy danych lub pliku bazy danych.

### <a name="dataset"></a>Dataset

Aby utworzyć zestaw danych jako źródło danych, uruchom **Kreatora konfiguracji źródła danych,** wybierając pozycję **Project** > **Add New Data Source**. Wybierz typ źródła danych **bazy danych** i postępuj zgodnie z monitami, aby określić nowe lub istniejące połączenie bazy danych lub plik bazy danych.

### <a name="entity-classes"></a>Klasy jednostek

Aby utworzyć model struktury encji jako źródło danych:

1. Uruchom **Kreatora modeli danych encji,** aby utworzyć klasy encji. Wybierz **pozycję Project** > **Add New Item** > **ADO.NET Entity Data Model**.

   ![Element projektu nowego modelu struktury encji](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Wybierz metodę, według której chcesz wygenerować model.

   ![Kreator modelu danych encji](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Dodaj model jako źródło danych. Wygenerowane klasy są wyświetlane w **Kreatorze konfiguracji źródła danych** po wybraniu kategorii **Obiekty.**

   ![Kreator konfiguracji źródła danych z klasami encji](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Źródło danych dla usługi

Aby utworzyć źródło danych z usługi, uruchom **Kreatora konfiguracji źródła danych** i wybierz typ źródła danych **usługi.** Jest to tylko skrót do okna dialogowego Dodawanie odwołania do **usługi,** do którego można również uzyskać dostęp, klikając prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierając pozycję **Dodaj odwołanie do usługi**.

Podczas tworzenia źródła danych z usługi visual studio dodaje odwołanie do usługi do projektu. Visual Studio tworzy również obiekty proxy, które odpowiadają obiektom, które zwraca usługa. Na przykład usługa, która zwraca zestaw danych jest reprezentowana w projekcie jako zestaw danych; usługa, która zwraca określonego typu jest reprezentowana w projekcie jako typ zwracany.

Źródło danych można utworzyć z następujących typów usług:

- [Usługi danych WCF](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Usługi WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Usługi sieci Web

    > [!NOTE]
    > Elementy, które pojawiają się w oknie Źródła danych są **zależne** od danych, które zwraca usługa. Niektóre usługi mogą nie dostarczać wystarczających informacji dla **Kreatora konfiguracji źródła danych** do tworzenia obiektów, które można powiązać. Na przykład jeśli usługa zwraca zestaw danych bez typu, żadne elementy nie są wyświetlane w oknie **Źródła danych** po zakończeniu pracy kreatora. Dzieje się tak, ponieważ zestawy danych bez typu nie zapewniają schematu, dlatego kreator nie ma wystarczającej ilości informacji do utworzenia źródła danych.

## <a name="data-source-for-an-object"></a>Źródło danych dla obiektu

Źródło danych można utworzyć z dowolnego obiektu, który udostępnia jedną lub więcej właściwości publicznych, uruchamiając **Kreatora konfiguracji źródła danych,** a następnie wybierając typ źródła danych **obiektu.** Wszystkie właściwości publiczne obiektu są wyświetlane w oknie **Źródła danych.** Jeśli używasz entity framework i wygenerował model, jest to, gdzie można znaleźć klasy jednostek, które są źródła danych dla aplikacji.

Na stronie **Zaznacz obiekty danych** rozwiń węzły w widoku drzewa, aby zlokalizować obiekty, z którymi chcesz powiązać. Widok drzewa zawiera węzły dla projektu i dla zestawów i innych projektów, do których odwołuje się projekt.

Jeśli chcesz powiązać z obiektem w zestawie lub projekcie, który nie pojawia się w widoku drzewa, kliknij przycisk **Dodaj odwołanie** i użyj **okna dialogowego Dodaj odwołanie,** aby dodać odwołanie do zestawu lub projektu. Po dodaniu odwołania zestaw lub projekt jest dodawany do widoku drzewa.

> [!NOTE]
> Może być konieczne zbudowanie projektu zawierającego obiekty, zanim obiekty pojawią się w widoku drzewa.

> [!NOTE]
> Aby obsługiwać powiązanie danych przeciągania <xref:System.ComponentModel.ITypedList> i <xref:System.ComponentModel.IListSource> upuszczania, obiekty implementują lub interfejs musi mieć domyślny konstruktor. W przeciwnym razie program Visual Studio nie może utworzyć wystąpienia obiektu źródła danych i wyświetla błąd podczas przeciągania elementu na powierzchnię projektu.

## <a name="data-source-for-a-sharepoint-list"></a>Źródło danych dla listy programu SharePoint

Źródło danych z listy programu SharePoint można utworzyć, uruchamiając **Kreatora konfiguracji źródła danych** i wybierając typ źródła danych **programu SharePoint.** Program SharePoint udostępnia dane za pośrednictwem usług WCF Data Services, więc utworzenie źródła danych programu SharePoint jest takie samo jak tworzenie źródła danych z usługi. Wybranie elementu **programu SharePoint** w **Kreatorze konfiguracji źródła danych** powoduje otwarcie okna dialogowego Dodawanie odwołania do **usługi,** w którym łączysz się z usługą danych programu SharePoint, wskazując serwer programu SharePoint. Wymaga to sdk programu SharePoint.

## <a name="see-also"></a>Zobacz też

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

---
title: Dodawanie nowych źródeł danych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1131f6d569d01787d26bea7dde1c993401ce9580
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670176"
---
# <a name="add-new-data-sources"></a>Dodawanie nowych źródeł danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W kontekście programu .NET data tools w programie Visual Studio termin *źródła danych* odwołuje się do obiektów platformy .NET, połączyć się z magazynem danych, które udostępniają dane do aplikacji .NET. Projektantów programu Visual Studio mogą wykorzystywać dane wyjściowe źródła danych, aby wygenerować standardowy kod, który powiąże dane do formularzy podczas przeciągania i upuszczania obiektów bazy danych z **źródeł danych** okna. Tego rodzaju źródła danych może być:  
  
-   Klasa w modelu Entity Framework, który jest skojarzony z pewnego rodzaju bazy danych.  
  
-   Zestaw danych, który jest skojarzony z pewnego rodzaju bazy danych.  
  
-   Klasa, która reprezentuje usługę sieciową, takich jak usługi danych usługi Windows Communication Foundation (WCF) lub usługi REST.  
  
-   Klasa, która reprezentuje usługę programu SharePoint.  
  
-   Klasa lub kolekcji w rozwiązaniu.  
  
> [!NOTE]
>  Jeśli nie używasz funkcji wiązania danych, zestawy danych, platformy Entity Framework LINQ to SQL, WCF lub programu SharePoint, pojęcie "źródło danych" nie ma zastosowania. Po prostu Połącz bezpośrednio z bazą danych przy użyciu obiektów klasy SQLCommand i komunikować się bezpośrednio z bazy danych.  
  
 Możesz tworzyć i edytować źródła danych za pomocą **Kreatora konfiguracji źródła danych** w aplikacji Windows Forms lub Windows Presentation Foundation. Entity Framework, należy najpierw utworzyć swoje klas jednostek, a następnie uruchomić kreatora, wybierając **projektu** > **Dodaj nowe źródło danych** (opisany bardziej szczegółowo w dalszej części tego artykułu).  
  
 ![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png "Kreatora konfiguracji źródła danych")  
  
 Po utworzeniu źródła danych, zostanie wyświetlony w **źródeł danych** okno narzędzi (Shift + Alt + D lub **widoku** > **Windows inne**  >  **Źródła danych**). Można przeciągnąć źródła danych z **źródeł danych** okna na powierzchnię projektową formularza lub formantu. Powoduje to, że schematyczny kod służący do wygenerowania — kod, który wyświetla dane, które pochodzą z magazynu danych dla użytkownika. Poniższa ilustracja przedstawia zestaw danych, który został porzucony w formularzu Windows. Jeśli wybrano F5 w aplikacji, danych z bazy danych pojawią się w kontrolkach formularza.  
  
 ![Źródło danych operacji przeciągania](../data-tools/media/raddata-data-source-drag-operation.png "operacji przeciągania raddata źródła danych")  
  
## <a name="data-source-for-a-database-or-a-database-file"></a>Źródło danych dla bazy danych lub plik bazy danych  
  
### <a name="dataset"></a>Zestaw danych  
 Aby utworzyć zestaw danych jako źródła danych, uruchom **Kreatora konfiguracji źródła danych** (**projektu** > **Dodaj nowe dane** źródła) i wybierz polecenie  **Baza danych** typ źródła danych. Postępuj zgodnie z monitami, aby określić połączenia nowej lub istniejącej bazy danych lub plik bazy danych.  
  
### <a name="entity-classes"></a>Klas jednostek  
 Aby utworzyć model Entity Framework jako źródło danych, najpierw uruchom **Kreator modelu Entity Data Model** do tworzenia klas jednostek (**projektu** > **Dodaj nowy element**  >  **Modelu danych jednostki ADO.NET**).  
  
 ![Nowy element projektu modelu Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata nowej struktury jednostki modelu projektu elementu")  
  
 Wybierz metodę, za pomocą którego chcesz wygenerować model.  
  
 ![Kreator modelu Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png "raddata Kreator modelu Entity Data Model")  
  
 Model można dodać jako źródła danych. Klasy, które zostały wygenerowane są wyświetlane w **Kreatora konfiguracji źródła danych** po wybraniu **obiektów** kategorii.  
  
 ![Kreator konfiguracji źródła danych przy użyciu klas jednostek](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata Kreatora konfiguracji źródła danych przy użyciu klas jednostek")  
  
## <a name="data-source-for-a-service"></a>Źródło danych dla usługi  
 Aby utworzyć źródło danych z usługi, uruchom **Kreatora konfiguracji źródła danych** i wybierz polecenie **usługi** typ źródła danych. Jest to tak naprawdę po prostu skrótem do **Dodaj odwołanie do usługi** okno dialogowe, które można również przejść, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **Dodaj odwołanie do usługi** .  
  
 Po utworzeniu źródła danych z usługi Visual Studio dodaje odwołanie do usługi do projektu. Visual Studio tworzy również obiekty proxy, które odnoszą się do obiektów, które usługa zwraca. Na przykład usługa, która zwraca zestaw danych jest reprezentowana w projekcie jako zestaw danych; Usługa, która zwraca określony typ jest reprezentowana w projekcie jako typ zwracany.  
  
 Można utworzyć źródło danych z następujących rodzajów usług:  
  
-   Usługi danych WCF. Aby uzyskać więcej informacji, zobacz [Przegląd](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).  
  
-   Usługi danych WCF. Aby uzyskać więcej informacji, zobacz [Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Usługi sieci Web.  
  
    > [!NOTE]
    >  Elementy, które pojawiają się w **źródeł danych** są zależne od danych zwracanemu przez usługę. Niektóre usługi mogą nie dostarczać wystarczających informacji dla **Kreatora konfiguracji źródła danych** do tworzenia obiektów, które można powiązać. Na przykład, jeśli usługa zwraca zestaw danych bez typu, żadne elementy nie pojawią się w **źródeł danych** okno po zakończeniu działania kreatora. Jest to spowodowane nietypizowane zestawy danych są oferowane schematem i dlatego Kreator nie ma wystarczających informacji, aby utworzyć źródło danych.  
  
## <a name="data-source-for-an-object"></a>Źródło danych obiektu  
 Można utworzyć źródło danych z dowolnego obiektu, który udostępnia jedną lub więcej właściwości publicznych uruchamiając **Kreatora konfiguracji źródła danych** , a następnie wybierając **obiektu** typ źródła danych. Wszystkie publiczne właściwości obiektu są wyświetlane w **źródeł danych** okna.   Jeśli są używający narzędzia Entity Framework i wygenerowaniu modelu, oznacza to, gdzie znaleźć klas jednostek, które będą znajdować się źródła danych dla aplikacji.  
  
 Na **wybierz obiekty danych** stronie, a następnie rozwiń węzły w widoku drzewa do lokalizowania obiektów, które chcesz powiązać. Widok drzewa zawiera węzły w projekcie, a w przypadku zestawów i inne projekty, które są przywoływane przez projekt.  
  
 Jeśli chcesz powiązać z obiektem w zestaw lub projekt, który nie jest wyświetlana w widoku drzewa, kliknij przycisk **Dodaj odwołanie** i używać **Dodaj odwołanie — okno dialogowe** można dodać odwołania do zestawu lub projektu. Po dodaniu odwołania, zestaw lub projekt jest dodawany do widoku drzewa.  
  
> [!NOTE]
>  Może być konieczne do tworzenia projektu, który zawiera obiekty, zanim obiekty zostaną wyświetlone w widoku drzewa.  
  
> [!NOTE]
>  Do obsługi powiązania danych przeciągnij i upuść obiekty, które implementują <xref:System.ComponentModel.ITypedList> lub <xref:System.ComponentModel.IListSource> interfejsu należy zastosować Konstruktor domyślny. W przeciwnym razie program Visual Studio nie można utworzyć wystąpienia obiektu źródła danych i zostanie wyświetlony błąd, jeśli przeciągniesz element do powierzchni projektowej.  
  
## <a name="data-source-for-a-sharepoint-list"></a>Źródło danych dla listy programu SharePoint  
 Można utworzyć źródło danych z listy programu SharePoint, uruchamiając **Kreatora konfiguracji źródła danych** i wybierając polecenie **SharePoint** typ źródła danych. SharePoint udostępnia dane za pomocą [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], dzięki czemu tworzenie źródła danych programu SharePoint jest taka sama, jak podczas tworzenia źródła danych z usługi. Wybieranie **SharePoint** pozycja **Kreatora konfiguracji źródła danych** otwiera **Dodaj odwołanie do usługi** okno dialogowe, którego następuje połączenie z usługą danych programu SharePoint poprzez wskazanie serwera SharePoint.  Ta migracja wymaga zestawu SDK programu SharePoint.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

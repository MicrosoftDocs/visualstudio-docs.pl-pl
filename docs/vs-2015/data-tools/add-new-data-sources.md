---
title: Dodawanie nowych źródeł danych | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85c07ad7995bc614df4b988bb17fa8977452b5d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673064"
---
# <a name="add-new-data-sources"></a>Dodawanie nowych źródeł danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W kontekście narzędzi .NET Data Tools w programie Visual Studio termin *Źródło danych* odnosi się do obiektów .NET, które łączą się z magazynem danych i uwidaczniają dane dla aplikacji .NET. Projektanci programu Visual Studio mogą wykorzystać dane wyjściowe źródła danych w celu wygenerowania kodu standardowego, który wiąże dane z formularzami podczas przeciągania i upuszczania obiektów bazy danych z okna **źródła danych** . Ten rodzaj źródła danych może być następujący:

- Klasa w modelu Entity Framework, która jest skojarzona z pewnym rodzajem bazy danych.

- Zestaw danych, który jest skojarzony z pewnym rodzajem bazy danych.

- Klasa, która reprezentuje usługę sieciową, taką jak usługa danych Windows Communication Foundation (WCF) lub usługa REST.

- Klasa, która reprezentuje usługę programu SharePoint.

- Klasa lub kolekcja w rozwiązaniu.

> [!NOTE]
> Jeśli nie korzystasz z funkcji, zestawów danych, Entity Framework, LINQ to SQL, WCF ani programu SharePoint, pojęcie "Źródło danych" nie ma zastosowania. Po prostu Połącz się bezpośrednio z bazą danych przy użyciu obiektów SqlCommand i Komunikuj się bezpośrednio z bazą danych.

 Źródła danych można tworzyć i edytować za pomocą **Kreatora konfiguracji źródła danych** w aplikacji Windows Forms lub Windows Presentation Foundation. Aby uzyskać Entity Framework, najpierw utwórz klasy jednostek, a następnie uruchom kreatora, wybierając pozycję **Project**  > **Dodaj nowe źródło danych** (opisane w dalszej części tego artykułu).

 ![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png "Kreator konfiguracji źródła danych")

 Po utworzeniu źródła danych pojawia się ono w oknie narzędzia **źródła danych** (Shift + Alt + D lub **Widok**  >  inne**Źródło danych** > **systemu Windows** ). Możesz przeciągnąć źródło danych z okna **źródła danych** na powierzchnię lub kontrolkę projektu formularza. Powoduje to wygenerowanie kodu standardowego — kod, który wyświetla dane, które pochodzą z magazynu danych do użytkownika. Na poniższej ilustracji przedstawiono zestaw danych, który został porzucony w formularzu systemu Windows. W przypadku wybrania opcji F5 w aplikacji dane z podstawowej bazy danych pojawią się w kontrolkach formularza.

 ![Operacja przeciągania źródła danych](../data-tools/media/raddata-data-source-drag-operation.png "raddata operacji przeciągania źródła danych")

## <a name="data-source-for-a-database-or-a-database-file"></a>Źródło danych dla bazy danych lub pliku bazy danych

### <a name="dataset"></a>Zestaw danych
 Aby utworzyć zestaw danych jako źródło danych, uruchom **Kreatora konfiguracji źródła danych** (**projekt**  > **Dodaj nowe źródło danych** ) i wybierz typ źródła dane **bazy** danych. Postępuj zgodnie z monitami, aby określić nowe lub istniejące połączenie z bazą danych albo plik bazy danych.

### <a name="entity-classes"></a>Klasy jednostek
 Aby utworzyć model Entity Framework jako źródło danych, najpierw uruchom **kreatora Entity Data Model** , aby utworzyć klasy jednostek (**projekt**  > **dodaj nowy element**  > **ADO.NET Entity Data Model**).

 ![Nowy element projektu Entity Framework modelu](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata nowy element projektu modelu Entity Framework")

 Wybierz metodę, za pomocą której chcesz wygenerować model.

 ![Kreator Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png "Kreator Entity Data Model raddata")

 Dodaj model jako źródło danych. Klasy, które zostały wygenerowane, są wyświetlane w **Kreatorze konfiguracji źródła danych** po wybraniu kategorii **obiekty** .

 ![Kreator konfiguracji źródła danych z klasami jednostek](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "Kreator konfiguracji źródła danych raddata z klasami jednostek")

## <a name="data-source-for-a-service"></a>Źródło danych dla usługi
 Aby utworzyć źródło danych z usługi, uruchom **Kreatora konfiguracji źródła danych** i wybierz typ źródła danych **usługi** . Jest to tylko skrót do okna dialogowego **Dodaj odwołanie do usługi** , do którego można uzyskać dostęp, klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierając pozycję **Dodaj odwołanie do usługi**.

 Podczas tworzenia źródła danych z usługi program Visual Studio dodaje odwołanie do usługi do projektu. Program Visual Studio tworzy również obiekty proxy odpowiadające obiektom zwracanym przez usługę. Na przykład usługa zwracająca zestaw danych jest reprezentowana w projekcie jako zestaw danych; Usługa zwracająca konkretny typ jest reprezentowana w projekcie jako zwracany typ.

 Można utworzyć źródło danych z następujących typów usług:

- Usługi danych programu WCF. Aby uzyskać więcej informacji, zobacz [Omówienie](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- Usługi danych programu WCF. Aby uzyskać więcej informacji, zobacz [Windows Communication Foundation usług i usługi danych programu WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).

- Usługi sieci Web.

    > [!NOTE]
    > Elementy wyświetlane w oknie **źródła danych** są zależne od danych zwracanych przez usługę. Niektóre usługi mogą nie zapewniać wystarczającej ilości informacji dla **Kreatora konfiguracji źródła danych** , aby utworzyć obiekty możliwe do powiązania. Na przykład jeśli usługa zwraca zestaw danych bez typu, w oknie **źródła danych** nie będą wyświetlane żadne elementy po zakończeniu pracy kreatora. Wynika to z faktu, że niewpisane zestawy danych nie udostępniają schematu, w związku z czym Kreator nie ma wystarczających informacji do utworzenia źródła danych.

## <a name="data-source-for-an-object"></a>Źródło danych dla obiektu
 Można utworzyć źródło danych z dowolnego obiektu, który uwidacznia co najmniej jedną właściwość publiczną, uruchamiając **Kreatora konfiguracji źródła danych** , a następnie wybierając typ źródła danych **obiektu** . Wszystkie właściwości publiczne obiektu są wyświetlane w oknie **źródła danych** .   Jeśli używasz Entity Framework i wygenerowałeś model, w tym miejscu znajdziesz klasy jednostek, które będą źródłami danych aplikacji.

 Na stronie **Wybierz obiekty danych** rozwiń węzły w widoku drzewa, aby zlokalizować obiekty, do których chcesz utworzyć powiązanie. Widok drzewa zawiera węzły dla projektu oraz dla zestawów i innych projektów, do których odwołuje się projekt.

 Jeśli chcesz powiązać z obiektem w zestawie lub projekcie, który nie jest wyświetlany w widoku drzewa, kliknij przycisk **Dodaj odwołanie** i użyj okna **dialogowego Dodaj odwołanie** , aby dodać odwołanie do zestawu lub projektu. Po dodaniu odwołania zestaw lub projekt zostanie dodany do widoku drzewa.

> [!NOTE]
> Może być konieczne skompilowanie projektu zawierającego obiekty przed wyświetleniem ich w widoku drzewa.

> [!NOTE]
> Aby można było obsługiwać powiązanie danych przeciągnij i upuść, obiekty implementujące interfejs <xref:System.ComponentModel.ITypedList> lub <xref:System.ComponentModel.IListSource> muszą mieć konstruktora domyślnego. W przeciwnym razie program Visual Studio nie może utworzyć wystąpienia obiektu źródła danych, a po przeciągnięciu elementu na powierzchnię projektu zostanie wyświetlony komunikat o błędzie.

## <a name="data-source-for-a-sharepoint-list"></a>Źródło danych dla listy programu SharePoint
 Można utworzyć źródło danych z listy programu SharePoint, uruchamiając **Kreatora konfiguracji źródła danych** i wybierając typ źródła danych **programu SharePoint** . Program SharePoint udostępnia dane za pośrednictwem [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], więc tworzenie źródła danych programu SharePoint jest takie samo jak w przypadku tworzenia źródła danych z usługi. Wybranie elementu **programu SharePoint** w **Kreatorze konfiguracji źródła danych** powoduje otwarcie okna dialogowego **Dodaj odwołanie do usługi** , w którym można nawiązać połączenie z usługą danych programu SharePoint, wskazując serwerowi programu SharePoint.  Wymaga to zestawu SDK programu SharePoint.

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

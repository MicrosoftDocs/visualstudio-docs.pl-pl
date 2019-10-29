---
title: Integrowanie danych firmowych z programem SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 06d9e8059db8daa1c27b8c1d5fecc50940b7facb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986391"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrowanie danych firmowych z programem SharePoint
  Dane biznesowe można zintegrować z programem SharePoint. Dane biznesowe mogą pochodzić z aplikacji serwera zaplecza, takich jak [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel i SAP lub usługa sieci Web. Użytkownicy mogą wyświetlać, dodawać, aktualizować i usuwać dane biznesowe przy użyciu list zewnętrznych lub danych firmowych składniki Web Part w programie SharePoint.  Użytkownicy mogą również uzyskiwać dostęp do tych danych w trybie offline w aplikacji Microsoft Office, takiej jak Microsoft Outlook. Aby uzyskać więcej informacji, zobacz [gdzie można pokazać dane zewnętrzne](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Aby zintegrować dane z programem SharePoint, Utwórz model usługi łączności danych biznesowych (BDC). Usługa BDC jest aplikacją w programie SharePoint, która przechowuje informacje o danych w aplikacjach biznesowych. Aby uzyskać więcej informacji, zobacz [Usługa łączności danych biznesowych (BDC)](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Modele w programie Visual Studio
 Modele w programie Visual Studio umożliwiają pisanie niestandardowego kodu w celu pobierania i aktualizowania danych z źródeł danych zaplecza. Można również agregować dane z wielu źródeł danych. Można na przykład wyświetlić listę klientów, którzy zawierają dane z bazy danych [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] i usługi sieci Web.

 Można również zaimportować modele, które są już wdrożone w programie SharePoint. Po zaimportowaniu modelu można dodać kod niestandardowy lub po prostu użyć programu Visual Studio do spakowania i wdrożenia modelu w wielu farmach serwerów programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Projektowanie modelu w programie Visual Studio
 Model można zaprojektować za pomocą projektanta i kilku okien narzędzi. Podczas projektowania modelu program Visual Studio generuje kod XML modelu. Aby uzyskać więcej informacji, zobacz [Omówienie narzędzi projektowania modelu usługi BDC](../sharepoint/bdc-model-design-tools-overview.md).

 Model zawiera jednostki i metody.

### <a name="entities"></a>obiekty
 Jednostka opisuje kolekcję pól. Na przykład jednostka może reprezentować tabelę w bazie danych. Jednostka zostanie wyświetlona jako zewnętrzny typ zawartości w programie SharePoint. Aby uzyskać więcej informacji na temat typów zawartości zewnętrznej, zobacz [co to są typy zawartości zewnętrznej?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Metody
 Metoda umożliwia klientom typu zawartości zewnętrznej wykonywanie akcji na polach jednostki. Na przykład Metoda Aktualizator może umożliwić użytkownikom zmianę adresu i daty urodzenia klienta, gdzie `Address` i `BirthDate` są polami jednostki `Customer`.

 Program Visual Studio generuje plik kodu usługi dla każdej jednostki w modelu. Po dodaniu metody do modelu program Visual Studio generuje odpowiednią metodę w pliku kodu usługi. Dodaj kod do każdej metody, aby wykonać odpowiednie zadanie. Na przykład w przypadku dodania metody Creator do modelu program Visual Studio generuje metodę Creator w pliku kodu usługi. Ta metoda jest wywoływana przez usługę BDC, gdy użytkownik kliknie przycisk **nowy element** na liście, która jest oparta na modelu. W związku z tym Dodaj kod do metody Creator, która dodaje nowe dane do źródła danych. Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie modelu łączności danych firmy](../sharepoint/creating-a-business-data-connectivity-model.md)|Pokazuje, jak utworzyć nowy model lub zaimportować model eksportowany z programu SharePoint.|
|[Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)|Wyjaśniono, jak zaprojektować elementy modelu przy użyciu narzędzi do projektowania programu Visual Studio.|
|[Kiedy używać programu SharePoint Designer a Visual Studio podczas kompilowania rozwiązań przy użyciu usług BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Pomaga zdecydować, czy należy użyć programu Visual Studio, czy utworzyć model dla usługi BDC przy użyciu programu SharePoint Designer.|

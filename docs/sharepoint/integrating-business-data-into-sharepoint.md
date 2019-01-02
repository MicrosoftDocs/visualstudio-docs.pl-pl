---
title: Integrowanie danych biznesowych programu SharePoint | Dokumentacja firmy Microsoft
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 194f2e0c88a0cbce9ef34f77246cf7969066833e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934443"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrowanie danych biznesowych programu SharePoint
  Pozwala integrować dane biznesowe w programie SharePoint. Dane biznesowe mogą pochodzić z serwerów zaplecza aplikacji, takich jak [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel i SAP, lub usługi sieci Web. Użytkownicy mogą wyświetlić, dodać, aktualizować lub usuwać dane firmy przy użyciu list zewnętrznych lub składniki Web Part danych biznesowych w programie SharePoint.  Użytkownicy mogą również dostęp do tych danych w trybie offline w aplikacji pakietu Microsoft Office, takich jak Microsoft Outlook. Aby uzyskać więcej informacji, zobacz [gdzie można możesz wyświetlić dane zewnętrzne](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Do integracji danych programu SharePoint, należy utworzyć model usługi łączności danych biznesowych (BDC). Usługa łączności danych biznesowych jest aplikacji w programie SharePoint, która przechowuje informacje dotyczące danych w aplikacjach biznesowych. Aby uzyskać więcej informacji, zobacz [usługi łączności danych biznesowych (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Modele w programie Visual Studio  
 Modele w programie Visual Studio umożliwiają pisanie kodu niestandardowego w celu pobierania i aktualizowania danych ze źródeł danych zaplecza. Można również zagregowanych danych z wielu źródeł danych. Na przykład, można wyświetlić listę klientów, które zawiera dane z [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] bazy danych i usług sieci Web.  
  
 Można również zaimportować modeli, które są już wdrożone w programie SharePoint. Po zaimportowaniu modelu, można dodać niestandardowy kod lub po prostu użyć programu Visual Studio, pakowanie i wdrażanie modelu na wiele farm serwerów programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="design-a-model-in-visual-studio"></a>Projektowanie modelu w programie Visual Studio
 Można zaprojektować model przy użyciu projektanta i kilkoma oknami narzędzi. Podczas projektowania modelu programu Visual Studio generuje plik XML modelu. Aby uzyskać więcej informacji, zobacz [Omówienie narzędzia projektowania modelu usługi łączności danych biznesowych](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Model zawiera jednostek i metody.  
  
### <a name="entities"></a>Jednostki  
 Jednostki w tym artykule opisano kolekcji pól. Na przykład jednostka może reprezentować tabelę w bazie danych. Jednostka jest wyświetlana jako typu zawartości zewnętrznej w SharePoint. Aby uzyskać więcej informacji na temat typów zawartości zewnętrznej zobacz [co to są typy zawartości zewnętrznej?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Metody  
 Metoda umożliwia odbiorcy zewnętrznego typu zawartości, do wykonania akcji w polach jednostki. Na przykład metody Updater mogą umożliwić użytkownikom zmienić adres i urodzenia Data klienta gdzie `Address` i `BirthDate` są pola `Customer` jednostki.  
  
 Program Visual Studio generuje plik kodu usługi dla każdej jednostki w modelu. Po dodaniu metody do modelu programu Visual Studio generuje odpowiedniej metody w pliku kodu usługi. Dodaj kod do każdej metody, aby wykonać odpowiednie zadanie. Na przykład jeśli dodasz metody Creator do modelu programu Visual Studio generuje metody Creator w pliku kodu usługi. Ta metoda jest wywoływana przez usługi BDC, gdy użytkownik kliknie **nowy element** przycisku na liście, która jest oparta na modelu. W związku z tym należy dodać kod do metody Creator, który dodaje nowe dane do źródła danych. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)|Pokazuje, jak utworzyć nowy model lub zaimportować modelu, który można eksportować z programu SharePoint.|  
|[Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)|Wyjaśnia, jak zaprojektować elementów modelu przy użyciu narzędzi do projektowania programu Visual Studio.|  
|[Kiedy vs Użyj programu SharePoint Designer. Rozwiązania Visual Studio Budując przy użyciu usług łączności Biznesowej](http://go.microsoft.com/fwlink/?LinkID=183448)|Ułatwia podjęcie decyzji o użyciu programu Visual Studio lub używanie programu SharePoint Designer na potrzeby tworzenia modelu łączności danych biznesowych.|  

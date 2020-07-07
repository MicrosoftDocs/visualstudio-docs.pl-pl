---
title: 'Instrukcje: Dodawanie lub usuwanie połączeń programu SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cec1389294c8baf169db055acb87619114d7d19b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014568"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Instrukcje: Dodawanie lub usuwanie połączeń programu SharePoint
  Eksplorator serwera umożliwia przeglądanie witryn programu SharePoint oraz połączeń danych. Jednak zanim będzie można przeglądać zawartość witryny programu SharePoint, należy ją dodać do węzła **połączenia programu SharePoint** .

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Aby dodać witrynę programu SharePoint do węzła połączenia programu SharePoint

1. Na pasku menu wybierz **Widok**, **Eksplorator serwera**.

2. W **Eksplorator serwera**wybierz węzeł **połączenia programu SharePoint** , a następnie na pasku menu wybierz kolejno opcje **Narzędzia**  >  **Dodaj połączenie programu SharePoint**.

3. W polu **Dodaj połączenie programu SharePoint** wprowadź [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] dla witryny programu SharePoint (na przykład http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Aby usunąć witrynę programu SharePoint z węzła połączenia programu SharePoint

1. Na pasku menu wybierz **Widok**, **Eksplorator serwera** otworzyć **Eksplorator serwera**.

2. Rozwiń węzeł **połączenia programu SharePoint** , aby odsłonić witrynę programu SharePoint, która ma zostać usunięta z **Eksplorator serwera**.

3. Wybierz lokację, a następnie na pasku menu wybierz polecenie **Edytuj**  >  **Usuń**.

    > [!NOTE]
    > Ten krok nie powoduje usunięcia lokacji podstawowej; usuwa tylko połączenie z **Eksplorator serwera**.

## <a name="see-also"></a>Zobacz także
- [Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)

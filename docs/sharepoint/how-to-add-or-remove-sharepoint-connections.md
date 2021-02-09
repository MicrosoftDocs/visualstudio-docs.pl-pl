---
title: 'Instrukcje: Dodawanie lub usuwanie połączeń programu SharePoint | Microsoft Docs'
description: Dodawanie lub usuwanie połączeń programu SharePoint przy użyciu węzła połączenia programu SharePoint w oknie Eksplorator serwera programu Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 57ff132274ba7f720a845078b0424fe235d9c31e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923447"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Instrukcje: Dodawanie lub usuwanie połączeń programu SharePoint
  Eksplorator serwera umożliwia przeglądanie witryn programu SharePoint oraz połączeń danych. Jednak zanim będzie można przeglądać zawartość witryny programu SharePoint, należy ją dodać do węzła **połączenia programu SharePoint** .

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Aby dodać witrynę programu SharePoint do węzła połączenia programu SharePoint

1. Na pasku menu wybierz **Widok**, **Eksplorator serwera**.

2. W **Eksplorator serwera** wybierz węzeł **połączenia programu SharePoint** , a następnie na pasku menu wybierz kolejno opcje **Narzędzia**  >  **Dodaj połączenie programu SharePoint**.

3. W polu **Dodaj połączenie programu SharePoint** wprowadź [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] dla witryny programu SharePoint (na przykład http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Aby usunąć witrynę programu SharePoint z węzła połączenia programu SharePoint

1. Na pasku menu wybierz **Widok**, **Eksplorator serwera** otworzyć **Eksplorator serwera**.

2. Rozwiń węzeł **połączenia programu SharePoint** , aby odsłonić witrynę programu SharePoint, która ma zostać usunięta z **Eksplorator serwera**.

3. Wybierz lokację, a następnie na pasku menu wybierz polecenie **Edytuj**  >  **Usuń**.

    > [!NOTE]
    > Ten krok nie powoduje usunięcia lokacji podstawowej; usuwa tylko połączenie z **Eksplorator serwera**.

## <a name="see-also"></a>Zobacz też
- [Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)

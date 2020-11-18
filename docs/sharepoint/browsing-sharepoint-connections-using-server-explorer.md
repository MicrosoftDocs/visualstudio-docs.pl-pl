---
title: Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera | Microsoft Docs
description: Przeglądaj połączenia programu SharePoint przy użyciu Eksplorator serwera. Dowiedz się więcej na temat Eksplorator serwera węzłów i poleceń menu skrótów węzła.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
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
ms.openlocfilehash: 79e8d3dbc1dab865b2ab9048cea8d13c478f2a12
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849834"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera
  Teraz można przeglądać lokalne połączenia programu SharePoint w **Eksplorator serwera**. Korzystając z tej techniki, można przechodzić przez składniki witryny programu SharePoint w systemie. Składniki witryny programu SharePoint, takie jak definicje list i typy zawartości, są wyświetlane w węźle o nazwie **połączenia programu SharePoint** w widoku drzewa **Eksplorator serwera**. Aby wyświetlić **Eksplorator serwera**, na pasku menu wybierz **Widok**  >  **Eksplorator serwera**. Oprócz wyświetlania składników witryny programu SharePoint, można usunąć elementy, wyświetlić ich właściwości lub odświeżyć widok drzewa przy użyciu poleceń w menu skrótów.

> [!IMPORTANT]
> Aby przeglądać witrynę programu SharePoint, musisz być administratorem kolekcji witryn programu SharePoint i musi być uruchomiony program Visual Studio jako administrator komputera lokalnego. W przeciwnym razie lokacja zostanie wyświetlona w **Eksplorator serwera**, ale nie będzie można rozwinąć jej węzła. Aby sprawdzić, czy jesteś administratorem zbioru witryn, Otwórz witrynę w przeglądarce sieci Web, otwórz menu **Akcje witryny** , wybierz pozycję **uprawnienia lokacji**, a następnie na stronie **uprawnienia: Witryna zespołu** wybierz polecenie **Administratorzy kolekcji witryn** z grupy **Zarządzaj** na Wstążce. Twoja nazwa zostanie wyświetlona w polu tekstowym, jeśli jesteś administratorem zbioru witryn. Jeśli polecenie **Administratorzy zbioru witryn** nie pojawia się w grupie Zarządzaj na Wstążce, nie jesteś administratorem zbioru witryn i musisz uzyskać odpowiednie uprawnienia od administratora lokacji.

## <a name="server-explorer-nodes"></a>Eksplorator serwera węzły
 Każdy składnik witryny programu SharePoint jest reprezentowany przez węzeł w widoku drzewa **Eksplorator serwera** w obszarze **połączenia programu SharePoint**. Na przykład domyślne witryny programu SharePoint obejmują typ zawartości o nazwie dyskusja, która reprezentuje typ dyskusji, który jest wyświetlany na stronie **Dyskusje** w witrynie programu SharePoint. Typ zawartości dyskusji zawiera kilka pól. Aby wyświetlić te pola w **Eksplorator serwera**, rozwiń węzeł **ContentTypes** , a następnie węzeł **dyskusji** . Poniżej znajduje się kilka węzłów pól, takich jak treść, podmiot dyskusji i tytuł.

## <a name="node-shortcut-menu-commands"></a>Polecenia menu skrótów węzła
 Każdy węzeł ma menu skrótów, do których masz dostęp, klikając prawym przyciskiem myszy węzeł lub wybierając go, a następnie wybierając klawisze **SHIFT** + **F10** . Polecenia węzła mogą obejmować następujące elementy:

|Nazwa polecenia|Opis|
|------------------|-----------------|
|Odśwież|Aktualizuje widok drzewa, aby odzwierciedlić wszelkie zmiany, które mogły wystąpić od czasu ostatniego wyświetlenia węzła.|
|Usuwanie|Usuwa wybrany węzeł z widoku drzewa. **Uwaga:**  To polecenie jest włączone tylko dla połączeń programu SharePoint znajdujących się w węźle **połączenia programu SharePoint** .|
|Właściwości|Wyświetla dostępne właściwości wybranego węzła w oknie **Właściwości** . Właściwości są tylko do odczytu, a nie każdy węzeł ma skojarzone z nim właściwości.|
|Dodaj połączenie|Pozwala określić witrynę programu SharePoint, którą chcesz przeglądać. Dostępne w węźle **połączenia programu SharePoint** i węzły podrzędne lokacji.|
|Wyświetl w przeglądarce|Wyświetla wybraną listę w przeglądarce sieci Web. To polecenie jest dostępne na niektórych **listach, które** znajdują się na **listach i w bibliotekach**.|

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: Dodawanie lub usuwanie połączeń programu SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Zawiera opis czynności, które są wymagane do dodania nowej witryny programu SharePoint do węzła **połączenia programu SharePoint** w **Eksplorator serwera**.|

## <a name="see-also"></a>Zobacz także
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)

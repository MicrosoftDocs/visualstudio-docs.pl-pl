---
title: Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d3804b97967cffb299393e7e3a8866e51a2e3224
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931362"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera
  Możesz teraz przeglądać lokalnych połączeń SharePoint w **Eksploratora serwera**. Korzystając z tej techniki, możesz przejść za pośrednictwem składników witryny programu SharePoint w Twoim systemie. Składniki witryny programu SharePoint, takich jak definicje list i typów zawartości, są wyświetlane w węźle, który nosi nazwę **połączeń SharePoint** w widoku drzewa **Eksploratora serwera**. Aby wyświetlić **Eksploratora serwera**, na pasku menu wybierz **widoku** > **Eksploratora serwera**. Oprócz wyświetlania składników witryny programu SharePoint, możesz usunąć elementy, przeglądać ich właściwości lub Odśwież widok drzewa za pomocą poleceń w menu skrótów.  
  
> [!IMPORTANT]  
>  Aby przeglądać witryny programu SharePoint, musisz być administratorem zbioru witryn programu SharePoint i uruchamiania programu Visual Studio jako administrator komputera lokalnego. W przeciwnym razie pojawi się w witrynie **Eksploratora serwera**, ale nie można rozwinąć jego węzła. Aby sprawdzić, czy jesteś administratorem zbioru witryn, otwórz witrynę w przeglądarce sieci web, otwórz **Akcje witryny** menu, wybierz **uprawnienia witryny**, a następnie na **uprawnienia: Zespół witryny** wybierz **Administratorzy zbioru witryn** polecenia **Zarządzaj** grupę na Wstążce. Twoja nazwa będzie widoczna w polu tekstowym, jeśli jesteś administratorem zbioru witryn. Jeśli **Administratorzy zbioru witryn** polecenie nie pojawi się w grupie zarządzania, na Wstążce, jesteś administratorem zbioru witryn i odpowiednie uprawnienia należy uzyskać od administratora lokacji.  
  
## <a name="server-explorer-nodes"></a>Węzły w Eksploratorze serwera
 Każdy składnik witryny programu SharePoint jest reprezentowany przez węzeł w **Eksploratora serwera** drzewa widoku w obszarze **połączeń SharePoint**. Na przykład, domyślnej witryny programu SharePoint zawiera typ zawartości o nazwie dyskusji, który reprezentuje typ dyskusji, który wyświetla **dyskusje** strony w witrynie programu SharePoint. Typ zawartości Dyskusja zawiera kilka pól. Aby wyświetlić te pola w **Eksploratora serwera**, rozwiń węzeł **typów zawartości** węzła, a następnie **dyskusji** węzła. W obszarze są kilka węzłów pól, takich jak treść, temat dyskusji i tytuł.  
  
## <a name="node-shortcut-menu-commands"></a>Polecenia menu skrótów dla węzła
 Każdy węzeł ma menu skrótów, które są dostępne przez kliknięcie prawym przyciskiem myszy węzeł lub wybierając go, a następnie wybierając **Shift**+**F10** kluczy. Polecenia węzła może być następujące:  
  
|Nazwa polecenia|Opis|  
|------------------|-----------------|  
|Odśwież|Aktualizuje widok drzewa, aby odzwierciedlić zmiany, które mogły wystąpić od czasu ostatniego wyświetlania węzła.|  
|Usuwanie|Usuwa wybrany węzeł w widoku drzewa. **Uwaga:**  To polecenie jest włączone tylko na połączenia programu SharePoint, na liście **połączeń SharePoint** węzła.|  
|Właściwości|Wyświetla dostępne właściwości dla wybranego węzła w **właściwości** okna. Właściwości są wszystkie tylko do odczytu, a nie za każdy węzeł ma właściwości skojarzone z nim.|  
|Dodawanie połączenia|Umożliwia określenie witryny programu SharePoint, które chcesz przeglądać. Dostępne na **połączeń SharePoint** węzła i węzłów podrzędnych lokacji.|  
|Pokaż w przeglądarce|Wyświetla listę wybranych w przeglądarce sieci Web. To polecenie jest dostępne na niektóre listy w obszarze **Wyświetla** węzeł, który jest zawarty w **list i bibliotek**.|  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Dodawanie lub usuwanie połączeń SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|W tym artykule opisano kroki, które są wymagane, aby dodać nową witrynę programu SharePoint do **połączeń SharePoint** w węźle **Eksploratora serwera**.|  
  
## <a name="see-also"></a>Zobacz także
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  

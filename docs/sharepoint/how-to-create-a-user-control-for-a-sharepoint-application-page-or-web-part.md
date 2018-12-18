---
title: 'Porady: tworzenie kontrolki użytkownika dla strony aplikacji SharePoint lub składnika Web Part | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1e099cd5e3de88d88fa3a48b1d9b287d5d185000
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296167"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Porady: tworzenie kontrolki użytkownika dla części strony lub sieci web aplikacji programu SharePoint
  Można tworzyć niestandardowe kontrolki użytkownika, które dostarczają niestandardowych funkcjonalności dla rozwiązania SharePoint oraz można używać tych funkcjonalności ponownie w obrębie projektu. Można dołączyć kontrolki użytkownika do części sieci lub strony aplikacji, dodać inne kontrolki ASP.NET oraz SharePoint oraz zdefiniować właściwości o metody dla kontrolki. Aby uzyskać więcej informacji dotyczących kontrolek użytkownika, zobacz [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) i [kontrolki użytkownika oraz serwera w programie SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>Aby utworzyć kontrolkę użytkownika dla programu SharePoint  
  
1.  W programie Visual Studio otwórz lub utwórz projekt programu SharePoint.  
  
     Zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu.  
  
3.  Na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
4.  W **zainstalowane** okienku wybierz **Office/SharePoint** węzła.  
  
5.  Na liście szablonów programu SharePoint, wybierz opcję **kontrolki użytkownika (tylko rozwiązanie farmy)**.  
  
    > [!NOTE]  
    >  Kontrolki użytkownika działają tylko w rozwiązaniach farmy.  
  
6.  W **nazwa** , określ nazwę dla kontrolki użytkownika, a następnie wybierz **Dodaj** przycisku.  
  
     Program Visual Studio dodaje kilka folderów i plików do projektu. Aby uzyskać więcej informacji o tych plikach, zobacz [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Domyślnie plik kontrolki użytkownika pojawia się w **źródła** Widok projektanta Visual Web Developer. W tym widoku można edytować znaczniki XML kontrolki. Możesz przełączyć się do **projektowania** wyświetlić, aby wizualnie projektować kontrolkę poprzez przeciąganie kontrolek z **przybornika**. Zobacz [widoku projektu, Projektant stron internetowych](/previous-versions/aspnet/ms178149\(v\=vs.100\)).  
  
7.  Aby obsługiwać zdarzenia występujące w kontrolce, należy dodać kod do pliku kodu kontrolki użytkownika.  
  
     Ten plik pojawia się w **Eksploratora rozwiązań** pod plikiem kontrolki użytkownika i ma *.cs* lub *.vb* rozszerzenia, w zależności od języka projektu.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  

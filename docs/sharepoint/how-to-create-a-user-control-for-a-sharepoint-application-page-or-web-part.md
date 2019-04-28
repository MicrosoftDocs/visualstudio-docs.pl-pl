---
title: 'Instrukcje: Tworzenie kontrolki użytkownika dla strony aplikacji SharePoint lub składnika Web Part | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 17f8acd38df810d0ea7e5c0da2293a5de31eb281
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446507"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Instrukcje: Tworzenie kontrolki użytkownika dla części strony lub sieci web aplikacji programu SharePoint
  Można tworzyć niestandardowe kontrolki użytkownika, które dostarczają niestandardowych funkcjonalności dla rozwiązania SharePoint oraz można używać tych funkcjonalności ponownie w obrębie projektu. Można dołączyć kontrolki użytkownika do części sieci lub strony aplikacji, dodać inne kontrolki ASP.NET oraz SharePoint oraz zdefiniować właściwości o metody dla kontrolki. Aby uzyskać więcej informacji dotyczących kontrolek użytkownika, zobacz [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) i [kontrolki użytkownika oraz serwera w programie SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Aby utworzyć kontrolkę użytkownika dla programu SharePoint

1. W programie Visual Studio otwórz lub utwórz projekt programu SharePoint.

     Zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. W **Eksploratora rozwiązań**, wybierz węzeł projektu.

3. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

     **Dodaj nowy element** zostanie otwarte okno dialogowe.

4. W **zainstalowane** okienku wybierz **Office/SharePoint** węzła.

5. Na liście szablonów programu SharePoint, wybierz opcję **kontrolki użytkownika (tylko rozwiązanie farmy)**.

    > [!NOTE]
    > Kontrolki użytkownika działają tylko w rozwiązaniach farmy.

6. W **nazwa** , określ nazwę dla kontrolki użytkownika, a następnie wybierz **Dodaj** przycisku.

     Program Visual Studio dodaje kilka folderów i plików do projektu. Aby uzyskać więcej informacji o tych plikach, zobacz [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     Domyślnie plik kontrolki użytkownika pojawia się w **źródła** Widok projektanta Visual Web Developer. W tym widoku można edytować znaczniki XML kontrolki. Możesz przełączyć się do **projektowania** wyświetlić, aby wizualnie projektować kontrolkę poprzez przeciąganie kontrolek z **przybornika**. Zobacz [widoku projektu, Projektant stron internetowych](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Aby obsługiwać zdarzenia występujące w kontrolce, należy dodać kod do pliku kodu kontrolki użytkownika.

     Ten plik pojawia się w **Eksploratora rozwiązań** pod plikiem kontrolki użytkownika i ma *.cs* lub *.vb* rozszerzenia, w zależności od języka projektu.

## <a name="see-also"></a>Zobacz także
- [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)

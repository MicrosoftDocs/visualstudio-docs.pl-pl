---
title: Tworzenie kontrolki użytkownika dla strony lub składnika Web Part aplikacji SharePoint
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 2fbf1b646ae9e7fb697fcab93adfb8661a4372c6
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016968"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Instrukcje: Tworzenie kontrolki użytkownika dla strony aplikacji lub składnika sieci Web programu SharePoint
  Można tworzyć niestandardowe kontrolki użytkownika, które dostarczają niestandardowych funkcjonalności dla rozwiązania SharePoint oraz można używać tych funkcjonalności ponownie w obrębie projektu. Można dołączyć kontrolki użytkownika do części sieci lub strony aplikacji, dodać inne kontrolki ASP.NET oraz SharePoint oraz zdefiniować właściwości o metody dla kontrolki. Aby uzyskać więcej informacji dotyczących kontrolek użytkownika, zobacz [Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) oraz kontrolek [serwera w programie SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Aby utworzyć kontrolkę użytkownika dla programu SharePoint

1. W programie Visual Studio otwórz lub utwórz projekt programu SharePoint.

     Zobacz [Szablony projektów i elementów projektu programu SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. W **Eksplorator rozwiązań**wybierz węzeł projektu.

3. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

     Zostanie otwarte okno dialogowe **Dodaj nowy element** .

4. W **zainstalowanym** okienku wybierz węzeł **Office/SharePoint** .

5. Na liście szablonów programu SharePoint wybierz pozycję **Kontrola użytkownika (tylko rozwiązanie farmy)**.

    > [!NOTE]
    > Kontrolki użytkownika działają tylko w rozwiązaniach farmy.

6. W polu **Nazwa** Określ nazwę kontrolki użytkownika, a następnie wybierz przycisk **Dodaj** .

     Program Visual Studio dodaje kilka folderów i plików do projektu. Aby uzyskać więcej informacji o tych plikach, zobacz [Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     Domyślnie plik kontrolki użytkownika jest wyświetlany w widoku **Źródło** projektanta Visual Web Developer. W tym widoku można edytować znaczniki XML kontrolki. Możesz przełączyć się do widoku **projektu** , jeśli chcesz zaprojektować formant wizualnie, przeciągając kontrolki z **przybornika**. Zobacz [Widok projektu, Projektant stron sieci Web](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Aby obsługiwać zdarzenia występujące w kontrolce, należy dodać kod do pliku kodu kontrolki użytkownika.

     Ten plik jest wyświetlany w **Eksplorator rozwiązań** pod plikiem kontrolnym użytkownika i ma rozszerzenie *. cs* lub *. vb* , w zależności od języka projektu.

## <a name="see-also"></a>Zobacz także
- [Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)

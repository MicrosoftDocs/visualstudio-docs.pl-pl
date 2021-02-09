---
title: 'Instrukcje: Tworzenie strony aplikacji | Microsoft Docs'
description: Utwórz stronę sieci Web ASP.NET (znaną również jako Strona aplikacji) w programie Visual Studio dla co najmniej jednej witryny programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 74e7aab4cbc012afbf045672dbf4af248ada4c61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925628"
---
# <a name="how-to-create-an-application-page"></a>Instrukcje: Tworzenie strony aplikacji
  Można utworzyć stronę sieci Web ASP.NET dla jednej lub kilku witryn programu SharePoint. W programie SharePoint te strony są nazywane stronami aplikacji. W przeciwieństwie do strony witryny, Strona aplikacji zawiera kod, który jest uruchamiany za stroną. Aby uzyskać więcej informacji, zobacz [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Aby utworzyć stronę aplikacji

1. W programie Visual Studio otwórz lub utwórz projekt programu SharePoint.

     Aby uzyskać więcej informacji, zobacz [Szablony projektów i elementów projektu programu SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. W **Eksplorator rozwiązań** wybierz węzeł projektu.

3. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

4. W oknie dialogowym **Dodaj nowy element** rozwiń węzeł **SharePoint** , a następnie wybierz element **2010** .

5. Na liście szablonów programu SharePoint wybierz pozycję **Strona aplikacji**.

6. W polu **Nazwa** Określ nazwę strony aplikacji, a następnie wybierz przycisk **Dodaj** .

     Program Visual Studio dodaje kilka folderów i plików do projektu. Aby uzyskać więcej informacji o tych plikach, zobacz [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     W widoku **źródła** Visual Web Developer Designer pojawia się plik strony ASP.NET. Stronę można zaprojektować przez dodanie formantów z **przybornika** i umieszczenie ich w symbolach zastępczych zawartości. Aby uzyskać więcej informacji, zobacz [Widok źródła, Projektant stron sieci Web](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Jeśli chcesz obsłużyć zdarzenia kontroli, Dodaj kod do pliku kodu dla strony aplikacji.

     Plik kodu jest wyświetlany, jeśli rozszerzasz węzeł pliku stronicowania ASP.NET i ma rozszerzenie *. cs* lub *. vb* , w zależności od języka projektu. Aby zapoznać się z kompleksowym przykładem tworzenia strony aplikacji, zobacz [Przewodnik: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Zobacz też
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Przewodnik: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)

---
title: 'Instrukcje: Tworzenie strony aplikacji | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 32e6fbb7cece4c3b7513dfc1f5de3aca22f145ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016945"
---
# <a name="how-to-create-an-application-page"></a>Instrukcje: Tworzenie strony aplikacji
  Można utworzyć stronę sieci Web ASP.NET dla jednej lub kilku witryn programu SharePoint. W programie SharePoint te strony są nazywane stronami aplikacji. W przeciwieństwie do strony witryny, Strona aplikacji zawiera kod, który jest uruchamiany za stroną. Aby uzyskać więcej informacji, zobacz [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Aby utworzyć stronę aplikacji

1. W programie Visual Studio otwórz lub utwórz projekt programu SharePoint.

     Aby uzyskać więcej informacji, zobacz [Szablony projektów i elementów projektu programu SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. W **Eksplorator rozwiązań**wybierz węzeł projektu.

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

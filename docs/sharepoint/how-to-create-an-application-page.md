---
title: 'Instrukcje: Tworzenie strony aplikacji | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: fb5c4d7497525706384ced52caae1ba8e02f3e23
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063026"
---
# <a name="how-to-create-an-application-page"></a>Instrukcje: Tworzenie strony aplikacji
  Możesz utworzyć stronę sieci web ASP.NET w przynajmniej jednej witryny programu SharePoint. W programie SharePoint te strony są nazywane stron aplikacji. W przeciwieństwie do strony strony aplikacji zawiera kod, który uruchamia się w stronę. Aby uzyskać więcej informacji, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Aby utworzyć stronę aplikacji

1. W programie Visual Studio otwórz lub utwórz projekt programu SharePoint.

     Aby uzyskać więcej informacji, zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. W **Eksploratora rozwiązań**, wybierz węzeł projektu.

3. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

4. W **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzła, a następnie wybierz **2010** elementu.

5. Na liście szablonów programu SharePoint, wybierz opcję **strony aplikacji**.

6. W **nazwa** , określ nazwę dla strony aplikacji, a następnie wybierz **Dodaj** przycisku.

     Program Visual Studio dodaje kilka folderów i plików do projektu. Aby uzyskać więcej informacji o tych plikach, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     W **źródła** zostanie wyświetlony widok projektanta Visual Web Developer, plik strony ASP.NET. Można zaprojektować stronie przez dodanie formantów z **przybornika** i wprowadzanie ich na zawartości symbole zastępcze. Aby uzyskać więcej informacji, zobacz [widok źródła, Projektant stron sieci Web](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Jeśli chcesz obsługiwać zdarzenia formantu, Dodaj kod do pliku kodu strony aplikacji.

     Plik kodu po rozwinięciu węzła pliku strony ASP.NET i jest *.cs* lub *.vb* rozszerzenia, w zależności od języka projektu. Jak utworzyć witrynę aplikacji, na przykład end-to-end, zobacz [instruktażu: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Zobacz także
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Przewodnik: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)

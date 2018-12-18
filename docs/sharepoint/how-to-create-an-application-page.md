---
title: 'Porady: Tworzenie strony aplikacji | Dokumentacja firmy Microsoft'
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9f390ddf14925b43f1aa1d9e79db05e2aa64f234
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296206"
---
# <a name="how-to-create-an-application-page"></a>Porady: Tworzenie strony aplikacji
  Możesz utworzyć stronę sieci web ASP.NET w przynajmniej jednej witryny programu SharePoint. W programie SharePoint te strony są nazywane stron aplikacji. W przeciwieństwie do strony strony aplikacji zawiera kod, który uruchamia się w stronę. Aby uzyskać więcej informacji, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>Aby utworzyć stronę aplikacji  
  
1.  W programie Visual Studio otwórz lub utwórz projekt programu SharePoint.  
  
     Aby uzyskać więcej informacji, zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu.  
  
3.  Na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
4.  W **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzła, a następnie wybierz **2010** elementu.  
  
5.  Na liście szablonów programu SharePoint, wybierz opcję **strony aplikacji**.  
  
6.  W **nazwa** , określ nazwę dla strony aplikacji, a następnie wybierz **Dodaj** przycisku.  
  
     Program Visual Studio dodaje kilka folderów i plików do projektu. Aby uzyskać więcej informacji o tych plikach, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     W **źródła** zostanie wyświetlony widok projektanta Visual Web Developer, plik strony ASP.NET. Można zaprojektować stronie przez dodanie formantów z **przybornika** i wprowadzanie ich na zawartości symbole zastępcze. Aby uzyskać więcej informacji, zobacz [widok źródła, Projektant stron sieci Web](/previous-versions/aspnet/ms178154\(v\=vs.100\)).  
  
7.  Jeśli chcesz obsługiwać zdarzenia formantu, Dodaj kod do pliku kodu strony aplikacji.  
  
     Plik kodu po rozwinięciu węzła pliku strony ASP.NET i jest *.cs* lub *.vb* rozszerzenia, w zależności od języka projektu. Jak utworzyć witrynę aplikacji, na przykład end-to-end, zobacz [wskazówki: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Przewodnik: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  

---
title: 'Instrukcje: Tworzenie składnika Web Part programu SharePoint za pomocą projektanta | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0830cec748d68f010397c42334a5ed83365ee6b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016480"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Instrukcje: Tworzenie składnika Web Part programu SharePoint przy użyciu narzędzia Projektant
  Można utworzyć składnik Web Part poprzez dodanie elementu **wizualnego składnika Web Part** do dowolnego projektu programu SharePoint. Spowoduje to otwarcie projektanta Visual Web Developer w programie Visual Studio, w którym można dodać kontrolki i kod do składnika Web Part. Wizualne składniki Web Part działają tak samo jak części sieci Web. Jedyną różnicą jest zaprojektowanie wizualnych części sieci Web w Visual Web Developer Designer.

### <a name="to-create-a-project-for-visual-web-parts"></a>Aby utworzyć projekt dla wizualnych części sieci Web

1. Na pasku menu wybierz pozycję **plik**  > **Nowy**  >  **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

2. W oknie dialogowym **Nowy projekt** w obszarze **Visual C#** lub **Visual Basic**rozwiń węzeł **Office/SharePoint** , a następnie wybierz kategorię **rozwiązania SharePoint** .

3. Na liście szablonów projektu wybierz pozycję **SharePoint 2013 — wizualny składnik Web Part**, a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

4. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** Określ adres URL witryny programu SharePoint, która znajduje się na komputerze lokalnym, a następnie wybierz przycisk **Zakończ** .

     W **Eksplorator rozwiązań**zostanie wyświetlony składnik Web Part. Po zaprojektowaniu składnika Web Part w programie Visual Web Developer Designer przetestujesz go w określonej lokacji.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Aby dodać wizualny składnik Web Part do istniejącego projektu programu SharePoint

1. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz węzeł **Office/SharePoint** .

3. Na liście szablonów projektu wybierz pozycję **Visual Web Part**, nadaj jej nazwę, a następnie wybierz przycisk **Dodaj** .

     W **Eksplorator rozwiązań**zostanie wyświetlony składnik Web Part. Po zaprojektowaniu składnika Web Part w programie Visual Web Developer Designer przetestujesz go w określonej lokacji.

## <a name="see-also"></a>Zobacz też
- [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Instrukcje: Tworzenie składnika Web Part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Przewodnik: Tworzenie składnika Web Part dla programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Przewodnik: Tworzenie składnika Web Part dla programu SharePoint przy użyciu narzędzia Projektant](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)

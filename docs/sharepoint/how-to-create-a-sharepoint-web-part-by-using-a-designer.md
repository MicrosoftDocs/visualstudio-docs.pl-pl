---
title: 'How to: Create a SharePoint Web Part by Using a Designer | (Jak utworzyć element Web Part programu SharePoint przy użyciu interfejsu | Microsoft Docs'
titleSuffix: ''
description: Utwórz element Web Part, dodając element wizualnego elementu web part do projektu programu SharePoint, co spowoduje otwarcie projektanta Visual Web Developer w Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cbbb290af0029329910a23a71f68024ee0e5e5f4
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112387"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>How to: Create a SharePoint Web Part by using a designer (Jak utworzyć element Web Part programu SharePoint przy użyciu projektanta)

  Możesz utworzyć element Web Part, dodając element **Visual Web Part** do dowolnego projektu programu SharePoint. Spowoduje to otwarcie projektanta Visual Web Developer Visual Studio którym można dodawać kontrolki i kod do części web part. Wizualne elementy Web Part działają tak samo jak części web part. Jedyną różnicą jest to, że projektuje się wizualne elementy Web Part w projektancie visual web developer.

## <a name="to-create-a-project-for-visual-web-parts"></a>Aby utworzyć projekt dla wizualnych składników Web Part

1. Na pasku menu wybierz pozycję **Plik**  > **Nowy**  >  **projekt.**
::: moniker range="=vs-2017"

2. W **oknie dialogowym** Nowy projekt w obszarze **Visual C#** **lub Visual Basic** rozwiń węzeł **Office/SharePoint,** a następnie wybierz **kategorię Rozwiązania SharePoint.**

3. Na liście szablonów projektów wybierz pozycję **SharePoint 2013 — Visual Web Part,** a następnie wybierz **przycisk OK.**

     Zostanie **wyświetlony Kreator dostosowywania programu SharePoint.**
::: moniker-end
::: moniker range=">=vs-2019"
2. W **oknie dialogowym Create a New Project** (Tworzenie nowego projektu) wybierz pozycję *SharePoint Visual Web Part** dla określonej zainstalowanej wersji programu SharePoint. Jeśli na przykład masz zainstalowany program SharePoint 2019, wybierz szablon **SharePoint 2019 — Visual Web Part.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Zmień nazwę projektu, jeśli chcesz, a następnie wybierz **przycisk** Utwórz.

::: moniker-end
4. Na stronie **Określanie witryny i** poziomu zabezpieczeń do debugowania określ adres URL witryny programu SharePoint, która znajduje się na komputerze lokalnym, a następnie wybierz **przycisk** Zakończ.

     W **Eksplorator rozwiązań** zostanie wyświetlony element Web Part. Po zaprojektowaniu części web part w projektancie Visual Web Developer przetestujesz go w witrynie, która jest przez Ciebie określana.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Aby dodać wizualny element Web Part do istniejącego projektu programu SharePoint

1. Na pasku menu wybierz pozycję **Projekt**  >  **Dodaj nowy element.**

2. W **oknie dialogowym Dodawanie** nowego elementu wybierz węzeł **Office/SharePoint.**

3. Na liście szablonów projektów wybierz pozycję **Visual Web Part,** nadaj jej nazwę, a następnie wybierz **przycisk** Dodaj.

     W **Eksplorator rozwiązań** zostanie wyświetlony twój element Web Part. Po zaprojektowaniu części web part w projektancie Visual Web Developer przetestujesz go w witrynie, która jest przez Ciebie określana.

## <a name="see-also"></a>Zobacz też

- [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [How to: Create a SharePoint Web Part (Jak utworzyć część web part programu SharePoint)](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Przewodnik: tworzenie składników Web Part dla programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Przewodnik: tworzenie składników Web Part dla programu SharePoint przy użyciu projektanta](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)

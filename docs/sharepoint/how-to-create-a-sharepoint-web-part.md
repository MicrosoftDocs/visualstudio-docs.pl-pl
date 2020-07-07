---
title: 'Instrukcje: Tworzenie składnika Web Part programu SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a8c02cce2f55374b4d62ba5663e8b3fe85b55b5
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016442"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Instrukcje: Tworzenie składnika Web Part programu SharePoint
  Składnik Web Part można utworzyć i dostosować, dodając element **składnika Web Part** do dowolnego projektu programu SharePoint, a następnie edytując plik kodu dla składnika Web Part lub korzystając z projektanta. Aby uzyskać więcej informacji, zobacz [How to: Create a SharePoint Web Part za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>Aby utworzyć składnik Web Part programu SharePoint

1. Utwórz lub Otwórz projekt programu SharePoint.

     Aby uzyskać więcej informacji, zobacz [Szablony projektów i elementów projektu programu SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Wybierz węzeł projektu programu SharePoint w **Eksplorator rozwiązań** a następnie wybierz pozycję **projekt**  >  **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

4. Na liście szablonów programu SharePoint wybierz pozycję **składnik Web Part**.

5. W polu **Nazwa** Określ nazwę składnika Web Part, a następnie wybierz przycisk **Dodaj** .

     Część sieci Web zostanie wyświetlona w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji na temat plików, które zawiera składnik Web Part, zobacz [Create Web Part for SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

6. W **Eksplorator rozwiązań**Otwórz plik kodu dla składnika Web Part, który został właśnie utworzony.

     Na przykład jeśli nazwa składnika sieci Web jest *WebPart1*, Otwórz *WebPart1. vb* (w Visual Basic) lub *WebPart1.cs* (w języku C#).

7. W pliku kodu Dodaj formanty do <xref:System.Web.UI.Control.CreateChildControls%2A> metody.

     Aby zapoznać się z przykładem, zobacz [Przewodnik: Tworzenie składnika Web Part dla programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Zobacz także
- [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Instrukcje: Tworzenie składnika Web Part programu SharePoint przy użyciu narzędzia Projektant](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Przewodnik: Tworzenie składnika Web Part dla programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Przewodnik: Tworzenie składnika Web Part dla programu SharePoint przy użyciu narzędzia Projektant](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)

---
title: 'Instrukcje: Dodawanie formantów XMLMappedRange do arkuszy'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f5f11b09c5fd44b59ed47702d0eee2e6f563223
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856595"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Instrukcje: Dodawanie formantów XMLMappedRange do arkuszy
  Kiedy mapujesz — element XML do komórki w programie Microsoft Excel pakietu Office, Visual Studio automatycznie dodaje <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formantu do arkusza.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Formant nie jest dostępny na **przybornika** lub **źródeł danych** okna. Ponadto nie można utworzyć <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontroluje programowo.  
  
## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Aby dodać kontrolkę XMLMappedRange do arkusza  
  
1.  Otwórz skoroszyt programu Excel w Projektancie Visual Studio.  
  
2.  Otwórz arkusz, w którym chcesz dodać formant.  
  
3.  Na **Developer** kliknij pozycję **źródła**.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna na Wstążce, należy je włączyć. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     **Źródła XML** pojawi się okienko zadań.  
  
4.  W **źródła XML** okienka zadań, kliknij przycisk **mapy XML**.  
  
5.  W **mapy XML** okno dialogowe, kliknij przycisk **Dodaj**.  
  
     **Źródła XML** pojawi się okno dialogowe.  
  
6.  Wybierz schemat XML z **źródła XML** dialogowym i kliknij przycisk **Otwórz**.  
  
     Schemat jest dodawany do **mapy XML** okno dialogowe.  
  
7.  W **mapy XML** okno dialogowe, kliknij przycisk **OK**.  
  
8.  Przeciągnij element z **źródła XML** okienka zadań do komórki w arkuszu.  
  
     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Zostanie utworzony i dodany do projektu.  
  
    > [!NOTE]  
    >  Jeśli przeciągniesz element nadrzędny z **źródła XML** okienka zadań <xref:Microsoft.Office.Tools.Excel.ListObject> formant zostanie utworzony.  
  
## <a name="see-also"></a>Zobacz także  
 [Xmlmappedrange — formant](../vsto/xmlmappedrange-control.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Instrukcje: Mapowanie schematów z arkuszami w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  

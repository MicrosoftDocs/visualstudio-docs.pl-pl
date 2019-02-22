---
title: PowerPoint — rozwiązania
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 34175d2e53e897160e601f29bc2279f226fb5d11
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601255"
---
# <a name="powerpoint-solutions"></a>PowerPoint — rozwiązania
  Program Visual Studio udostępnia szablony projektów, służących do tworzenia dodatków narzędzi VSTO dla programu Microsoft PowerPoint pakietu Office. Za pomocą dodatków narzędzi VSTO dla programów Automatyzacja programu PowerPoint, Rozszerz funkcje programu PowerPoint lub dostosowywanie interfejsu użytkownika (UI) programu PowerPoint.

 Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym programistą w pakiecie Microsoft Office, zobacz [wprowadzenie &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

> [!NOTE]
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.

 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Tworzenie dodatku dla programu Microsoft PowerPoint? ](http://go.microsoft.com/fwlink/?LinkId=132767).

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>W programie PowerPoint zautomatyzować za pomocą modelu obiektów programu PowerPoint
 Model obiektów programu PowerPoint uwidacznia wiele typów, których można użyć do zautomatyzowania programu PowerPoint. Te typy umożliwiają pisanie kodu w celu wykonywania typowych zadań:

- Programowo utworzyć i sformatować prezentacji.

- Dodawanie lub usuwanie slajdy z prezentacji.

- Dodaj lub zmień kształtów na slajdzie.

  Dostęp do modelu obiektów programu PowerPoint z dodatku narzędzi VSTO dla programów, należy użyć `Application` pole `ThisAddIn` klasy w projekcie. `Application` Pole zwraca <xref:Microsoft.Office.Interop.PowerPoint.Application> obiekt reprezentujący bieżące wystąpienie programu PowerPoint. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

  Gdy wywołujesz modelu obiektów programu PowerPoint, należy użyć typów, które są dostarczane w podstawowy zestaw międzyoperacyjny dla programu PowerPoint. Podstawowy zestaw międzyoperacyjny działa jako Most między kodu zarządzanego w dodatku narzędzi VSTO dla programów i model obiektów COM w programie PowerPoint. Wszystkie typy w programie PowerPoint podstawowy zestaw międzyoperacyjny są zdefiniowane w <xref:Microsoft.Office.Interop.PowerPoint> przestrzeni nazw. Aby uzyskać więcej informacji na temat podstawowych usług międzyoperacyjnych, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).

##  <a name="WordOMDocumentation"></a> Zapoznaj się z dokumentacją modelu obiektu programu PowerPoint
 Aby uzyskać pełne informacje o modelu obiektów programu PowerPoint mogą odwoływać się do programu PowerPoint odwołanie do zestawu podstawowej usługi międzyoperacyjnej (PIA) i dokumentacja modelu obiektów języka VBA.

### <a name="primary-interop-assembly-reference"></a>Odwołanie do zestawu podstawowej usługi międzyoperacyjnej
 Dokumentacja referencyjna programu PowerPoint PIA w tym artykule opisano typy w podstawowy zestaw międzyoperacyjny dla programu PowerPoint. Ta dokumentacja jest dostępna z następującej lokalizacji: [Odwołanie do zestawu podstawowej usługi międzyoperacyjnej PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

 Aby uzyskać więcej informacji na temat projektowania PIA programu PowerPoint, takie jak różnice między klasami i interfejsy, które PIA i sposobu implementacji zdarzenia w PIA, zobacz [Przegląd klasy i interfejsy podstawowe zestawy międzyoperacyjne pakietu Office ](http://go.microsoft.com/fwlink/?LinkId=199885).

### <a name="vba-object-model-reference"></a>Dokumentacja modelu obiektów VBA
 Dokumentacja modelu obiektów VBA dokumentów modelu obiektów programu PowerPoint, ponieważ jest narażony na język Visual Basic for Applications (VBA) kod. Aby uzyskać więcej informacji, zobacz [dokumentacja modelu obiektów programu PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)

 Wszystkie obiekty i elementy członkowskie w dokumentacja modelu obiektów VBA odnoszą się do typów i członków w programie PowerPoint podstawowego zestawu międzyoperacyjnego (PIA). Na przykład obiekt prezentacji w dokumentacja modelu obiektów VBA odnosi się do <xref:Microsoft.Office.Interop.PowerPoint.Presentation> wpisz PIA programu PowerPoint. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metody i zdarzenia, należy translacji kodu VBA w ramach tego odwołania do kodu języka Visual Basic lub Visual C#, jeśli chcesz użyć ich w projekcie dodatku narzędzi VSTO dla programu PowerPoint, które tworzysz przy użyciu Program Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Dostosowywanie interfejsu użytkownika programu PowerPoint
 Interfejs użytkownika programu PowerPoint można zmodyfikować w następujący sposób.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Tworzenie niestandardowego okienka zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|
|Dodaj niestandardowe karty do wstążki.|[Wstążka — omówienie](../vsto/ribbon-overview.md)|
|Dodaj niestandardowe grupy do wbudowanej karty na Wstążce.|[Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)|

 Aby uzyskać więcej informacji o dostosowywaniu interfejsu użytkownika programu PowerPoint i inne aplikacje Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [PowerPoint 2010 w rozwój pakietu Office](http://go.microsoft.com/fwlink/?LinkId=199015)

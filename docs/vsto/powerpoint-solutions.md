---
title: Rozwiązania programu PowerPoint
ms.date: 08/14/2019
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
ms.openlocfilehash: c41b2942b53c97222abf7308b6706a7cdc734df1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985656"
---
# <a name="powerpoint-solutions"></a>Rozwiązania programu PowerPoint
  Program Visual Studio zawiera szablony projektów, których można użyć do tworzenia dodatków narzędzi VSTO dla programu Microsoft Office PowerPoint. Za pomocą dodatków VSTO można zautomatyzować program PowerPoint, zwiększyć funkcje programu PowerPoint lub dostosować interfejs użytkownika programu PowerPoint.

 Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO, zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](getting-started-programming-vsto-add-ins.md) i [architektury dodatków narzędzi VSTO](architecture-of-vsto-add-ins.md). Jeśli jesteś nowym sposobem programowania przy użyciu Microsoft Office, zobacz [wprowadzenie &#40;Programowanie Office w&#41;Visual Studio ](getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatyzowanie programu PowerPoint przy użyciu modelu obiektów programu PowerPoint
 Model obiektów programu PowerPoint uwidacznia wiele typów, których można użyć do zautomatyzowania programu PowerPoint. Te typy umożliwiają pisanie kodu w celu wykonywania typowych zadań:

- Programowe tworzenie i formatowanie prezentacji.

- Dodaj lub Usuń slajdy z prezentacji.

- Dodaj lub Zmień kształty na slajdzie.

  Aby uzyskać dostęp do modelu obiektów programu PowerPoint z dodatku VSTO, użyj `Application` pola `ThisAddIn` klasy w projekcie. `Application`Pole zwraca obiekt [aplikacji](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) , który reprezentuje bieżące wystąpienie programu PowerPoint. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](programming-vsto-add-ins.md).

  W przypadku wywołania do modelu obiektów programu PowerPoint należy użyć typów, które są dostępne w podstawowym zestawie międzyoperacyjnym dla programu PowerPoint. Podstawowy zestaw międzyoperacyjny działa jako Most między zarządzanym kodem w dodatku VSTO i modelem obiektów COM w programie PowerPoint. Wszystkie typy w podstawowym zestawie międzyoperacyjnym programu PowerPoint są zdefiniowane w przestrzeni nazw [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Aby uzyskać więcej informacji na temat podstawowych zestawów międzyoperacyjnych, zobacz [Omówienie tworzenia rozwiązań pakietu office &#40;narzędzi VSTO&#41;](office-solutions-development-overview-vsto.md) i [podstawowych zestawów międzyoperacyjnych pakietu Office](office-primary-interop-assemblies.md).

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a> Korzystanie z dokumentacji modelu obiektów programu PowerPoint
 Aby uzyskać pełne informacje na temat modelu obiektów programu PowerPoint, można odwołać się do odwołania do podstawowego zestawu międzyoperacyjnego (PIA) programu PowerPoint i odwołania do modelu obiektów VBA.

### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoperacyjnego
 Dokumentacja PIA do programu PowerPoint zawiera opis typów w podstawowym zestawie międzyoperacyjnym dla programu PowerPoint. Ta dokumentacja jest dostępna w następującej lokalizacji: [odwołanie do podstawowego zestawu międzyoperacyjnego programu PowerPoint 2010](office-primary-interop-assemblies.md).

 Aby uzyskać więcej informacji o projektowaniu PIA programu PowerPoint, takich jak różnice między klasami i interfejsami w PIAu i sposobie implementacji zdarzeń w PIA, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/developer/office-2010/ff759900(v=office.14)).

### <a name="vba-object-model-reference"></a>Odwołanie do modelu obiektów VBA
 Dokumentacja modelu obiektów VBA dokumentuje model obiektów programu PowerPoint, który jest udostępniany w kodzie Visual Basic for Applications (VBA). Aby uzyskać więcej informacji, zobacz [Dokumentacja modelu obiektów programu PowerPoint 2010](/office/vba/api/overview/PowerPoint/object-model).

 Wszystkie obiekty i elementy członkowskie w odwołaniu modelu obiektów VBA odpowiadają typom i elementom członkowskim w podstawowym zestawie międzyoperacyjnym programu PowerPoint (PIA). Na przykład obiekt prezentacji w odniesieniu do modelu obiektów VBA odnosi się do typu [prezentacji](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) w Piau programu PowerPoint. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod VBA w tym odwołaniu do Visual Basic lub Visual C#, jeśli chcesz użyć ich w projekcie dodatku VSTO dla programu PowerPoint utworzonym za pomocą programu Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Dostosowywanie interfejsu użytkownika programu PowerPoint
 Interfejs użytkownika programu PowerPoint można modyfikować w następujący sposób.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Utwórz niestandardowe okienko zadań.|[Niestandardowe okienka zadań](custom-task-panes.md)|
|Dodaj karty niestandardowe do wstążki.|[Omówienie wstążki](ribbon-overview.md)|
|Dodawanie grup niestandardowych do wbudowanej karty na Wstążce.|[Instrukcje: dostosowywanie wbudowanej karty](how-to-customize-a-built-in-tab.md)|

 Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika programu PowerPoint i innych aplikacji Microsoft Office, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](office-ui-customization.md).

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](getting-started-programming-vsto-add-ins.md)
- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](how-to-create-office-projects-in-visual-studio.md)
- [Dodatki narzędzi VSTO programu](programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjności pakietu Office](office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](office-ui-customization.md)
- [PowerPoint 2010 w programowaniu pakietu Office](/previous-versions/office/developer/office-2010/ff604967(v=office.14))

---
title: Rozwiązania projektu
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5fe9f47fca2b83e0095c67e59c2db54a4a04159
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447057"
---
# <a name="project-solutions"></a>Rozwiązania projektu
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] zawiera szablony projektów, służących do tworzenia dodatków narzędzi VSTO dla programu Microsoft Office Project. Za pomocą dodatków narzędzi VSTO dla programów do projektu automatyzacji, Rozszerz funkcje projektu lub dostosować projekt interfejsu użytkownika (UI).

 Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym programistą w pakiecie Microsoft Office, zobacz [wprowadzenie &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

> [!NOTE]
> Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.

## <a name="automate-project-by-using-the-project-object-model"></a>Automatyzacja projektu przy użyciu modelu obiektu projektu
 Model obiektu projektu uwidacznia wiele typów, których można użyć do zautomatyzowania projektu. Te typy umożliwiają pisanie kodu w celu wykonywania typowych zadań, takich jak programowo tworzenia i modyfikowania zadań w projekcie.

 Dostęp do modelu obiektu projektu z dodatku narzędzi VSTO dla programów, należy użyć `Application` pole `ThisAddIn` klasy w projekcie. `Application` Pole zwraca `Microsoft.Office.Interop.MsProject.Application` obiekt reprezentujący bieżące wystąpienie projektu. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

 Po wywołaniu do modelu obiektu projektu, możesz użyć typów, które są dostarczane w podstawowy zestaw międzyoperacyjny dla projektu. Podstawowy zestaw międzyoperacyjny działa jako Most między kodu zarządzanego w dodatku narzędzi VSTO dla programów i model obiektów COM w projekcie. Wszystkie typy w projekcie podstawowy zestaw międzyoperacyjny są zdefiniowane w `Microsoft.Office.Interop.MSProject` przestrzeni nazw. Aby uzyskać więcej informacji na temat podstawowych usług międzyoperacyjnych, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Zapoznaj się z dokumentacją modelu obiektu projektu
 Aby uzyskać pełne informacje na temat modelu obiektu projektu mogą odwoływać się do projektu VBA odwołania modelu obiektów. Dokumentacja modelu obiektów VBA dokumenty model obiektu projektu, ponieważ jest narażony na język Visual Basic for Applications (VBA) kod. Aby uzyskać więcej informacji, zobacz [dokumentacja modelu obiektów programu Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).

 Wszystkie obiekty i elementy członkowskie w dokumentacja modelu obiektów VBA odnoszą się do typów i członków w projekcie zestawu podstawowej usługi międzyoperacyjnej (PIA). Na przykład obiekt kalendarza w dokumentacja modelu obiektów VBA odnosi się do `Microsoft.Office.Interop.MSProject.Calendar` wpisz PIA projektu. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy translacji kodu VBA w ramach tego odwołania do kodu języka Visual Basic lub Visual C#, jeśli chcesz użyć ich w projekcie dodatku narzędzi VSTO projektu, które tworzysz przy użyciu programu Visual Studio.

> [!NOTE]
> W tej chwili brak Dokumentacja referencyjna dla projektu podstawowego zestawu międzyoperacyjnego.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Typy infrastruktury w projekcie podstawowy zestaw międzyoperacyjny
 Podczas pisania kodu, który używa PIA projektu, można zauważyć wiele typów, które nie zostały opisane w dokumentacji języka VBA. Te dodatkowe typy pomóc w tłumaczeniu obiekty w modelu opartym na modelu COM obiektu projektu do kodu zarządzanego, nie są przeznaczone do użycia bezpośrednio w kodzie.

 Aby uzyskać więcej informacji, zobacz [Przegląd klasy i interfejsy podstawowe zestawy międzyoperacyjne pakietu Office](http://go.microsoft.com/fwlink/?LinkId=189592).

## <a name="customize-the-user-interface-of-project"></a>Dostosowywanie interfejsu użytkownika programu project
 Projekt interfejsu użytkownika można dostosować w następujący sposób.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dodaj niestandardowe karty do wstążki w projekcie|[Wstążka — omówienie](../vsto/ribbon-overview.md)|

 Aby uzyskać więcej informacji o dostosowywaniu interfejsu użytkownika projektu i inne aplikacje Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Project 2010 i Project Server 2010 w rozwój pakietu Office](http://go.microsoft.com/fwlink/?LinkId=199016)

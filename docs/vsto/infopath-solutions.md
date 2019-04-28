---
title: rozwiązania InfoPath
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c7342524d1e7682fd088c4f7ea44037a32c220e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441754"
---
# <a name="infopath-solutions"></a>rozwiązania InfoPath
  Program Visual Studio udostępnia szablony projektów, służących do tworzenia dodatków narzędzi VSTO dla pakietu Microsoft Office InfoPath 2013 i InfoPath 2010. InfoPath nie jest dostępna w pakiecie Office 2016.

> [!NOTE]
> Można nadal tworzyć dodatku narzędzi VSTO dla programu InfoPath, nawet jeśli po zainstalowaniu pakietu Office 2016. W pakiecie Office 2016, po prostu zainstaluj InfoPath 2013 lub Office 2013 side-by-side.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

> [!NOTE]
> Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.

 Dodatków narzędzi VSTO dla programu InfoPath są podobne do dodatków narzędzi VSTO dla innych aplikacji Microsoft Office. Tego rodzaju rozwiązania składają się z zestawu, który jest ładowany przez aplikację. Użytkownicy końcowi mogą mieć dostęp do funkcji tego zestawu, niezależnie od tego, które tworzą lub formularz szablonu jest otwarty. Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Program Visual Studio 2015 nie zawiera projekty szablonu formularza programu InfoPath, które zostały dostarczone w poprzednich wersjach programu Visual Studio. Możesz również nie można użyć programu Visual Studio 2015 do otwarcia lub edycji projektu szablonu formularza programu InfoPath, który został utworzony w poprzedniej wersji programu Visual Studio. Jednak możesz otwierać i edytować projekt szablonu formularza programu InfoPath za pomocą programu Visual Studio Tools dla aplikacji. Aby uzyskać więcej informacji, zobacz [pracować z projektami 2008 narzędzi VSTO dla programów w programie InfoPath 2010.](http://go.microsoft.com/fwlink/?LinkID=218903).

## <a name="automate-infopath-by-using-an-add-in"></a>Automatyzowanie programu InfoPath za pomocą dodatku
 Aby uzyskać dostęp do modelu obiektów programu InfoPath, od dodatku narzędzi VSTO dla pakietu Office utworzone przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, należy użyć `Application` pole `ThisAddIn` klasy w projekcie. `Application` Pole zwraca <xref:Microsoft.Office.Interop.InfoPath.Application> obiekt reprezentujący bieżące wystąpienie programu InfoPath. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

 Po wywołaniu modelu obiektów programu InfoPath z dodatku narzędzi VSTO dla programów, możesz użyć typów, które są dostarczane w podstawowy zestaw międzyoperacyjny dla programu InfoPath. Podstawowy zestaw międzyoperacyjny działa jako Most między kodu zarządzanego w dodatku narzędzi VSTO dla programów i model obiektów COM w programie InfoPath. Wszystkie typy w programie InfoPath podstawowy zestaw międzyoperacyjny są zdefiniowane w <xref:Microsoft.Office.Interop.InfoPath> przestrzeni nazw. Aby uzyskać więcej informacji na temat programu InfoPath podstawowy zestaw międzyoperacyjny zobacz [podstawowy zestaw międzyoperacyjny o Microsoft InfoPath pakietu Office](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Aby uzyskać więcej informacji na temat podstawowych usług międzyoperacyjnych ogólnie rzecz biorąc, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Dostosowywanie interfejsu użytkownika programu InfoPath za pomocą dodatku
 Podczas tworzenia dodatku narzędzi VSTO dla programu InfoPath, masz kilka różnych opcji dostosowywania interfejsu użytkownika. W poniższej tabeli wymieniono niektóre z tych opcji.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Tworzenie niestandardowego okienka zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|
|Dodaj niestandardowe karty do wstążki w programie InfoPath.|[Dostosowywanie wstążki do InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika programu InfoPath i innych aplikacji Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Zobacz także
- [Program Microsoft Office InfoPath podstawowy zestaw międzyoperacyjny — informacje](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 w rozwój pakietu Office](http://go.microsoft.com/fwlink/?LinkId=199012)

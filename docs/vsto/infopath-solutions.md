---
title: rozwiązania InfoPath
description: Dowiedz się, jak za pomocą programu Visual Studio utworzyć dodatki narzędzi VSTO dla programów Microsoft InfoPath 2013 i InfoPath 2010.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3feab4a4b66ed2d6cf96fbccc8aaf1fb7de3bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962369"
---
# <a name="infopath-solutions"></a>rozwiązania InfoPath
  Program Visual Studio zawiera szablony projektów, których można użyć do tworzenia dodatków narzędzi VSTO dla Microsoft Office InfoPath 2013 i InfoPath 2010. Program InfoPath nie jest dostępny w pakiecie Office 2016.

> [!NOTE]
> Nadal można utworzyć dodatek narzędzi VSTO dla programu InfoPath, nawet jeśli zainstalowano pakiet Office 2016. Po prostu zainstaluj program InfoPath 2013 lub pakiet Office 2013 jednocześnie z pakietem Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Dodatki narzędzi VSTO dla programu InfoPath są podobne do dodatków narzędzi VSTO dla innych aplikacji Microsoft Office. Te typy rozwiązań składają się z zestawu, który jest ładowany przez aplikację. Użytkownicy końcowi mogą mieć dostęp do funkcji tego zestawu niezależnie od tego, który formularz lub szablon formularza jest otwarty. Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO, zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [architektury dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Program Visual Studio 2015 nie zawiera projektów szablonów formularzy programu InfoPath, które zostały podane w poprzednich wersjach programu Visual Studio. Nie można również użyć programu Visual Studio 2015 do otwierania lub edytowania projektu szablonu formularza programu InfoPath, który został utworzony w poprzedniej wersji programu Visual Studio. Można jednak otworzyć i edytować projekt szablonu formularza programu InfoPath przy użyciu Visual Studio Tools for Applications. Aby uzyskać więcej informacji, zobacz [prace z projektami VSTO 2008 w programie InfoPath 2010.](/archive/blogs/infopath/working-with-vsto-2008-projects-in-infopath-2010)

## <a name="automate-infopath-by-using-an-add-in"></a>Automatyzowanie programu InfoPath przy użyciu dodatku
 Aby uzyskać dostęp do modelu obiektów programu InfoPath z dodatku pakietu Office VSTO utworzonego przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, użyj `Application` pola `ThisAddIn` klasy w projekcie. `Application`Pole zwraca <xref:Microsoft.Office.Interop.InfoPath.Application> obiekt, który reprezentuje bieżące wystąpienie programu InfoPath. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

 W przypadku wywołania do modelu obiektów programu InfoPath z dodatku VSTO należy użyć typów, które są dostępne w podstawowym zestawie międzyoperacyjnym dla programu InfoPath. Podstawowy zestaw międzyoperacyjny działa jako Most między zarządzanym kodem w dodatku VSTO i modelem obiektów COM w programie InfoPath. Wszystkie typy w podstawowym zestawie międzyoperacyjnym programu InfoPath są zdefiniowane w <xref:Microsoft.Office.Interop.InfoPath> przestrzeni nazw. Więcej informacji o podstawowym zestawie międzyoperacyjnym programu InfoPath znajduje się w temacie [Informacje o podstawowym zestawie międzyoperacyjnym](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)programu InfoPath Microsoft Office. Aby uzyskać więcej informacji na temat ogólnych zestawów międzyoperacyjnych, zobacz [Omówienie tworzenia rozwiązań pakietu office &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) i [podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Dostosowywanie interfejsu użytkownika programu InfoPath przy użyciu dodatku
 Podczas tworzenia dodatku narzędzi VSTO dla programu InfoPath istnieje kilka różnych opcji dostosowywania interfejsu użytkownika. W poniższej tabeli wymieniono niektóre z tych opcji.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Utwórz niestandardowe okienko zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|
|Dodaj niestandardowe karty do wstążki w programie InfoPath.|[Dostosowywanie wstążki dla programu InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika programu InfoPath i innych aplikacji Microsoft Office, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Zobacz też
- [Informacje o podstawowym zestawie międzyoperacyjnym programu Microsoft Office InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 w programowaniu pakietu Office](/previous-versions/office/developer/office-2010/ff604966(v=office.14))
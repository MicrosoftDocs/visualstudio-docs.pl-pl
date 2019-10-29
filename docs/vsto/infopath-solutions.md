---
title: rozwiązania InfoPath
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7eda46c04cdbe5ba73e32e124486cfc391e5ac17
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985743"
---
# <a name="infopath-solutions"></a>rozwiązania InfoPath
  Program Visual Studio zawiera szablony projektów, których można użyć do tworzenia dodatków narzędzi VSTO dla Microsoft Office InfoPath 2013 i InfoPath 2010. Program InfoPath nie jest dostępny w pakiecie Office 2016.

> [!NOTE]
> Nadal można utworzyć dodatek narzędzi VSTO dla programu InfoPath, nawet jeśli zainstalowano pakiet Office 2016. Po prostu zainstaluj program InfoPath 2013 lub pakiet Office 2013 jednocześnie z pakietem Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Dodatki narzędzi VSTO dla programu InfoPath są podobne do dodatków narzędzi VSTO dla innych aplikacji Microsoft Office. Te typy rozwiązań składają się z zestawu, który jest ładowany przez aplikację. Użytkownicy końcowi mogą mieć dostęp do funkcji tego zestawu niezależnie od tego, który formularz lub szablon formularza jest otwarty. Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO, zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [architektury dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Program Visual Studio 2015 nie zawiera projektów szablonów formularzy programu InfoPath, które zostały podane w poprzednich wersjach programu Visual Studio. Nie można również użyć programu Visual Studio 2015 do otwierania lub edytowania projektu szablonu formularza programu InfoPath, który został utworzony w poprzedniej wersji programu Visual Studio. Można jednak otworzyć i edytować projekt szablonu formularza programu InfoPath przy użyciu Visual Studio Tools for Applications. Aby uzyskać więcej informacji, zobacz [prace z projektami VSTO 2008 w programie InfoPath 2010.](https://blogs.msdn.microsoft.com/infopath/2011/04/14/working-with-vsto-2008-projects-in-infopath-2010/)

## <a name="automate-infopath-by-using-an-add-in"></a>Automatyzowanie programu InfoPath przy użyciu dodatku
 Aby uzyskać dostęp do modelu obiektów programu InfoPath z dodatku pakietu Office VSTO utworzonego przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, należy użyć pola `Application` klasy `ThisAddIn` w projekcie. Pole `Application` zwraca obiekt <xref:Microsoft.Office.Interop.InfoPath.Application>, który reprezentuje bieżące wystąpienie programu InfoPath. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

 W przypadku wywołania do modelu obiektów programu InfoPath z dodatku VSTO należy użyć typów, które są dostępne w podstawowym zestawie międzyoperacyjnym dla programu InfoPath. Podstawowy zestaw międzyoperacyjny działa jako Most między zarządzanym kodem w dodatku VSTO i modelem obiektów COM w programie InfoPath. Wszystkie typy w podstawowym zestawie międzyoperacyjnym programu InfoPath są zdefiniowane w przestrzeni nazw <xref:Microsoft.Office.Interop.InfoPath>. Więcej informacji o podstawowym zestawie międzyoperacyjnym programu InfoPath znajduje się w temacie [Informacje o podstawowym zestawie międzyoperacyjnym](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)programu InfoPath Microsoft Office. Aby uzyskać więcej informacji na temat ogólnych zestawów międzyoperacyjnych, zobacz temat [programowanie &#40;rozwiązań&#41; pakietu Office — Omówienie programu VSTO](../vsto/office-solutions-development-overview-vsto.md) i [podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Dostosowywanie interfejsu użytkownika programu InfoPath przy użyciu dodatku
 Podczas tworzenia dodatku narzędzi VSTO dla programu InfoPath istnieje kilka różnych opcji dostosowywania interfejsu użytkownika. W poniższej tabeli wymieniono niektóre z tych opcji.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Utwórz niestandardowe okienko zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|
|Dodaj niestandardowe karty do wstążki w programie InfoPath.|[Dostosowywanie wstążki dla programu InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika programu InfoPath i innych aplikacji Microsoft Office, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Zobacz także
- [Informacje o podstawowym zestawie międzyoperacyjnym programu Microsoft Office InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Programowanie rozwiązań pakietu Office &#40;— Omówienie&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 w programowaniu pakietu Office](/previous-versions/office/developer/office-2010/ff604966(v=office.14))

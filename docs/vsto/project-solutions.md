---
title: Rozwiązania projektu
description: Dowiedz się, jak można użyć dodatków VSTO do automatyzowania projektu, rozszerzenia funkcji projektu lub dostosowywania interfejsu użytkownika projektu.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b17ff0312574a4e41b283bd3c631977a834c64c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971820"
---
# <a name="project-solutions"></a>Rozwiązania projektu
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] zawiera szablony projektów, których można użyć do tworzenia dodatków narzędzi VSTO dla Microsoft Office projektu. Dodatków VSTO można używać do automatyzowania projektu, rozszerzenia funkcji projektu lub dostosowywania interfejsu użytkownika projektu.

 Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO, zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [architektury dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym sposobem programowania przy użyciu Microsoft Office, zobacz [wprowadzenie &#40;Programowanie Office w&#41;Visual Studio ](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Automatyzowanie projektu przy użyciu modelu obiektów projektu
 Model obiektów projektu ujawnia wiele typów, których można użyć do zautomatyzowania projektu. Te typy umożliwiają pisanie kodu w celu wykonywania typowych zadań, takich jak Programistyczne tworzenie i modyfikowanie zadań w projekcie.

 Aby uzyskać dostęp do modelu obiektów projektu z dodatku VSTO, użyj `Application` pola `ThisAddIn` klasy w projekcie. `Application`Pole zwraca `Microsoft.Office.Interop.MsProject.Application` obiekt, który reprezentuje bieżące wystąpienie projektu. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

 Podczas wywoływania do modelu obiektów projektu, należy użyć typów, które są dostępne w podstawowym zestawie międzyoperacyjnym dla projektu. Podstawowy zestaw międzyoperacyjny działa jako Most między zarządzanym kodem w dodatku VSTO i modelem obiektów COM w projekcie. Wszystkie typy w podstawowym zestawie międzyoperacyjnym projektu są zdefiniowane w `Microsoft.Office.Interop.MSProject` przestrzeni nazw. Aby uzyskać więcej informacji na temat podstawowych zestawów międzyoperacyjnych, zobacz [Omówienie tworzenia rozwiązań pakietu office &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) i [podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Korzystanie z dokumentacji modelu obiektów projektu
 Aby uzyskać pełne informacje na temat modelu obiektów projektu, można odwołać się do dokumentacji modelu obiektów VBA projektu. Dokumentacja modelu obiektów VBA dokumentuje model obiektów projektu, ponieważ jest on uwidoczniony w kodzie Visual Basic for Applications (VBA). Aby uzyskać więcej informacji, zobacz [Dokumentacja modelu obiektów projektu](/office/vba/api/project.object).

 Wszystkie obiekty i elementy członkowskie w odwołaniu modelu obiektów VBA odpowiadają typom i elementom członkowskim w podstawowym zestawie międzyoperacyjnym projektu (PIA). Na przykład obiekt Calendar w odniesieniu do modelu obiektów VBA odnosi się do `Microsoft.Office.Interop.MSProject.Calendar` typu w PIA projektu. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod VBA w tym odwołaniu do Visual Basic lub Visual C#, jeśli chcesz użyć ich w projekcie dodatku VSTO dla projektu, który tworzysz przy użyciu programu Visual Studio.

> [!NOTE]
> W tej chwili nie ma dokumentacji referencyjnej dla podstawowego zestawu międzyoperacyjnego projektu.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Typy infrastruktury w podstawowym zestawie międzyoperacyjnym projektu
 Podczas pisania kodu, który używa PIA projektu, można zauważyć wiele typów, które nie zostały opisane w dokumentacji VBA. Te dodatkowe typy ułatwiają translację obiektów w modelu obiektów opartych na modelu COM w programie Project na kod zarządzany, nie są przeznaczone do użycia bezpośrednio w kodzie.

 Aby uzyskać więcej informacji, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/office-12/ms247299(v=office.12)).

## <a name="customize-the-user-interface-of-project"></a>Dostosuj interfejs użytkownika projektu
 Interfejs użytkownika projektu można dostosować w następujący sposób.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dodawanie niestandardowych kart do wstążki w projekcie|[Omówienie wstążki](../vsto/ribbon-overview.md)|

 Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika programu Project i innych aplikacji Microsoft Office, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Project 2010 i Project Server 2010 w programowaniu pakietu Office](/previous-versions/office/developer/office-2010/ee758031(v=office.14))

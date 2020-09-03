---
title: Rozwiązania programu Visio
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a79b3c9964a24daf0a12ab90f47fb5903d89cdd0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985510"
---
# <a name="visio-solutions"></a>Rozwiązania programu Visio
  Program Visual Studio zawiera szablony projektów, których można użyć do tworzenia dodatków narzędzi VSTO dla programu Microsoft Office Visio. Za pomocą dodatków VSTO można zautomatyzować program Visio, zwiększyć funkcjonalność programu Visio lub dostosować interfejs użytkownika programu Visio.

 Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO, zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [architektury dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym sposobem programowania przy użyciu Microsoft Office, zobacz [wprowadzenie &#40;Programowanie Office w&#41;Visual Studio ](../vsto/getting-started-office-development-in-visual-studio.md).

 **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu Visio 2010. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatyzowanie programu Visio przy użyciu modelu obiektów programu Visio
 Model obiektów programu Visio uwidacznia wiele klas, których można użyć do zautomatyzowania programu Visio do tworzenia diagramów schematów organizacyjnych, schematów blokowych, osi czasu projektu, diagramów sieci, miejsc biurowych i innych. Interfejs API umożliwia pisanie kodu w celu wykonywania typowych zadań:

- Konstruowanie i pozycjonowanie kształtów i tekstu w diagramach.

- Zarządzanie zachowaniem kształtu na podstawie logiki biznesowej i danych wejściowych użytkownika.

- Wizualizacja diagramu kontroli, taka jak panoramowanie i powiększanie.

- Dostosuj interfejs użytkownika aplikacji.

- Zaimportuj dane zewnętrzne do programu Visio, połącz je z kształtami i wyświetlaj je graficznie na stronie.

  Można wyświetlić procedury krok po kroku i przykłady kodu umożliwiające korzystanie z modelu obiektów programu Visio do pracy z dokumentami i kształtami w [pracy z dokumentami programu Visio](../vsto/working-with-visio-documents.md) i [pracy z kształtami programu Visio](../vsto/working-with-visio-shapes.md).

  Aby uzyskać dostęp do modelu obiektów programu Visio z dodatku VSTO, użyj `Application` pola `ThisAddIn` klasy w projekcie. `Application`Pole zwraca `Microsoft.Office.Interop.Visio.Application` obiekt, który reprezentuje bieżące wystąpienie programu Visio. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

  Gdy wywołujesz model obiektów programu Visio, używasz typów, które są dostępne w podstawowym zestawie międzyoperacyjnym (PIA) dla programu Visio. PIA działa jako Most między zarządzanym kodem w dodatku VSTO i modelem obiektów COM w programie Visio. Wszystkie typy w programie Visio PIA są zdefiniowane w `Microsoft.Office.Interop.Visio` przestrzeni nazw. Aby uzyskać więcej informacji na temat podstawowych zestawów międzyoperacyjnych, zobacz [Omówienie tworzenia rozwiązań pakietu office &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) i [podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Model obiektów programu Visio — Omówienie
 Przegląd modelu obiektów programu Visio można znaleźć w temacie [Omówienie modelu obiektów programu](../vsto/visio-object-model-overview.md)Visio, który obejmuje linki do odwołania do modelu obiektów programu Visio i zestawów SDK.

## <a name="customize-the-user-interface-of-visio"></a>Dostosowywanie interfejsu użytkownika programu Visio
 Interfejs użytkownika programu Visio ma następujące opcje dostosowywania.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dostosuj Wstążkę.|[Wstążka — omówienie](../vsto/ribbon-overview.md)|

 Aby uzyskać informacje na temat dostosowywania interfejsu użytkownika programu Visio, zobacz dokumentację referencyjną języka VBA dla klasy [Visio. UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Visio 2010 w programowaniu pakietu Office](/previous-versions/office/developer/office-2010/ff604964(v=office.14))

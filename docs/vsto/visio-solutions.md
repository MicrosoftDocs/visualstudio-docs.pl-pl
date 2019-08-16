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
ms.openlocfilehash: 69d795fe9e4243bbce51e1e137bb6704492bae32
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551274"
---
# <a name="visio-solutions"></a>Rozwiązania programu Visio
  Program Visual Studio zawiera szablony projektów, których można użyć do tworzenia dodatków narzędzi VSTO dla programu Microsoft Office Visio. Za pomocą dodatków VSTO można zautomatyzować program Visio, zwiększyć funkcjonalność programu Visio lub dostosować interfejs użytkownika programu Visio.

 Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO, zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [architektury dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym sposobem programowania przy użyciu Microsoft Office, zobacz Wprowadzenie [do &#40;programowania Office w programie Visual&#41;Studio](../vsto/getting-started-office-development-in-visual-studio.md).

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

  Aby uzyskać dostęp do modelu obiektów programu Visio z dodatku VSTO, użyj `Application` pola `ThisAddIn` klasy w projekcie. `Application` Pole`Microsoft.Office.Interop.Visio.Application` zwraca obiekt, który reprezentuje bieżące wystąpienie programu Visio. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

  Gdy wywołujesz model obiektów programu Visio, używasz typów, które są dostępne w podstawowym zestawie międzyoperacyjnym (PIA) dla programu Visio. PIA działa jako Most między zarządzanym kodem w dodatku VSTO i modelem obiektów COM w programie Visio. Wszystkie typy w programie Visio PIA są zdefiniowane w `Microsoft.Office.Interop.Visio` przestrzeni nazw. Aby uzyskać więcej informacji na temat podstawowych zestawów międzyoperacyjnych, zobacz temat [programowanie rozwiązań pakietu Office — omówienie &#40;programu VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/office-primary-interop-assemblies.md)

## <a name="visio-object-model-overview"></a>Model obiektów programu Visio — Omówienie
 Przegląd modelu obiektów programu Visio można znaleźć w temacie [Omówienie modelu obiektów programu](../vsto/visio-object-model-overview.md)Visio, który obejmuje linki do odwołania do modelu obiektów programu Visio i zestawów SDK.

## <a name="customize-the-user-interface-of-visio"></a>Dostosowywanie interfejsu użytkownika programu Visio
 Interfejs użytkownika programu Visio ma następujące opcje dostosowywania.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dostosuj Wstążkę.|[Wstążka — omówienie](../vsto/ribbon-overview.md)|

 Aby uzyskać informacje na temat dostosowywania interfejsu użytkownika programu Visio, zobacz dokumentację referencyjną języka VBA dla klasy [Visio. UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Programowanie rozwiązań pakietu Office &#40;— Omówienie&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów pakietu Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Visio 2010 w programowaniu pakietu Office](http://go.microsoft.com/fwlink/?LinkId=199017)

---
title: Rozwiązania programu Visio
ms.date: 02/02/2017
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
ms.openlocfilehash: beb51866fdce18c640e41cb90a5f357fda6e5190
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628900"
---
# <a name="visio-solutions"></a>Rozwiązania programu Visio
  Program Visual Studio udostępnia szablony projektów, służących do tworzenia dodatków narzędzi VSTO dla programu Microsoft Office Visio. Za pomocą dodatków narzędzi VSTO dla programów Automatyzacja programu Visio, Rozszerz funkcje programu Visio lub dostosowywanie interfejsu użytkownika (UI) programu Visio.

 Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO zobacz [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym programistą w pakiecie Microsoft Office, zobacz [wprowadzenie &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu Visio 2010. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatyzowanie programu Visio za pomocą modelu obiektów programu Visio
 Model obiektów programu Visio udostępnia wiele klas, które służą do automatyzowania programu Visio do tworzenia diagramów, schematy organizacyjne, blokowe, osi czasu projektów, diagramy sieciowe, miejsca do magazynowania pakietu office i innym. Interfejs API umożliwia pisanie kodu w celu wykonywania typowych zadań:

- Konstrukcja i położenie kształty i tekst w diagramach.

- Zarządzanie zachowanie kształtu opartą na logice biznesowej i danych wprowadzonych przez użytkownika.

- Kontrolowanie wizualizacji diagramu, takich jak przesuwać i powiększać.

- Dostosowywanie interfejsu użytkownika aplikacji.

- Importowanie danych zewnętrznych do programu Visio, połączyć kształty i graficznej na stronie.

  Możesz wyświetlić procedury krok po kroku i przykłady dotyczące korzystania z modelu obiektów programu Visio do pracy z dokumentami i kształty w kodu [Praca z dokumentami Visio](../vsto/working-with-visio-documents.md) i [Praca z dokumentami Visio shapes](../vsto/working-with-visio-shapes.md).

  Dostęp do modelu obiektów programu Visio z dodatku narzędzi VSTO dla programów, należy użyć `Application` pole `ThisAddIn` klasy w projekcie. `Application` Pole zwraca `Microsoft.Office.Interop.Visio.Application` obiekt reprezentujący bieżące wystąpienie programu Visio. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

  Gdy wywołujesz modelu obiektów programu Visio, należy użyć typów, które są dostarczane w podstawowego zestawu międzyoperacyjnego (PIA) dla programu Visio. PIA działa jako Most między kodu zarządzanego w dodatku narzędzi VSTO dla programów i model obiektów COM w programie Visio. Wszystkie typy w programie Visio PIA są zdefiniowane w `Microsoft.Office.Interop.Visio` przestrzeni nazw. Aby uzyskać więcej informacji na temat podstawowych usług międzyoperacyjnych, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Model obiektu Visio ― omówienie
 Możesz znaleźć omówienie modelu obiektów programu Visio w [model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md), który zawiera linki do dokumentacja modelu obiektów programu Visio i zestawy SDK.

## <a name="customize-the-user-interface-of-visio"></a>Dostosowywanie interfejsu użytkownika programu Visio
 Interfejs użytkownika programu Visio ma następujące opcje dostosowywania.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dostosuj Wstążkę.|[Wstążka — omówienie](../vsto/ribbon-overview.md)|

 Aby uzyskać informacji o dostosowywaniu interfejsu użytkownika programu Visio, zobacz dokumentację referencyjną VBA [Visio.UIObject](/office/vba/api/Visio.UIObject) klasy.

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)
- [Visio 2010 w rozwój pakietu Office](http://go.microsoft.com/fwlink/?LinkId=199017)

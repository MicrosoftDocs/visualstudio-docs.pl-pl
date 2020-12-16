---
title: Model obiektów programu Visio — Omówienie
description: Dowiedz się, w jaki sposób można pracować z modelem obiektów programu Visio w celu opracowywania rozwiązań pakietu Office dla programu Microsoft Visio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9278cede2dc7f105b2741d5d63b01b4cd966c790
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528384"
---
# <a name="visio-object-model-overview"></a>Model obiektów programu Visio — Omówienie
  Do tworzenia rozwiązań pakietu Office dla programu Microsoft Office Visio można korzystać z modelu obiektów programu Visio. Ten model obiektów składa się z klas i interfejsów, które są dostępne w podstawowym zestawie międzyoperacyjnym dla programu Visio i są zdefiniowane w `Microsoft.Office.Interop.Visio` przestrzeni nazw.

 Ten temat zawiera krótkie omówienie modelu obiektów programu Visio. Aby uzyskać informacje na temat używania modelu obiektów programu Visio do wykonywania zadań w projektach pakietu Office, zobacz następujące tematy:

- [Współpraca z dokumentami programu Visio](../vsto/working-with-visio-documents.md)

- [Współpraca z kształtami programu Visio](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Omówienie modelu obiektów programu Visio
 Program Visio zawiera wiele obiektów, z którymi można korzystać. Te obiekty są zorganizowane w hierarchii, która blisko interfejsu użytkownika. W górnej części hierarchii jest obiekt [Microsoft. Office. Interop. Visio. Application](/office/vba/api/Visio.Application) . Ten obiekt reprezentuje bieżące wystąpienie programu Visio. `Microsoft.Office.Interop.Visio.Application`Obiekt zawiera `Microsoft.Office.Interop.Visio.Document` obiekty i, a `Microsoft.Office.Interop.Visio.Page` także `Microsoft.Office.Interop.Visio.Documents` `Microsoft.Office.Interop.Visio.Pages` kolekcje i. Każdy z tych obiektów i kolekcji ma wiele metod i właściwości, do których można uzyskać dostęp w celu manipulowania nimi i korzystania z niego.

 Aby uzyskać więcej informacji, zobacz dokumentację referencyjną języka VBA dla [Microsoft. Office. Interop. Visio. Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)i [Microsoft. Office. Interop. Visio. page](/office/vba/api/Visio.Page) Objects, a także [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) i [Microsoft. Office. Interop. Visio. Pages](/office/vba/api/Visio.Pages) .

 W poniższych sekcjach krótko opisano obiekty najwyższego poziomu i sposób współdziałania ze sobą. Te obiekty obejmują następujące obiekty:

- Obiekt aplikacji

- Obiekt dokumentu

- obiekt strony

### <a name="application-object"></a>Obiekt aplikacji
 Obiekt Microsoft. Office. Interop. Visio. Application reprezentuje aplikację Visio i jest elementem nadrzędnym wszystkich innych obiektów. Jego członkowie zazwyczaj mają zastosowanie do programu Visio jako całości. Aby kontrolować środowisko programu Visio, można użyć właściwości i metod programu Microsoft. Office. Interop. Visio. Application i `Microsoft.Office.Interop.Visio.ApplicationSettings` obiektów.

 W projektach dodatku VSTO można uzyskać dostęp do obiektu Microsoft. Office. Interop. Visio. Application przy użyciu `Application` pola `ThisAddIn` klasy. Aby uzyskać więcej informacji, zobacz [Programowanie dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>Obiekt dokumentu
 Obiekt Microsoft.Office.Interop.Visio.Document jest centralny do programowania programu Visio. Reprezentuje plik rysunku, wzornika lub szablonu. W przypadku otwarcia dokumentu programu Visio lub utworzenia nowego dokumentu tworzony jest nowy obiekt Microsoft.Office.Interop.Visio.Document, który jest dodawany do kolekcji Microsoft.Office.Interop.Visio.Documents elementu Microsoft. Office. Interop. Visio. Application.

 Dokument, który ma fokus, jest nazywany aktywnym dokumentem. Jest reprezentowana przez `Microsoft.Office.Interop.Visio.Application.ActiveDocument` właściwość obiektu Microsoft. Office. Interop. Visio. Application.

### <a name="page-object"></a>obiekt strony
 Obiekt Microsoft. Office. Interop. Visio. Page reprezentuje obszar rysowania strony pierwszego planu lub strony tła. Możesz użyć właściwości, `Microsoft.Office.Interop.Visio.Page.Background` Aby określić, czy strona jest stroną pierwszego planu, czy na tle.

 Aby utworzyć kształty, można użyć metod, które zawierają `Microsoft.Office.Interop.Visio.Page.DrawSpline` metody i `Microsoft.Office.Interop.Visio.Page.DrawOval` . Ponadto można pobrać wzorce ze wzorników i umieścić kształty na stronie przy użyciu `Microsoft.Office.Interop.Visio.Page.Drop` `Microsoft.Office.Interop.Visio.Page.DropMany` metod lub.

## <a name="use-the-visio-object-model-documentation"></a>Korzystanie z dokumentacji modelu obiektów programu Visio
 Aby uzyskać pełne informacje na temat modelu obiektów programu Visio, można odwołać się do odwołania do modelu obiektów VBA programu Visio. Dokumentacja modelu obiektów VBA dokumentuje model obiektów programu Visio, który jest udostępniany w kodzie Visual Basic for Applications (VBA). Aby uzyskać więcej informacji, zobacz [Dokumentacja modelu obiektów programu Visio](/office/vba/api/overview/visio/object-model).

 Wszystkie obiekty i elementy członkowskie w odwołaniu modelu obiektów VBA odpowiadają typom i elementom członkowskim w podstawowym zestawie międzyoperacyjnym programu Visio (PIA). Na przykład `Document` obiekt w odniesieniu do modelu obiektów VBA odnosi się do Microsoft.Office.Interop.Visio.Doctypu ument w Piau programu Visio. Chociaż dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod VBA w tym odwołaniu do Visual Basic lub Visual C#, jeśli chcesz użyć ich w projekcie dodatku VSTO programu Visio utworzonym przy użyciu programu Visual Studio.

> [!NOTE]
> W tej chwili nie ma dokumentacji referencyjnej dla podstawowego zestawu międzyoperacyjnego programu Visio.

 Aby zapoznać się z przykładami kodu i dodatkowymi narzędziami do tworzenia rozwiązań dla programu Visio, zobacz temat [visio 2010 Software Development Kit](https://www.microsoft.com/download/details.aspx?id=12365).

### <a name="additional-types-in-primary-interop-assemblies"></a>Dodatkowe typy w podstawowych zestawach międzyoperacyjnych
 Możesz znaleźć typy w podstawowych zestawach międzyoperacyjnych, które nie są widoczne dla języka VBA z powodu różnic w implementacji. Język VBA zawiera widok modelu obiektów programu Visio, który zawiera tylko te obiekty i elementy członkowskie, których można używać bezpośrednio. Podstawowe zestawy międzyoperacyjności uwidaczniają ten sam model obiektów, ale zawierają również inne interfejsy, klasy i elementy członkowskie, które tłumaczą obiekty w modelu obiektów COM na kod zarządzany. Te dodatkowe elementy nie są przeznaczone do użycia bezpośrednio w kodzie.

 Aby uzyskać więcej informacji, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/office-12/ms247299(v=office.12)) i [podstawowych zestawach międzyoperacyjnych pakietu Office](../vsto/office-primary-interop-assemblies.md).

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Współpraca z dokumentami programu Visio](../vsto/working-with-visio-documents.md)
- [Współpraca z kształtami programu Visio](../vsto/working-with-visio-shapes.md)

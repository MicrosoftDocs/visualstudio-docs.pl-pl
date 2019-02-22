---
title: Model obiektu Visio ― omówienie
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
ms.openlocfilehash: 806a2a2165dc604969e2bd8f35a0eb9c1cf07556
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636713"
---
# <a name="visio-object-model-overview"></a>Model obiektu Visio ― omówienie
  Do opracowywania rozwiązań pakietu Office dla programu Microsoft Office Visio, możesz korzystać z modelu obiektów programu Visio. Ten model obiektów składa się z klasy i interfejsy, które znajdują się w podstawowy zestaw międzyoperacyjny dla programu Visio i są definiowane w `Microsoft.Office.Interop.Visio` przestrzeni nazw.

 Ten temat zawiera krótkie omówienie modelu obiektów programu Visio. Aby dowiedzieć się, jak za pomocą modelu obiektów programu Visio do wykonywania zadań w projektach pakietu Office zobacz następujące tematy:

-   [Praca z dokumentami Visio](../vsto/working-with-visio-documents.md)

-   [Praca z dokumentami Visio shapes](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Informacje o modelu obiektów programu Visio
 Program Visio zawiera wiele obiektów, z którymi możesz wchodzić w interakcje. Te obiekty są zorganizowane w hierarchii, który jest ściśle zgodna interfejsu użytkownika. W górnej części hierarchii jest [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) obiektu. Ten obiekt reprezentuje bieżące wystąpienie programu Visio. `Microsoft.Office.Interop.Visio.Application` Obiekt zawiera `Microsoft.Office.Interop.Visio.Document` i `Microsoft.Office.Interop.Visio.Page` obiekty, jak również `Microsoft.Office.Interop.Visio.Documents` i `Microsoft.Office.Interop.Visio.Pages` kolekcji. Każda z tych obiektów i kolekcji ma wiele metod i właściwości, do których masz dostęp do manipulowania i korzystać z niego.

 Aby uzyskać więcej informacji, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document), i [ Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) obiektów, a także [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) i [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) Kolekcje.

 W poniższych sekcjach opisano skrótowo obiektów najwyższego poziomu i jak współdziałają ze sobą. Te obiekty obejmują następujące obiekty:

-   Obiekt aplikacji

-   Obiekt dokumentu

-   obiekt strony

### <a name="application-object"></a>Obiekt aplikacji
 Obiekt Microsoft.Office.Interop.Visio.Application reprezentuje aplikacji Visio, a jest nadrzędne względem wszystkich innych obiektów. Jej członków zwykle mają zastosowanie do programu Visio jako całości. Można użyć właściwości i metody Microsoft.Office.Interop.Visio.Application i `Microsoft.Office.Interop.Visio.ApplicationSettings` obiektów w celu kontrolowania środowiska programu Visio.

 W projektach dodatku narzędzi VSTO obiektu Microsoft.Office.Interop.Visio.Application mieli dostęp za pomocą `Application` pole `ThisAddIn` klasy. Aby uzyskać więcej informacji, zobacz [programowania dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>Obiekt dokumentu
 Obiekt Microsoft.Office.Interop.Visio.Document stanowi podstawę do programowania programu Visio. Reprezentuje rysunku, wzornika lub pliku szablonu. Po otwarciu dokumentu programu Visio lub utworzyć nowy dokument, Utwórz nowy obiekt Microsoft.Office.Interop.Visio.Document, który zostanie dodany do kolekcji Microsoft.Office.Interop.Visio.Documents obiektu Microsoft.Office.Interop.Visio.Application .

 Dokument, który ma fokus nosi nazwę aktywnego dokumentu. Jest reprezentowany przez `Microsoft.Office.Interop.Visio.Application.ActiveDocument` właściwości obiektu Microsoft.Office.Interop.Visio.Application.

### <a name="page-object"></a>obiekt strony
 Obiekt Microsoft.Office.Interop.Visio.Page reprezentuje obszaru rysowania stronę pierwszego planu i tła strony. Możesz użyć `Microsoft.Office.Interop.Visio.Page.Background` właściwości w celu określenia, czy jest to strona pierwszego planu i tła.

 Aby tworzyć kształty, można użyć metod, które obejmują `Microsoft.Office.Interop.Visio.Page.DrawSpline` i `Microsoft.Office.Interop.Visio.Page.DrawOval` metody. Ponadto pobieranie wzorców z wzorników i umieścić kształty na stronie przy użyciu `Microsoft.Office.Interop.Visio.Page.Drop` lub `Microsoft.Office.Interop.Visio.Page.DropMany` metody.

## <a name="use-the-visio-object-model-documentation"></a>Zapoznaj się z dokumentacją model obiektu Visio
 Aby uzyskać pełne informacje na temat modelu obiektów programu Visio mogą odwoływać się do dokumentacja modelu obiektów programu Visio VBA. Dokumentacja modelu obiektów VBA dokumenty model obiektów programu Visio, jak jest narażony na język Visual Basic for Applications (VBA) kod. Aby uzyskać więcej informacji, zobacz [dokumentacja modelu obiektów programu Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199775).

 Wszystkie obiekty i elementy członkowskie w dokumentacja modelu obiektów VBA odnoszą się do typów i członków w programie Visio podstawowego zestawu międzyoperacyjnego (PIA). Na przykład `Document` obiektu w dokumentacja modelu obiektów VBA odpowiada typowi Microsoft.Office.Interop.Visio.Document w PIA programu Visio. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metody i zdarzenia, należy translacji kodu VBA w ramach tego odwołania do Visual Basic lub Visual C# Jeśli chcesz używać ich w projekcie dodatku narzędzi VSTO programu Visio utworzonego za pomocą Program Visual Studio.

> [!NOTE]
>  W tej chwili brak Dokumentacja referencyjna dla podstawowego zestawu międzyoperacyjnego programu Visio.

 Przykłady kodu powiązany i dodatkowych narzędzi do tworzenia rozwiązania programu Visio można znaleźć [zestaw Visio 2010 software development kit](http://go.microsoft.com/fwlink/?LinkId=196501).

### <a name="additional-types-in-primary-interop-assemblies"></a>Dodatkowe typy w podstawowych zestawów międzyoperacyjnych
 Typów można znaleźć w podstawowe zestawy międzyoperacyjne, które nie są widoczne (VBA) z powodu różnic w implementacji. VBA udostępnia widok modelu obiektów programu Visio, który zawiera tylko te obiekty i elementy członkowskie, które są dostępne bezpośrednio. Podstawowe zestawy międzyoperacyjne udostępnianie tego samego modelu obiektu, ale te aktualizacje obejmują również inne interfejsy, klasy i elementów członkowskich, które dadzą obiekty w modelu obiektów COM z kodem zarządzanym. Te dodatkowe elementy nie są przeznaczone do użycia bezpośrednio w kodzie.

 Aby uzyskać więcej informacji, zobacz [Przegląd klasy i interfejsy podstawowe zestawy międzyoperacyjne pakietu Office](http://go.microsoft.com/fwlink/?LinkId=189592) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).

## <a name="see-also"></a>Zobacz także
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Praca z dokumentami Visio](../vsto/working-with-visio-documents.md)
- [Praca z dokumentami Visio shapes](../vsto/working-with-visio-shapes.md)

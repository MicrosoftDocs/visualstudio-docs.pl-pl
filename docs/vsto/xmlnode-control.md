---
title: formant XMLNode
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 04c2bd062b90f94349a67f52146319e3d37bab3a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869856"
---
# <a name="xmlnode-control"></a>formant XMLNode
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest prezentowane wyłącznie do korzyści i korzystanie z innym osobom oraz organizacjom, którzy znajdują się poza w Stanach Zjednoczonych i ich terytoriach lub korzystających z lub tworzenie programy, korzystających z produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy kod XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word nie mogą być odczytywane lub używane przez osoby i organizacje w Stanach Zjednoczonych lub jego terytoria, którzy za pomocą lub opracowywanie programów uruchamianych na produkty Microsoft Word, które są licencjonowane przez firmę Microsoft, po 10 stycznia 2010 r. ; te produkty będą nie działa tak samo jako produkty licencjonowane przed tą datą lub kupić i licencjonowane do użycia poza Stanami Zjednoczonymi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Formant jest zamapowany obiekt węzła XML udostępnia zdarzenia, która może być powiązana z danymi. <xref:Microsoft.Office.Tools.Word.XMLNode> Formant zostanie utworzony tylko wtedy, gdy element schematu niepowtarzający jest mapowana na dokument programu Microsoft Office Word. Gdy program Visual Studio utworzy węzła XML, można programować względem go bezpośrednio, bez konieczności przechodzenia z modelu obiektów programu Word.  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Kontroli można usunąć tylko wtedy, usuwając mapowania elementu w programie Word.  
  
## <a name="bind-data-to-the-control"></a>Wiązanie danych do kontrolki  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Kontrolka obsługuje proste powiązanie danych. Węzeł XML powinien być związany ze źródłem danych przy użyciu <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości. Jeśli dane w powiązanej zestaw danych zostanie zaktualizowane, <xref:Microsoft.Office.Tools.Word.XMLNode> kontroli zmiany zostały uwzględnione.  
  
## <a name="formatting"></a>Formatowanie  
 Formatowanie, które mogą być stosowane do <xref:Microsoft.Office.Interop.Word.XMLNode> obiektu można zastosować do <xref:Microsoft.Office.Tools.Word.XMLNode> kontroli. W tym czcionki, tekst podkreślony i style znaków.  
  
## <a name="events"></a>Zdarzenia  
 Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Word.XMLNode> sterowania:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="compare-events"></a>Porównanie zdarzeń  
 Można przechwycić zdarzenie, gdy użytkownik przesuwa kursor jej w kontekście określonego <xref:Microsoft.Office.Tools.Word.XMLNode> kontroli. Na przykład, Niewykluczone, że <xref:Microsoft.Office.Tools.Word.XMLNode> formantu o nazwie `Customer` ma element podrzędny <xref:Microsoft.Office.Tools.Word.XMLNode> formantu o nazwie `Company`, i `Company` ma dwa podrzędny <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolki o nazwie `CompanyName` i `CompanyRegion` w następujący sposób:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Jeśli chcesz wyświetlić formant w okienku Akcje zawsze, gdy kursor jest przenoszony do `Company` węzła, go powinna nie ma znaczenia, czy znajduje się kursor w `CompanyName` lub `CompanyRegion` ponieważ są one zarówno w kontekście `Company`. W tym przypadku pisanie kodu w <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zdarzenia `Company`.  
  
 W większości przypadków, gdy kursor przejdzie <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolować zarówno <xref:Microsoft.Office.Tools.Word.XMLNode.Select> i <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zdarzenia są wywoływane. W poniższej tabeli przedstawiono różnice między tymi zdarzeniami.  
  
|Wybierz zdarzenie|Zdarzenie ContextEnter|  
|------------------|------------------------|  
|Występuje, gdy kursor znajduje się wewnątrz <xref:Microsoft.Office.Tools.Word.XMLNode>.|Występuje, gdy kursor znajduje się wewnątrz <xref:Microsoft.Office.Tools.Word.XMLNode> lub jeden z jego węzłów podrzędnych z obszaru poza kontekstem węzła. Innymi słowy jest zgłaszany tylko wtedy, gdy zmienia kontekst.|  
  
 Na przykład, gdy kursor jest z poza `Customer` do `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zdarzenie `Customer`, `Company`, i `CompanyName` jest wywoływane. Jeśli następnie przesuń kursor z `CompanyName` do `CompanyRegion`, tylko <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zdarzenie `CompanyRegion` jest wywoływane, ponieważ są nadal w kontekście zarówno `Company` i `Customer`.  
  
 Tym samym różnice między <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> zdarzeń i <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> zdarzeń.  
  
## <a name="see-also"></a>Zobacz także  
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Formant XMLNodes](../vsto/xmlnodes-control.md)   
 [Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Instrukcje: Mapowanie schematów z dokumentami programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  

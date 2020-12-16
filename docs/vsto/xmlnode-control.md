---
title: formant XMLNode
description: Dowiedz się, że formant XMLNode jest zmapowanym obiektem węzła XML, który uwidacznia zdarzenia i może być powiązany z danymi.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 58f9c5db883f55c00236bc202797dcf2ec3003f6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528340"
---
# <a name="xmlnode-control"></a>formant XMLNode
  **Ważne** Informacje przedstawione w tym temacie dotyczące programu Microsoft Word są prezentowane wyłącznie na korzyść i użytkowanie przez osoby i organizacje, które znajdują się poza Stany Zjednoczoneą i jej terytoriami, lub opracowywaniem programów, które są uruchamiane w programie Microsoft Word, które zostały licencjonowane przez firmę Microsoft przed 2010 stycznia, gdy firma Microsoft usunie implementację konkretnych funkcji związanych z niestandardowym kodem XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word mogą nie być odczytane lub używane przez osoby lub organizacje w Stany Zjednoczone lub na terytoriach, którzy korzystają z programu lub opracowywania programów, które są uruchamiane w programie, produkty Microsoft Word, które zostały licencjonowane przez firmę Microsoft po 10 stycznia 2010; te produkty nie będą działać tak samo jak produkty licencjonowane przed tą datą lub zakupione i licencjonowane do użycia poza Stany Zjednoczone.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNode>Kontrolka jest mapowanym obiektem węzła XML, który uwidacznia zdarzenia i może być powiązany z danymi. <xref:Microsoft.Office.Tools.Word.XMLNode>Formant jest tworzony tylko wtedy, gdy niepowtarzany element schematu jest mapowany do dokumentu programu Microsoft Office Word. Po utworzeniu węzła XML przez program Visual Studio można bezpośrednio go zaprogramować bez konieczności przechodzenia przez model obiektów programu Word.

 <xref:Microsoft.Office.Tools.Word.XMLNode>Formant można usunąć tylko przez usunięcie mapowania elementu w programie Word.

## <a name="bind-data-to-the-control"></a>Powiąż dane z kontrolką
 <xref:Microsoft.Office.Tools.Word.XMLNode>Kontrolka obsługuje proste powiązanie danych. Węzeł XML powinien być powiązany ze źródłem danych przy użyciu <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości. Jeśli dane w powiązanym zestawie danych zostaną zaktualizowane, <xref:Microsoft.Office.Tools.Word.XMLNode> formant odzwierciedla zmiany.

## <a name="formatting"></a>Formatowanie
 Formatowanie, które można zastosować do <xref:Microsoft.Office.Interop.Word.XMLNode> obiektu, można zastosować do <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolki. Obejmuje to czcionki, style podkreślenia i style znaków.

## <a name="events"></a>Zdarzenia
 Dla kontrolki dostępne są następujące zdarzenia <xref:Microsoft.Office.Tools.Word.XMLNode> :

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Porównaj zdarzenia
 Możesz przechwytywać zdarzenie, gdy użytkownik przesunie swój kursor w kontekście określonej <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolki. Na przykład można mieć <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolkę o nazwie, `Customer` która ma <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolkę podrzędną o nazwie `Company` i `Company` ma dwie <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolki podrzędne o nazwie `CompanyName` i `CompanyRegion` w następujący sposób:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Jeśli chcesz, aby kontrolka była wyświetlana w okienku Akcje za każdym razem, gdy kursor zostanie przeniesiony do `Company` węzła, nie powinien on mieć znaczenia, czy kursor znajduje się w `CompanyName` lub w `CompanyRegion` kontekście `Company` . W takim przypadku można napisać kod w <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zdarzeniu `Company` .

 W większości przypadków, gdy kursor przejdzie do <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolki, <xref:Microsoft.Office.Tools.Word.XMLNode.Select> <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> są wywoływane zdarzenia i. W poniższej tabeli przedstawiono różnice między tymi zdarzeniami.

|Wybierz zdarzenie|Zdarzenie ContextEnter|
|------------------|------------------------|
|Występuje, gdy kursor jest umieszczony wewnątrz <xref:Microsoft.Office.Tools.Word.XMLNode> .|Występuje, gdy kursor zostanie umieszczony wewnątrz <xref:Microsoft.Office.Tools.Word.XMLNode> lub w jednym z jego węzłów podrzędnych, z obszaru poza kontekstem węzła. Innymi słowy, jest wywoływany tylko w przypadku zmiany kontekstu.|

 Na przykład po przesunięciu kursora z zewnątrz `Customer` do `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zdarzenie dla `Customer` , `Company` , i `CompanyName` jest wywoływane. Jeśli następnie przeniesiesz kursor z `CompanyName` do `CompanyRegion` , zostanie <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zgłoszone tylko zdarzenie dla zdarzenia, `CompanyRegion` ponieważ nadal znajduje się w kontekście obu `Company` i `Customer` .

 Istnieją takie same różnice między <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> zdarzeniem i <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> zdarzeniem.

## <a name="see-also"></a>Zobacz też
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Formant XMLNodes](../vsto/xmlnodes-control.md)
- [Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Instrukcje: mapowanie schematów do dokumentów programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

---
title: formant XMLNodes
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ad16165924a33a25dab2b1cfb49a0a7bbfe0875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64834598"
---
# <a name="xmlnodes-control"></a>formant XMLNodes
  **Ważne** Informacje przedstawione w tym temacie dotyczące programu Microsoft Word są prezentowane wyłącznie na korzyść i użytkowanie przez osoby i organizacje, które znajdują się poza Stany Zjednoczoneą i jej terytoriami, lub opracowywaniem programów, które są uruchamiane w programie Microsoft Word, które zostały licencjonowane przez firmę Microsoft przed 2010 stycznia, gdy firma Microsoft usunie implementację konkretnych funkcji związanych z niestandardowym kodem XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word mogą nie być odczytane lub używane przez osoby lub organizacje w Stany Zjednoczone lub na terytoriach, którzy korzystają z programu lub opracowywania programów, które są uruchamiane w programie, produkty Microsoft Word, które zostały licencjonowane przez firmę Microsoft po 10 stycznia 2010; te produkty nie będą działać tak samo jak produkty licencjonowane przed tą datą lub zakupione i licencjonowane do użycia poza Stany Zjednoczone.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNodes>Kontrolka jest kolekcją mapowanych obiektów węzła XML, które ujawniają zdarzenia. <xref:Microsoft.Office.Tools.Word.XMLNodes>Formant jest tworzony tylko wtedy, gdy powtarzalny element schematu jest mapowany do dokumentu programu Microsoft Office Word. Jeśli element powtarzający zawiera elementy podrzędne, każdy element podrzędny jest również tworzony jako <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolka.

 Po utworzeniu kolekcji węzłów XML przez program Visual Studio możesz programować bezpośrednio kontrolę bez konieczności przechodzenia przez model obiektów programu Word. <xref:Microsoft.Office.Tools.Word.XMLNodes>Formant można usunąć tylko przez usunięcie mapowania elementu z dokumentu.

> [!NOTE]
> Jeśli uzyskujesz dostęp do elementu podrzędnego <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki za pomocą <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> właściwości, zwraca <xref:Microsoft.Office.Interop.Word.XMLNode> obiekt, a nie <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolkę. Aby uzyskać więcej informacji, zobacz Ograniczenia programowe [elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Powiąż dane z kontrolką
 <xref:Microsoft.Office.Tools.Word.XMLNodes>Formant nie obsługuje powiązania danych. Dzieje się tak <xref:Microsoft.Office.Tools.Word.XMLNodes> , ponieważ kontrolka nie ma złożonych możliwości powiązań danych, a proste powiązanie danych nie może reprezentować powtarzających się danych.

## <a name="formatting"></a>Formatowanie
 Wszelkie formatowanie, które można zastosować do tekstu w dokumencie, można zastosować do <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki.

## <a name="events"></a>Zdarzenia
 Zdarzenia dostępne dla <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki są następujące:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Porównaj zdarzenia
 Możesz przechwytywać zdarzenie, gdy użytkownik przesunie swój kursor w kontekście określonej <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki. Na przykład można mieć <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolkę o nazwie, `Customer` która ma <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolkę podrzędną o nazwie `Company` i `Company` ma dwie <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki podrzędne o nazwie `CompanyName` i `CompanyRegion` w następujący sposób:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Jeśli chcesz, aby kontrolka była wyświetlana w okienku Akcje za każdym razem, gdy kursor zostanie przeniesiony do `Company` węzła, nie powinien on mieć znaczenia, czy kursor znajduje się w `CompanyName` lub w `CompanyRegion` kontekście `Company` . W takim przypadku można napisać kod w <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzeniu `Company` .

 W większości przypadków, gdy kursor przejdzie do <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki, <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> są wywoływane zdarzenia i. W poniższej tabeli przedstawiono różnice między tymi zdarzeniami.

|Wybierz zdarzenie|Zdarzenie ContextEnter|
|------------------|------------------------|
|Występuje, gdy kursor zostanie umieszczony w jednym z węzłów <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekcji.|Występuje, gdy kursor znajduje się w jednym z węzłów lub węzłów podrzędnych <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekcji, od obszaru poza kontekstem węzła. Innymi słowy, jest uruchamiany tylko wtedy, gdy zmienia się kontekst, i może zostać wywołane dla wielu <xref:Microsoft.Office.Tools.Word.XMLNodes> formantów zagnieżdżonych.|

 Na przykład po przesunięciu kursora z poza `Customer` do `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzenia dla `Customer` , `Company` i `CompanyName` są wywoływane. Po przeniesieniu kursora od `CompanyName` do `CompanyRegion` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzenie `CompanyRegion` jest wywoływane, ponieważ kontekst jest taki sam dla obu `Company` i `Customer` . W dokumencie można mieć wiele `Company` węzłów. Jeśli przesuniesz kursor z `CompanyName` węzła jednego `Company` do `CompanyName` drugiego `Company` , kontekst jest taki sam, więc <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> zostanie zgłoszone tylko zdarzenie.

 Istnieją takie same różnice między <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> zdarzeniem i <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> zdarzeniem.

## <a name="see-also"></a>Zobacz też
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode — formant](../vsto/xmlnode-control.md)
- [Instrukcje: Dodawanie kontrolek XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Instrukcje: mapowanie schematów do dokumentów programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

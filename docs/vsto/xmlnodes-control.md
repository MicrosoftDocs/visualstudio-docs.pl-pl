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
ms.openlocfilehash: b2be6fbafc1520e190cc52bea839c6cf9e208ca4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090583"
---
# <a name="xmlnodes-control"></a>formant XMLNodes
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest prezentowane wyłącznie do korzyści i korzystanie z innym osobom oraz organizacjom, którzy znajdują się poza w Stanach Zjednoczonych i ich terytoriach lub korzystających z lub tworzenie programy, korzystających z produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy kod XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word nie mogą być odczytywane lub używane przez osoby i organizacje w Stanach Zjednoczonych lub jego terytoria, którzy za pomocą lub opracowywanie programów uruchamianych na produkty Microsoft Word, które są licencjonowane przez firmę Microsoft, po 10 stycznia 2010 r. ; te produkty będą nie działa tak samo jako produkty licencjonowane przed tą datą lub kupić i licencjonowane do użycia poza Stanami Zjednoczonymi.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNodes> Kontroli to zbiór mapowanych obiektów węzła XML, który przedstawia zdarzenia. <xref:Microsoft.Office.Tools.Word.XMLNodes> Formant zostanie utworzony tylko wtedy, gdy powtarzający się element schematu jest mapowana na dokument programu Microsoft Office Word. Jeśli powtarzający się element zawiera elementy podrzędne, każdy z elementów podrzędnych jest tworzona jako <xref:Microsoft.Office.Tools.Word.XMLNodes> kontroli.

 Gdy program Visual Studio utworzy kolekcję węzłów XML, można programować względem kontrolki bezpośrednio, bez konieczności przechodzenia z modelu obiektów programu Word. <xref:Microsoft.Office.Tools.Word.XMLNodes> Kontroli można usunąć tylko wtedy, usuwając mapowania elementu z dokumentu.

> [!NOTE]
>  Jeśli masz dostępu do elementu podrzędnego <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolować za pośrednictwem <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> właściwość zwraca <xref:Microsoft.Office.Interop.Word.XMLNode> obiektu zamiast <xref:Microsoft.Office.Tools.Word.XMLNode> kontroli. Aby uzyskać więcej informacji, zobacz [ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Wiązanie danych do kontrolki
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Formant nie obsługuje powiązanie danych. Jest to spowodowane <xref:Microsoft.Office.Tools.Word.XMLNodes> formant nie ma powiązania możliwości złożonych danych i proste powiązanie danych nie może reprezentować powtarzających się danych.

## <a name="formatting"></a>Formatowanie
 Żadne formatowanie, który można zastosować do tekstu w obrębie dokumentu mogą być stosowane do <xref:Microsoft.Office.Tools.Word.XMLNodes> kontroli.

## <a name="events"></a>Zdarzenia
 Zdarzenia dostępne dla <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrola to:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Porównanie zdarzeń
 Można przechwycić zdarzenie, gdy użytkownik przesuwa kursor jej w kontekście określonego <xref:Microsoft.Office.Tools.Word.XMLNodes> kontroli. Na przykład, Niewykluczone, że <xref:Microsoft.Office.Tools.Word.XMLNodes> formantu o nazwie `Customer` ma element podrzędny <xref:Microsoft.Office.Tools.Word.XMLNodes> formantu o nazwie `Company`, i `Company` ma dwa podrzędny <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki o nazwie `CompanyName` i `CompanyRegion` w następujący sposób:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Jeśli chcesz wyświetlić formant w okienku Akcje zawsze, gdy kursor jest przenoszony do `Company` węzła, go powinna nie ma znaczenia, czy znajduje się kursor w `CompanyName` lub `CompanyRegion` ponieważ są one zarówno w kontekście `Company`. W tym przypadku pisanie kodu w <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzenia `Company`.

 W większości przypadków, gdy kursor przejdzie <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolować zarówno <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> i <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzenia są wywoływane. W poniższej tabeli przedstawiono różnice między tymi zdarzeniami.

|Wybierz zdarzenie|Zdarzenie ContextEnter|
|------------------|------------------------|
|Występuje, gdy kursor znajduje się w jednym z węzłów <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekcji.|Występuje, gdy kursor znajduje się w jednym z węzłów i węzłów podrzędnych <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekcji z obszaru poza kontekstem węzła. Innymi słowy, jest zgłaszany tylko wtedy, gdy zmienia kontekst i może nie być zgłaszany wielu zagnieżdżonych <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki.|

 Na przykład, gdy kursor jest z poza `Customer` do `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzeń związanych z `Customer`, `Company`, i `CompanyName` są wywoływane. Jeśli następnie przesuń kursor z `CompanyName` do `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzenia tylko dla `CompanyRegion` jest wywoływane, ponieważ kontekst ma takie same dla obu `Company` i `Customer`. Masz wiele `Company` węzły w dokumencie. Jeśli przesuniesz kursor z `CompanyName` jeden węzeł `Company` do `CompanyName` węzła innego `Company`, kontekstu jest taka sama, dlatego tylko <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> zdarzenie jest wywoływane.

 Tym samym różnice między <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> zdarzeń i <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> zdarzeń.

## <a name="see-also"></a>Zobacz także
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Formant XMLNode](../vsto/xmlnode-control.md)
- [Instrukcje: Dodawanie formantów XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Instrukcje: Mapowanie schematów z dokumentami programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

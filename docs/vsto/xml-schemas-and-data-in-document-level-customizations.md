---
title: Schematy XML i dane w dostosowaniach na poziomie dokumentu
description: Program Microsoft Excel i program Word zapewniają możliwość mapowania schematów na dokumenty oraz upraszczają importowanie i eksportowanie danych XML do i z dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 54e993f41787cfa44bb0aaa78cc7aff8fbad53d8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826593"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Schematy XML i dane w dostosowaniach na poziomie dokumentu
  **Ważne** Informacje przedstawione w tym temacie dotyczące programu Microsoft Word są prezentowane wyłącznie na rzecz osób i organizacji, które znajdują się poza firmą Stany Zjednoczone i jej terytoriami lub korzystają z produktów Microsoft Word licencjonowanych przez firmę Microsoft przed styczniem 2010 r., gdy firma Microsoft usunęła z programu Microsoft Word implementację konkretnych funkcji związanych z niestandardowym kodem XML. Te informacje dotyczące programu Microsoft Word nie mogą być odczytywane ani używane przez osoby ani organizacje z witryny Stany Zjednoczone lub jej terytoriów, które z nich korzystają, ani nie opracowują programów uruchamianych w produktach Microsoft Word licencjonowanych przez firmę Microsoft po 10 stycznia 2010 r.; te produkty nie będą zachowywać się tak samo jak produkty licencjonowane przed tym dniem lub zakupione i licencjonowane do użytku poza Stany Zjednoczone.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office excel i Microsoft Office Word zapewniają możliwość mapowania schematów na dokumenty. Ta funkcja może uprościć importowanie i eksportowanie danych XML do i z dokumentu.

 Visual Studio uwidacznia zamapowane elementy schematu w dostosowaniach na poziomie dokumentu jako kontrolki w modelu programowania. W przypadku programu Excel Visual Studio obsługę powiązania kontrolek z danymi w bazach danych, usługach sieci Web i obiektach. W przypadku programów Word i Excel Visual Studio obsługę okienek akcji, które mogą być używane z dokumentami mapowanych w schemacie w celu utworzenia ulepszonego interfejsu użytkownika końcowego dla rozwiązań. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

> [!NOTE]
> W rozwiązaniach programu Excel nie można używać wieloczęściowych schematów XML.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Obiekty tworzone, gdy schematy są dołączane do skoroszytów programu Excel
 Po dołączeniu schematu do skoroszytu program Visual Studio automatycznie tworzy kilka obiektów i dodaje je do projektu. Tych obiektów nie należy usuwać przy użyciu Visual Studio, ponieważ są one zarządzane przez program Excel. Aby je usunąć, usuń zamapowane elementy z arkusza lub odłącz schemat przy użyciu narzędzi programu Excel.

 Istnieją dwa główne obiekty:

- Schemat XML (plik XSD). Dla każdego schematu w skoroszycie Visual Studio dodaje schemat do projektu. Jest on wyświetlany jako element projektu z rozszerzeniem XSD w **Eksplorator rozwiązań**.

- Klasa <xref:System.Data.DataSet> typowana. Ta klasa jest tworzona na podstawie schematu. Ta klasa zestawu danych jest widoczna w **Widok klasy**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Obiekty tworzone, gdy elementy schematu są mapowane na arkusze programu Excel
 Podczas mapowania elementu schematu z okienka zadań Źródło **XML** do arkusza program Visual Studio automatycznie tworzy kilka obiektów i dodaje je do projektu:

- Formantów. Dla każdego zamapowanych obiektów w skoroszycie w modelu programowania jest tworzona kontrolka (dla nie powtarzających się elementów schematu) lub kontrolka (do powtarzania <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> elementów schematu). Kontrolkę <xref:Microsoft.Office.Tools.Excel.ListObject> można usunąć tylko przez usunięcie mapowań i zamapowanych obiektów ze skoroszytu. Aby uzyskać więcej informacji na temat kontrolek, zobacz [Host items and host controls overview (Elementy hosta i kontrolki hosta — omówienie).](../vsto/host-items-and-host-controls-overview.md)

- Bindingsource. Podczas tworzenia obiektu przez mapowanie nie powtarzających się elementów schematu na arkusz tworzony jest obiekt , a kontrolka jest powiązana <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:System.Windows.Forms.BindingSource> z <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> elementem <xref:System.Windows.Forms.BindingSource> . Należy powiązać obiekt z wystąpieniem źródła danych, które jest takie samo jak schemat zamapowany na dokument, na przykład z wystąpieniem klasy typkowanej, <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> która została utworzona. Utwórz powiązanie, ustawiając właściwości <xref:System.Windows.Forms.BindingSource.DataSource%2A> i , które są widoczne w <xref:System.Windows.Forms.BindingSource.DataMember%2A> **oknie** Właściwości.

    > [!NOTE]
    > Obiekt <xref:System.Windows.Forms.BindingSource> nie jest tworzony dla obiektów <xref:Microsoft.Office.Tools.Excel.ListObject> . Musisz ręcznie powiązać plik ze źródłem <xref:Microsoft.Office.Tools.Excel.ListObject> danych, ustawiając właściwości <xref:System.Windows.Forms.BindingSource.DataSource%2A> i w <xref:System.Windows.Forms.BindingSource.DataMember%2A> **oknie** Właściwości.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Zamapowane schematy pakietu Office i Visual Studio źródła danych pakietu Office
 Zarówno funkcja zamapowanych schematów pakietu Office, jak i Visual Studio **źródła** danych mogą ułatwić prezentowanie danych w arkuszu programu Excel do raportowania lub edytowania. W obu przypadkach można przeciągać elementy danych do arkusza programu Excel. Obie metody tworzą kontrolki, które są powiązane przez dane ze źródłem <xref:System.Windows.Forms.BindingSource> danych, takim jak usługa <xref:System.Data.DataSet> lub usługa internetowa.

> [!NOTE]
> Podczas mapowania powtarzającego się elementu schematu do arkusza program Visual Studio obiekt <xref:Microsoft.Office.Tools.Excel.ListObject> . Nie <xref:Microsoft.Office.Tools.Excel.ListObject> jest automatycznie powiązana z danymi za pośrednictwem . <xref:System.Windows.Forms.BindingSource> Musisz ręcznie powiązać plik ze źródłem <xref:Microsoft.Office.Tools.Excel.ListObject> danych, ustawiając właściwości <xref:System.Windows.Forms.BindingSource.DataSource%2A> i w <xref:System.Windows.Forms.BindingSource.DataMember%2A> **oknie** Właściwości.

 W poniższej tabeli przedstawiono niektóre różnice między tymi dwiema metodami.

|Schemat XML|Data Sources — Okno|
|----------------|-------------------------|
|Używa interfejsu pakietu Office.|Używa **okna Źródła danych** w Visual Studio.|
|Włącza wbudowane funkcje pakietu Office do importowania i eksportowania danych z plików XML.|Należy programowo udostępnić funkcje importowania i eksportowania.|
|Musisz napisać kod, aby wypełnić wygenerowane kontrolki danymi.|Kontrolki dodane w **oknie Źródła** danych mają automatycznie generowany kod w celu ich wypełnienia wraz z niezbędnymi ciągami połączenia podczas korzystania z serwerów baz danych.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Zachowanie podczas dołączania schematów do dokumentów programu Word
 Obiekty danych nie są tworzone podczas dołączania schematu do dokumentu programu Word, który jest używany w projekcie pakietu Office na poziomie dokumentu. Jednak podczas mapowania elementu schematu na dokument są tworzone kontrolki. Typ kontrolki zależy od typu mapowego elementu; Powtarzające się elementy generują kontrolki, a elementy nie <xref:Microsoft.Office.Tools.Word.XMLNodes> powtarzające się generują <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolki. Aby uzyskać więcej informacji, zobacz [XMLNodes Control](../vsto/xmlnodes-control.md) and XMLNode Control (Kontrolka [XMLNodes i kontrolka XMLNode).](../vsto/xmlnode-control.md)

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Wdrażanie rozwiązań, które obejmują schematy XML
 Należy utworzyć instalatora w celu wdrożenia rozwiązania, które używa schematu XML zamapego na dokument. Instalator powinien zarejestrować schemat w bibliotece schematów na komputerze użytkownika. Jeśli schemat nie zostanie zarejestrowany, rozwiązanie będzie nadal działać, ponieważ program Word generuje tymczasowy schemat na podstawie elementów, które znajdują się w dokumencie, gdy użytkownik otworzy go. Jednak użytkownik nie będzie mógł przeprowadzić weryfikacji ani zapisać schematu użytego do utworzenia projektu. Aby uzyskać więcej informacji na temat instalatorów, zobacz [Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

 Możesz również dodać kod do projektu, aby sprawdzić, czy schemat znajduje się w bibliotece i jest zarejestrowany. Jeśli tak nie jest, możesz ostrzec użytkownika.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs" id="Snippet1":::

## <a name="see-also"></a>Zobacz też

- [How to: Mapowanie schematów na dokumenty programu Word w Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [How to: Mapowanie schematów na arkusze wewnątrz Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)

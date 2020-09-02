---
title: Schematy XML i dane w dostosowaniach na poziomie dokumentu
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb8bc9b9d3149112517d893cd3a704826b6d92d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808383"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Schematy XML i dane w dostosowaniach na poziomie dokumentu
  **Ważne** Informacje przedstawione w tym temacie dotyczące programu Microsoft Word są prezentowane wyłącznie na korzyść i użytkowanie przez osoby i organizacje, które znajdują się poza Stany Zjednoczoneą i jej terytoriami, lub opracowywaniem programów, które są uruchamiane w programie Microsoft Word, które zostały licencjonowane przez firmę Microsoft przed 2010 stycznia, gdy firma Microsoft usunie implementację konkretnych funkcji związanych z niestandardowym kodem XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word mogą nie być odczytane lub używane przez osoby lub organizacje w Stany Zjednoczone lub na terytoriach, którzy korzystają z programu lub opracowywania programów, które są uruchamiane w programie, produkty Microsoft Word, które zostały licencjonowane przez firmę Microsoft po 10 stycznia 2010; te produkty nie będą działać tak samo jak produkty licencjonowane przed tą datą lub zakupione i licencjonowane do użycia poza Stany Zjednoczone.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel i Microsoft Office Word umożliwiają mapowanie schematów do dokumentów. Ta funkcja może uprościć Importowanie i eksportowanie danych XML do i z dokumentu.

 Program Visual Studio uwidacznia zamapowane elementy schematu w dostosowaniu na poziomie dokumentu jako kontrolki w modelu programowania. W przypadku programu Excel program Visual Studio dodaje obsługę wiązania formantów do danych w bazach danych, usługach sieci Web i obiektach. W przypadku programów Word i Excel program Visual Studio dodaje obsługę okienek akcji, które mogą być używane z dokumentem mapowanym na schemat, aby utworzyć udoskonalone środowisko użytkownika końcowego dla swoich rozwiązań. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

> [!NOTE]
> Nie można używać wieloczęściowych schematów XML w rozwiązaniach programu Excel.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Obiekty tworzone, gdy schematy są dołączone do skoroszytów programu Excel
 Po dołączeniu schematu do skoroszytu program Visual Studio automatycznie tworzy kilka obiektów i dodaje je do projektu. Tych obiektów nie należy usuwać przy użyciu narzędzi programu Visual Studio, ponieważ są one zarządzane przez program Excel. Aby je usunąć, Usuń zmapowane elementy z arkusza lub odłącz schemat przy użyciu narzędzi programu Excel.

 Istnieją dwa główne obiekty:

- Schemat XML (plik XSD). Dla każdego schematu w skoroszycie program Visual Studio dodaje schemat do projektu. Jest on wyświetlany jako element projektu z rozszerzeniem XSD w **Eksplorator rozwiązań**.

- Klasa z określonym typem <xref:System.Data.DataSet> . Ta klasa jest tworzona w oparciu o schemat. Ta klasa DataSet jest widoczna w **Widok klasy**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Obiekty utworzone, gdy elementy schematu są mapowane do arkuszy programu Excel
 Po zmapowaniu elementu schematu z okienka zadań **Źródło XML** do arkusza program Visual Studio automatycznie tworzy kilka obiektów i dodaje je do projektu:

- Kontrolek. Dla każdego zamapowanego obiektu w skoroszycie, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> w modelu programowania tworzone jest kontrolka (dla niepowtarzających się elementów schematu) lub <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolka (dla powtarzających się elementów schematu). <xref:Microsoft.Office.Tools.Excel.ListObject>Formant można usunąć tylko przez usunięcie mapowań i mapowanych obiektów ze skoroszytu. Aby uzyskać więcej informacji na temat kontrolek, zobacz temat [elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md).

- Powoduje. Podczas tworzenia <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> przez mapowanie niepowtarzalnego elementu schematu do arkusza <xref:System.Windows.Forms.BindingSource> jest tworzony i <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formant jest powiązany z <xref:System.Windows.Forms.BindingSource> . Należy powiązać <xref:System.Windows.Forms.BindingSource> do wystąpienia źródła danych, które pasuje do schematu zamapowanego do dokumentu, takiego jak wystąpienie <xref:System.Data.DataSet> klasy, która została utworzona. Utwórz powiązanie, ustawiając <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości i, które są widoczne w oknie **Właściwości** .

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>Nie utworzono dla <xref:Microsoft.Office.Tools.Excel.ListObject> obiektów. Musisz ręcznie powiązać ze <xref:Microsoft.Office.Tools.Excel.ListObject> źródłem danych, ustawiając <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości i w oknie **Właściwości** .

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Zmapowane schematy pakietu Office i okno źródeł danych programu Visual Studio
 Funkcje zamapowanego schematu pakietu Office i okna **źródła danych** programu Visual Studio mogą ułatwić prezentowanie danych w arkuszu programu Excel na potrzeby raportowania lub edycji. W obu przypadkach można przeciągnąć elementy danych do arkusza programu Excel. Obie metody tworzą kontrolki, które są powiązane ze <xref:System.Windows.Forms.BindingSource> źródłem danych, takim jak <xref:System.Data.DataSet> lub usługą sieci Web.

> [!NOTE]
> Po zmapowaniu powtarzalnego elementu schematu do arkusza program Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.ListObject>Nie jest on automatycznie powiązany z danymi za pomocą <xref:System.Windows.Forms.BindingSource> . Musisz ręcznie powiązać ze <xref:Microsoft.Office.Tools.Excel.ListObject> źródłem danych, ustawiając <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości i w oknie **Właściwości** .

 W poniższej tabeli przedstawiono niektóre różnice między tymi dwiema metodami.

|Schemat XML|Data Sources — Okno|
|----------------|-------------------------|
|Używa interfejsu pakietu Office.|Używa okna **źródeł danych** w programie Visual Studio.|
|Włącza wbudowane funkcje pakietu Office do importowania i eksportowania danych z plików XML.|Funkcje importowania i eksportowania należy zapewnić programowo.|
|Musisz napisać kod, aby wypełnić wygenerowane kontrolki danymi.|Formanty dodane z okna **źródła danych** mają automatycznie wygenerowany kod, aby wypełnić je wraz z niezbędnymi parametrami połączenia w przypadku korzystania z serwerów baz danych.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Zachowanie, gdy schematy są dołączone do dokumentów programu Word
 Obiekty danych nie są tworzone podczas dołączania schematu do dokumentu programu Word, który jest używany w projekcie pakietu Office na poziomie dokumentu. Jednak podczas mapowania elementu schematu do dokumentu są tworzone formanty. Typ formantu zależy od typu mapowanego elementu; powtarzające się elementy generują <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki i niepowtarzające się elementy generują <xref:Microsoft.Office.Tools.Word.XMLNode> formanty. Aby uzyskać więcej informacji, zobacz [formant XMLNodes](../vsto/xmlnodes-control.md) i [formant XmlNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Wdrażanie rozwiązań obejmujących schematy XML
 Należy utworzyć Instalatora w celu wdrożenia rozwiązania, które używa schematu XML, który jest mapowany do dokumentu. Instalator powinien zarejestrować schemat w bibliotece schematów na komputerze użytkownika. Jeśli schemat nie zostanie zarejestrowany, rozwiązanie będzie nadal działało, ponieważ program Word generuje tymczasowy schemat oparty na elementach, które znajdują się w dokumencie, gdy użytkownik go otworzy. Jednak użytkownik nie będzie mógł przeprowadzić walidacji ani zapisać schematu, który został użyty do utworzenia projektu. Aby uzyskać więcej informacji na temat instalatorów, zobacz [wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

 Możesz również dodać kod do projektu, aby sprawdzić, czy schemat znajduje się w bibliotece i jest zarejestrowany. Jeśli tak nie jest, można ostrzec użytkownika.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>Zobacz też

- [Instrukcje: mapowanie schematów do dokumentów programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Instrukcje: mapowanie schematów do arkuszy w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)

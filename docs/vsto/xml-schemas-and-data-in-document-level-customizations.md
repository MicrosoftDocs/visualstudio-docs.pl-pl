---
title: Schematy XML i dane dostosowywane na poziomie dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4320625326549f554491f12ab33bd4d43838a5e4
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803088"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Schematy XML i dane dostosowywane na poziomie dokumentu
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest prezentowane wyłącznie do korzyści i korzystanie z innym osobom oraz organizacjom, którzy znajdują się poza w Stanach Zjednoczonych i ich terytoriach lub korzystających z lub tworzenie programy, korzystających z produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy kod XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word nie mogą być odczytywane lub używane przez osoby i organizacje w Stanach Zjednoczonych lub jego terytoria, którzy za pomocą lub opracowywanie programów uruchamianych na produkty Microsoft Word, które są licencjonowane przez firmę Microsoft, po 10 stycznia 2010 r. ; te produkty będą nie działa tak samo jako produkty licencjonowane przed tą datą lub kupić i licencjonowane do użycia poza Stanami Zjednoczonymi.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel i Microsoft Office Word zapewniają możliwość mapowanie schematów z dokumentów. Ta funkcja może uprościć, importowanie i eksportowanie danych XML i dokumentu.

 Visual Studio udostępnia zamapowane elementy schematu w dostosowaniach na poziomie dokumentu jako formanty w modelu programowania. Dla programu Excel programu Visual Studio dodaje obsługę powiązanie kontrolek z danymi w bazach danych, usług sieci Web i obiektów. Dla programów Word i Excel programu Visual Studio dodaje obsługę okienka akcji, które mogą być używane do utworzenia większą wygodę dla rozwiązań za pomocą zamapowany schematu dokumentu. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).

> [!NOTE]
>  Nie można użyć wieloczęściowego schematów XML w rozwiązaniach programu Excel.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Obiekty tworzone podczas schematy są dołączone do skoroszytów programu Excel
 Po dołączeniu schematu do skoroszytu programu Visual Studio tworzy kilka obiektów i automatycznie dodaje je do projektu. Te obiekty nie powinny być usuwane przy użyciu narzędzi programu Visual Studio, ponieważ są one zarządzane przez program Excel. Aby je usunąć, Usuń zamapowane elementy z arkusza lub odłącz schematu przy użyciu narzędzi programu Excel.

 Istnieją dwa główne obiekty:

-   Schemat XML (plik XSD). Dla każdego schematu w skoroszycie programu Visual Studio dodaje schematu do projektu. Ta opcja ma nazwę elementu projektu z rozszerzeniem XSD w **Eksploratora rozwiązań**.

-   Wpisane <xref:System.Data.DataSet> klasy. Ta klasa jest tworzona w oparciu o schemacie. Ta klasa dataset jest widoczna w **Widok klas**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Obiekty utworzone, gdy elementy schematu są mapowane do arkusza programu Excel
 Podczas mapowania elementu schematu z **źródła XML** okienka zadań do arkusza programu Visual Studio automatycznie tworzy kilka obiektów i dodaje je do projektu:

-   Kontrolki. Dla każdego obiektu zamapowanych w skoroszycie <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontroli (dla elementów schematu niepowtarzający) lub <xref:Microsoft.Office.Tools.Excel.ListObject> formantu (w przypadku powtarzające się elementy schematu) jest tworzony w modelu programowania. <xref:Microsoft.Office.Tools.Excel.ListObject> Kontroli można usunąć tylko przez usunięcie mapowania i mapowanych obiektów ze skoroszytu. Aby uzyskać więcej informacji na temat formantów, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

-   BindingSource. Po utworzeniu <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> przez mapowanie elementu schematu niepowtarzający w arkuszu <xref:System.Windows.Forms.BindingSource> jest tworzony i <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>. Musi być powiązany <xref:System.Windows.Forms.BindingSource> do wystąpienia źródła danych, które pasuje do schematu mapowane do dokumentu, takiego jak wystąpienie wpisanego <xref:System.Data.DataSet> klasę, która została utworzona. Utwórz powiązanie, ustawiając <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości, które są widoczne w **właściwości** okna.

    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource> Nie został utworzony dla <xref:Microsoft.Office.Tools.Excel.ListObject> obiektów. Należy samodzielnie ręcznie powiązali <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródłem danych, ustawiając <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości w **właściwości** okna.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office mapowane schematy i okna źródeł danych w usłudze Visual Studio
 Funkcje zamapowanego schematu pakietu Office i programu Visual Studio **źródeł danych** okna może pomóc w przedstawienie danych w arkuszu programu Excel, raportowanie i edytowania. W obu przypadkach można przeciągnąć elementy danych, na arkuszu programu Excel. Obie metody tworzenia formantów, które są danymi powiązanymi za pośrednictwem <xref:System.Windows.Forms.BindingSource> ze źródłem danych, takich jak <xref:System.Data.DataSet> lub usługi sieci web.

> [!NOTE]
>  Kiedy mapujesz powtarzający się element schematu do arkusza programu Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Automatycznie nie jest powiązany z danymi za pośrednictwem <xref:System.Windows.Forms.BindingSource>. Należy samodzielnie ręcznie powiązali <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródłem danych, ustawiając <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości w **właściwości** okna.

 W poniższej tabeli przedstawiono niektóre różnice między obiema metodami.

|Schemat XML|Data Sources — Okno|
|----------------|-------------------------|
|Używa interfejsu pakietu Office.|Używa **źródeł danych** okna w programie Visual Studio.|
|Udostępnia wbudowane funkcje pakietu Office do importowania i eksportowania danych z plików XML.|Musisz podać importowanie i eksportowanie funkcji programowo.|
|Należy napisać kod, aby wypełnić wygenerowanego kontrolki z danymi.|Formanty dodane z **źródeł danych** okno ma kod wygenerowany automatycznie, aby wypełnić go, oraz parametry połączenia niezbędne podczas korzystania z serwerów bazy danych.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Zachowanie, gdy schematy są dołączone do dokumentów programu Word
 Obiekty danych nie są tworzone, gdy Dołącz schemat do dokumentu programu Word, który jest używany w dokumencie projektów pakietu Office. Jednak podczas mapowania elementu schematu do dokumentu, formanty są tworzone. Typ formantu zależy od rodzaju elementu mapy; powtarzające się generowanie elementy <xref:Microsoft.Office.Tools.Word.XMLNodes> formanty i niepowtarzający elementy Generowanie <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolki. Aby uzyskać więcej informacji, zobacz [formant XMLNodes](../vsto/xmlnodes-control.md) i [formant XMLNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Wdrażanie rozwiązań, które obejmują schematów XML
 Należy utworzyć Instalatora, aby wdrożyć rozwiązanie, które używa schematu XML, który jest zamapowany do dokumentu. Instalator należy zarejestrować schemat w bibliotece schematów na komputerze użytkownika. Jeśli schemat nie jest zarejestrowane, rozwiązanie nadal będzie działać, ponieważ program Word generuje schemat tymczasowe oparte na elementach, które znajdują się w dokumencie, gdy użytkownik otworzy go. Jednak użytkownik nie będzie można wykonywać sprawdzanie poprawności względem lub zapisać schematu, który został użyty do utworzenia projektu. Aby uzyskać więcej informacji na temat instalatory zobacz [wdrażania aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

 Można również dodać kod do projektu, aby sprawdzić, czy schemat w bibliotece i zarejestrowana. Jeśli nie jest dostępne, możesz ostrzeżenia dla użytkownika.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Mapowanie schematów z dokumentami programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Instrukcje: Mapowanie schematów z arkuszami w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)

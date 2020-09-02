---
title: Niestandardowe części XML — Omówienie
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b94deacad38f40d76b4c8485186bfd563808d912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784416"
---
# <a name="custom-xml-parts-overview"></a>Niestandardowe części XML — Omówienie
  Możesz osadzić dane XML w dokumentach dla niektórych Microsoft Office aplikacji. Po osadzeniu danych XML w dokumencie dane są nazywane *niestandardowym elementem XML*.

 Możesz tworzyć i modyfikować niestandardowe części XML w dokumencie przy użyciu dodatku VSTO lub rozwiązania na poziomie dokumentu w programie Visual Studio. Nie musisz uruchamiać aplikacji Microsoft Office, aby tworzyć i modyfikować niestandardowe części XML.

 **Dotyczy:** Informacje przedstawione w tym temacie mają zastosowanie do projektów na poziomie dokumentu i projektów dodatku VSTO dla programów Excel, PowerPoint i Word. Aby uzyskać więcej informacji, zobacz [dostępność funkcji według aplikacji pakietu Office i typów projektów](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Program Visual Studio umożliwia również buforowanie obiektów danych w dostosowaniach na poziomie dokumentu. Ta funkcja różni się od niestandardowych części XML, chociaż istnieją inne podobieństwa. Aby uzyskać więcej informacji, zobacz [buforowane dane w dostosowywaniu na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md).

## <a name="understand-custom-xml-parts"></a>Zrozumienie niestandardowych części XML
 Niestandardowe części XML wprowadzono w systemie 2007 Microsoft Office wraz z otwartymi formatami XML. Te formaty zawierają nowe formaty plików XML dla programów Excel, PowerPoint i Word (takie jak *xlsx*, *pptx*i *docx*). Dokumenty w tych formatach składają się z plików XML (nazywanych również *częściami XML*), które są zorganizowane w folderach w archiwum zip. Większość części XML to wbudowane części, które ułatwiają Definiowanie struktury i stanu dokumentu. Jednak dokumenty mogą również zawierać niestandardowe części XML, których można użyć do przechowywania dowolnych danych XML w dokumentach.

 Formaty plików XML umożliwiają aplikacjom współpracę z dokumentami w sposób, który nie jest możliwy w przypadku starszych formatów plików binarnych (takich jak *xls*, *PPT*i *. doc*). Wszystkie aplikacje, które mogą odczytywać archiwa ZIP, mogą przeglądać i modyfikować zawartość dokumentów, nawet jeśli nie zainstalowano Microsoft Office.

 Aby uzyskać więcej informacji na temat struktury otwartych składników XML i niestandardowych części XML, zobacz następujące artykuły:

- [Wprowadzenie do pakietu Office (2007) otwartych formatów plików XML](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

- [Instrukcje: manipulowanie otwartymi formatami XML dokumentów](/previous-versions/office/developer/office-2007/aa982683(v=office.12))

- [Przewodnik: format XML programu Word 2007](/previous-versions/office/developer/office-2007/bb266220(v=office.12))

- [Kompiluj dokumenty programu Word 2007 przy użyciu otwartych formatów XML](/previous-versions/office/developer/office-2007/bb264572(v=office.12))

> [!NOTE]
> Programy Excel, Word i PowerPoint umożliwiają również korzystanie z niestandardowych części XML w dokumentach, które są zapisane w formatach plików binarnych. Jeśli jednak dokument jest zapisywany w formacie binarnym, nie można dodawać ani modyfikować niestandardowych części XML bez uruchamiania aplikacji Microsoft Office.

## <a name="create-and-modify-custom-xml-parts"></a>Tworzenie i modyfikowanie niestandardowych części XML
 Możesz tworzyć lub modyfikować niestandardowe części XML, gdy dokument jest otwarty w aplikacji pakietu Office lub gdy dokument zostanie zamknięty — nawet jeśli nie zainstalowano Microsoft Office.

### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Modyfikuj części XML, gdy aplikacja pakietu Office jest uruchomiona
 Można korzystać z niestandardowych części XML przy użyciu dostosowania na poziomie dokumentu lub dodatku VSTO. Jeśli używasz dostosowania na poziomie dokumentu, zazwyczaj pracujesz z niestandardowymi częściami XML, które znajdują się w dostosowanym dokumencie. Jeśli używasz dodatku VSTO, możesz tworzyć lub modyfikować niestandardowe części XML w dowolnym dokumencie, który jest otwarty w aplikacji.

 Aby utworzyć niestandardową część XML przy użyciu programu Visual Studio, Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> do <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w dokumencie. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="modify-xml-parts-without-starting-the-office-application"></a>Modyfikowanie części XML bez uruchamiania aplikacji pakietu Office
 Możesz dodać lub zmodyfikować niestandardową część XML bez uruchamiania programu Excel, PowerPoint lub Word. Jest to przydatne, jeśli chcesz korzystać z danych XML w dokumencie na komputerze, na którym nie zainstalowano aplikacji Microsoft Office, takich jak serwer.

 Aby dodać niestandardową część XML bez uruchamiania Microsoft Office, użyj klas w otwartym zestawie XML SDK. Te klasy zostały zaprojektowane w celu zapewnienia dostępu do otwartej zawartości XML, która jest specyficzna dla dokumentów pakietu Office. Na przykład, aby dodać niestandardową część XML do skoroszytu programu Excel, należy użyć <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> metody <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> obiektu. Aby uzyskać więcej informacji, zobacz [Open XML SDK](/office/open-xml/open-xml-sdk).

## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Powiązywanie niestandardowych części XML z kontrolkami zawartości programu Word
 Można powiązać kontrolki zawartości w rozwiązaniu programu Word z elementami w niestandardowym składniku XML. Gdy formant zawartości jest powiązany z niestandardowym elementem XML, dane w niestandardowej części XML są wyświetlane w interfejsie użytkownika formantu zawartości. Jeśli użytkownik edytuje tekst w kontrolce, odpowiedni element XML zostanie automatycznie zaktualizowany. Podobnie, jeśli wartości elementów w niestandardowych częściach XML są zmieniane, formanty zawartości, które są powiązane z elementami XML, wyświetlają nowe dane. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).

## <a name="see-also"></a>Zobacz też
- [Schematy XML i dane w dostosowaniach na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
- [Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
- [Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
- [Kontrolki zawartości](../vsto/content-controls.md)
- [Wskazówki: powiązywanie kontrolek zawartości z niestandardowymi częściami XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)

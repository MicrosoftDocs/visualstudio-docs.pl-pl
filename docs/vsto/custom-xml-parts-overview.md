---
title: Niestandardowe części XML ― omówienie
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71720ef96ee7d17bd52ea118a8c44a8f4b117cad
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671732"
---
# <a name="custom-xml-parts-overview"></a>Niestandardowe części XML ― omówienie
  Dane XML można osadzić w dokumentach niektórych aplikacji pakietu Microsoft Office. Osadzenie danych XML w dokumencie, dane o nazwie *niestandardowym elementem XML*.  
  
 Można utworzyć i zmodyfikować niestandardowe elementy XML w dokumencie za pomocą dodatku narzędzi VSTO lub na poziomie dokumentu rozwiązanie w programie Visual Studio. Nie trzeba uruchomić aplikację Microsoft Office do tworzenia i modyfikowania niestandardowe elementy XML.  
  
 **Dotyczy:** informacje przedstawione w tym temacie dotyczą projektów na poziomie dokumentu i projektów dodatku VSTO dla programów Excel, PowerPoint i Word. Aby uzyskać więcej informacji, zobacz [funkcje, które są dostępne przez typ aplikacji i projektów pakietu Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Program Visual Studio umożliwia także do obiektów danych w pamięci podręcznej dostosowywane na poziomie dokumentu. Ta funkcja jest inny niż niestandardowe elementy XML, chociaż istnieją pewne podobieństwa. Aby uzyskać więcej informacji, zobacz [dane dostosowywane na poziomie dokumentu z pamięci podręcznej](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understand-custom-xml-parts"></a>Omówienie niestandardowych części XML  
 Niestandardowe elementy XML zostały wprowadzone w programie Microsoft Office system 2007, wraz z otwartych formatów XML. Te formaty obejmują nowe formaty plików oparty na składni XML dla programu Excel, PowerPoint i Word (takie jak *xlsx*, *pptx*, i *.docx*). Dokumenty w tych formatach składają się z plikami XML (o nazwie *części XML*), są zorganizowane w foldery w archiwum ZIP. Większość części XML to wbudowane części, które pomogą Ci określić strukturę i stanu dokumentu. Jednak dokumenty mogą także zawierać niestandardowe elementy XML, których można użyć, aby przechowywać dowolne dane XML w dokumentach.  
  
 Włączanie aplikacji do pracy z dokumentami w sposób, który nie jest możliwe za pomocą starsze formaty plików binarnych formaty plików XML (takie jak *xls*, *ppt*, i *doc*). Każda aplikacja, która może odczytywać archiwa ZIP można zbadać i modyfikować zawartość dokumentów, nawet jeśli nie zainstalowano programu Microsoft Office.  
  
 Aby uzyskać więcej informacji na temat struktury Open XML i niestandardowe elementy XML zobacz następujące artykuły:  
  
-   [Wprowadzenie do formatów pakietu Office (2007) Open XML](/previous-versions/office/developer/office-2007/aa338205(v=office.12))  
  
-   [Porady: manipulowanie dokumentów formatów Open XML](/previous-versions/office/developer/office-2007/aa982683(v=office.12))  
  
-   [Wskazówki: Format programu Word 2007 XML](/previous-versions/office/developer/office-2007/bb266220(v=office.12))  
  
-   [Tworzenie dokumentów programu Word 2007 za pomocą formatów Open XML](/previous-versions/office/developer/office-2007/bb264572(v=office.12))  
  
> [!NOTE]  
>  Program Excel, Word i PowerPoint również włączyć przy użyciu niestandardowych części XML w dokumentach, które są zapisane w formacie plików binarnych. Jednak jeśli dokument zostanie zapisany w formacie binarnym, nie możesz dodawać ani modyfikować niestandardowe elementy XML bez uruchamiania aplikacji programu Microsoft Office.  
  
## <a name="create-and-modify-custom-xml-parts"></a>Tworzenie i modyfikowanie niestandardowe elementy XML  
 Można tworzyć lub modyfikować niestandardowe elementy XML w przypadku, gdy dokument jest otwarty w aplikacji pakietu Office lub w przypadku, gdy dokument zostanie zamknięty — nawet jeśli nie zainstalowano programu Microsoft Office.  
  
### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Zmodyfikuj elementy XML w uruchomionej aplikacji pakietu Office  
 Niestandardowe elementy XML można pracować przy użyciu dostosowywania poziomie dokumentu lub dodatku narzędzi VSTO. Jeśli używasz dostosowywania poziomie dokumentu, zwykle korzystania z niestandardowych części XML znajdujących się w dokumencie dostosowane. Jeśli używasz dodatku narzędzi VSTO dla programów, mogą tworzenia lub modyfikowania niestandardowe elementy XML w dowolny dokument, który jest otwarty w aplikacji.  
  
 Aby utworzyć z niestandardowym elementem XML przy użyciu programu Visual Studio, Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> do <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w dokumencie. Więcej informacji znajduje się w następujących tematach:  
  
-   [Porady: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Porady: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modify-xml-parts-without-starting-the-office-application"></a>Zmodyfikuj elementy XML bez uruchamiania aplikacji pakietu Office  
 Można dodawania lub modyfikowania z niestandardowym elementem XML bez konieczności uruchamiania programu Excel, PowerPoint lub Word. Jest to przydatne, jeśli chcesz pracować z danymi XML w dokumencie programu na komputerze, który nie ma aplikacji Microsoft Office, zainstalowane, takim jak serwer.  
  
 Aby dodać z niestandardowym elementem XML bez konieczności uruchamiania programu Microsoft Office, należy użyć klas Open XML zestawu SDK. Te klasy są przeznaczone do zapewniają dostęp do zawartości Open XML, które są specyficzne dla dokumentów pakietu Office. Na przykład, aby dodać niestandardowe części XML do skoroszytu programu Excel, należy użyć <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> metody <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> obiektu. Aby uzyskać więcej informacji, zobacz [Open XML SDK](/office/open-xml/open-xml-sdk).  
  
## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Niestandardowe elementy XML należy powiązać formanty zawartości programu Word  
 Możesz powiązać formanty zawartości w ramach rozwiązania programu Word do elementów w niestandardowym elementem XML. Gdy formant zawartości jest powiązana z niestandardowym elementem XML, dane w niestandardowym elementem XML są wyświetlane w interfejsie użytkownika (UI) zawartości formantu. Jeśli użytkownik dokona edycji tekstu w kontrolce, odpowiadający mu element XML jest aktualizowane automatycznie. Podobnie zmiana wartości elementów w niestandardowych części XML formanty zawartości, które są powiązane elementy XML wyświetlania nowych danych. Aby uzyskać więcej informacji, zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Schematy XML i dane dostosowywane na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Porady: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Porady: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Formanty zawartości](../vsto/content-controls.md)   
 [Wskazówki: Powiązywanie kontrolek zawartości do niestandardowych części XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  

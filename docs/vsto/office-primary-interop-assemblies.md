---
title: podstawowe zestawy międzyoperacyjne pakietu Office
ms.date: 09/20/2018
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f83a2b61a80616fdcdb8b48c7501b4fa47f0b99c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926740"
---
# <a name="office-primary-interop-assemblies"></a>podstawowe zestawy międzyoperacyjne pakietu Office

Aby korzystać z funkcji aplikacji pakietu Microsoft Office z projektu pakietu Office, należy użyć podstawowego zestawu międzyoperacyjnego (PIA) dla aplikacji. Zestaw PIA umożliwia interakcję z modelem obiektów opartym na modelu COM aplikacji pakietu Microsoft Office kodu zarządzanego.  
  
Podczas tworzenia nowego projektu pakietu Office, Visual Studio dodaje odwołania do zestawów PIA, które są wymagane do skompilowania projektu. W niektórych scenariuszach może być konieczne, można dodać odwołania do dodatkowych zestawów PIA (na przykład, jeśli chcesz używać funkcji programu Microsoft Office Word w projekcie dla programu Microsoft Office Excel).  
  
W tym temacie opisano następujące aspekty użycia zestawów Microsoft Office PIA w projektach pakietu Office:  
  
- [Oddzielne podstawowych zestawów międzyoperacyjnych do kompilowania i uruchamiania projektów](#separateassemblies)  
  
- [Korzystać z funkcji wielu aplikacji pakietu Microsoft Office w jednym projekcie](#usingfeatures)  
  
- [Pełna lista podstawowych zestawów międzyoperacyjnych dla aplikacji Microsoft Office](#pialist)  
  
Aby uzyskać więcej informacji na temat podstawowych usług międzyoperacyjnych, zobacz [podstawowe zestawy międzyoperacyjne](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  

<a name="separateassemblies"></a> 

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Oddzielne podstawowych zestawów międzyoperacyjnych do kompilowania i uruchamiania projektów  

Visual Studio używa różnych zestawów PIA na komputerze deweloperskim. Te różne zbiory zestawów znajdują się w następujących lokalizacjach:  
  
- Folder w katalogu program files  
  
  Te kopie zestawów są używane podczas pisania kodu i kompilacji projektów. Program Visual Studio automatycznie instaluje te zestawy.  
  
- Global assembly cache  
  
  Te kopie zestawów są używane podczas niektórych zadań deweloperskich, takich jak podczas uruchamiania lub debugowania projektów. Program Visual Studio nie może zainstalować i zarejestrować tych zestawów; możesz zrobić to samodzielnie.  
  
### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Podstawowe zestawy międzyoperacyjne w katalogu program files  

Po zainstalowaniu programu Visual Studio, zestawy PIA są automatycznie instalowane w lokalizacji w systemie plików, poza globalną pamięcią podręczną zestawów. Podczas tworzenia nowego projektu programu Visual Studio automatycznie dodaje odwołania do tych kopii zestawów PIA do projektu. Visual Studio używa tych kopii zestawów PIA, zamiast zestawów w globalnej pamięci podręcznej do rozpoznawania odwołań typu podczas rozwijania i budowania projektu.  
  
Te kopie zestawów PIA pomagają programowi Visual Studio uniknąć kilka problemów projektowych, które mogą wystąpić, jeśli zarejestrowano różne wersje zestawów PIA w globalnej pamięci podręcznej.  
  
Program Visual Studio instaluje te kopie zestawów PIA w następujących lokalizacjach na komputerze deweloperskim:  
  
- *%ProgramFiles%\Microsoft visual Studio 12. 0\visual Studio Tools for Office\PIA\Office14*  
  
  (lub *% ProgramFiles (x86) %\Microsoft Visual Studio 12. 0\visual Studio Tools for Office\PIA\Office14* na 64-bitowych systemach operacyjnych)  
  
- *%ProgramFiles%\Microsoft visual Studio 12. 0\visual Studio Tools for Office\PIA\Office15*  
  
  (lub *% ProgramFiles (x86) %\Microsoft Visual Studio 12. 0\visual Studio Tools for Office\PIA\Office15* na 64-bitowych systemach operacyjnych)  
  
### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Podstawowe zestawy międzyoperacyjne w globalnej pamięci podręcznej  

Do wykonywania określonych zadań projektowania, musi być zainstalowane i zarejestrowane w globalnej pamięci podręcznej na komputerze deweloperskim zestawy PIA. Zazwyczaj zestawy PIA są instalowane automatycznie podczas instalowania pakietu Office na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
Zestawy PIA pakietu Office nie są wymagane na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office. Aby uzyskać więcej informacji, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).  

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Korzystać z funkcji wielu aplikacji pakietu Microsoft Office w jednym projekcie  

Każdy szablon projektu pakietu Office w programie Visual Studio jest przeznaczona do pracy z pojedynczą aplikacją Microsoft Office. Aby korzystać z funkcji wielu aplikacji pakietu Microsoft Office lub korzystać z funkcji w aplikacji lub składnika, który nie ma projektu w programie Visual Studio, należy dodać odwołanie do wymaganych zestawów PIA.  
  
W większości przypadków należy dodać odwołania do zestawów PIA, które są instalowane przez program Visual Studio w obszarze `%ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\` katalogu. Te wersje zestawów są wyświetlane na **Framework** karcie **Menadżer odwołań** okno dialogowe. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
Jeśli masz zainstalowane i zarejestrowane zestawy PIA w globalnej pamięci podręcznej, te wersje zestawów są wyświetlane na **COM** karcie **Menadżer odwołań** okno dialogowe. Dodawanie odwołania do tych wersji zespołów, należy unikać, ponieważ istnieją pewne problemy projektowe, które mogą wystąpić podczas korzystania z nich. Na przykład, jeśli zarejestrowano różne wersje zestawów PIA w globalnej pamięci podręcznej zestawów, projekt będzie automatycznie wiązany wersji zestawu, która została zarejestrowana jako ostatnia — nawet jeśli określisz inną wersję zestawu na  **COM** karcie **Menadżer odwołań** okno dialogowe.  
  
> [!NOTE]  
>  Niektóre zestawy są automatycznie dodawane do projektu po dodaniu zestawu, który odwołuje się do nich. Na przykład odwołuje się do *zestawów Office.dll* i *Microsoft.Vbe.Interop.dll* zestawy są dodawane automatycznie po dodaniu odwołania do programu Word, Excel, Outlook, Microsoft Forms lub Graph zestawy.  

<a name="pialist"></a> 

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Podstawowe zestawy międzyoperacyjne dla aplikacji Microsoft Office  

W poniższej tabeli wymieniono podstawowe zestawy międzyoperacyjne, które są dostępne dla [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  

<br/>

|Aplikacja pakietu Office lub składnika|Podstawowy zestaw międzyoperacyjny nazwy|  
|-------------------------------------|-----------------------------------|  
|Biblioteka obiektów programu Microsoft Access 14.0<br /><br /> Biblioteka obiektów programu Microsoft Access 15.0|Microsoft.Office.Interop.Access.dll|  
|Microsoft Office 14.0 dostęp do bazy danych aparatu Object Library<br /><br /> Microsoft Office 15.0 dostępu do bazy danych aparatu Object Library|Microsoft.Office.Interop.Access.Dao.dll|  
|Biblioteka obiektów programu Microsoft Excel 14.0<br /><br /> Biblioteka obiektów programu Microsoft Excel 15.0|[Microsoft.Office.Interop.Excel.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.excel?view=excel-pia)|  
|Microsoft Graph 14.0 Object Library (używany przez program PowerPoint, Access i Word dla wykresów)<br /><br /> Biblioteka obiektów programu Microsoft Graph 15.0|Microsoft.Office.Interop.Graph.dll|  
|Program Microsoft InfoPath 2.0 biblioteki typów (tylko program InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.infopath?view=infopath-form)|  
|Program Microsoft InfoPath XML Interop Assembly (tylko program InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Microsoft Office 14.0 Object Library (funkcje wspólne pakietu Office)<br /><br /> Biblioteki obiektów Microsoft Office 15.0 (funkcje wspólne pakietu Office)|zestawów Office.dll|  
|Formantu widoku pakietu Microsoft Office Outlook (może służyć w stronach sieci Web i aplikacji dostępu do skrzynki odbiorczej)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Biblioteka obiektów programu Microsoft Outlook 14.0<br /><br /> Biblioteka obiektów programu Microsoft Outlook 15.0|[Microsoft.Office.Interop.Outlook.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia)|  
|Biblioteka obiektów programu Microsoft PowerPoint 14.0<br /><br /> Biblioteka obiektów programu Microsoft PowerPoint 15.0|Microsoft.Office.Interop.PowerPoint.dll|  
|Biblioteka obiektów programu Microsoft Project 14.0<br /><br /> Biblioteka obiektów programu Microsoft Project 15.0|[Microsoft.Office.Interop.MSProject.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.msproject?view=office-project-server)|  
|Biblioteka obiektów programu Microsoft Publisher 14.0<br /><br /> Biblioteka obiektów programu Microsoft Publisher 15.0|Microsoft.Office.Interop.Publisher.dll|  
|Microsoft SharePoint Designer 14.0 Web Bibliotaka odwołań|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Microsoft SharePoint Designer 14.0 obiektu strony Reference Library|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|2.0 biblioteki typów tagów inteligentnych Microsoft **Uwaga:**  Tagi inteligentne są przestarzałe w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|  
|Program Microsoft Visio 14.0 Biblioteka typów<br /><br /> Biblioteki typów w programie Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.dll|  
|Program Microsoft Visio 14.0 Zapisz jako biblioteki typów sieci Web<br /><br /> Program Microsoft Visio 15.0 Zapisz jako biblioteki typów sieci Web|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Biblioteka typów kontroli rysunku programu Microsoft Visio 14.0<br /><br /> Biblioteka typów kontroli rysunku programu Microsoft Visio 15.0|Microsoft.Office.Interop.VisOcx.dll|  
|Biblioteka obiektów programu Microsoft Word 14.0<br /><br /> Biblioteka obiektów programu Microsoft Word 15.0|[Microsoft.Office.Interop.Word.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.word?view=word-pia)|  
|Microsoft Visual Basic dla aplikacji Extensibility 5.3|Microsoft.Vbe.Interop.dll|  
  
### <a name="binding-redirect-assemblies"></a>Zestawy przekierowania powiązań  

Podczas instalowania i rejestrowania zestawów Office PIA w globalnej pamięci podręcznej zestawów (albo z pakietem Office, instalując pakiet redystrybucyjny dla zestawów PIA), zestawy przekierowania powiązań są również instalowane tylko w globalnej pamięci podręcznej. Te zestawy pomagają upewnić się, że poprawną wersję podstawowe zestawy międzyoperacyjne jest ładowany w czasie wykonywania. 

Na przykład kiedy rozwiązanie odwołujące [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] zestawu, który jest uruchamiany na komputerze, który ma [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] wersji tego samego podstawowego zestawu międzyoperacyjnego, zestawu powiązania przekierowania nakazuje [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] środowiska uruchomieniowego do załadowania [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] Wersja podstawowy zestaw międzyoperacyjny. 

Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznego przekierowywania powiązań](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).  
  
## <a name="see-also"></a>Zobacz także  

- [Instrukcje: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
- [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)   
- [Rozwiązania InfoPath](../vsto/infopath-solutions.md)   
- [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
- [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md)   
- [Rozwiązania projektu](../vsto/project-solutions.md)   
- [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
- [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)   
- [Informacje ogólne &#40;programowanie Office w Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)  

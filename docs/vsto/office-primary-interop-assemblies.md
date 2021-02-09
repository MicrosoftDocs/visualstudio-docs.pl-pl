---
title: podstawowe zestawy międzyoperacyjne pakietu Office
description: Dowiedz się, jak używać podstawowego zestawu międzyoperacyjnego (PIA), aby uzyskać dostęp do funkcji aplikacji Microsoft Office z projektu pakietu Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2041c1d8b39f88f611cee09f17c498ea54130122
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892063"
---
# <a name="office-primary-interop-assemblies"></a>podstawowe zestawy międzyoperacyjne pakietu Office

Aby korzystać z funkcji aplikacji Microsoft Office z projektu pakietu Office, należy użyć podstawowego zestawu międzyoperacyjnego (PIA) dla aplikacji. PIA umożliwia współdziałanie kodu zarządzanego z modelem obiektów opartym na modelu COM aplikacji Microsoft Office.

[!include[Add-ins note](includes/addinsnote.md)]

Podczas tworzenia nowego projektu pakietu Office Program Visual Studio dodaje odwołania do zestawów Pia, które są wymagane do skompilowania projektu. W niektórych scenariuszach może być konieczne dodanie odwołań do dodatkowych zestawów PIA (na przykład jeśli chcesz użyć funkcji programu Microsoft Office Word w projekcie dla Microsoft Office Excel).

W tym temacie opisano następujące aspekty używania Microsoft Office zestawów PIA w projektach pakietu Office:

- [Oddziel podstawowe zestawy międzyoperacyjności do kompilowania i uruchamiania projektów](#separateassemblies)

- [Korzystanie z funkcji wielu Microsoft Office aplikacji w jednym projekcie](#usingfeatures)

- [Pełna lista podstawowych zestawów międzyoperacyjnych dla aplikacji Microsoft Office](#pialist)

Aby uzyskać więcej informacji na temat podstawowych zestawów międzyoperacyjnych, zobacz [podstawowe zestawy międzyoperacyjności](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

<a name="separateassemblies"></a>

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Oddziel podstawowe zestawy międzyoperacyjności do kompilowania i uruchamiania projektów

Program Visual Studio używa różnych zestawów zestawów Pia na komputerze deweloperskim. Te różne zestawy zestawów znajdują się w następujących lokalizacjach:

- Folder w katalogu Program Files

  Te kopie zestawów są używane podczas pisania kodu i kompilowania projektów. Program Visual Studio automatycznie instaluje te zestawy.

- Globalna pamięć podręczna zestawów

  Te kopie zestawów są używane podczas niektórych zadań programistycznych, na przykład podczas uruchamiania lub debugowania projektów. Program Visual Studio nie instaluje i nie rejestruje tych zestawów; musisz to zrobić samodzielnie.

### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Podstawowe zestawy międzyoperacyjności w katalogu Program Files

Podczas instalowania programu Visual Studio zestawów PIA są automatycznie instalowane do lokalizacji w systemie plików, poza globalną pamięcią podręczną zestawów. Podczas tworzenia nowego projektu program Visual Studio automatycznie dodaje odwołania do tych kopii zestawów Pia do projektu. Program Visual Studio używa tych kopii zestawów Pia zamiast zestawów w globalnej pamięci podręcznej zestawów, aby rozpoznać odwołania do typów podczas opracowywania i kompilowania projektu.

Te kopie zestawów Pia ułatwiają programowi Visual Studio uniknięcie kilku problemów programistycznych, które mogą wystąpić, gdy różne wersje zestawów PIA są zarejestrowane w globalnej pamięci podręcznej zestawów.

Począwszy od programu Visual Studio 2017, te kopie zestawów PIA są instalowane w następujących lokalizacjach udostępnionych na komputerze deweloperskim:

- `%ProgramFiles%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\`

- (lub `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` w 64-bitowych systemach operacyjnych)

> [!NOTE]
> W przypadku starszych wersji programu Visual Studio te zestawów Pia zostaną zainstalowane do folderu Visual Studio Tools dla Office\PIA w `%ProgramFiles%` folderze dla tej wersji programu Visual Studio.
> Na przykład: `%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Visual Studio Tools for Office\PIA\`

### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Podstawowe zestawy międzyoperacyjności w globalnej pamięci podręcznej zestawów

Aby wykonać pewne zadania deweloperskie, zestawów Pia musi być zainstalowana i zarejestrowana w globalnej pamięci podręcznej zestawów na komputerze deweloperskim. Zazwyczaj zestawów PIA są instalowane automatycznie podczas instalowania pakietu Office na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

Na komputerach użytkowników końcowych nie są wymagane do uruchamiania rozwiązań pakietu Office. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Korzystanie z funkcji wielu Microsoft Office aplikacji w jednym projekcie

Każdy szablon projektu pakietu Office w programie Visual Studio jest przeznaczony do pracy z pojedynczą aplikacją Microsoft Office. Aby korzystać z funkcji w wielu aplikacjach Microsoft Office lub użyć funkcji w aplikacji lub składniku, który nie ma projektu w programie Visual Studio, należy dodać odwołanie do wymaganego zestawów Pia.

W większości przypadków należy dodać odwołania do zestawów Pia, które są instalowane przez program Visual Studio w `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` katalogu. Te wersje zestawów są wyświetlane na karcie **Struktura** okna dialogowego **Menedżer odwołań** . Aby uzyskać więcej informacji, zobacz [jak: docelowa aplikacja pakietu Office za poorednictwem podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

Jeśli zainstalowano i zarejestrowano zestawów PIA w globalnej pamięci podręcznej zestawów, te wersje zestawów są wyświetlane na karcie **com** okna dialogowego **Menedżer odwołań** . Należy unikać dodawania odwołań do tych wersji zestawów, ponieważ występują pewne problemy z programowaniem, które mogą wystąpić podczas ich używania. Jeśli na przykład zarejestrowano różne wersje zestawów PIA w globalnej pamięci podręcznej zestawów, projekt zostanie automatycznie powiązany z wersją zestawu, który został zarejestrowany jako ostatni — nawet w przypadku określenia innej wersji zestawu na karcie **com** okna dialogowego **Menedżer odwołań** .

> [!NOTE]
> Niektóre zestawy są dodawane do projektu automatycznie po dodaniu zestawu, który się do nich odwołuje. Na przykład odwołania do `Office.dll` `Microsoft.Vbe.Interop.dll` zestawów i są dodawane automatycznie po dodaniu odwołania do zestawów programów Word, Excel, Outlook, Microsoft Forms lub Graph.

<a name="pialist"></a>

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Podstawowe zestawy międzyoperacyjności dla aplikacji Microsoft Office

Poniższa tabela zawiera listę podstawowych zestawów międzyoperacyjnych, które są dostępne dla [!INCLUDE[Office_16_short](../vsto/includes/office-16-short-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

<br/>

|Aplikacja lub składnik pakietu Office|Nazwa podstawowego zestawu międzyoperacyjnego|
|-------------------------------------|-----------------------------------|
|Biblioteka obiektów programu Microsoft Access 14,0<br /><br /> Biblioteka obiektów programu Microsoft Access 15,0|Microsoft.Office.Interop.Access.dll|
|Biblioteka obiektów aparatu bazy danych programu Microsoft Office 14,0<br /><br /> Biblioteka obiektów aparatu bazy danych programu Microsoft Office 15,0|Microsoft.Office.Interop.Access.Dao.dll|
|Biblioteka obiektów programu Microsoft Excel 14,0<br /><br /> Biblioteka obiektów programu Microsoft Excel 15,0|[Microsoft.Office.Interop.Excel.dll](/dotnet/api/microsoft.office.interop.excel?view=excel-pia&preserve-view=true)|
|Biblioteka obiektów Microsoft Graph 14,0 (używana przez program PowerPoint, dostęp i program Word dla wykresów)<br /><br /> Biblioteka obiektów Microsoft Graph 15,0|Microsoft.Office.Interop.Graph.dll|
|Biblioteka typów programu Microsoft InfoPath 2,0 (tylko dla programu InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](/dotnet/api/microsoft.office.interop.infopath?view=infopath-form&preserve-view=true)|
|Zestaw międzyoperacyjny programu Microsoft InfoPath XML (tylko dla programu InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|
|Biblioteka obiektów Microsoft Office 14,0 (funkcja udostępniona przez pakiet Office)<br /><br /> Biblioteka obiektów Microsoft Office 15,0 (funkcja udostępniona przez pakiet Office)|office.dll|
|Kontrolka widoku programu Outlook Microsoft Office (może być używana w stronach sieci Web i aplikacjach do uzyskiwania dostępu do Twojej skrzynki odbiorczej)|Microsoft.Office.Interop.OutlookViewCtl.dll|
|Biblioteka obiektów programu Microsoft Outlook 14,0<br /><br /> Biblioteka obiektów programu Microsoft Outlook 15,0|[Microsoft.Office.Interop.Outlook.dll](/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia&preserve-view=true)|
|Biblioteka obiektów programu Microsoft PowerPoint 14,0<br /><br /> Biblioteka obiektów programu Microsoft PowerPoint 15,0|Microsoft.Office.Interop.PowerPoint.dll|
|Biblioteka obiektów programu Microsoft Project 14,0<br /><br /> Biblioteka obiektów programu Microsoft Project 15,0|[Microsoft.Office.Interop.MSProject.dll](/dotnet/api/microsoft.office.interop.msproject?view=office-project-server&preserve-view=true)|
|Biblioteka obiektów programu Microsoft Publisher 14,0<br /><br /> Biblioteka obiektów programu Microsoft Publisher 15,0|Microsoft.Office.Interop.Publisher.dll|
|Biblioteka odwołań obiektów sieci Web programu Microsoft SharePoint Designer 14,0|Microsoft.Office.Interop.SharePointDesigner.dll|
|Biblioteka odwołań obiektów stron programu Microsoft SharePoint Designer 14,0|Microsoft.Office.Interop.SharePointDesignerPage.dll|
|Microsoft Smart Tags 2,0 — Biblioteka typów **Uwaga:**  Tagi inteligentne są przestarzałe w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] .|Microsoft.Office.Interop.SmartTag.dll|
|Biblioteka typów programu Microsoft Visio 14,0<br /><br /> Biblioteka typów programu Microsoft Visio 15,0|Microsoft.Office.Interop.Visio.dll|
|Microsoft Visio 14,0 Zapisz jako biblioteka typów sieci Web<br /><br /> Microsoft Visio 15,0 Zapisz jako biblioteka typów sieci Web|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|
|Biblioteka typów kontrolek rysowania programu Microsoft Visio 14,0<br /><br /> Biblioteka typów kontrolek rysowania programu Microsoft Visio 15,0|Microsoft.Office.Interop.VisOcx.dll|
|Biblioteka obiektów programu Microsoft Word 14,0<br /><br /> Biblioteka obiektów programu Microsoft Word 15,0|[Microsoft.Office.Interop.Word.dll](/dotnet/api/microsoft.office.interop.word?view=word-pia&preserve-view=true)|
|Rozszerzalność Visual Basic for Applications firmy Microsoft 5,3|Microsoft.Vbe.Interop.dll|

### <a name="binding-redirect-assemblies"></a>Zestawy przekierowania powiązań

W przypadku instalowania i rejestrowania pakietu Office zestawów PIA w globalnej pamięci podręcznej zestawów (z pakietem Office lub przez zainstalowanie pakietu redystrybucyjnego dla zestawów PIA) zestawy przekierowania powiązań również są instalowane tylko w globalnej pamięci podręcznej zestawów. Te zestawy pomagają upewnić się, że poprawna wersja podstawowych zestawów międzyoperacyjnych jest załadowana w czasie wykonywania.

Na przykład, gdy rozwiązanie, które odwołuje się do [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] zestawu, działa na komputerze, który ma [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] wersję tego samego podstawowego zestawu międzyoperacyjnego, zestaw przekierowania powiązania instruuje [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] środowisko uruchomieniowe do załadowania [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] wersji podstawowego zestawu międzyoperacyjnego.

Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznego przekierowywania powiązań](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).

## <a name="see-also"></a>Zobacz też

- [Jak: docelowa aplikacja pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md)
- [Rozwiązania programu InfoPath](../vsto/infopath-solutions.md)
- [Model obiektów programu Outlook — Omówienie](../vsto/outlook-object-model-overview.md)
- [Rozwiązania programu PowerPoint](../vsto/powerpoint-solutions.md)
- [Rozwiązania projektu](../vsto/project-solutions.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Ogólne informacje &#40;Office Development w programie Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)

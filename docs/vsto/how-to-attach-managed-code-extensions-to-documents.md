---
title: 'Instrukcje: Dołączanie rozszerzenia kodu zarządzanego do dokumentów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e54e8f4b2cb4e94a83446497c24f9f808210f7f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849797"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Instrukcje: Dołączanie rozszerzenia kodu zarządzanego do dokumentów
  Zestaw dostosowania można dołączyć do istniejącego dokumentu Microsoft Office Word lub skoroszytu programu Microsoft Office Excel. Dokument lub skoroszyt może być w dowolnym formacie pliku, który jest obsługiwany przez program Microsoft Office projektów i narzędzi programistycznych w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aby dołączyć dostosowanie do dokumentu programu Word lub Excel, należy użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metody <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy. Ponieważ <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy jest przeznaczony do uruchamiania na komputerze, który nie ma programu Microsoft Office zainstalowany, możesz użyć tej metody w rozwiązaniach, które nie są bezpośrednio związane z Microsoft Office development (na przykład konsoli lub aplikacji Windows Forms).  
  
> [!NOTE]  
>  Dostosowanie nie będzie można załadować, jeśli kod oczekuje formantów, które nie ma określonego dokumentu.  
  
 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Dołączanie lub odłączanie zestaw narzędzi VSTO dla programów z dokumentu programu Word? ](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Aby dołączanie rozszerzenia kodu zarządzanego do dokumentu  
  
1.  W projekcie, który nie wymaga programu Microsoft Office, takich jak aplikacji konsoli lub projekt Windows Forms, Dodaj odwołanie do *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* i  *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* zestawów.  
  
2.  Dodaj następujący kod **Importy** lub **przy użyciu** instrukcji na górze pliku kodu.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Wywołaj statyczną <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metody.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> przeciążenia. To przeciążenie pobiera pełną ścieżkę dokumentu i <xref:System.Uri> określający lokalizację pliku manifestu wdrożenia, dostosowywania, którego chcesz dołączyć do dokumentu. W tym przykładzie założono, że dokument programu Word o nazwie **WordDocument1.docx** znajduje się na pulpicie, a manifest wdrażania znajduje się w folderze o nazwie **Publikuj** to także na pulpicie.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Skompilować projekt i uruchomić aplikację na komputerze, w której chcesz dołączyć dostosowania. Na komputerze musi być Visual Studio 2010 Tools for Office Runtime zainstalowane.  
  
## <a name="see-also"></a>Zobacz także  
 [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Instrukcje: Usuwanie rozszerzenia kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  

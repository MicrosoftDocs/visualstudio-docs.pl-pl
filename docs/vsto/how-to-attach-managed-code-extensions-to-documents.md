---
title: 'Instrukcje: dołączanie rozszerzeń kodu zarządzanego do dokumentów'
description: Dowiedz się, jak dołączyć zestaw dostosowywania do Microsoft Office istniejącego dokumentu programu Word lub Microsoft Office skoroszytu programu Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 063b66af781ee412e7f7d2ab8014e009bc93bad9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954114"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Instrukcje: dołączanie rozszerzeń kodu zarządzanego do dokumentów
  Zestaw dostosowania można dołączyć do istniejącego dokumentu programu Microsoft Office Word lub Microsoft Office skoroszytu programu Excel. Dokument lub skoroszyt może być w dowolnym formacie pliku, który jest obsługiwany przez projekty Microsoft Office i narzędzia programistyczne w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Aby dołączyć dostosowanie do dokumentu programu Word lub Excel, użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metody <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy. Ponieważ <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasa została zaprojektowana tak, aby była uruchamiana na komputerze, na którym nie zainstalowano Microsoft Office, można użyć tej metody w rozwiązaniach, które nie są bezpośrednio związane z Microsoft Office programowaniem (np. konsolą lub aplikacją Windows Forms).

> [!NOTE]
> Nie można załadować dostosowania, jeśli kod oczekiwał kontroli, że określony dokument nie ma.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Aby dołączyć rozszerzenia kodu zarządzanego do dokumentu

1. W projekcie, który nie wymaga Microsoft Office, takich jak Aplikacja konsolowa lub Windows Forms projektu, Dodaj odwołanie do zestawów *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* i *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* .

2. Dodaj następujące instrukcje **Import** lub **using** na początku pliku kodu.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Wywołaj metodę statyczną <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> .

     Poniższy przykład kodu używa <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> przeciążenia. To Przeciążenie pobiera pełną ścieżkę do dokumentu i <xref:System.Uri> określa lokalizację manifestu wdrażania dla dostosowania, które ma zostać dołączone do dokumentu. W tym przykładzie przyjęto założenie, że dokument programu Word o nazwie **WordDocument1.docx** znajduje się na pulpicie, a manifest wdrożenia znajduje się w folderze o nazwie **Publish** , który znajduje się również na pulpicie.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Skompiluj projekt i uruchom aplikację na komputerze, na którym chcesz dołączyć dostosowanie. Na komputerze musi być zainstalowany program Visual Studio 2010 Tools for Office Runtime.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Instrukcje: usuwanie rozszerzeń kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)

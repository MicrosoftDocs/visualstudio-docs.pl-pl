---
title: 'How to: Attach managed code extensions to documents (Jak dołączyć rozszerzenia kodu zarządzanego do dokumentów)'
description: Dowiedz się, jak dołączyć zestaw dostosowywania do istniejącego Microsoft Office programu Word lub Microsoft Office programu Excel.
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
ms.openlocfilehash: 60fc27345ef148fd47fdcee15924917ce63f8d68
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825501"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>How to: Attach managed code extensions to documents (Jak dołączyć rozszerzenia kodu zarządzanego do dokumentów)
  Zestaw dostosowywania można dołączyć do istniejącego Microsoft Office programu Word lub Microsoft Office programu Excel. Dokument lub skoroszyt może być w dowolnym formacie pliku obsługiwanym przez projekty Microsoft Office i narzędzia programowe w Visual Studio. Aby uzyskać więcej informacji, [zobacz Architecture of document-level customizations](../vsto/architecture-of-document-level-customizations.md)(Architektura dostosowań na poziomie dokumentu).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Aby dołączyć dostosowanie do dokumentu programu Word lub Excel, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> użyj metody <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy . Ponieważ klasa jest przeznaczona do uruchamiania na komputerze bez zainstalowanego programu Microsoft Office, można użyć tej metody w rozwiązaniach, które nie są bezpośrednio związane z programem Microsoft Office (na przykład konsoli lub aplikacji <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Windows Forms).

> [!NOTE]
> Załadowanie dostosowania nie powiedzie się, jeśli kod oczekuje kontrolek, których nie ma w określonym dokumencie.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Aby dołączyć rozszerzenia kodu zarządzanego do dokumentu

1. W projekcie, który nie Microsoft Office aplikacji konsolowej lub projektu programu Windows Forms, dodaj odwołanie  doMicrosoft.VisualStudio.Tools.Applications.ServerDocument.dlli *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* zestawów.

2. Dodaj następujące **instrukcje Imports** lub **using** na początku pliku kodu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet4":::

3. Wywołaj metodę <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> statyczną.

     W poniższym przykładzie kodu użyto <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> przeciążenia . To przeciążenie przyjmuje pełną ścieżkę dokumentu i wartość określającą lokalizację manifestu wdrożenia dla dostosowania, które chcesz <xref:System.Uri> dołączyć do dokumentu. W tym przykładzie przyjęto założenie, że dokument programu Word o **nazwieWordDocument1.docx** znajduje się na pulpicie, a manifest wdrożenia znajduje się w folderze o nazwie **Publish** (Publikuj), który również znajduje się na pulpicie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet3":::

4. Skompilowanie projektu i uruchomienie aplikacji na komputerze, na którym chcesz dołączyć dostosowanie. Na komputerze musi być zainstalowany Visual Studio 2010 Tools for Office Runtime.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie dokumentami na serwerze przy użyciu klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Jak usunąć rozszerzenia kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)

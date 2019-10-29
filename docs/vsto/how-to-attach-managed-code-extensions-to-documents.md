---
title: 'Instrukcje: dołączanie rozszerzeń kodu zarządzanego do dokumentów'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8fb212f9c5441d697cfa92feee7dc18fab9270d2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985978"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Instrukcje: dołączanie rozszerzeń kodu zarządzanego do dokumentów
  Zestaw dostosowania można dołączyć do istniejącego dokumentu programu Microsoft Office Word lub Microsoft Office skoroszytu programu Excel. Dokument lub skoroszyt może być w dowolnym formacie pliku, który jest obsługiwany przez projekty Microsoft Office i narzędzia programistyczne w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Aby dołączyć dostosowanie do dokumentu programu Word lub Excel, użyj metody <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> klasy <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>. Ponieważ Klasa <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> została zaprojektowana tak, aby była uruchamiana na komputerze, na którym nie zainstalowano Microsoft Office, można użyć tej metody w rozwiązaniach, które nie są bezpośrednio związane z Microsoft Office programowaniem (np. konsolą lub aplikacją Windows Forms).

> [!NOTE]
> Nie można załadować dostosowania, jeśli kod oczekiwał kontroli, że określony dokument nie ma.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Aby dołączyć rozszerzenia kodu zarządzanego do dokumentu

1. W projekcie, który nie wymaga Microsoft Office, takich jak Aplikacja konsolowa lub Windows Forms projektu, Dodaj odwołanie do *pliku Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll* i  *Zestawy Microsoft. VisualStudio. Tools. Applications. Runtime. dll* .

2. Dodaj następujące instrukcje **Import** lub **using** na początku pliku kodu.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Wywołaj metodę static <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.

     Poniższy przykład kodu używa przeciążenia <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>. To Przeciążenie pobiera pełną ścieżkę do dokumentu i <xref:System.Uri>, który określa lokalizację manifestu wdrażania, który ma zostać dołączony do dokumentu. W tym przykładzie przyjęto założenie, że dokument programu Word o nazwie **WordDocument1. docx** znajduje się na pulpicie, a manifest wdrożenia znajduje się w folderze o nazwie **Publish** , który znajduje się również na pulpicie.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Skompiluj projekt i uruchom aplikację na komputerze, na którym chcesz dołączyć dostosowanie. Na komputerze musi być zainstalowany program Visual Studio 2010 Tools for Office Runtime.

## <a name="see-also"></a>Zobacz także
- [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Instrukcje: usuwanie rozszerzeń kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)

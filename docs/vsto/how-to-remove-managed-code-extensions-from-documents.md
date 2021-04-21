---
title: Jak usunąć rozszerzenia kodu zarządzanego z dokumentów
description: Programowe usuwanie zestawu dostosowywania z dokumentu lub skoroszytu, który jest częścią dostosowania na poziomie dokumentu dla programu Microsoft Word lub Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129b1bda44abf7283efe1996f1898491025ee9d9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825449"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Jak usunąć rozszerzenia kodu zarządzanego z dokumentów
  Zestaw dostosowywania można programowo usunąć z dokumentu lub skoroszytu, który jest częścią dostosowania na poziomie dokumentu dla programu Microsoft Office Word lub Microsoft Office Excel. Użytkownicy mogą następnie otwierać dokumenty i wyświetlać ich zawartość, ale żaden niestandardowy interfejs użytkownika (UI) dodawania do dokumentów nie zostanie wyświetlony i kod nie zostanie uruchomiony.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Zestaw dostosowywania można usunąć przy użyciu jednej z `RemoveCustomization` metod dostarczonych przez . [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Metoda, której użyjemy, zależy od tego, czy chcesz usunąć dostosowanie w czasie działania (czyli uruchamiając kod w dostosowywaniu, gdy dokument programu Word lub skoroszyt programu Excel jest otwarty), czy też chcesz usunąć dostosowanie z zamkniętego dokumentu lub dokumentu, który znajduje się na serwerze, który nie Microsoft Office zainstalowany.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Aby usunąć zestaw dostosowywania w czasie uruchamiania

1. W kodzie dostosowywania wywołaj metodę (dla programu <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> Word) <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> lub metodę (dla programu Excel). Ta metoda powinna być wywoływana dopiero wtedy, gdy dostosowanie nie jest już potrzebne.

     Miejsce wywołania tej metody w kodzie zależy od sposobu, w jaki jest używane dostosowanie. Jeśli na przykład klienci korzystają z funkcji twojego dostosowania, dopóki nie będą gotowi do wysłania dokumentu do innych klientów, którzy potrzebują tylko samego dokumentu (a nie dostosowania), możesz udostępnić interfejs użytkownika, który wywołuje usługę, gdy klient kliknie `RemoveCustomization` go. Alternatywnie, jeśli dostosowanie wypełnia dokument danymi przy pierwszym otwarciu, ale dostosowanie nie zapewnia żadnych innych funkcji, do których mają dostęp bezpośrednio klienci, możesz wywołać pozycję RemoveCustomization zaraz po zakończeniu inicjowania dokumentu.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Aby usunąć zestaw dostosowywania z zamkniętego dokumentu lub dokumentu na serwerze

1. W projekcie, który nie wymaga Microsoft Office aplikacji konsolowej lub projektu Windows Forms, dodaj  odwołanie doMicrosoft.VisualStudio.Tools.Applications.ServerDocument.dllzestawu.

2. Dodaj następującą **instrukcje Imports** lub **using** na początku pliku kodu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet1":::

3. Wywołaj metodę <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> statyczną <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy i określ ścieżkę dokumentu rozwiązania dla parametru .

     W poniższym przykładzie kodu założono, że usuwasz dostosowanie z dokumentu o *nazwieWordDocument1.docx* który znajduje się na pulpicie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet2":::

4. Skompilowanie projektu i uruchomienie aplikacji na komputerze, na którym chcesz usunąć dostosowanie. Na komputerze musi być zainstalowany Visual Studio 2010 Tools for Office Runtime.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie dokumentami na serwerze przy użyciu klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [How to: Attach Managed code extensions to documents (Jak dołączyć rozszerzenia kodu zarządzanego do dokumentów)](../vsto/how-to-attach-managed-code-extensions-to-documents.md)

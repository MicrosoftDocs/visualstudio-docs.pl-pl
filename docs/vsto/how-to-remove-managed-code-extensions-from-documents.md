---
title: 'Instrukcje: usuwanie rozszerzeń kodu zarządzanego z dokumentów'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b4f5cb3098289463cea7e650332583ec7b12258
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541313"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Instrukcje: usuwanie rozszerzeń kodu zarządzanego z dokumentów
  Można programowo usunąć zestaw dostosowań z dokumentu lub skoroszytu, który jest częścią dostosowania na poziomie dokumentu dla Microsoft Office Word lub Microsoft Office Excel. Następnie użytkownicy mogą otwierać dokumenty i wyświetlać zawartość, ale nie będą wyświetlane żadne niestandardowe interfejsy użytkownika (UI) dodawane do dokumentów, a kod nie zostanie uruchomiony.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Zestaw dostosowania można usunąć za pomocą jednej z `RemoveCustomization` metod dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Używana metoda zależy od tego, czy chcesz usunąć dostosowanie w czasie wykonywania (czyli przez uruchomienie kodu w dostosowaniu, gdy dokument programu Word lub skoroszyt programu Excel jest otwarty), lub jeśli chcesz usunąć dostosowanie z zamkniętego dokumentu lub dokumentu znajdującego się na serwerze, na którym nie zainstalowano Microsoft Office.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Aby usunąć zestaw dostosowywania w czasie wykonywania

1. W kodzie dostosowania Wywołaj <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> metodę (dla słowa) lub <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> metodę (dla programu Excel). Ta metoda powinna być wywoływana tylko po dostosowaniu nie jest już potrzebne.

     Miejsce, w którym wywoływana jest metoda w kodzie, zależy od sposobu użycia dostosowania. Na przykład jeśli klienci używają funkcji dostosowywania do momentu, gdy nie będą gotowi do wysłania dokumentu do innych klientów, którzy potrzebują tylko samego dokumentu (nie dostosowania), możesz udostępnić interfejs użytkownika, który wywołuje, `RemoveCustomization` gdy klient kliknie. Alternatywnie, jeśli dostosowanie wypełnia dokument danymi przy pierwszym otwarciu, ale dostosowanie nie udostępnia żadnych innych funkcji, które są dostępne bezpośrednio dla klientów, można wywołać RemoveCustomization zaraz po zainicjowaniu dokumentu przez dostosowanie.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Aby usunąć zestaw dostosowań z zamkniętego dokumentu lub dokumentu na serwerze

1. W projekcie, który nie wymaga Microsoft Office, takich jak Aplikacja konsolowa lub Windows Forms projektu, Dodaj odwołanie do zestawu *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

2. Dodaj następującą instrukcję **Imports** lub **using** na początku pliku kodu.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. Wywoływanie statycznej <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> metody <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy i Określanie ścieżki dokumentu rozwiązania dla parametru.

     W poniższym przykładzie kodu przyjęto założenie, że dostosowanie zostało usunięte z dokumentu o nazwie *WordDocument1.docx* znajdującego się na pulpicie.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. Skompiluj projekt i uruchom aplikację na komputerze, na którym chcesz usunąć dostosowanie. Na komputerze musi być zainstalowany program Visual Studio 2010 Tools for Office Runtime.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Instrukcje: dołączanie rozszerzeń kodu zarządzanego do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md)

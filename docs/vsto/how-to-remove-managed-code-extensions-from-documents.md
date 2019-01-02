---
title: 'Instrukcje: Usuwanie rozszerzenia kodu zarządzanego z dokumentów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2057fe53a571bccf04373636f83aaedecebfd4ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964776"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Instrukcje: Usuwanie rozszerzenia kodu zarządzanego z dokumentów
  Zestaw dostosowania można programowo usunąć dokument lub skoroszyt, który jest częścią dostosowywania poziomie dokumentu dla programu Microsoft Office Word lub Microsoft Office Excel. Użytkownicy mogą otwierać dokumentów i wyświetlanie zawartości, ale dowolnego niestandardowego interfejsu użytkownika (UI) dodawanie do dokumentów, nie będą widoczne, a kod nie będzie działał.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Możesz usunąć zestaw dostosowania przy użyciu jednej z `RemoveCustomization` metod dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Wybór metody zależy od tego, czy chcesz usunąć dostosowania w czasie wykonywania (oznacza to, uruchamiając kod w dostosowaniu podczas wyraz dokument lub skoroszyt programu Excel jest otwarty), lub jeśli chcesz usunąć dostosowania z zamkniętej dokumentu lub że s na serwerze, który ma zainstalowany w Microsoft Office.  
  
 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak zrobić I: Dołączanie lub odłączanie zestaw narzędzi VSTO dla programów z dokumentu programu Word? ](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
## <a name="to-remove-the-customization-assembly-at-runtime"></a>Aby usunąć zestaw dostosowania w czasie wykonywania  
  
1.  W kodzie dostosowywania wywołać <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> — metoda (dla programu Word) lub <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> — metoda (dla programu Excel). Tę metodę należy wywoływać tylko wtedy, gdy dostosowanie nie jest już potrzebny.  
  
     Gdzie chcesz wywołać tę metodę w kodzie zależy od tego, jak dostosowywanie jest używany. Na przykład, jeśli klienci korzystać z funkcji usługi dostosowywania aż będą gotowe do wysyłania dokumentu do innych klientów, którzy muszą tylko dokumentem (nie dostosowywania), musisz podać niektóre interfejsu użytkownika, który wywołuje `RemoveCustomization` gdy klient kliknie go. Alternatywnie Jeśli dostosowanie wypełnia dokumentu z danymi, po pierwszym otwarciu, ale dostosowanie nie zapewnia inne funkcje, które są dostępne bezpośrednio przez klientów, następnie możesz wywołać RemoveCustomization tak szybko, jak dostosowywanie Inicjowanie dokumentu zostanie zakończone.  
  
## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Aby usunąć zestaw dostosowania z dokumentu zamknięte lub na serwerze  
  
1.  W projekcie, który nie wymaga programu Microsoft Office, takich jak aplikacji konsoli lub projekt Windows Forms, Dodaj odwołanie do *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* zestawu.  
  
2.  Dodaj następujący kod **Importy** lub **przy użyciu** instrukcji na górze pliku kodu.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Wywołaj statyczną <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> metody <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy, a następnie określ ścieżkę dokumentu rozwiązanie dla parametru.  
  
     Poniższy przykład kodu zakłada, z dokumentu o nazwie usuwasz dostosowania *WordDocument1.docx* znajduje się na pulpicie.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Skompilować projekt i uruchomić aplikację na komputerze, w której chcesz usunąć dostosowania. Na komputerze musi być Visual Studio 2010 Tools dla pakietu Office runtime zainstalowane.  
  
## <a name="see-also"></a>Zobacz także  
 [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Instrukcje: Dołączanie rozszerzenia kodu zarządzanego do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  

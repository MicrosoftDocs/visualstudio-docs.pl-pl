---
title: Utworzenie wystąpienia podstawowy edytor za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769621"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Utworzenie wystąpienia podstawowy edytor za pomocą starszej wersji interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor jest odpowiedzialny za edycji funkcji, takich jak wstawianie, usuwanie, kopiowanie i wklejanie tekstu. Łączy te funkcje z udostępnianych przez usługi w języka, takich jak tekst, kolorowanie, wcięcia i instrukcji IntelliSense.  
  
 Możliwe jest utworzenie wystąpienia podstawowy edytor w jeden z trzech sposobów:  
  
- Jawnie utworzyć wystąpienie podstawowe edytora w oknie.  
  
- Podaj fabryka edytora, która zwraca wystąpienie podstawowy edytor  
  
- Otwórz plik z hierarchii projektu.  
  
  W poniższych sekcjach omówiono, jak utworzyć wystąpienia edytora za pomocą starszej wersji interfejsu API.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Jawnie otwierania wystąpienia edytorze podstawowych funkcji  
 Podczas uzyskiwania jawnie wystąpienie podstawowy edytor:  
  
- Uzyskaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do przechowywania obiektu danych dokumentu edytowany.  
  
- Utwórz reprezentację wiersza zorientowanej na obiekt danych dokumentów, tworząc <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfejs z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsu.  
  
- Ustaw <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> jako obiekt danych dokumentu w przypadku wystąpienia domyślna Implementacja klasy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interfejs, za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> metody.  
  
   Host <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> wystąpienia w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejs, za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> metody.  
  
  W tym momencie wyświetlanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejs zapewnia okna, który zawiera wystąpienie podstawowy edytor.  
  
  Jednak to nie jest wystąpieniem bardzo przydatne, ponieważ nie ma klawiszy skrótów, lub uzyskać dostęp do zaawansowanych funkcji. Aby uzyskać dostępu do skróty i zaawansowane funkcje:  
  
- Użyj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> do kojarzenia usługi językowej i obiekt danych dokumentu, który korzysta z edytora.  
  
- Tworzenie własnych skrótów klawiaturowych albo użyj domyślnego systemu przez ustawienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekty będą wyświetlane właściwości. Aby to zrobić, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> metody z <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> właściwości.  
  
   Aby uzyskać i używać niestandardowych skrótów klawiaturowych, wygenerować je przy użyciu pliku vsct. Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Jak uzyskać podstawowy edytor za pomocą fabryki edytora  
 Podczas implementowania podstawowy edytor z fabryki edytora przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, wykonaj wszystkie kroki opisane w poprzedniej sekcji, aby jawnie obsługiwać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> obiektu danych dokumentu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiektu.  
  
 Aby wyświetlić tekst, Uzyskaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejs z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> obiektu, a następnie wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Aby zapewnić obsługę języka edytora, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodę w ramach <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Można uzyskać domyślnego klawiszy skrótów, inaczej niż w poprzedniej sekcji, używasz kontekstu polecenia zwrócony przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody podczas uzyskiwania podstawowy edytor z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metoda zwraca to samo polecenie identyfikator GUID edytora tekstu, wystąpienie podstawowy edytor automatycznie uzyskuje wartość domyślna klawiszy skrótów.  
  
 Aby uzyskać ogólne informacje, zobacz [instruktażu: Tworzenie edytorze podstawowych i rejestrowanie typu pliku w edytorze](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Zobacz też  
 [W edytorze podstawowych](../extensibility/inside-the-core-editor.md)   
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Przewodnik: Tworzenie edytorze podstawowych i rejestrowanie typu pliku w edytorze](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)

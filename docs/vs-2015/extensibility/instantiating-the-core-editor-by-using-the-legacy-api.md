---
title: Tworzenie wystąpienia podstawowego edytora przy użyciu starszej wersji interfejsu API | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203911"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Tworzenie wystąpienia edytora podstawowego przy użyciu starszej wersji interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor jest odpowiedzialny za funkcje edycji tekstu, takie jak wstawianie, usuwanie, kopiowanie i wklejanie. Łączy te funkcje z tymi, które są udostępniane przez usługi języka, takie jak kolorowanie tekstu, wcięcia i uzupełnianie instrukcji IntelliSense.  
  
 Wystąpienie podstawowego edytora można utworzyć na jeden z trzech sposobów:  
  
- Jawnie Utwórz wystąpienie podstawowego edytora w oknie.  
  
- Podaj fabrykę edytora, która zwraca wystąpienie podstawowego edytora  
  
- Otwórz plik z hierarchii projektu.  
  
  W poniższych sekcjach omówiono sposób użycia starszego interfejsu API w celu utworzenia wystąpienia edytora.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Jawne otwieranie wystąpienia podstawowego edytora  
 W przypadku jawnego uzyskiwania wystąpienia podstawowego edytora:  
  
- Uzyskaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do przechowywania edytowanego obiektu danych dokumentu.  
  
- Utwórz zorientowaną na linie reprezentację obiektu danych dokumentu przez utworzenie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfejsu z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsu.  
  
- Ustaw <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> jako obiekt danych dokumentu dla wystąpienia domyślnej implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interfejsu przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> metody.  
  
   Hostowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> wystąpienia w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejsie przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> metody.  
  
  W tym momencie wyświetlanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejsu zapewnia okno zawierające wystąpienie podstawowego edytora.  
  
  Nie jest to jednak bardzo przydatne wystąpienie, ponieważ nie ma on klawiszy skrótów ani nie ma dostępu do zaawansowanych funkcji. Aby uzyskać dostęp do klawiszy skrótów i funkcji zaawansowanych:  
  
- Użyj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody, aby skojarzyć usługę języka z obiektem danych dokumentu, który jest używany przez Edytor.  
  
- Utwórz własne klawisze skrótów lub Użyj ustawień domyślnych systemu, ustawiając <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> właściwości wyświetlania obiektów. W tym celu należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> metodę z <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> właściwością.  
  
   Aby uzyskać i użyć niestandardowych klawiszy skrótów, wygeneruj je przy użyciu pliku. vsct. Aby uzyskać więcej informacji, zobacz [tabela poleceń programu Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Jak uzyskać podstawowy edytor przy użyciu fabryki edytora  
 Podczas wdrażania podstawowego edytora z fabryką edytora przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody wykonaj wszystkie kroki opisane w poprzedniej sekcji, aby jawnie hostować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> obiektu danych dokumentu w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekcie.  
  
 Aby wyświetlić tekst, uzyskaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejs z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> obiektu i Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodę.  
  
 Aby zapewnić obsługę języka dla edytora, wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodę w ramach <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Aby uzyskać domyślne klawisze skrótów, w przeciwieństwie do poprzedniej sekcji, należy użyć kontekstu poleceń zwróconego przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodę podczas uzyskiwania podstawowego edytora z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Metoda zwraca ten sam identyfikator GUID polecenia co Edytor tekstu, wystąpienie podstawowego edytora automatycznie uzyskuje domyślne klawisze skrótów.  
  
 Aby uzyskać ogólne informacje, zobacz [Przewodnik: Tworzenie podstawowego edytora i rejestrowanie typu pliku edytora](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wewnątrz edytora podstawowego](../extensibility/inside-the-core-editor.md)   
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Przewodnik: tworzenie edytora podstawowego i rejestrowanie typu pliku edytora](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)

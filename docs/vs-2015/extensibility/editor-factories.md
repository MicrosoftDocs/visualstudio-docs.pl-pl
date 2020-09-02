---
title: Fabryki edytora | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197763"
---
# <a name="editor-factories"></a>Fabryki edytorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fabryka edytorów tworzy obiekty edytora i umieszcza je w ramce okna, znanej jako widok fizyczny. Tworzy on dane dokumentu i obiekty widoku dokumentu, które są niezbędne do tworzenia edytorów i projektantów. Fabryka edytora jest wymagana do utworzenia edytora podstawowego programu Visual Studio i dowolnego edytora standardowego. Edytor niestandardowy można także opcjonalnie utworzyć przy użyciu fabryki edytora.  
  
 Tworzysz fabrykę edytora przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu. Poniższy przykład ilustruje sposób wdrażania <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> programu w celu utworzenia fabryki edytora:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Edytor jest ładowany podczas pierwszego otwierania typu pliku obsługiwanego przez ten edytor. Można wybrać opcję otwarcia określonego edytora lub domyślnego edytora. W przypadku wybrania edytora domyślnego zintegrowane środowisko programistyczne (IDE) określi odpowiedni edytor do otwarcia, a następnie otworzy go. Aby uzyskać więcej informacji, zobacz [ustalanie, który Edytor otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Rejestrowanie fabryk edytora  
 Aby można było użyć utworzonego przez siebie edytora, należy najpierw zarejestrować informacje o nim, w tym rozszerzenia plików, które może obsłużyć.  
  
 Jeśli pakietu VSPackage jest zapisywana w kodzie zarządzanym, można użyć metody Managed Package Framework (MPF), <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> Aby zarejestrować fabrykę edytora po załadowaniu pakietu VSPackage. Jeśli pakietu VSPackage jest zapisywana w kodzie niezarządzanym, należy zarejestrować fabrykę edytora za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> usługi.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Rejestrowanie fabryki edytora za pomocą kodu zarządzanego  
 Musisz zarejestrować fabrykę edytora w swojej `Initialize` metodzie pakietu VSPackage. Pierwsze wywołanie `base.Initialize` , a następnie wywołanie <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> dla każdej fabryki edytora  
  
 W kodzie zarządzanym nie ma potrzeby wyrejestrowywania fabryki edytora, ponieważ pakietu VSPackage ją obsłuży. Ponadto, jeśli fabryka edytorów implementuje <xref:System.IDisposable> , jest automatycznie usuwana po wyrejestrowaniu.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Rejestrowanie fabryki edytora przy użyciu kodu niezarządzanego  
 W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementacji pakietu edytora Użyj `QueryService` metody do wywołania `SVsRegisterEditors` . Wykonanie tej operacji zwraca wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> . Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodę, przekazując implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu. Należy mplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> w oddzielnym klasie.  
  
## <a name="the-editor-factory-registration-process"></a>Proces rejestracji fabryki edytora  
 Następujący proces występuje, gdy program Visual Studio ładuje Edytor przy użyciu fabryki edytora:  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]System projektu wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
2. Ta metoda zwraca fabrykę edytora. Program Visual Studio opóźnia ładowanie pakietu edytora, jednak do momentu, gdy system projektu rzeczywiście wymaga edytora.  
  
3. Gdy system projektu wymaga edytora, wywołań programu Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , wyspecjalizowanej metody, która zwraca zarówno widok dokumentu, jak i obiekty danych dokumentu.  
  
4. Jeśli wywołania wykonywane przez program Visual Studio do fabryki edytora przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> zwracają zarówno obiekt danych dokumentu, jak i obiekt widoku dokumentu, program Visual Studio utworzy okno dokumentu, umieści w nim obiekt widok dokumentu, a następnie wprowadza wpis do uruchomionej tabeli dokumentu (RDT) dla obiektu danych dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Uruchamianie tabeli dokumentu](../extensibility/internals/running-document-table.md)

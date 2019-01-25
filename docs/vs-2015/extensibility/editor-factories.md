---
title: Fabryki edytora | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fbf30d1fdb4fcce1e28a3c10c9949f1a11eae529
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834712"
---
# <a name="editor-factories"></a>Fabryki edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fabryka edytora tworzy obiekty edytora i umieszcza je w ramkę okna, znane jako fizyczny widok. Tworzy dane dokumentu i obiekty widoku dokumentu, które są niezbędne do utworzenia w edytorach i projektantach. Fabryka edytora jest wymagana do utworzenia podstawowy edytor programu Visual Studio i dowolnego edytora standardowego. Niestandardowy Edytor również opcjonalnie mogą być tworzone za pomocą fabryki edytora.  
  
 Tworzenie fabryki edytora implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu. Poniższy przykład ilustruje sposób implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> do utworzenia fabryki edytora:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Edytor jest ładowany podczas pierwszego otwierania określonego typu plików obsługiwane przez tego edytora. Można otworzyć określonego edytora lub domyślnego edytora. Jeśli wybierzesz domyślnego edytora, zintegrowanego środowiska programistycznego (IDE) określa poprawne edytora, aby otworzyć i następnie go otwiera. Aby uzyskać więcej informacji, zobacz [określająca, które edytora otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Zarejestrowanie fabryki edytora  
 Zanim użyjesz Edytor który został utworzony, najpierw należy zarejestrować informacje o tym, włącznie z rozszerzeniami, które mogą obsługiwać.  
  
 Jeśli Twojego pakietu VSPackage są zapisywane w kodzie zarządzanym, możesz użyć metody zarządzane pakietu Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> można zarejestrować fabryki edytora po załadowaniu Twojego pakietu VSPackage. Jeśli Twojego pakietu VSPackage są zapisywane w niezarządzanym kodzie, a następnie fabryką edytora należy zarejestrować przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> usługi.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Zarejestrowanie fabryki edytora przy użyciu kodu zarządzanego  
 Należy zarejestrować fabryką edytora w swojej pakietu VSPackage `Initialize` metody. Pierwsze wywołanie `base.Initialize`, a następnie wywołaj <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> każdej fabryki edytora  
  
 W kodzie zarządzanym nie ma potrzeby wyrejestrować fabryki edytora ponieważ pakietu VSPackage będzie obsługiwać to dla Ciebie. Ponadto jeśli implementuje fabryką edytora <xref:System.IDisposable>, zostanie automatycznie usunięty, w momencie wyrejestrowania.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Zarejestrowanie fabryki edytora za pomocą kodu niezarządzanego  
 W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> wdrożenia dla pakietu edytora, użyj `QueryService` metodę do wywołania `SVsRegisterEditors`. W ten sposób zwraca wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metody przez przekazanie implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu. Należy najpierw mplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> w osobnej klasy.  
  
## <a name="the-editor-factory-registration-process"></a>Proces rejestracji fabryki edytora  
 Następujący proces występuje, gdy program Visual Studio ładuje edytora przy użyciu usługi fabryka edytora:  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projektu wywołań systemowych <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Ta metoda zwraca fabryka edytora. Visual Studio opóźnia ładowanie pakiet edytora, dopóki system projektu jest faktycznie potrzebny edytora.  
  
3.  Jeśli system projektu musi edytora, Visual Studio wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, wyspecjalizowanych metodę zwracającą widok dokumentu i dokumentu obiektów danych.  
  
4.  Jeśli wywołuje przez program Visual Studio z fabryki edytora za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> zwracają obiekt danych dokumentu i obiekt widoku dokumentu, Visual Studio następnie tworzy okno dokumentu, umieszcza obiekt widoku dokumentu w nim i sprawia, że wpis do uruchomionego dokumentu Tabela (Normalizacją) dla obiektu danych dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Uruchamianie tabeli dokumentu](../extensibility/internals/running-document-table.md)

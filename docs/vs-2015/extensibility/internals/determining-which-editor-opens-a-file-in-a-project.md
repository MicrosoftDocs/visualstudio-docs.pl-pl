---
title: Określanie, który Edytor otwiera plik w projekcie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c79860f770a6b04a17786cfb281fc3c0e4dffda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196760"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Określanie, który edytor służy do otwierania pliku w projekcie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gdy użytkownik otwiera plik w projekcie, środowisko przechodzi przez proces sondowania, ostatecznie otwierając odpowiedni edytor lub projektanta dla tego pliku. Procedura początkowa stosowana przez środowisko jest taka sama dla edytorów standardowych i niestandardowych. Środowisko używa różnych kryteriów podczas sondowania, który Edytor służy do otwierania pliku, a pakietu VSPackage musi być koordynowany ze środowiskiem w trakcie tego procesu.  
  
 Na przykład, gdy użytkownik wybierze polecenie **Otwórz** z menu **plik** , a następnie wybierze `filename` . rtf (lub dowolnego innego pliku z rozszerzeniem. rtf), środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementację dla każdego projektu, ostatecznie cyklicznie przez wszystkie wystąpienia projektu w rozwiązaniu. Projekty zwracają zestaw flag, które identyfikują oświadczenia w dokumencie według priorytetu. Przy użyciu najwyższego priorytetu środowisko wywołuje odpowiednią <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodę. Aby uzyskać więcej informacji o procesie sondowania, [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Projekt różne pliki przejmuje wszystkie pliki, które nie zostały przejęte przez inne projekty. W ten sposób niestandardowe edytory mogą otwierać dokumenty przed ich otwarciem przez edytory standardowe. Jeśli projekt różne pliki zgłasza oświadczenia do pliku, środowisko wywołuje metodę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Aby otworzyć plik ze standardowym edytorem. Środowisko sprawdza wewnętrzną listę zarejestrowanych edytorów, które obsługują pliki. RTF. Ta lista znajduje się w rejestrze w następującym kluczu:  
  
 [HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ < `version`> \Editors \\ {<`editor factory guid`>} \Extensions]  
  
 Środowisko sprawdza także identyfikatory klas w HKEY_CLASSES_ROOT kluczu \CLSID dla wszystkich obiektów, które mają podkluczą DocObject. Jeśli rozszerzenie pliku zostanie znalezione, w programie Visual Studio zostanie utworzona wbudowana wersja aplikacji, na przykład Microsoft Word. Te obiekty dokumentu muszą być plikami złożonymi implementującymi <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interfejs lub obiektem musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfejs.  
  
 Jeśli w rejestrze nie ma fabryki edytora dla plików RTF, środowisko szuka w \\ kluczu HKEY_CLASSES_ROOT. rtf i otworzy Edytor określony w tym miejscu. Jeśli rozszerzenie pliku nie zostanie znalezione w HKEY_CLASSES_ROOT, środowisko używa podstawowego edytora tekstu programu Visual Studio, aby otworzyć plik, jeśli jest to plik tekstowy.  
  
 Jeśli podstawowy edytor tekstu nie powiedzie się, co się stanie, jeśli plik nie jest plikiem tekstowym, środowisko używa jego edytora binarnego dla tego pliku.  
  
 Jeśli środowisko odnajdzie edytor dla rozszerzenia. rtf w jego rejestrze, ładuje pakietu VSPackage, który implementuje tę fabrykę edytora. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodę na nowym pakietu VSPackage. Pakietu VSPackage wywołuje `QueryService` metodę w `SID_SVsRegistorEditor` <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> celu zarejestrowania fabryki edytora przy użyciu środowiska.  
  
 Środowisko teraz ponownie sprawdza swoją wewnętrzną listę zarejestrowanych edytorów w celu znalezienia nowo zarejestrowanej fabryki edytora dla plików RTF. Środowisko wywołuje implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, przekazując nazwę pliku i typ widoku do utworzenia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

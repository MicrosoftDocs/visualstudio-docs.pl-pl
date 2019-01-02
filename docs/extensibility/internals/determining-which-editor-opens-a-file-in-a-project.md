---
title: Określanie, które edytora otwiera plik w projekcie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61aa726a7088d08db6d759a9835816dcaf826a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941063"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Określić, które edytora otwiera plik w projekcie
Gdy użytkownik otwiera plik w projekcie, środowiska przechodzi przez proces sondowania, po pewnym czasie otwarcie odpowiedniego edytora lub projektanta dla tego pliku. Procedury początkowej zatrudnionych przez środowisko jest taki sam dla standardowych i niestandardowych edytorów. Środowisko używa różnych kryteriów, podczas sondowania edytory, które służy do otwierania pliku i pakietu VSPackage skoordynować ze środowiskiem w trakcie tego procesu.  
  
 Na przykład, gdy użytkownik wybierze **Otwórz** polecenia **pliku** menu, a następnie *filename.rtf* (lub dowolnego innego pliku za pomocą *.rtf*rozszerzenia), wywołuje środowisko <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> wdrożenia dla każdego projektu, po pewnym czasie okrągło wszystkich wystąpień projektu w rozwiązaniu. Projekty zwracają zestaw flag, które identyfikują oświadczeń w dokumencie według priorytetu. Korzystając z najwyższym priorytetem, środowisko wywołuje odpowiednią <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody. Aby uzyskać więcej informacji na temat procesu sondowania, zobacz [Dodaj projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Projekt różne pliki oświadczeń wszystkie pliki, które nie są żądane przez inne projekty. W ten sposób niestandardowych edytorów otwierać dokumenty przed standardowych edytorów je otworzyć. Jeśli projekt różne pliki oświadczeń pliku, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby otworzyć go za pomocą edytora standardowego. Środowiska sprawdza jego wewnętrzną listę zarejestrowanych edytory dla jednego, który obsługuje *.rtf* plików. Ta lista znajduje się w rejestrze pod następujący klucz:  
  
 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<wersji > \Editors\\\<identyfikator guid fabryki edytora > \Extensions**
  
 Środowiska sprawdza również, identyfikatory klasy **HKEY_CLASSES_ROOT\CLSID** klucza dla obiektów, które mają podklucz **DocObject**. Jeśli rozszerzenie pliku znajduje się tam, wbudowana wersja aplikacji, takiego jak Microsoft Word, zostanie utworzony w miejscu, w programie Visual Studio. Te obiekty dokumentu musi być złożone plików, które implementują <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> musi implementować interfejs lub obiekt <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfejsu.  
  
 Jeśli brak fabryki edytora dla *.rtf* pliki w rejestrze, a następnie przeszukuje środowiska **HKEY_CLASSES_ROOT\\.rtf** klucza i zostanie otwarty Edytor określone. Jeśli rozszerzenie pliku nie zostanie znaleziony w **HKEY_CLASSES_ROOT**, następnie środowiska używa Edytor tekstu Visual Studio core można otworzyć pliku, jeśli jest plikiem tekstowym.  
  
 W przypadku niepowodzenia podstawowy edytor tekstu, która pojawia się Jeśli plik nie jest plikiem tekstowym, następnie środowiska korzysta z jego edytora binarnego pliku.  
  
 Jeśli środowisko znaleźć edytora *.rtf* rozszerzenia w jego rejestrze, ładuje pakietu VSPackage, który implementuje Ta fabryka edytora. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metody nowego pakietu VSPackage. Wywołania pakietu VSPackage `QueryService` dla `SID_SVsRegistorEditor`przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodę, aby zarejestrować fabryki edytora ze środowiskiem.  
  
 Środowiska sprawdza teraz ponownie jego wewnętrzną listę zarejestrowanych edytory można odnaleźć fabryki edytora nowo zarejestrowanego dla *.rtf* plików. Środowisko wywołuje implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, przekazując typ nazwy i widok pliku do utworzenia.  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
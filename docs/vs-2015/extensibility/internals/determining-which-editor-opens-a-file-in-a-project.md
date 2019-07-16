---
title: Określanie, które edytora otwiera plik w projekcie | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196760"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Określanie, który edytor służy do otwierania pliku w projekcie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gdy użytkownik otwiera plik w projekcie, środowiska przechodzi przez proces sondowania, po pewnym czasie otwarcie odpowiedniego edytora lub projektanta dla tego pliku. Procedury początkowej zatrudnionych przez środowisko jest taki sam dla standardowych i niestandardowych edytorów. Środowisko używa różnych kryteriów, podczas sondowania edytory, które służy do otwierania pliku i pakietu VSPackage skoordynować ze środowiskiem w trakcie tego procesu.  
  
 Na przykład, gdy użytkownik wybierze **Otwórz** polecenia **pliku** menu, a następnie `filename`RTF (lub dowolnego innego pliku z rozszerzeniem .rtf) wywołań środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Implementacja dla każdego projektu, po pewnym czasie okrągło wszystkich wystąpień projektu w rozwiązaniu. Projekty zwracają zestaw flag, które identyfikują oświadczeń w dokumencie według priorytetu. Korzystając z najwyższym priorytetem, środowisko wywołuje odpowiednią <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody. Aby uzyskać więcej informacji na temat procesu sondowania [Dodawanie projektu i szablonów elementów projektów](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Projekt różne pliki oświadczeń wszystkie pliki, które nie są żądane przez inne projekty. W ten sposób niestandardowych edytorów otwierać dokumenty przed standardowych edytorów je otworzyć. Jeśli projekt różne pliki oświadczeń pliku, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby otworzyć go za pomocą edytora standardowego. Środowiska sprawdza jego wewnętrzną listę zarejestrowanych edytory dla jednego, który obsługuje .rtf — pliki. Ta lista znajduje się w rejestrze pod następujący klucz:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 Środowiska sprawdza również identyfikatory klasy w kluczu HKEY_CLASSES_ROOT\CLSID dla obiektów, które mają DocObject podklucza. Jeśli rozszerzenie pliku znajduje się tam, wbudowana wersja aplikacji, takiego jak Microsoft Word, zostanie utworzony w miejscu, w programie Visual Studio. Te obiekty dokumentu musi być złożone plików, które implementują <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> musi implementować interfejs lub obiekt <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfejsu.  
  
 Jeśli brak fabryki edytora plików RTF w rejestrze, a następnie środowiska wygląda w kluczu HKEY_CLASSES_ROOT \\klucz RTF i zostanie otwarty Edytor określone. Jeśli rozszerzenie pliku nie zostanie znaleziony w kluczu HKEY_CLASSES_ROOT, następnie środowisko użyje Edytor tekstu Visual Studio core można otworzyć pliku, jeśli jest plikiem tekstowym.  
  
 W przypadku niepowodzenia podstawowy edytor tekstu, która pojawia się Jeśli plik nie jest plikiem tekstowym, następnie środowiska korzysta z jego edytora binarnego pliku.  
  
 Jeśli środowiska znaleźć edytora dla rozszerzenia rtf w jego rejestrze, ładuje pakietu VSPackage, który implementuje Ta fabryka edytora. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metody nowego pakietu VSPackage. Wywołania pakietu VSPackage `QueryService` dla `SID_SVsRegistorEditor`przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodę, aby zarejestrować fabryki edytora ze środowiskiem.  
  
 Środowisko ponownie sprawdza jego wewnętrzną listę zarejestrowanych edytory odnaleźć fabryki edytora nowo zarejestrowanego dla .rtf — pliki. Środowisko wywołuje implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, przekazując typ nazwy i widok pliku do utworzenia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

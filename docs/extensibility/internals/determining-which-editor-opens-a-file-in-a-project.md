---
title: Określanie, który edytor otwiera plik w projekcie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708659"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Określanie, który edytor otwiera plik w projekcie
Gdy użytkownik otwiera plik w projekcie, środowisko przechodzi przez proces sondowania, ostatecznie otwierając odpowiedni edytor lub projektant dla tego pliku. Początkowa procedura stosowana przez środowisko jest taka sama zarówno dla edytorów standardowych, jak i niestandardowych. Środowisko używa różnych kryteriów podczas sondowania, który edytor do użycia do otwarcia pliku i VSPackage musi koordynować ze środowiskiem podczas tego procesu.

 Na przykład, gdy użytkownik wybierze polecenie **Otwórz** z menu **Plik,** a następnie wybierze *plik filename.rtf* (lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> dowolny inny plik z rozszerzeniem *.rtf),* środowisko wywołuje implementację dla każdego projektu, ostatecznie przechodząc przez wszystkie wystąpienia projektu w rozwiązaniu. Projekty zwracają zestaw flag, które identyfikują oświadczenia w dokumencie według priorytetu. Przy użyciu najwyższego priorytetu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> środowisko wywołuje odpowiednią metodę. Aby uzyskać więcej informacji na temat procesu sondowania, zobacz [Dodawanie szablonów elementów projektu i projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Projekt Różne pliki twierdzi, że wszystkie pliki, które nie są zgłaszane przez inne projekty. W ten sposób edytorzy niestandardowi mogą otwierać dokumenty, zanim otworzą je standardowe edytory. Jeśli projekt Różne pliki żąda pliku, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę otwierania pliku za pomocą standardowego edytora. Środowisko sprawdza wewnętrzną listę zarejestrowanych edytorów dla jednego, który obsługuje pliki *.rtf.* Ta lista znajduje się w rejestrze pod następującym kluczem:

 **\\\<HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio version>\Editors\\\<editor factory guid>\Extensions**

 Środowisko sprawdza również identyfikatory klas w **kluczu HKEY_CLASSES_ROOT\CLSID** dla wszystkich obiektów, które mają podklucz **DocObject**. Jeśli zostanie tam znalezione rozszerzenie pliku, osadzona wersja aplikacji, taka jak Microsoft Word, jest tworzona w miejscu w programie Visual Studio. Te obiekty dokumentu muszą być <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> pliki złożone, które implementują interfejs lub obiekt musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfejs.

 Jeśli w rejestrze nie ma fabryki edytora plików *.rtf,* środowisko szuka w **HKEY_CLASSES_ROOT\\.rtf** i otwiera edytor określony tam. Jeśli rozszerzenie pliku nie zostanie znalezione w **HKEY_CLASSES_ROOT,** środowisko używa edytora tekstu core programu Visual Studio do otwierania pliku, jeśli jest to plik tekstowy.

 Jeśli podstawowy edytor tekstu nie powiedzie się, co występuje, jeśli plik nie jest plikiem tekstowym, środowisko używa edytora binarnego dla pliku.

 Jeśli środowisko znajdzie edytor dla rozszerzenia *.rtf* w rejestrze, ładuje VSPackage, który implementuje tę fabrykę edytora. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodę na nowy VSPackage. VSPackage wywołuje `QueryService` `SID_SVsRegistorEditor`, przy <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> użyciu metody, aby zarejestrować fabrykę edytora w środowisku.

 Środowisko sprawdza teraz ponownie swoją wewnętrzną listę zarejestrowanych edytorów, aby znaleźć nowo zarejestrowaną fabrykę edytora dla plików *.rtf.* Środowisko wywołuje implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, przekazywanie w nazwie pliku i typu widoku do utworzenia.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

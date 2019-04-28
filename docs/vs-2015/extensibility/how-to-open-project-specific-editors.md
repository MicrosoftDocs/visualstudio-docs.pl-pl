---
title: 'Instrukcje: Otwieranie edytorów specyficznych dla projektu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2439a07f63b8da854ca8dc331d26e30f49503257
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435943"
---
# <a name="how-to-open-project-specific-editors"></a>Instrukcje: Otwieranie edytorów specyficznych dla projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli plik elementu otwierana przez projekt wewnętrznie jest powiązany z określonego edytora dla tego projektu, projekt musi otworzyć plik za pomocą edytora specyficznych dla projektu. Plik nie może być delegowane do środowiska IDE mechanizm wybierania edytora. Na przykład zamiast za pomocą edytora standardowego mapy bitowej służy tej opcji edytora specyficznych dla projektu do określenia Edytor mapa bitowa szczególnych, który rozpoznaje informacje zawarte w pliku, który jest unikatowy dla projektu.  
  
 Wywołania środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody Określa, że plik powinien zostać otwarty przez określonego projektu. Aby uzyskać więcej informacji, zobacz [wyświetlanie plików za pomocą polecenia Otwórz plik](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Skorzystaj z poniższych wskazówek w celu zaimplementowania `OpenItem` metoda będzie miała projektu otwórz plik przy użyciu edytora specyficznych dla projektu.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Aby wdrożyć metodę OpenItem za pomocą edytora specyficznych dla projektu  
  
1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> — metoda (RDT_EditLock) w celu ustalenia, czy plik (obiekt danych dokumentu), jest już otwarty.  
  
    > [!NOTE]
    > Aby uzyskać więcej informacji na temat danych dokumentów i obiektów widoku dokumentu, zobacz [dane dokumentu i Widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2. Jeśli plik jest już otwarty, można go resurface przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody i określając wartość IDO_ActivateIfOpen dla `grfIDO` parametru.  
  
     Jeśli plik jest otwarty dokument jest własnością projekt inny niż projektu wywołującego, pojawi się ostrzeżenie do użytkownika, że edytor jest otwarty w innym projekcie. Okno w pliku jest następnie udostępniane.  
  
3. Jeśli chcesz do niej dołączyć inny widok usługi buforu tekstowego (obiekt danych dokument) jest już otwarty, użytkownik jest odpowiedzialny Podłączanie tego widoku. Zalecane podejście do tworzenia wystąpienia widoku (obiekt widoku dokumentu) z projektu, jest następujący:  
  
    1. Wywołaj `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> usługi, aby uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interfejsu.  
  
    2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metodę, aby utworzyć wystąpienie klasy widoku dokumentu.  
  
4. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metody, określając nazwę obiektu widoku dokumentu.  
  
     Ta metoda witryn obiekt widoku dokumentu w oknie dokumentu.  
  
5. Wykonaj odpowiednie wywołania albo <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> metody.  
  
     W tym momencie widok powinien być pełni zainicjowana i może zostać otwarty.  
  
6. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodę, aby wyświetlić, a następnie otwórz widok.  
  
## <a name="see-also"></a>Zobacz też  
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Instrukcje: Otwieranie standardowych edytorów](../extensibility/how-to-open-standard-editors.md)   
 [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../extensibility/how-to-open-editors-for-open-documents.md)

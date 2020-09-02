---
title: 'Instrukcje: otwieranie edytorów standardowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 792ac8a0859481fd97b2eaee4bd66753f0460a37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204131"
---
# <a name="how-to-open-standard-editors"></a>Instrukcje: otwieranie standardowych edytorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po otwarciu standardowego edytora, można pozwolić IDE określić standardowy edytor dla wyznaczony typ pliku, zamiast określać Edytor specyficzny dla projektu dla tego pliku.  
  
 Aby zaimplementować metodę, należy wykonać poniższą procedurę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> . Spowoduje to otwarcie pliku projektu w standardowym edytorze.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Aby zaimplementować metodę OpenItem przy użyciu standardowego edytora  
  
1. Call <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> ( `RDT_EditLock` ), aby określić, czy plik obiektu danych dokumentu jest już otwarty.  
  
2. Jeśli plik jest już otwarty, należy go ponownie utworzyć, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodę, określając wartość `IDO_ActivateIfOpen` `grfIDO` parametru.  
  
     Jeśli plik jest otwarty, a dokument jest własnością innego projektu niż wywołujący projekt, projekt otrzymuje ostrzeżenie, że otwarty Edytor pochodzi z innego projektu. Następnie zostanie wyświetlone okno plik.  
  
3. Jeśli dokument nie jest otwarty lub nie znajduje się w uruchomionej tabeli dokumentu, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę ( `OSE_ChooseBestStdEditor` ), aby otworzyć standardowy edytor dla tego pliku.  
  
     Po wywołaniu metody środowisko IDE wykonuje następujące zadania:  
  
    1. IDE skanuje edytory/{guidEditorType}/rozszerzenia w rejestrze, aby określić, który Edytor może otworzyć plik i ma najwyższy priorytet.  
  
    2. Po ustaleniu przez środowisko IDE, który Edytor może otworzyć plik, wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . Implementacja Edytora ta metoda zwraca informacje wymagane przez środowisko IDE do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> nowo otwartego dokumentu.  
  
    3. Na koniec IDE ładuje dokument przy użyciu zwykłego interfejsu trwałości, takiego jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .  
  
    4. Jeśli środowisko IDE wcześniej ustaliło, że hierarchia lub element hierarchii jest dostępny, Metoda IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> metodę w projekcie, aby uzyskać wskaźnik kontekstu na poziomie projektu, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> który zostanie przekazany z <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> wywołaniem metody.  
  
4. Zwraca <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> wskaźnik do środowiska IDE, gdy środowisko IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> projekt, jeśli chcesz zezwolić edytorowi na pobieranie kontekstu z projektu.  
  
     Wykonanie tego kroku umożliwi projektowi oferowanie dodatkowych usług dla edytora.  
  
     Jeśli widok dokumentu lub obiekt widoku dokumentu został pomyślnie zlokalizowany w ramce okna, obiekt jest inicjowany z danymi przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> .  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Instrukcje: otwieranie edytorów specyficznych dla projektu](../extensibility/how-to-open-project-specific-editors.md)   
 [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

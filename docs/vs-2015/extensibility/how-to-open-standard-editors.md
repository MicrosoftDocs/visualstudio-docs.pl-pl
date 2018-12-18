---
title: 'Porady: otwieranie standardowych edytorów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc6829ba4d1267d7a17c609f973b5ee6b570e9ac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742504"
---
# <a name="how-to-open-standard-editors"></a>Porady: otwieranie standardowych edytorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po otwarciu edytora standardowego, możesz zezwolić IDE określić Edytor standardowy do wyznaczonego typu pliku, zamiast określania edytora specyficznych dla projektu w pliku.  
  
 Wykonaj następującą procedurę, aby zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody. Spowoduje to otwarcie pliku projektu za pomocą edytora standardowego.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Aby wdrożyć metodę OpenItem za pomocą edytora standardowego  
  
1.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) do określenia, czy plik obiektu danych dokumentu jest już otwarty.  
  
2.  Jeśli plik jest już otwarty, można go resurface przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody, określając wartość `IDO_ActivateIfOpen` dla `grfIDO` parametru.  
  
     Jeśli plik jest otwarty dokument jest własnością innego projektu niż projektu wywołującego, Twój projekt otrzymuje ostrzeżenie, że edytor otwierana pochodzi z innego projektu. Okno w pliku jest następnie udostępniane.  
  
3.  Jeśli dokument nie jest otwarty lub nie w uruchomionej tabeli dokumentu, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> — metoda (`OSE_ChooseBestStdEditor`) aby otworzyć Edytor standardowy w pliku.  
  
     Po wywołaniu metody, IDE wykonuje następujące zadania:  
  
    1.  IDE skanuje edytory / {guidEditorType} / rozszerzenia podkluczu w rejestrze, aby określić, edytor, którego można otworzyć ten plik i ma najwyższy priorytet tego zrobić.  
  
    2.  Po IDE stwierdził, edytor, którego można otworzyć plik, IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Edytor implementacja tej metody zwraca informacje, które są wymagane dla środowiska IDE wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> i lokacji nowo otwartego dokumentu.  
  
    3.  Na koniec IDE ładuje dokumentu przy użyciu interfejsu zwykle trwałości, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Jeśli IDE wcześniej stwierdził, że hierarchia lub hierarchia elementów jest dostępny, IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> metody na projekt, aby pobrać kontekstu na poziomie projektu <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> wskaźnik, aby przekazać ponownie przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> wywołania metody.  
  
4.  Zwróć <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> wskaźnik do IDE, gdy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> nad projektem, jeśli chcesz umożliwić kontekstu get edytora z projektu.  
  
     Wykonanie tego kroku umożliwia oferta projektu dodatkowych usług do edytora.  
  
     Jeśli widok dokumentu lub obiektu widoku dokumentu został pomyślnie ulokowany ramki okna, obiekt jest inicjowany ze swoimi danymi, przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Porady: otwieranie edytorów specyficznych dla projektu](../extensibility/how-to-open-project-specific-editors.md)   
 [Porady: otwieranie edytorów dla otwartych dokumentów](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)


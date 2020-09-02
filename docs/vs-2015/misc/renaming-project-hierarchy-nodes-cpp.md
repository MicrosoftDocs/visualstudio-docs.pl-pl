---
title: Zmiana nazw węzłów hierarchii projektu (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686590"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Zmiana nazw węzłów hierarchii projektu (C++)
Można zmienić nazwę węzła hierarchia folderów projektu przy użyciu struktury projektu HierUtil7 dla niezarządzanego języka C++. Aby uzyskać więcej informacji, zobacz [przykład HierUtil7](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Rozszerzanie węzła hierarchii  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Aby rozwinąć węzeł hierarchia i zmienić nazwę folderu  
  
1. Wybierz węzeł hierarchia przy użyciu następującej metody:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` jest kontenerem hierarchii odpowiadającym folderowi i `EXPF_SelectItem` pochodzi z <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> wyliczenia. `GUID_MacroExplorer`Jest to stała identyfikatora GUID zdefiniowana w vsshell. idl i jest przykładem dla `rguidPersistenceSlot` sygnatury funkcji `ExtExpand` , zdefiniowanej w Hu_node. h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Plik Hu_node. h można znaleźć w folderze, \<installation root> \Program Files\VSIP 8.0 \ EnvSDK\common\hierutil7:  
  
2. Zmień nazwę folderu, publikując polecenie Zmień nazwę za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> wskaźnikiem: `<IVsUIShell>``srpVsUIShell` . `guiVSStd97` jest unikatowym identyfikatorem grupy poleceń, do której należy polecenie `cmdidRename` zdefiniowane w vsshlids. h.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie typów projektów](../extensibility/internals/creating-project-types.md)   
 [Przykłady VSSDK](../misc/vssdk-samples.md)
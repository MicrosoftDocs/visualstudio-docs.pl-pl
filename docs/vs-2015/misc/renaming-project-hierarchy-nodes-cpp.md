---
title: Zmiana nazwy węzłów hierarchii projektu (C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 3d1d99bd49d7a5fd78b38262725b65c5d1b3aab9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978113"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Zmiana nazwy węzłów hierarchii projektu (C++)
Możesz zmienić nazwę węzła hierarchii folderu projektu, przy użyciu struktury projektu HierUtil7 for niezarządzanego C++. Aby uzyskać więcej informacji, zobacz [przykładowe HierUtil7](http://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Rozwinięcie węzła hierarchii  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Rozwiń węzeł hierarchii i Zmień nazwę folderu  
  
1. Wybierz węzeł hierarchii przy użyciu następującej metody:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` jest kontenerem hierarchii odpowiadający folder i `EXPF_SelectItem` pochodzi z <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> wyliczenia. `GUID_MacroExplorer` Jest zdefiniowany w Vsshell.idl stałą identyfikator GUID i znajduje się przykład dla `rguidPersistenceSlot` w podpisie funkcja `ExtExpand`zdefiniowaną w Hu_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Plik Hu_node.h można znaleźć w folderze \<głównego instalacji > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7:  
  
2. Zmień nazwę folderu, publikując polecenia rename przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> wskaźnika: `<IVsUIShell>``srpVsUIShell`. `guiVSStd97` Unikatowy identyfikator grupy poleceń, do którego polecenie `cmdidRename` należy, zdefiniowane w Vsshlids.h.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie typów projektów](../extensibility/internals/creating-project-types.md)   
 [Przykłady VSSDK](../misc/vssdk-samples.md)
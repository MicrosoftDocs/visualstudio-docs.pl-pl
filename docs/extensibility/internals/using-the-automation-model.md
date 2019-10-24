---
title: Korzystanie z modelu automatyzacji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f1e1479232a684758359de7527f0c2fc9990cc7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722098"
---
# <a name="using-the-automation-model"></a>Korzystanie z modelu automatyzacji
Po nawiązaniu połączenia pakietu VSPackage z automatyzacją można uzyskać właściwości i metody, wywołując metodę <xref:EnvDTE.DTEClass.GetObject%2A> na obiekcie <xref:EnvDTE._DTE>, przekazując ciąg reprezentujący obiekt, który ma zostać pobrany.

## <a name="obtaining-project-objects"></a>Uzyskiwanie obiektów projektu
 Poniżej przedstawiono dwa przykłady kodu, które pokazują, jak konsument automatyzacji uzyskuje obiekty automatyzacji projektu. Aby uzyskać informacje na temat pobierania obiektu DTE, zobacz [How to: Get References to the DTE i DTE2 Objects](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 W tym momencie można użyć standardowych obiektów projektu, które są częścią określonego pakietu VSPackage, aby przenieść model hierarchii.

 Poniższy przykład kodu pokazuje, jak uzyskać niestandardowy obiekt, który jest właściwością niestandardowego typu projektu.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Poniższy kod wyświetla nazwy wszystkich właściwości w opcji **Ogólne** środowiska [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w menu **Narzędzia** :

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Zobacz także
- <xref:EnvDTE.DTEClass.GetObject%2A>
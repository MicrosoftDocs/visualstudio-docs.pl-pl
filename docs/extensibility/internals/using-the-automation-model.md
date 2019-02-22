---
title: Przy użyciu modelu automatyzacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37a5fb96d7f1e63bf28a9227333362ff79f3cd3d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602965"
---
# <a name="using-the-automation-model"></a>Korzystanie z modelu automatyzacji
Po połączeniu usługi pakietu VSPackage do automatyzacji, wywołując można uzyskać właściwości i metody <xref:EnvDTE.DTEClass.GetObject%2A> metody <xref:EnvDTE._DTE> obiektu, przekazując ciąg reprezentujący obiekt, który chcesz pobrać.

## <a name="obtaining-project-objects"></a>Uzyskiwanie obiektów projektu
 Poniżej przedstawiono dwa przykłady kodu, które pokazują, jak konsumenta automatyzacji uzyskuje projektu obiektów automatyzacji. Aby uzyskać informacje o tym, jak można pobrać obiektu DTE, zobacz [jak: Pobieranie odwołań do obiektów DTE i DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

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

 W tym momencie można użyć obiektów standardowy projekt, które należą do określonego pakietu VSPackage, aby przenieść w dół hierarchii modelu.

 Poniższy przykład kodu pokazuje, jak uzyskać niestandardowy obiekt, który jest właściwością typu niestandardowego projektu.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Poniższy kod wyświetla nazwy wszystkich właściwości w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska **ogólne** opcja **narzędzia** menu:

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Zobacz też
- <xref:EnvDTE.DTEClass.GetObject%2A>
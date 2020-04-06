---
title: Korzystanie z modelu automatyzacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b9d7bd789a41f7a5e801552ca07f9f228921867
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704218"
---
# <a name="using-the-automation-model"></a>Korzystanie z modelu automatyzacji
Po połączeniu vsPackage do automatyzacji, można uzyskać właściwości i <xref:EnvDTE.DTEClass.GetObject%2A> metody, <xref:EnvDTE._DTE> wywołując metodę na obiekcie, przekazując ciąg reprezentujący obiekt, który chcesz pobrać.

## <a name="obtaining-project-objects"></a>Uzyskiwanie obiektów projektu
 Poniżej przedstawiono dwa przykłady kodu, które pokazują, jak konsument automatyzacji uzyskuje obiektów automatyzacji projektu. Aby uzyskać informacje na temat sposobu uzyskania obiektu DTE, zobacz [Jak: Pobierz odwołania do obiektów DTE i DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

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

 W tym momencie można użyć standardowych obiektów projektu, które są częścią określonego VSPackage, aby przenieść w dół modelu hierarchii.

 Poniższy przykład kodu pokazuje, jak uzyskać obiekt niestandardowy, który jest właściwością niestandardowego typu projektu.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Poniższy kod zawiera nazwy wszystkich właściwości w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisku **Opcja ogólne** w menu **Narzędzia:**

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

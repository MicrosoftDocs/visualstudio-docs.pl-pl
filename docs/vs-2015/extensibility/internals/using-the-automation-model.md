---
title: Przy użyciu modelu automatyzacji | Dokumentacja firmy Microsoft
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
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea911dd70ae3a5ca0e53888b47ed2a8d859827c4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789138"
---
# <a name="using-the-automation-model"></a>Korzystanie z modelu automatyzacji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po połączeniu usługi pakietu VSPackage do automatyzacji, wywołując można uzyskać właściwości i metody <xref:EnvDTE.DTEClass.GetObject%2A> metody <xref:EnvDTE._DTE> obiektu, przekazując ciąg reprezentujący obiekt, który chcesz pobrać.  
  
## <a name="obtaining-project-objects"></a>Uzyskiwanie obiektów projektu  
 Poniżej przedstawiono dwa przykłady kodu, które pokazują, jak konsumenta automatyzacji uzyskuje projektu obiektów automatyzacji. Aby uzyskać informacje o tym, jak można pobrać obiektu DTE, zobacz [porady: pobieranie odwołań do obiektów DTE i DTE2](http://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
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
  
 Poniższy kod wyświetla nazwy wszystkich właściwości w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska **ogólne** opcja **narzędzia** menu:  
  
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
 <xref:EnvDTE.DTEClass.GetObject%2A>


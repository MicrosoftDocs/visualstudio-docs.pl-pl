---
title: Dodawanie katalogów do okna dialogowego Dodaj nowy element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203929"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniższy przykład kodu demonstruje sposób rejestrowania nowego zestawu katalogów dla okna dialogowego **Dodaj nowy element** . Katalogi dla okna dialogowego **Dodawanie nowego elementu** są różne dla każdego projektu. W związku z tym katalogi są rejestrowane w podkluczu projekty, które znajdują się w \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> :  
  
## <a name="the-registry-script"></a>Skrypt rejestru  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 Wartość Template_Path określa pełną ścieżkę katalogu, który zawiera szablony projektu. Te szablony mogą być plikami vsz lub plikami szablonów prototypowe do sklonowania.  
  
 Wartość SortPriority określa priorytet sortowania.  
  
## <a name="adding-items-to-an-existing-project"></a>Dodawanie elementów do istniejącego projektu  
 Możesz również dodać elementy do istniejącego projektu. Na przykład dla [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektu można dodać elementy do \<root> folderu \Program Files\Microsoft Visual Studio \VC # \CSharpProjectItems\LocalProjectItems. W tym przypadku `%GUID_Project%` jest to identyfikator GUID projektu C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Można także rozciągnąć istniejący projekt przez programowanie podtypu projektu. W przypadku podtypu projektu można zwiększyć projekt bez tworzenia nowego typu projektu. Aby uzyskać więcej informacji na temat podtypów projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie szablonów projektu i elementu](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Dodawanie elementów do okien dialogowych Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

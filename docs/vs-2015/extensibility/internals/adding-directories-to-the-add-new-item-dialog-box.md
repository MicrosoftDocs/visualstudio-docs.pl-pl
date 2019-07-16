---
title: Dodawanie katalogów do nowego elementu, okno dialogowe Dodawanie | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203929"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniższy przykład kodu pokazuje, jak zarejestrować nowy zestaw katalogów **Dodaj nowy element** okno dialogowe. Katalogi dla **Dodaj nowy element** okno dialogowe różnią się dla każdego projektu. W związku z tym, katalogi są rejestrowane w podkluczu projektów w \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
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
  
 Wartość Template_Path Określa pełną ścieżkę katalogu, który zawiera szablony projektów. Szablony te mogą być plików .vsz lub pliki szablonów prototypowe można sklonować.  
  
 Wartość SortPriority określa priorytet sortowania.  
  
## <a name="adding-items-to-an-existing-project"></a>Dodawanie elementów do istniejącego projektu  
 Można również dodać elementy do istniejącego projektu. Na przykład w przypadku [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektu, można dodać elementów do \<główny > \Program Files\Microsoft programu Visual Studio \VC#\CSharpProjectItems\LocalProjectItems folderu. W tym przypadku `%GUID_Project%` to identyfikator GUID projektu C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Można także rozszerzyć istniejący projekt, Programując podtypu projektu. Za pomocą podtypem projektu można rozszerzyć projektu bez konieczności pisania nowych typów projektów. Aby uzyskać więcej informacji na temat podtypy projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Dodawanie elementów do Dodaj nowy element okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

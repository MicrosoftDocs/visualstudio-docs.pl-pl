---
title: Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu | Microsoft Docs
description: Dowiedz się, jak dodać katalogi do okna dialogowego Dodawanie nowego elementu Visual Studio pomocą skryptu rejestru w celu zarejestrowania katalogów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dab135f8e8632755674d7b3ddf5972592f74d315
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904363"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu
Poniższy przykład kodu przedstawia sposób rejestrowania nowego zestawu katalogów dla okna dialogowego Dodawanie **nowego** elementu. Katalogi okna **dialogowego Dodawanie nowego elementu** są różne dla każdego projektu. W związku z tym katalogi są rejestrowane w **podkluczu Projects** (Projekty) w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Skrypt rejestru

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

 Wartość `%Template_Path%` określa pełną ścieżkę katalogu, który zawiera szablony projektu. Te szablony mogą być *plikami vsz* lub plikami szablonów prototypowych do sklonowania.

 Wartość `SortPriority` określa priorytet sortowania.

## <a name="add-items-to-an-existing-project"></a>Dodawanie elementów do istniejącego projektu
 Możesz również dodać elementy do istniejącego projektu. Na przykład w przypadku projektu można dodać elementy do folderu [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] *\<root> \Program Files\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems.* W tym przypadku jest identyfikatorem GUID projektu `%GUID_Project%` języka C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Możesz również rozszerzyć istniejący projekt, programjąc podtyp projektu. Za pomocą podtypu projektu można rozszerzyć projekt bez pisania nowego typu projektu. Aby uzyskać więcej informacji na temat podtypów projektu, [zobacz Podtypy projektu](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Zobacz też
- [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

---
title: Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710252"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu
Poniższy przykład kodu pokazuje, jak zarejestrować nowy zestaw katalogów dla okna dialogowego **Dodawanie nowego elementu.** Katalogi okna dialogowego **Dodawanie nowego elementu** są różne dla każdego projektu. W związku z tym katalogi są rejestrowane w podkluczu **Projekty,** znalezionym w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

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

 Wartość `%Template_Path%` określa pełną ścieżkę katalogu zawierającego szablony projektu. Szablony te mogą być plikami *.vsz* lub prototypowymi plikami szablonów do sklonowania.

 Wartość `SortPriority` określa priorytet sortowania.

## <a name="add-items-to-an-existing-project"></a>Dodawanie elementów do istniejącego projektu
 Można również dodać elementy do istniejącego projektu. Na przykład w [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] przypadku projektu można dodać elementy do folderu * \<główny>\Program Files\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems* folder. W takim `%GUID_Project%` przypadku jest identyfikator GUID dla projektu C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Istniejący projekt można również rozszerzyć, programowanie podtypu projektu. Za pomocą podtypu projektu można rozszerzyć projekt bez pisania nowego typu projektu. Aby uzyskać więcej informacji na temat podtypów projektu, zobacz [Podtypy projektu](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Zobacz też
- [Rejestrowanie szablonów projektów i towarów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

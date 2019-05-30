---
title: Dodawanie katalogów do nowego elementu, okno dialogowe Dodawanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 981b65df9354277580ee1c816f4e0fd0977f9a85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328017"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Dodawanie katalogów do okna dialogowego Dodaj nowy element
Poniższy przykład kodu pokazuje, jak zarejestrować nowy zestaw katalogów **Dodaj nowy element** okno dialogowe. Katalogi dla **Dodaj nowy element** okno dialogowe różnią się dla każdego projektu. W związku z tym, katalogi są zarejestrowane w obszarze **projektów** podklucza, znaleziono w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

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

 `%Template_Path%` Wartość określa pełną ścieżkę katalogu, który zawiera szablony projektów. Te szablony mogą być albo *.vsz* plików lub stacji szablonu można sklonować.

 `SortPriority` Wartość określa priorytet sortowania.

## <a name="add-items-to-an-existing-project"></a>Dodaj elementy do istniejącego projektu
 Można również dodać elementy do istniejącego projektu. Na przykład w przypadku [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu, można dodać elementów do  *\<główny > \Program Files\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems* folderu. W tym przypadku `%GUID_Project%` to identyfikator GUID projektu C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Można także rozszerzyć istniejący projekt, Programując podtypu projektu. Za pomocą podtypem projektu można rozszerzyć projektu bez konieczności pisania nowych typów projektów. Aby uzyskać więcej informacji na temat podtypy projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Zobacz także
- [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Dodawanie elementów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
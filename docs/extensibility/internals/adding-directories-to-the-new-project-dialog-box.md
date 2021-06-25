---
title: Dodawanie katalogów do okna dialogowego Nowy projekt | Microsoft Docs
description: Dowiedz się, jak dodać katalogi do okna dialogowego Nowy projekt Visual Studio, aby można było tworzyć nowe typy projektów i wyświetlać je do użycia jako szablony.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44554c8bd7b758f1bf191d1a4bef9ba07941191d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901841"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Dodawanie katalogów do okna dialogowego Nowy projekt
Podczas tworzenia nowych typów projektów można również zarejestrować  nowy katalog w oknie dialogowym Nowy projekt, aby wyświetlić go do użycia jako szablony. W poniższym przykładzie kodu wyjaśniono, jak zarejestrować nowy katalog, nazywany również węzłem. W tym przykładzie szablony udostępniane przez pakiet VSPackage *CLSID_Package*, są rejestrowane. W związku z tym po  lewej stronie okna dialogowego Nowy projekt jest dodawany węzeł o nazwie określanej *przez Folder_Label_ResID* zasobów. Ten zasób jest ładowany z biblioteki DLL satellite vspackage.

 Wartość **Folder** reprezentuje identyfikator GUID folderu, w którym *jest Folder_Label_ResID* węzeł. W tym przykładzie identyfikator GUID reprezentuje folder **Inne projekty** w **okienku Typy projektów** okna **dialogowego Nowy** projekt. Jeśli wartość **Other Projects (Inne** projekty) jest nieobecna, etykieta zostanie umieszczony na najwyższym poziomie.

 Wartość `TemplatesDir` określa pełną ścieżkę katalogu, który zawiera szablony projektu. Mogą to być pliki *vsz* lub typowe pliki szablonów do sklonowania.

 Jeśli określisz wartość , musi to być identyfikator zasobu ciągu, który określa nazwę podkatalogu, który `TemplatesLocalizedSubDir` `TemplatesDir` przechowuje zlokalizowane szablony. Ponieważ ładuje zasób ciągu z biblioteki DLL satelicie, jeśli masz, każda sateliczna biblioteka DLL może [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawierać inną nazwę podkatalogu. Wartość `SortPriority` określa priorytet sortowania.

```
NoRemove NewProjectTemplates
{
    NoRemove TemplateDirs
  {
    ForceRemove %CLSID_Package%
    {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
      {
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'
        val TemplatesDir = s '%Template_Path%'
        val TemplatesLocalizedSubDir = s '#100'
        val SortPriority = d 1000
      }
    }
  }
}
```

## <a name="see-also"></a>Zobacz też
- [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

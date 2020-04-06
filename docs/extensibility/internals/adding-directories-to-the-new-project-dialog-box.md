---
title: Dodawanie katalogów do okna dialogowego Nowy projekt | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710244"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Dodawanie katalogów do okna dialogowego Nowy projekt
Podczas tworzenia nowych typów projektów można również zarejestrować nowy katalog w oknie dialogowym **Nowy projekt,** aby wyświetlić go do użycia jako szablony. W poniższym przykładzie kodu wyjaśniono, jak zarejestrować nowy katalog, znany również jako węzeł. W przykładzie szablony udostępniane przez VSPackage, *CLSID_Package*, są rejestrowane. W rezultacie po lewej stronie okna dialogowego **Nowy projekt** znajduje się dodany węzeł o nazwie określonej przez *Folder_Label_ResID* zasób. Ten zasób jest ładowany z biblioteki DLL satelity VSPackage.

 Wartość **folderu** reprezentuje identyfikator GUID folderu, w którym wyświetlany jest *węzeł Folder_Label_ResID.* W tym przykładzie identyfikator GUID reprezentuje folder **Inne projekty** w okienku **Typy projektów** okna dialogowego Nowy **projekt.** Jeśli **wartość Inne projekty** jest nieobecna, etykieta jest pozycjonowana na najwyższym poziomie.

 Wartość `TemplatesDir` określa pełną ścieżkę katalogu zawierającego szablony projektu. Pliki te mogą być plikami *.vsz* lub typowymi plikami szablonów, które mają zostać sklonowane.

 Jeśli określisz `TemplatesLocalizedSubDir`, musi to być identyfikator zasobu ciągu, `TemplatesDir` który nazywa podkatalog zawierający zlokalizowane szablony. Ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje zasób ciągu z biblioteki DLL satelity, jeśli masz jeden, każda biblioteka DLL satelity może zawierać inną nazwę podkatalogu. Wartość `SortPriority` określa priorytet sortowania.

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
- [Rejestrowanie szablonów projektów i towarów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

---
title: Dodawanie katalogów do okna dialogowego Nowy projekt | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d8e68413795b7004542ee312dcb27492e55e7f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910811"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Dodawanie katalogów do okna dialogowego Nowy projekt
Podczas tworzenia nowych typów projektów, możesz także zarejestrować nowy katalog w **nowy projekt** okno dialogowe, aby wyświetlić je do użycia jako szablon. W poniższym przykładzie kodu przedstawiono metody rejestracji w nowym katalogu, znany także jako węzeł. W tym przykładzie szablony udostępnianych przez pakietu VSPackage, *CLSID_Package*, są rejestrowane. Dzięki temu usługa po lewej stronie **nowy projekt** okno dialogowe oferuje dodano węzeł o nazwie ustalany na podstawie *Folder_Label_ResID* zasobów. Ten zasób jest ładowany z pakietu VSPackage satelitarną bibliotekę DLL.

 **Folderu** wartość reprezentuje identyfikator GUID folderze *Folder_Label_ResID* węzeł jest wyświetlany. W tym przykładzie reprezentuje identyfikator GUID **inne projekty** folderu w **typów projektów** okienku **nowy projekt** okno dialogowe. Jeśli **inne projekty** wartość jest nieobecne, etykieta znajduje się na najwyższym poziomie.

 `TemplatesDir` Wartość określa pełną ścieżkę katalogu, który zawiera szablony projektów. Te pliki mogą być albo *.vsz* pliki lub typowe szablonu można sklonować.

 Jeśli określisz `TemplatesLocalizedSubDir`, musi być identyfikator zasobu ciągu, który nazwy podkatalogu `TemplatesDir` zawierający zlokalizowane szablony. Ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje zasobu ciągu z satelitarną bibliotekę DLL Jeśli nie masz, każdy satelitarną bibliotekę DLL mogą zawierać nazwę podkatalogu innej. `SortPriority` Wartość określa priorytet sortowania.

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

## <a name="see-also"></a>Zobacz także
- [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Dodawanie elementów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Dodawanie katalogów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
---
title: Dodawanie katalogów do okna dialogowego Nowy projekt | Microsoft Docs
description: Dowiedz się, jak dodać katalogi do okna dialogowego Nowy projekt w programie Visual Studio, dzięki czemu można tworzyć nowe typy projektów i wyświetlać je do użycia jako szablony.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d65b7e4adc6d235bcb925efae1cef20d0aa2c9c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969038"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Dodawanie katalogów do okna dialogowego Nowy projekt
Podczas tworzenia nowych typów projektów można także zarejestrować nowy katalog w oknie dialogowym **Nowy projekt** , aby wyświetlić je do użycia jako szablony. Poniższy przykład kodu wyjaśnia sposób rejestrowania nowego katalogu, znanego również jako węzeł. W przykładzie zarejestrowano szablony udostępniane przez pakietu VSPackage *CLSID_Package*. W związku z tym lewa strona okna dialogowego **Nowy projekt** oferuje dodany węzeł, z nazwą określoną przez zasób *Folder_Label_ResID* . Ten zasób jest ładowany z satelitarnej biblioteki DLL pakietu VSPackage.

 Wartość **folderu** reprezentuje identyfikator GUID folderu, w którym jest wyświetlany węzeł *Folder_Label_ResID* . W przykładzie identyfikator GUID reprezentuje folder **inne projekty** w okienku **typy projektów** w oknie dialogowym **Nowy projekt** . Jeśli wartość **innych projektów** jest nieobecna, etykieta jest umieszczana na najwyższym poziomie.

 `TemplatesDir`Wartość określa pełną ścieżkę katalogu, który zawiera szablony projektu. Te pliki mogą być plikami *vsz* lub typowymi plikami szablonów do sklonowania.

 Jeśli określisz `TemplatesLocalizedSubDir` , musi to być identyfikator zasobu ciągu, który zawiera nazwę podkatalogu `TemplatesDir` zawierającego zlokalizowane szablony. Ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje zasób ciągu z satelickiej biblioteki DLL, jeśli taki istnieje, każda satelitarna Biblioteka DLL może zawierać inną nazwę podkatalogu. `SortPriority`Wartość określa priorytet sortowania.

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
- [Rejestruj szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Dodaj elementy do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Dodawanie katalogów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

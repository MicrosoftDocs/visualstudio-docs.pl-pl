---
title: Dodawanie katalogów do okna dialogowego Nowy projekt | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760862"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Dodawanie katalogów do okna dialogowego Nowy projekt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas tworzenia nowych typów projektów, możesz także zarejestrować nowy katalog w **nowy projekt** okno dialogowe, aby wyświetlić je do użycia jako szablon. W poniższym przykładzie kodu przedstawiono metody rejestracji w nowym katalogu, znany także jako węzeł. W tym przykładzie udostępnianych przez CLSID_Package pakietu VSPackage szablony są rejestrowane. Dzięki temu usługa po lewej stronie **nowy projekt** okno dialogowe oferuje dodano węzeł o nazwie ustalany na podstawie zasobów Folder_Label_ResID. Ten zasób jest ładowany z pakietu VSPackage satelitarną bibliotekę DLL.  
  
 **Folderu** wartość reprezentuje identyfikator GUID folderu, w którym jest wyświetlany węzeł Folder_Label_ResID. W tym przykładzie reprezentuje identyfikator GUID **inne projekty** folderu w **typów projektów** okienku **nowy projekt** okno dialogowe. Jeśli **inne projekty** wartość jest nieobecne, etykieta znajduje się na najwyższym poziomie.  
  
 Wartość TemplatesDir Określa pełną ścieżkę katalogu, który zawiera szablony projektów. Te pliki mogą być plików .vsz lub pliki szablonów typowe można sklonować.  
  
 Jeśli określisz TemplatesLocalizedSubDir, musi ona identyfikator zasobu ciągu, który nazwy podkatalogu TemplatesDir, który zawiera zlokalizowane szablony. Ponieważ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ładuje zasobu ciągu z satelitarną bibliotekę DLL Jeśli nie masz, każdy satelitarną bibliotekę DLL mogą zawierać nazwę podkatalogu innej. Wartość SortPriority określa priorytet sortowania.  
  
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
 [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Dodawanie elementów do Dodaj nowy element okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

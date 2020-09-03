---
title: Współtworzenie nowego elementu — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197021"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Dodawanie elementów do okna dialogowego Dodawanie nowego elementu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projektu może zapewnić kompletny nowy katalog elementów dla okna dialogowego **Dodaj nowy element** przez zarejestrowanie szablonów **dodawania elementów** w `Projects` podkluczu rejestru.  
  
## <a name="registering-add-new-item-templates"></a>Rejestrowanie szablonów dodawania nowych elementów  
 Ta sekcja znajduje się w obszarze **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\Projects** w rejestrze. W poniższych wpisach rejestru przyjęto założenie, że [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekt jest agregowany przez hipotetyczny podtyp projektu. Poniżej przedstawiono wpisy dla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektu.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 `AddItemTemplates\TemplateDirs`Podklucz zawiera wpisy rejestru ze ścieżką do katalogu, w którym są umieszczane elementy udostępniane w oknie dialogowym **Dodaj nowy element** .  
  
 Środowisko automatycznie ładuje wszystkie `AddItemTemplates` dane w `Projects` podkluczu rejestru. Może to obejmować dane dla podstawowych implementacji projektu, a także dane dla konkretnych typów podtypów projektu. Każdy podtyp projektu jest identyfikowany przez typ projektu `GUID` . Podtyp projektu może określać, że alternatywny zestaw `Add Item` szablonów powinien być używany dla określonego wystąpienia projektu, obsługując `VSHPROPID_ AddItemTemplatesGuid` Wyliczenie z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementacji w celu zwrócenia wartości identyfikatora GUID podtypu projektu. Jeśli `VSHPROPID_AddItemTemplatesGuid` Właściwość nie jest określona, używany jest podstawowy identyfikator GUID projektu.  
  
 Można filtrować elementy w oknie dialogowym **Dodaj nowy element** przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfejsu w obiekcie agregatora podtypów projektu. Na przykład podtyp projektu, który implementuje projekt bazy danych przez agregowanie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektu, może odfiltrować [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] określone elementy w oknie dialogowym **Dodaj nowy element** przez zaimplementowanie filtrowania, a z kolei może dodać elementy specyficzne dla projektu bazy danych przez obsługę `VSHPROPID_ AddItemTemplatesGuid` w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Aby uzyskać więcej informacji o filtrowaniu i dodawaniu elementów do okna dialogowego **Dodaj nowy element** , zobacz [Dodawanie elementów do okien dialogowych Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

---
title: Współtworzenie dialogowego Dodawanie nowego elementu | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762373"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Dodawanie elementów do okna dialogowego Dodawanie nowego elementu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtypu projektu może zapewnić pełną nowy katalog elementów dla **Dodaj nowy element** okno dialogowe, rejestrując **elementu Dodawanie** szablonów w ramach `Projects` podklucza rejestru.  
  
## <a name="registering-add-new-item-templates"></a>Rejestrowanie szablonów Dodaj nowy element  
 W tej sekcji znajduje się w folderze **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** w rejestrze. Wpisy rejestru poniżej założono [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektu agregowane przez podtypu projektu hipotetycznych. Wpisy dla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektu są wymienione poniżej.  
  
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
  
 `AddItemTemplates\TemplateDirs` Podklucz zawiera wpisy rejestru ścieżką do katalogu, gdzie elementy udostępnione w **Dodaj nowy element** znajdują się okno dialogowe.  
  
 Środowisko automatycznie ładuje wszystkie `AddItemTemplates` danych w ramach `Projects` podklucza rejestru. Może to obejmować dane dla implementacji projektu podstawowego, a także dane dla określonego projektu podtyp typów. Każdy podtypu projektu jest identyfikowany przez typ projektu `GUID`. Podtypu projektu można określić, czy alternatywnego zestaw `Add Item` sposób użycia szablonów dla wystąpienia określonego projektu przeznaczonego dzięki obsłudze `VSHPROPID_ AddItemTemplatesGuid` wyliczenie z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementacji do zwrócenia identyfikatora GUID wartość podtypu projektu. Jeśli `VSHPROPID_AddItemTemplatesGuid` właściwość nie jest określona, jest używany identyfikator GUID projektu podstawowego.  
  
 Możesz filtrować elementy w **Dodaj nowy element** okno dialogowe, implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfejsu na obiekt agregatora podtypu projektu. Na przykład podtypem projektu, który implementuje projekt bazy danych przez agregowanie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektu, można filtrować [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] określonych elementów z **Dodaj nowy element** Włącz okno dialogowe, implementując, filtrowanie i w, można dodać Baza danych określone elementy projektu dzięki obsłudze `VSHPROPID_ AddItemTemplatesGuid` w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Aby uzyskać więcej informacji na temat filtrowania i dodawanie elementów do **Dodaj nowy element** okno dialogowe, zobacz [Dodawanie elementów do dodawania nowego elementu okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

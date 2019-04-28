---
title: Współtworzenie dialogowego Dodawanie nowego elementu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77008b6a4403270c77e24607fc0f4f6f4456296e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861555"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Współtworzenie w oknie dialogowym Dodaj nowy element
Podtypu projektu może zapewnić pełną nowy katalog elementów dla **Dodaj nowy element** okno dialogowe, rejestrując **elementu Dodawanie** szablonów w ramach **projektów** podklucza rejestru.

## <a name="register-add-new-item-templates"></a>Rejestrowanie szablonów Dodaj nowy element
 W tej sekcji znajduje się w folderze **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** w rejestrze. Wpisy rejestru poniżej założono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu agregowane przez podtypu projektu hipotetycznych. Wpisy dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu są wymienione poniżej.

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

 **AddItemTemplates\TemplateDirs** podklucz zawiera wpisy rejestru ścieżką do katalogu, gdzie elementy udostępnione w **Dodaj nowy element** znajdują się okno dialogowe.

 Środowisko automatycznie ładuje wszystkie **AddItemTemplates** danych w ramach **projektów** podklucza rejestru. Te dane mogą obejmować dane dla implementacji projektu podstawowego, a także dane dla określonego projektu podtyp typów. Każdy podtypu projektu jest identyfikowany przez typ projektu **GUID**. Podtypu projektu można określić, czy alternatywnego zestaw **elementu Dodawanie** sposób użycia szablonów dla wystąpienia określonego projektu przeznaczonego dzięki obsłudze `VSHPROPID_ AddItemTemplatesGuid` wyliczenie z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementacja zwraca wartość identyfikatora GUID podtypu projektu. Jeśli `VSHPROPID_AddItemTemplatesGuid` właściwość nie jest określona, jest używany identyfikator GUID projektu podstawowego.

 Możesz filtrować elementy w **Dodaj nowy element** okno dialogowe, implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfejsu na obiekt agregatora podtypu projektu. Na przykład podtypem projektu, który implementuje projekt bazy danych przez agregowanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu, można filtrować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] określonych elementów z **Dodaj nowy element** Włącz okno dialogowe, implementując, filtrowanie i w, można dodać bazy danych elementów specyficznych dla projektu dzięki obsłudze `VSHPROPID_ AddItemTemplatesGuid` w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Aby uzyskać więcej informacji na temat filtrowania i dodawanie elementów do **Dodaj nowy element** okno dialogowe, zobacz [Dodawanie elementów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Identyfikatorów CatID obiektów, które zwykle służą do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
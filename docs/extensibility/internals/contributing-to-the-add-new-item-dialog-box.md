---
title: Współtworzenie okna dialogowego Dodawanie nowego elementu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709274"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Współtworzenie w oknie dialogowym Dodawanie nowego elementu
Podtyp projektu może dostarczyć kompletny nowy katalog elementów dla okna dialogowego **Dodawanie nowego elementu,** rejestrując szablony **dodaj element** w podkluczietu rejestru **Projekty.**

## <a name="register-add-new-item-templates"></a>Zarejestruj szablony dodaj nowy element
 Ta sekcja znajduje się w **obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** w rejestrze. Poniższe wpisy rejestru [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zakładają, że projekt jest agregowany przez hipotetyczny podtyp projektu. Wpisy dotyczące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu są wymienione poniżej.

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

 Podklucz **AddItemTemplates\TemplateDirs** zawiera wpisy rejestru ze ścieżką do katalogu, w którym są umieszczane elementy udostępnione w oknie dialogowym **Dodawanie nowego elementu.**

 Środowisko automatycznie ładuje wszystkie **dane AddItemTemplates** w podkluczu rejestru **Projekty.** Dane te mogą obejmować dane dla podstawowych implementacji projektu, a także dane dla określonych typów podtypu projektu. Każdy podtyp projektu jest identyfikowany za pomocą identyfikatora **GUID**typu projektu . Podtyp projektu można określić, że alternatywny zestaw **szablonów Dodaj element** powinien być `VSHPROPID_ AddItemTemplatesGuid` używany dla określonego <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> wystąpienia projektu smakowego, obsługując wyliczenie z implementacji w celu zwrócenia wartości GUID podtypu projektu. Jeśli `VSHPROPID_AddItemTemplatesGuid` właściwość nie jest określona, używany jest identyfikator GUID projektu podstawowego.

 Elementy można filtrować w oknie dialogowym Dodawanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> **nowego** elementu, implementując interfejs w obiekcie agregatora podtypu projektu. Na przykład podtyp projektu, który implementuje projekt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bazy danych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez agregowanie projektu, może filtrować określone elementy z okna dialogowego **Dodawanie nowego** `VSHPROPID_ AddItemTemplatesGuid` elementu, implementując filtrowanie, a z kolei można dodać elementy specyficzne dla projektu bazy danych, obsługując w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>programie . Aby uzyskać więcej informacji na temat filtrowania i dodawania elementów do okna **dialogowego Dodawanie nowego elementu,** zobacz [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Catidy dla obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

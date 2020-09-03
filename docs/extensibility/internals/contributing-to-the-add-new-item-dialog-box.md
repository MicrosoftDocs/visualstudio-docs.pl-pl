---
title: Współtworzenie nowego elementu — okno dialogowe | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709274"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Współtworzenie nowego elementu — okno dialogowe
Podtyp projektu może zapewnić kompletny nowy katalog elementów dla okna dialogowego **Dodaj nowy element** przez zarejestrowanie szablonów **dodawania elementów** w podkluczu rejestru **projekty** .

## <a name="register-add-new-item-templates"></a>Zarejestruj szablony dodawania nowych elementów
 Ta sekcja znajduje się w obszarze **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\Projects** w rejestrze. W poniższych wpisach rejestru przyjęto założenie, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekt jest agregowany przez hipotetyczny podtyp projektu. Poniżej przedstawiono wpisy dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu.

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

 Podklucz **AddItemTemplates\TemplateDirs** zawiera wpisy rejestru ze ścieżką do katalogu, w którym są umieszczane elementy udostępniane w oknie dialogowym **Dodaj nowy element** .

 Środowisko automatycznie ładuje wszystkie dane **AddItemTemplates** w podkluczu rejestru **projects** . Te dane mogą zawierać dane dla podstawowych implementacji projektu, a także dane dla konkretnych typów podtypów projektu. Każdy podtyp projektu jest identyfikowany przez **Identyfikator GUID**typu projektu. Podtyp projektu może określić, że alternatywny zestaw szablonów **dodawania elementów** ma być używany dla określonego wystąpienia projektu, obsługując `VSHPROPID_ AddItemTemplatesGuid` Wyliczenie z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementacji w celu zwrócenia wartości identyfikatora GUID podtypu projektu. Jeśli `VSHPROPID_AddItemTemplatesGuid` Właściwość nie jest określona, zostanie użyty podstawowy identyfikator GUID projektu.

 Można filtrować elementy w oknie dialogowym **Dodaj nowy element** przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfejsu w obiekcie agregatora podtypów projektu. Na przykład podtyp projektu, który implementuje projekt bazy danych przez agregowanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu, może odfiltrować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] określone elementy w oknie dialogowym **Dodaj nowy element** przez zaimplementowanie filtrowania, a z kolei może dodać elementy specyficzne dla projektu bazy danych przez obsługę `VSHPROPID_ AddItemTemplatesGuid` w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Aby uzyskać więcej informacji o filtrowaniu i dodawaniu elementów do okna dialogowego **Dodaj nowy element** , zobacz [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID dla obiektów, które są zwykle używane do rozszerania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

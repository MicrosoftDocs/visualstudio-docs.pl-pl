---
title: Filtrowanie okna dialogowego dla zagnieżdżonych projektów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538099"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrowanie okna dialogowego Dodawanie elementu dla projektów zagnieżdżonych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po wyświetleniu **AddItem** okno dialogowe dla projektu zagnieżdżonego projekt nadrzędny można kontrolować, jakie mają być wyświetlane w oknie dialogowym.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Interfejs umożliwia filtrowanie węzłów, które będą znajdować się w **AddItem** okno dialogowe. Jeśli projekt podrzędny Wyświetla **AddItem** okno dialogowe nadrzędny można zaimplementować `IVsFilterAddProjectItemDlg` interfejsu i filtrowanie elementów, które w przeciwnym razie będzie wyświetlana w projekcie elementu podrzędnego.  
  
 Gdy projekty są pogrupowane według funkcji w ramach projektów konkretny nadrzędny, można zaimplementować `IVsFilterAddProjectItemDlg` gdy użytkownik wybierze **elementu Dodawanie projektu** menu skrótów w projekcie zagnieżdżonych. Implementowanie `IvsFilterAddProjectItemDlg displays` tylko projekt elementy lub pliki specyficzne dla tej grupy. Elementy projektu dla innych grup są odfiltrowywane z okno dialogowe, nawet jeśli są one przechowywane w tym samym katalogu.  
  
 Gdy użytkownik uruchomi **AddItem** okno dialogowe podrzędnego implementacji projektu nadrzędnego `IVsFilterAddProjectItemDlg` nosi nazwę interfejsu.  
  
 `IVsFilterAddProjectItemDlg` Interfejsu można też wdrożyć filtrowanie według kategorii. Aby uzyskać więcej informacji, zobacz [Dodawanie elementów do dodawania nowego elementu okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) i [szablonów elementów i projektów rejestrowanie](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Dodawanie elementów do Dodaj nowy element okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)

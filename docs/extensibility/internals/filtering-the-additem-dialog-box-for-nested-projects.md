---
title: Filtrowanie okna dialogowego dla zagnieżdżonych projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8537cb9422639dcf815d7ebe46244e77729d114f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942597"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrowanie okna dialogowego AddItem dla zagnieżdżonych projektów
Po wyświetleniu **AddItem** okno dialogowe dla projektu zagnieżdżonego projekt nadrzędny można kontrolować, jakie mają być wyświetlane w oknie dialogowym.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Interfejs umożliwia filtrowanie węzłów, które będą znajdować się w **AddItem** okno dialogowe. Jeśli projekt podrzędny Wyświetla **AddItem** okno dialogowe nadrzędny można zaimplementować `IVsFilterAddProjectItemDlg` interfejsu i filtrowanie elementów, które w przeciwnym razie będzie wyświetlana w projekcie elementu podrzędnego.  
  
 Gdy projekty są pogrupowane według funkcji w ramach projektów konkretny nadrzędny, można zaimplementować `IVsFilterAddProjectItemDlg` gdy użytkownik wybierze **elementu Dodawanie projektu** menu skrótów w projekcie zagnieżdżonych. Implementowanie `IvsFilterAddProjectItemDlg displays` tylko projekt elementy lub pliki specyficzne dla tej grupy. Elementy projektu dla innych grup są odfiltrowywane z okno dialogowe, nawet jeśli są one przechowywane w tym samym katalogu.  
  
 Gdy użytkownik uruchomi **AddItem** okno dialogowe podrzędnego implementacji projektu nadrzędnego `IVsFilterAddProjectItemDlg` nosi nazwę interfejsu.  
  
 `IVsFilterAddProjectItemDlg` Interfejsu można też wdrożyć filtrowanie według kategorii. Aby uzyskać więcej informacji, zobacz [Dodawanie elementów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) i [rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Dodawanie elementów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)
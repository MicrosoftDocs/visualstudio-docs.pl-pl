---
title: Filtrowanie okna dialogowego AddItem dla zagnieżdżonych projektów | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538099"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrowanie okna dialogowego Dodawanie elementu dla projektów zagnieżdżonych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po wyświetleniu okna dialogowego **AddItem** dla projektu zagnieżdżonego, projekt nadrzędny może kontrolować elementy, które są wyświetlane w oknie dialogowym.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>Interfejs umożliwia filtrowanie węzłów, które będą znajdować się w oknie dialogowym **AddItem** . Gdy projekt podrzędny wyświetla okno dialogowe **AddItem** , obiekt nadrzędny może zaimplementować `IVsFilterAddProjectItemDlg` interfejs i filtrować elementy, które w przeciwnym razie będą wyświetlane w projekcie elementu podrzędnego.  
  
 Gdy projekty są pogrupowane według funkcji w ramach określonych projektów nadrzędnych, można zaimplementować, `IVsFilterAddProjectItemDlg` gdy użytkownik wybierze **pozycję Dodaj element projektu** w menu skrótów w zagnieżdżonym projekcie. Implementowanie `IvsFilterAddProjectItemDlg displays` tylko elementów projektu lub plików specyficznych dla tej grupy. Elementy projektu dla innych grup są odfiltrowane z okna dialogowego, nawet jeśli są przechowywane w tym samym katalogu.  
  
 Gdy użytkownik otwiera okno dialogowe **AddItem** dla elementu podrzędnego, jest wywoływana implementacja projektu nadrzędnego `IVsFilterAddProjectItemDlg` interfejsu.  
  
 `IVsFilterAddProjectItemDlg`Interfejs może również zaimplementować filtrowanie według kategorii. Aby uzyskać więcej informacji, zobacz [Dodawanie elementów do okien dialogowych Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) i [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Dodawanie elementów do okien dialogowych Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Rejestrowanie szablonów projektu i elementu](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)

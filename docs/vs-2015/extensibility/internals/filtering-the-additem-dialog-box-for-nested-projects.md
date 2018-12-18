---
title: Filtrowanie okna dialogowego dla zagnieżdżonych projektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 363ba8e38ae2de445bd18bb9378d48aa4d824298
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769762"
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


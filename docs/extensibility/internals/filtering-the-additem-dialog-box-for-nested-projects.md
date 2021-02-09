---
title: Filtrowanie okna dialogowego AddItem dla zagnieżdżonych projektów | Microsoft Docs
description: Dowiedz się, jak filtrować okno dialogowe AddItem dla projektu zagnieżdżonego w programie Visual Studio przez implementację interfejsu IVsFilterAddProjectItemDlg projektu nadrzędnego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 668a1c3bae34caa2dc6a12def2bcee56765adbb1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886954"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrowanie okna dialogowego AddItem dla zagnieżdżonych projektów
Po wyświetleniu okna dialogowego **AddItem** dla projektu zagnieżdżonego, projekt nadrzędny może kontrolować elementy, które są wyświetlane w oknie dialogowym.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>Interfejs umożliwia filtrowanie węzłów, które będą znajdować się w oknie dialogowym **AddItem** . Gdy projekt podrzędny wyświetla okno dialogowe **AddItem** , obiekt nadrzędny może zaimplementować `IVsFilterAddProjectItemDlg` interfejs i filtrować elementy, które w przeciwnym razie będą wyświetlane w projekcie elementu podrzędnego.

 Gdy projekty są pogrupowane według funkcji w ramach określonych projektów nadrzędnych, można zaimplementować, `IVsFilterAddProjectItemDlg` gdy użytkownik wybierze **pozycję Dodaj element projektu** w menu skrótów w zagnieżdżonym projekcie. Implementowanie `IvsFilterAddProjectItemDlg displays` tylko elementów projektu lub plików specyficznych dla tej grupy. Elementy projektu dla innych grup są odfiltrowane z okna dialogowego, nawet jeśli są przechowywane w tym samym katalogu.

 Gdy użytkownik otwiera okno dialogowe **AddItem** dla elementu podrzędnego, jest wywoływana implementacja projektu nadrzędnego `IVsFilterAddProjectItemDlg` interfejsu.

 `IVsFilterAddProjectItemDlg`Interfejs może również zaimplementować filtrowanie według kategorii. Aby uzyskać więcej informacji, zobacz [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) i [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Dodaj elementy do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Rejestruj szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)

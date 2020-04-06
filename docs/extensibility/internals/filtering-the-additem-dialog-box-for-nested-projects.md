---
title: Filtrowanie okna dialogowego AddItem dla projektów zagnieżdżonych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708383"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrowanie okna dialogowego AddItem dla projektów zagnieżdżonych
Po wyświetleniu okna dialogowego **AddItem** dla projektu zagnieżdżonego projekt nadrzędny może kontrolować, jakie elementy są wyświetlane w oknie dialogowym.

 Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> umożliwia filtrowanie węzłów, które będą w oknie dialogowym **AddItem.** Gdy projekt podrzędny wyświetla Okno dialogowe **AddItem,** element nadrzędny można zaimplementować `IVsFilterAddProjectItemDlg` interfejs i filtr elementów, które w przeciwnym razie byłyby wyświetlane w projekcie podrzędnym.

 Gdy projekty są pogrupowane według funkcji w `IVsFilterAddProjectItemDlg` ramach określonych projektów nadrzędnych, można zaimplementować, gdy użytkownik wybierze **Dodaj element projektu** w menu skrótów w projekcie zagnieżdżonego. Implementowanie `IvsFilterAddProjectItemDlg displays` tylko elementów projektu lub plików specyficznych dla tej grupy. Elementy projektu dla innych grup są filtrowane z okna dialogowego, nawet jeśli są przechowywane w tym samym katalogu.

 Gdy użytkownik otworzy okno dialogowe **AddItem** dla dziecka, wywoływana `IVsFilterAddProjectItemDlg` jest implementacja interfejsu przez projekt nadrzędny.

 Interfejs `IVsFilterAddProjectItemDlg` można również zaimplementować filtrowanie według kategorii. Aby uzyskać więcej informacji, zobacz [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) i [rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Rejestrowanie szablonów projektów i towarów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Projekty nest](../../extensibility/internals/nesting-projects.md)

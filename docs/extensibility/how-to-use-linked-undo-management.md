---
title: 'Instrukcje: Za pomocą przystawki Zarządzanie połączonego cofania | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f11ea8e93d7d952f28315481f65149122a7b68a3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63415584"
---
# <a name="how-to-use-linked-undo-management"></a>Instrukcje: Za pomocą przystawki Zarządzanie połączonego cofania
Połączonego cofania umożliwia użytkownikowi Cofnij równocześnie w tej samej zmiany w wielu plikach. Na przykład zmiany w tekście jednoczesnych na wiele plików programów, takich jak plik nagłówkowy i plik Visual C++ jest transakcji połączonego cofania. Funkcja połączonego cofania jest wbudowana w implementacji środowiska menedżera cofania i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> umożliwia manipulowanie tej możliwości. Połączonego cofania jest implementowany przez nadrzędnej jednostki cofania, który można połączyć cofania osobnych stosów ze sobą, aby być traktowane jako jednostka pojedynczą czynność cofnięcia. W poniższej sekcji opisano szczegółowo procedurę za pomocą połączonego cofania.

## <a name="to-use-linked-undo"></a>Aby użyć połączonego cofania

1. Wywołaj `QueryService` na `SVsLinkedUndoManager` uzyskać wskaźnik do `IVsLinkedUndoTransactionManager`.

2. Tworzenie początkowej nadrzędnej jednostki połączonego cofania, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Spowoduje to punkt początkowy dla zestawu cofnięcie stosów mają być grupowane w stosy połączonego cofania. W `OpenLinkedUndo` metody należy również określić, czy połączonego cofania strict lub nieścisłym. Zachowanie non-strict połączonego cofania oznacza, że zamknąć niektóre dokumenty z połączonego cofania elementów równorzędnych i nadal pozostanie innych połączone cofanie elementów równorzędnych na ich stosów. Zachowanie Strict połączonego cofania Określa, że można cofnąć, razem lub w ogóle nie wszystkie stosy element równorzędny połączonego cofania. Dodaj kolejne połączone cofnięcie stosów, wywołując [IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) metody.

3. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> konieczne przywrócenie początkowej kopii wszystkich jednostek połączonego cofania jako jeden.

    > [!NOTE]
    > Aby zaimplementować Zarządzanie połączonego cofania w edytorze, Dodaj zarządzania cofania. Aby uzyskać więcej informacji dotyczących implementowania połączonego cofania zarządzania, zobacz [jak: Implementowanie zarządzania cofania](../extensibility/how-to-implement-undo-management.md).

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>
- [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)
- [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)
- [Instrukcje: Implementowanie cofania zarządzania](../extensibility/how-to-implement-undo-management.md)
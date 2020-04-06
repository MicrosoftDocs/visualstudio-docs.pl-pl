---
title: Lista obiektów okna właściwości | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706147"
---
# <a name="properties-window-object-list"></a>Lista obiektów okna właściwości
Lista obiektów w oknie **Właściwości** jest listą rozwijaną, która umożliwia zmianę zaznaczenia na inne obiekty dostępne w jednym lub kilku zaznaczonych oknach. Wybranie innego obiektu z tej listy powoduje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> wywołanie, aby poinformować środowisko, że nowy obiekt został wybrany. Informacje wyświetlane w oknie **Właściwości** są następnie zmieniane w celu wyświetlenia właściwości skojarzonych z nowo wybranym obiektem.

## <a name="the-object-list"></a>Lista obiektów
 Lista obiektów składa się z dwóch pól: nazwy obiektu (wyświetlanej pogrubioną czcionką) i typu obiektu.

 Nazwa obiektu wyświetlana po lewej stronie typu obiektu pogrubioną `Name` czcionką jest <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> pobierana z samego obiektu przy użyciu właściwości dostarczonej przez interfejs. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, jedyna metoda <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>na <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> , zwraca dla tego interfejsu coclass. Okno **Właściwości** <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> używa, aby uzyskać nazwę coclass, który jest wyświetlany jako nazwa obiektu na liście rozwijanej.

 Jeśli obiekt nie ma `Name` właściwości, nazwa nie jest wyświetlana w obszarze Nazwa listy obiektów. Można dodać Name właściwości do obiektu, jeśli chcesz nazwę wyświetlaną na liście obiektów.

 Jeśli obiekt COM nie <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>implementuje, w oknie **Właściwości** zostanie wyświetlona nazwa interfejsu zamiast nazwy obiektu po lewej stronie listy.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)

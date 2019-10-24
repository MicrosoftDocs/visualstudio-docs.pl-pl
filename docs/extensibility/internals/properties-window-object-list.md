---
title: Lista obiektów okna właściwości | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e50b3fe46edb8d14cad9a03a45bc8650cb9713ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725187"
---
# <a name="properties-window-object-list"></a>Lista obiektów okna właściwości
Lista obiektów w oknie **Właściwości** jest listą rozwijaną, która umożliwia zmianę zaznaczenia na inne obiekty dostępne w jednym lub kilku wybranych oknach. Wybranie innego obiektu z tej listy wyzwala wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>, aby poinformować środowisko o wybranym nowym obiekcie. Informacje wyświetlane w oknie **Właściwości** są następnie zmieniane, aby pokazać właściwości skojarzone z nowo wybranym obiektem.

## <a name="the-object-list"></a>Lista obiektów
 Lista obiektów składa się z dwóch pól: nazwę obiektu (wyświetlaną pogrubioną czcionką) i typ obiektu.

 Nazwa obiektu wyświetlana po lewej stronie typu obiektu w pogrubieniu jest pobierana z samego obiektu za pomocą właściwości `Name` dostarczonej przez interfejs <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>jedyną metodą <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, zwraca <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> dla klasy coclass tego interfejsu. Okno **Właściwości** używa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, aby uzyskać nazwę klasy coclass, która jest wyświetlana jako nazwa obiektu na liście rozwijanej.

 Jeśli obiekt nie ma właściwości `Name`, nazwa nie zostanie wyświetlona w obszarze Nazwa listy obiektów. Możesz dodać właściwość Name do obiektu, jeśli chcesz, aby nazwa była wyświetlana na liście obiektów.

 Jeśli obiekt COM nie implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, w oknie **Właściwości** zostanie wyświetlona nazwa interfejsu w miejscu nazwy obiektu po lewej stronie listy.

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
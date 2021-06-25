---
title: Lista obiektów okna właściwości | Microsoft Docs
description: Dowiedz się więcej o interfejsach używanych do interakcji z listą obiektów w okno Właściwości w Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 908acf3f8ecad390266c3d085778dc13077a6fa8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903440"
---
# <a name="properties-window-object-list"></a>Lista obiektów okna właściwości
Lista obiektów w **oknie** Właściwości jest listą rozwijaną, która umożliwia zmianę wyboru na inne obiekty dostępne w co najmniej jednym wybranym oknie. Wybranie innego obiektu z tej listy wyzwala wywołanie do , aby poinformować środowisko, że nowy obiekt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> został wybrany. Informacje wyświetlane w **oknie Właściwości** są następnie zmieniane w celu wyświetlania właściwości skojarzonych z nowo wybranym obiektem.

## <a name="the-object-list"></a>Lista obiektów
 Lista obiektów składa się z dwóch pól: nazwy obiektu (wyświetlanego pogrubioną czcionką) i typu obiektu.

 Nazwa obiektu wyświetlana po lewej stronie typu obiektu pogrubiona jest pobierana z samego obiektu przy użyciu właściwości `Name` dostarczonej przez <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interfejs. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, jedyną metodą w <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> metodzie , jest <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> zwracana dla klasy coclass tego interfejsu. W **oknie** Właściwości jest używana nazwa klasy coclass, która jest wyświetlana jako nazwa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> obiektu na liście rozwijanej.

 Jeśli obiekt nie ma właściwości, nazwa nie jest wyświetlana w `Name` obszarze Nazwa listy obiektów. Możesz dodać właściwość Name do obiektu , jeśli chcesz, aby nazwa wyświetlana na liście obiektów.

 Jeśli obiekt COM nie implementuje obiektu , w oknie Właściwości wyświetlana jest nazwa interfejsu w miejsce nazwy obiektu po lewej <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> stronie listy. 

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)

---
title: Lista obiektów okna właściwości | Microsoft Docs
description: Dowiedz się więcej o interfejsach używanych do współdziałania z listą obiektów w okno Właściwości w środowisku IDE programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 489ea25e0b06ab69650d4b48a306483945b34598
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060981"
---
# <a name="properties-window-object-list"></a>Lista obiektów okna właściwości
Lista obiektów w oknie **Właściwości** jest listą rozwijaną, która umożliwia zmianę zaznaczenia na inne obiekty dostępne w jednym lub kilku wybranych oknach. Wybranie innego obiektu z tej listy wyzwala wywołanie do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> powiadomienia o środowisku, w którym został wybrany nowy obiekt. Informacje wyświetlane w oknie **Właściwości** są następnie zmieniane, aby pokazać właściwości skojarzone z nowo wybranym obiektem.

## <a name="the-object-list"></a>Lista obiektów
 Lista obiektów składa się z dwóch pól: nazwę obiektu (wyświetlaną pogrubioną czcionką) i typ obiektu.

 Nazwa obiektu wyświetlana po lewej stronie typu obiektu w pogrubieniu jest pobierana z samego obiektu przy użyciu `Name` Właściwości dostarczonej przez <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interfejs. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, jedyną metodą dla <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , zwraca wartość <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> dla klasy coclass tego interfejsu. Okno **Właściwości** używa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> do uzyskania nazwy klasy coclass, która jest wyświetlana jako nazwa obiektu na liście rozwijanej.

 Jeśli obiekt nie ma `Name` właściwości, nazwa nie jest wyświetlana w obszarze Nazwa listy obiektów. Możesz dodać właściwość Name do obiektu, jeśli chcesz, aby nazwa była wyświetlana na liście obiektów.

 Jeśli obiekt COM nie jest zaimplementowany <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , w oknie **Właściwości** zostanie wyświetlona nazwa interfejsu zamiast nazwy obiektu po lewej stronie listy.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)

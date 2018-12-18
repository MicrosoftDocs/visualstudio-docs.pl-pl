---
title: Lista obiektów okna właściwości | Dokumentacja firmy Microsoft
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
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bbb9153a216b2d2fcc7cdeba0399aa60fc73881e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768908"
---
# <a name="properties-window-object-list"></a>Lista obiektów okna właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lista obiektów w **właściwości** okno jest listy umożliwia zmianę zaznaczenia do innych obiektów, które są dostępne w ramach jednego lub kilku wybranych okien. Wybierając inny obiekt na tej liście wyzwala wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> poinformować środowiska wybrano nowego obiektu. Informacje wyświetlane w **właściwości** okna jest następnie zmieniane, aby wyświetlić właściwości skojarzone z nowo wybrany obiekt.  
  
## <a name="the-object-list"></a>Lista obiektów  
 Lista obiektów składa się z dwóch pól: Nazwa obiektu (wyświetlone czcionką pogrubioną) i typ obiektu.  
  
 Nazwa obiektu wyświetlany po lewej stronie, typu obiektu wytłuszczonym drukiem jest pobierana z samego obiektu przy użyciu `Name` podana przez właściwość <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interfejsu. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, jedyną metodą na <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, zwraca <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> dla klasy coclass tego interfejsu. **Właściwości** okno używa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> można pobrać nazwy klasy coclass, który jest wyświetlany jako nazwa obiektu na liście rozwijanej.  
  
 Jeśli obiekt nie ma `Name` właściwości, nazwa nie jest wyświetlana w obszarze nazwy listy obiektów. Jeśli chcesz, aby nazwa wyświetlana na liście obiektów, można dodać do obiektu Właściwość Name.  
  
 Jeśli obiekt COM nie implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **właściwości** okna wyświetla nazwę interfejsu zamiast nazwy obiektu po lewej stronie listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)


---
title: Ukrywanie właściwości, które mają właściwości podrzędnej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822389"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ukrywanie właściwości, które mają właściwości podrzędnej
Czy chcesz ukryć właściwości, które mają właściwości podrzędnej:  
  
- Jeśli masz zagnieżdżonych projektów, gdzie projekt nadrzędny programowo określa niektóre aspekty projekt podrzędny.  
  
- Jeśli możesz użyć formantu przy użyciu wyspecjalizowanego projektanta i nie chcesz dają deweloperom pełny dostęp do wszystkich właściwości formantu.  
  
- Jeśli masz zakresie własności obiektu i chce ograniczyć widoku właściwości.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Aby ukryć właściwości, które mają właściwości podrzędnej  
  
1. Ustaw `pfDisplay` parametru w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> do `FALSE`.  
  
2. Ustaw `pfHide` parametru w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> do `TRUE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Siatka wyświetlania właściwości](../extensibility/internals/properties-display-grid.md)
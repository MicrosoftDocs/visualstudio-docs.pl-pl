---
title: Ukrywanie właściwości, które mają właściwości podrzędne | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822389"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ukrywanie właściwości, które mają właściwości podrzędne
Chcesz ukryć właściwości, które mają właściwości podrzędne:  
  
- Jeśli istnieją zagnieżdżone projekty, w których projekt nadrzędny programowo kontroluje niektóre aspekty projektu podrzędnego.  
  
- Jeśli używasz kontrolki z wyspecjalizowanym projektantem i nie chcesz, aby deweloperzy mogli uzyskać pełny dostęp do wszystkich właściwości formantu.  
  
- Jeśli masz prawo własności do zakresu obiektu i chcesz ograniczyć widok właściwości.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Aby ukryć właściwości, które mają właściwości podrzędne  
  
1. Ustaw `pfDisplay` parametr w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> na `FALSE` .  
  
2. Ustaw `pfHide` parametr w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> na `TRUE` .  
  
## <a name="see-also"></a>Zobacz też  
 [Siatka wyświetlania właściwości](../extensibility/internals/properties-display-grid.md)
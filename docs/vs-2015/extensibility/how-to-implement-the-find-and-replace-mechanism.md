---
title: 'Instrukcje: Implementowanie Znajdź i Zamień mechanizm | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548700"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Instrukcje: Implementowanie Znajdź i Zamień mechanizm
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio udostępnia dwa sposoby wdrażania Znajdź/Zamień. Jednym ze sposobów jest przekazać obraz tekstu do powłoki i pozwól mu obsługę wyszukiwania, wyróżniania i zastępowanie tekstu. Dzięki temu użytkownicy mogą określić wiele zakresów tekstu. Alternatywnie Twoje pakietu VSPackage można kontrolować ta sama funkcja. W obu przypadkach należy powiadomić powłoki o bieżący element docelowy i elementy docelowe wszystkie otwarte dokumenty.  
  
### <a name="to-implement-findreplace"></a>Aby zaimplementować Znajdź i Zamień  
  
1. Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfejsu na jednym z obiektów zwróconych przez właściwości ramki <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> lub <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Jeśli tworzysz niestandardowy edytor, powinien implementować ten interfejs jako część klasy edytora niestandardowego.  
  
2. Użyj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> metody, aby określić opcje, które obsługuje edytora i, aby wskazać, czy implementuje wyszukiwanie obrazów tekstu.  
  
     Jeśli Edytor obsługuje wyszukiwanie obrazów tekstu, należy zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     W przeciwnym razie zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3. W przypadku zaimplementowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> metody, można ułatwić wyszukiwanie zadań, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>

---
title: 'Instrukcje: implementowanie mechanizmu znajdowania i zamieniania | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548700"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Instrukcje: implementowanie mechanizmu znajdowania i zamieniania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio oferuje dwa sposoby implementowania wyszukiwania/zamieniania. Jednym ze sposobów jest przekazanie obrazu tekstu do powłoki i umożliwienie przeszukiwania, wyróżniania i zamiany tekstu. Dzięki temu użytkownicy mogą określić wiele zakresów tekstu. Alternatywnie, pakietu VSPackage może kontrolować tę funkcjonalność. W obu przypadkach należy powiadomić powłokę o bieżącym miejscu docelowym i obiektach docelowych dla wszystkich otwartych dokumentów.  
  
### <a name="to-implement-findreplace"></a>Aby zaimplementować Znajdowanie/zamienianie  
  
1. Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfejs na jednym z obiektów zwracanych przez właściwości ramki <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> lub <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> . Jeśli tworzysz Edytor niestandardowy, należy zaimplementować ten interfejs jako część niestandardowej klasy edytora.  
  
2. Użyj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> metody, aby określić opcje obsługiwane przez Edytor i wskazać, czy implementuje wyszukiwanie obrazów tekstowych.  
  
     Jeśli Edytor obsługuje wyszukiwanie obrazów tekstowych, zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> .  
  
     W przeciwnym razie Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> .  
  
3. W przypadku zaimplementowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> metod i można uprościć wyszukiwanie, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfejs.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>

---
title: 'Instrukcje: aktualizowanie paska stanu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703146"
---
# <a name="how-to-update-the-status-bar"></a>Instrukcje: aktualizowanie paska stanu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Pasek stanu** to pasek sterowania znajdujący się u dołu wielu okien aplikacji, który zawiera jeden lub więcej linii lub wskaźników tekstu stanu.  
  
### <a name="to-update-the-status-bar"></a>Aby zaktualizować pasek stanu  
  
1. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> każdy pojedynczy obiekt widoku (DocView), który zawiera edytor, taki jak widok formularza i widok kodu.  
  
2. Po wywołaniu IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> należy zaktualizować informacje na **pasku stanu** , wywołując metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > Środowisko IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> się tylko wtedy, gdy okno dokumentu jest początkowo aktywowane. W przypadku pozostałej części czasu aktywnego okna dokumentu należy zaktualizować informacje **paska stanu** w miarę zmiany stanu edytora.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 **Pasek stanu** zawiera cztery oddzielne pola:  
  
- Tekst stanu  
  
- Pasek postępu  
  
- Animowana ikona  
  
- Informacje o Edytorze  
  
  Aby uzyskać więcej informacji, zobacz [paski stanu](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  IDE automatycznie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementacji po aktywowaniu okna dokumentu.  
  
  Pakietu VSPackage implementujący jest odpowiedzialny za aktualizowanie tekstu stanu na pasku stanu. IDE resetuje ten ciąg do "gotowe", jeśli pole tekst stanu ma wartość pusty tekst ("") w czasie bezczynności.  
  
## <a name="see-also"></a>Zobacz też  
 [Paski stanu](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)

---
title: 'Porady: aktualizowanie pasek stanu | Dokumentacja firmy Microsoft'
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
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb70e8799b74f470a2216a63aae4637fe1872681
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768350"
---
# <a name="how-to-update-the-status-bar"></a>Porady: aktualizowanie paska stanu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Pasek stanu** pasek sterowania znajduje się w dolnej części wiele okien aplikacji, zawierający co najmniej jeden stan wierszy tekstu lub wskaźniki.  
  
### <a name="to-update-the-status-bar"></a>Aby zaktualizować paska stanu  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> dla każdego obiektu poszczególnych widoku (DocView), zapewniająca edytora, takie jak widok formularza i widoku kodu.  
  
2.  Kiedy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, zaktualizuj informacje w **pasek stanu** przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Wywołania środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> tylko kiedy okno dokumentu został początkowo uaktywniony. Pozostały okres czasu, który okna dokumentu jest aktywny, należy zaktualizować **pasek stanu** informacji jako stan zmiany edytora.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 A **pasek stanu** zawiera cztery oddzielne pola:  
  
- Tekst statusu  
  
- Pasek postępu  
  
- Animowaną ikonę  
  
- Edytor informacji  
  
  Aby uzyskać więcej informacji, zobacz [paski stanu](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  IDE automatycznie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metody usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> wdrożenia po uaktywnieniu okna dokumentu.  
  
  Implementujący pakietu VSPackage jest odpowiedzialny za aktualizowanie tekst statusu na pasku stanu. IDE resetuje ten ciąg na "GOTOWY", jeśli pole tekstowe stan jest ustawiony na pusty tekst ("") w czasie bezczynności.  
  
## <a name="see-also"></a>Zobacz też  
 [Paski stanu](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)


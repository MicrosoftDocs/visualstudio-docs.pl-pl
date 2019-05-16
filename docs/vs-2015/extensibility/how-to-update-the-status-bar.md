---
title: 'Instrukcje: Na pasku stanu aktualizacji | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703146"
---
# <a name="how-to-update-the-status-bar"></a>Instrukcje: Aktualizacja paska stanu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Pasek stanu** pasek sterowania znajduje się w dolnej części wiele okien aplikacji, zawierający co najmniej jeden stan wierszy tekstu lub wskaźniki.  
  
### <a name="to-update-the-status-bar"></a>Aby zaktualizować paska stanu  
  
1. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> dla każdego obiektu poszczególnych widoku (DocView), zapewniająca edytora, takie jak widok formularza i widoku kodu.  
  
2. Kiedy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, zaktualizuj informacje w **pasek stanu** przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    > Wywołania środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> tylko kiedy okno dokumentu został początkowo uaktywniony. Pozostały okres czasu, który okna dokumentu jest aktywny, należy zaktualizować **pasek stanu** informacji jako stan zmiany edytora.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 A **pasek stanu** zawiera cztery oddzielne pola:  
  
- Tekst statusu  
  
- Pasek postępu  
  
- Animowaną ikonę  
  
- Edytor informacji  
  
  Aby uzyskać więcej informacji, zobacz [paski stanu](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  IDE automatycznie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metody usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> wdrożenia po uaktywnieniu okna dokumentu.  
  
  Implementujący pakietu VSPackage jest odpowiedzialny za aktualizowanie tekst statusu na pasku stanu. IDE resetuje ten ciąg na "GOTOWY", jeśli pole tekstowe stan jest ustawiony na pusty tekst ("") w czasie bezczynności.  
  
## <a name="see-also"></a>Zobacz też  
 [Paski stanu](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)

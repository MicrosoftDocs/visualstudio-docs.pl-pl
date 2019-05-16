---
title: 'Instrukcje: Zarządzanie trybami edytora | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 71f3b5b2c910bbbd61607f9112122569e5d3562e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685606"
---
# <a name="how-to-manage-editor-modes"></a>Instrukcje: Zarządzanie trybami edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor kodu programu Visual Studio można wyświetlić w różnych trybów wyświetlania.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="enabling-full-screen-mode"></a>Włączenie trybu pełnego ekranu  
 Można wybrać ukryć wszystkie okna narzędzi i wyświetlić tylko okna dokumentu, należy włączyć **pełny ekran** trybu.  
  
#### <a name="to-enable-full-screen-mode"></a>Aby włączyć tryb pełnoekranowy  
  
- Naciśnij klawisze ALT + SHIFT + ENTER, aby wprowadzić lub zamknąć **pełny ekran** trybu.  
  
     --lub--  
  
- Należy wydać polecenie `View.Fullscreen` w **polecenia** okna.  
  
## <a name="enabling-virtual-space-mode"></a>Włączanie tryb obszaru wirtualnego  
 W **wirtualną przestrzenią** tryb, spacje są dodawane na końcu każdego wiersza kodu. Wybierz tę opcję, aby umieść komentarze w momencie spójne obok kodu.  
  
#### <a name="to-enable-virtual-space-mode"></a>Aby włączyć tryb obszaru wirtualnego  
  
1. Wybierz **opcje** z **narzędzia** menu.  
  
2. Rozwiń **edytora tekstów** folderu i wybierz polecenie **wszystkie języki** globalnie Ustaw tę opcję, lub wybierz folder, do określonego języka. (Na przykład, aby włączyć numery wierszy tylko w języku Visual Basic, wybierz podstawowe, Opcje edytora tekstowego.)  
  
3. Wybierz **ogólne** opcje, a następnie w obszarze **ustawienia**, wybierz opcję **włączyć wirtualną przestrzenią**.  
  
    > [!NOTE]
    > **Wirtualna przestrzeń** jest włączone w **wybór kolumn** trybu. Gdy **wirtualną przestrzenią** nie jest włączony tryb punkt wstawiania przenoszony z końca jeden wiersz bezpośrednio do pierwszego znaku w następnym.  
  
## <a name="see-also"></a>Zobacz też  
 [Dopasowywanie edytora](../ide/customizing-the-editor.md)   
 [Instrukcje: Aranżowanie i dokowanie Windows](../misc/how-to-arrange-and-dock-windows.md)   
 [Czcionki i kolory, Środowisko, Opcje — okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)

---
title: 'Instrukcje: Edytowanie wartości rejestru | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0ea1e932f7651439dcb9a1ff85094bd30e5239bb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116169"
---
# <a name="how-to-edit-a-register-value"></a>Instrukcje: Edytowanie wartości rejestru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno rejestrów jest dostępna tylko wtedy, gdy debugowanie na poziomie adresów jest włączone w **opcje** okno dialogowe **debugowanie** węzła.  
  
### <a name="to-change-the-value-of-a-register"></a>Aby zmienić wartość rejestru  
  
1. W **rejestruje** okna, użyj klawisza TAB lub myszy do wstawiania wskaż wartość, aby zmienić. Po rozpoczęciu wpisywania kursor musi znajdować się przed wartością, którą chcesz zastąpić.  
  
2. Wpisz nową wartość.  
  
    > [!CAUTION]
    >  Zmiana wartości rejestru (szczególnie w rejestrach EIP i EBP) może wpłynąć na działanie programu.  
  
    > [!CAUTION]
    >  Edytowanie wartości zmiennoprzecinkowych może spowodować pomocnicza niezgodnościami z powodu konwersji dziesiętnych do pliku binarnego części ułamkowe. Nawet pozornie nieszkodliwe edycji może spowodować zmiany do niektórych najmniej znaczące bity w rejestrze zmiennoprzecinkowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)

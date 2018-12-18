---
title: 'Porady: Edytowanie wartości rejestru | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d0337f7c77d1ed601c7a6c13c702f4758cbfdbd
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257087"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Porady: Edytowanie wartości rejestru (C#, C++, Visual Basic F#)

Okno rejestrów jest dostępna tylko wtedy, gdy debugowanie na poziomie adresów jest włączone w **opcje** okno dialogowe **debugowanie** węzła.  
  
### <a name="to-change-the-value-of-a-register"></a>Aby zmienić wartość rejestru  
  
1.  W **rejestruje** okna, użyj klawisza TAB lub myszy do wstawiania wskaż wartość, aby zmienić. Po rozpoczęciu wpisywania kursor musi znajdować się przed wartością, którą chcesz zastąpić.  
  
2.  Wpisz nową wartość.  
  
    > [!CAUTION]
    >  Zmiana wartości rejestru (szczególnie w rejestrach EIP i EBP) może wpłynąć na działanie programu.  
  
    > [!CAUTION]
    >  Edytowanie wartości zmiennoprzecinkowych może spowodować pomocnicza niezgodnościami z powodu konwersji dziesiętnych do pliku binarnego części ułamkowe. Nawet pozornie nieszkodliwe edycji może spowodować zmiany do niektórych najmniej znaczące bity w rejestrze zmiennoprzecinkowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)
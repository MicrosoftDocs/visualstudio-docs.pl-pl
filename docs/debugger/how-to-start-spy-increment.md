---
title: 'Instrukcje: Uruchom narzędzie Spy ++ | Dokumentacja firmy Microsoft'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84e16c5d540aa59ae0c5d56ccb311618ab311bd9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993460"
---
# <a name="how-to-start-spy"></a>Instrukcje: Uruchamianie programu Spy++

Można uruchomić programu Spy ++ w programie Visual Studio lub w wierszu polecenia.  
  
 Po uruchomieniu programu Spy ++, jeśli zostanie wyświetlony komunikat o uprawnienia do wprowadzania zmian do komputera, wybierz opcję **tak**.  
  
> [!NOTE]
>  Można uruchomić tylko jedno wystąpienie programu Spy ++. Jeśli zostanie podjęta próba uruchomienia drugiego wystąpienia, powoduje po prostu aktualnie uruchomione wystąpienie, którego można pobrać fokus.

## <a name="prerequisites"></a>Wymagania wstępne

Spy ++ wymaga następujących składników. Możesz wybrać te składniki z Instalatora programu Visual Studio, wybierając **poszczególne składniki** kartę, a następnie wybierając następujące składniki.

* W obszarze debugowania i testowania, zaznacz **narzędzia profilowania dla języka C++**
* W obszarze działań programistycznych, wybierz **podstawowe funkcje programu Visual Studio C++**

Jeśli zostały wprowadzone zmiany, postępuj zgodnie z monitami, aby zainstalować te składniki.
  
## <a name="start-spy-from-visual-studio"></a>Uruchom narzędzie Spy ++ w programie Visual Studio
  
Na **narzędzia** menu, wybierz opcję **Spy ++**.  
  
Fakt, że narzędzie Spy ++ działają niezależnie, po jego uruchomieniu możesz zamknąć program Visual Studio.  
  
> [!NOTE]
>  Podczas rejestrowania komunikatów z programem Spy ++, może to spowodować systemu operacyjnego działać wolniej.  
  
## <a name="start-spy-at-a-command-prompt"></a>Uruchom narzędzie Spy ++ w wierszu polecenia  
  
1.  W oknie wiersza polecenia Zmień katalogi na folder, który zawiera spyxx.exe. Zazwyczaj jest ścieżka do tego folderu... \\ *Folder instalacji programu visual Studio*\Common7\Tools\\.  
  
2.  Enter **spyxx.exe**. 
  
## <a name="see-also"></a>Zobacz także  
 [Korzystanie z programu Spy ++](../debugger/using-spy-increment.md)   
 [Widoków programu Spy ++](../debugger/spy-increment-views.md)   
 [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)
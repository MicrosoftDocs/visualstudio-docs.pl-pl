---
title: Debuger nie może wyświetlić kodu źródłowego lub demontażu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce4460aecb634523de02f2e3f6929b206b415e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186495"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd odczytuje:  
  
 Debuger nie może wyświetlić kodu źródłowego lub odasemblowania dla bieżącej lokalizacji, w której wykonywanie zostało zatrzymane.  
  
 Ten komunikat o błędzie może wystąpić z kilku powodów:  
  
- Być może osiągnięto punkt przerwania w lokalizacji, dla której nie ma kodu źródłowego, podczas debugowania języka, który nie obsługuje demontażu. Otwórz okno **punkty przerwania** , Znajdź punkt przerwania i usuń go.  
  
- Jeśli debugujesz skrypt, być może osiągnięto punkt przerwania, gdy w programie nie było wątków. Wybierz pozycję **krok** lub **Kontynuuj** z menu **Debuguj** , aby wznowić debugowanie.  
  
- Zagadnienia dotyczące zabezpieczeń mogły uniemożliwić odczytywanie informacji o stosie, wątkach, rejestrowaniu i innych kontekstach z debugowanego programu. Najprawdopodobniej dzieje się tak, jeśli debugujesz aplikację sieci Web i nie masz odpowiednich uprawnień, aby uzyskać dostęp do katalogu wirtualnego. Ustaw dla katalogu wirtualnego zabezpieczenia anonimowe i spróbuj ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)

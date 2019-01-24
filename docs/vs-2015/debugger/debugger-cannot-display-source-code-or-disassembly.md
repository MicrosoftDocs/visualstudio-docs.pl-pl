---
title: Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2b197785cee0250959e26726b1a81a48bb15049a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760484"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Odczytuje ten błąd:  
  
 Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji dla bieżącej lokalizacji, w którym wykonywanie zostało zatrzymane.  
  
 Ten komunikat o błędzie może wystąpić z kilku powodów:  
  
-   Możesz przekroczyć punkt przerwania w lokalizacji, dla których nie ma żadnych kodu źródłowego podczas debugowania języka, który nie obsługuje dezasemblacji. Otwórz **punktów przerwania** oknie zlokalizować punkt przerwania i usuń go.  
  
-   Jeśli debugujesz skryptu możesz przekroczyć punkt przerwania podczas, gdy nie było żadnych wątków w programach. Wybierz **kroku** lub **Kontynuuj** z **debugowania** menu, aby wznowić debugowanie.  
  
-   Zagadnienia dotyczące zabezpieczeń może uniemożliwić debugera na podstawie odczytu stosu, wątek, zarejestruj się i innymi informacjami kontekstu z programu, który debugujesz. Jest to najbardziej prawdopodobne w przypadku debugowania aplikacji sieci Web i nie mieć odpowiednich uprawnień dostępu do katalogu wirtualnego. Ustawienia zabezpieczeń katalogu wirtualnego na anonimowe i spróbuj ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)

---
title: Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe3d745622666bd6458d5c3de916bc7b7787292e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916464"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji
Odczytuje ten błąd:  
  
 Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji dla bieżącej lokalizacji, w którym wykonywanie zostało zatrzymane.  
  
 Ten komunikat o błędzie może wystąpić z kilku powodów:  
  
-   Możesz przekroczyć punkt przerwania w lokalizacji, dla których nie ma żadnych kodu źródłowego podczas debugowania języka, który nie obsługuje dezasemblacji. Otwórz **punktów przerwania** oknie zlokalizować punkt przerwania i usuń go.  
  
-   Jeśli debugujesz skryptu możesz przekroczyć punkt przerwania podczas, gdy nie było żadnych wątków w programach. Wybierz **kroku** lub **Kontynuuj** z **debugowania** menu, aby wznowić debugowanie.  
  
-   Zagadnienia dotyczące zabezpieczeń może uniemożliwić debugera na podstawie odczytu stosu, wątek, zarejestruj się i innymi informacjami kontekstu z programu, który debugujesz. Jest to najbardziej prawdopodobne w przypadku debugowania aplikacji sieci Web i nie mieć odpowiednich uprawnień dostępu do katalogu wirtualnego. Ustawienia zabezpieczeń katalogu wirtualnego na anonimowe i spróbuj ponownie.  
  
## <a name="see-also"></a>Zobacz też
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
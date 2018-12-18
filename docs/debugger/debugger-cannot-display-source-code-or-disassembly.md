---
title: Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea95a2bb4c29f8a23fd597173a10a838baca051c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063969"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji
Odczytuje ten błąd:  
  
 Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji dla bieżącej lokalizacji, w którym wykonywanie zostało zatrzymane.  
  
 Ten komunikat o błędzie może wystąpić z kilku powodów:  
  
-   Możesz przekroczyć punkt przerwania w lokalizacji, dla których nie ma żadnych kodu źródłowego podczas debugowania języka, który nie obsługuje dezasemblacji. Otwórz **punktów przerwania** oknie zlokalizować punkt przerwania i usuń go.  
  
-   Jeśli debugujesz skryptu możesz przekroczyć punkt przerwania podczas, gdy nie było żadnych wątków w programach. Wybierz **kroku** lub **Kontynuuj** z **debugowania** menu, aby wznowić debugowanie.  
  
-   Zagadnienia dotyczące zabezpieczeń może uniemożliwić debugera na podstawie odczytu stosu, wątek, zarejestruj się i innymi informacjami kontekstu z programu, który debugujesz. Jest to najbardziej prawdopodobne w przypadku debugowania aplikacji sieci Web i nie mieć odpowiednich uprawnień dostępu do katalogu wirtualnego. Ustawienia zabezpieczeń katalogu wirtualnego na anonimowe i spróbuj ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md) [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)